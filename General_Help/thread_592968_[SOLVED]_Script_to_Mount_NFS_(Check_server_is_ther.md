---
title: "[SOLVED] Script to Mount NFS (Check server is there first)"
date: 2007-10-26
forum: General Help
---

### Post by blueorder on 2007-10-26
Hey y'all...

Pretty new to this scripting thing and was looking for some help with this.

I am looking to setup a script that first checks to see if the NFS server is there before mounting the NFS shares. This would be very helpful if the server is off and I wan't to use the client.

I remember seeing something to the effect that first pinged the server and did something with it but search provided no answers.

Thanks for you help...

---

### Post by kast on 2007-10-26
well i guess a simple way would be a little if statement

**#!/bin/sh**

 
# check to see if your NFS is mounted
# : means if your NFS is there then doing nothing
# if its not then mount your NFS
[B]
if [ -e /media/nfs ]        
then   :
            exit 1
else 
           Mount command
fi[/B]

---

### Post by blueorder on 2007-10-27
> **kast said:**
> well i guess a simple way would be a little if statement

**#!/bin/sh**

 
# check to see if your NFS is mounted
# : means if your NFS is there then doing nothing
# if its not then mount your NFS
[B]
if [ -e /media/nfs ]        
then   :
            exit 1
else 
           Mount command
fi[/B]

First, thanks for the reply.

That's almost what I need. The only other thing I would need in the script would be a check to make sure the server is there first.

THe issue is that if I try to log in with the NFS mount commands in fstab and the server is not there (it's off or offline for whatever reason) the NFS mount command for a server that is not there slows down the system a lot specially during login and sometimes doesn't even mount my second hard drive.

---

### Post by kast on 2007-10-27
# *if the ping command returns a "0 received" then we assume server down *
# *we then do nothing, because there inst a way to mount that NFS*
# *if we don't get the "0"  in received then we assume it already up and then run the Mount *
[B]
#!/bin/sh

if [ "$(ping -c 3 192.168.1.1 | grep '0 received')" ]
then 
          : ; exit 1

else
          Continue with the mount process
fi[/B]

You could obviously do more if the command did determine the server was down, like email you etc.... not just do nothing and exit. :) if you plan on needed visual feed back then an echo command would be useful something like echo "server is no up" etc....

you could also put this in a loop with say  a "while" statement then just put in a sleep 120 (or for how ever long) while the server is down, then once its up run the mount

---

### Post by blueorder on 2007-10-27
> **kast said:**
> # *if the ping command returns a "0 received" then we assume server down *
# *we then do nothing, because there inst a way to mount that NFS*
# *if we don't get the "0"  in received then we assume it already up and then run the Mount *
[B]
#!/bin/sh

if [ "$(ping -c 3 192.168.1.1 | grep '0 received')" ]
then 
          : ; exit 1

else
          Continue with the mount process
fi[/B]

You could obviously do more if the command did determine the server was down, like email you etc.... not just do nothing and exit. :) if you plan on needed visual feed back then an echo command would be useful something like echo "server is no up" etc....

you could also put this in a loop with say  a "while" statement then just put in a sleep 120 (or for how ever long) while the server is down, then once its up run the mount

Thanks for all your help. I was able to take what you posted and do a little bit more searching and came up with the following:
```

#!/bin/bash

# if the ping command returns a "0 received" then we assume server down
# we then do nothing, because there inst a way to mount that NFS
# if we don't get the "0" in received then we assume it already up and then run the Mount

if [ "$(ping -c 3 blueserv | grep '0 received')" ]
then
	: ; exit 1
else
	# check to see if your NFS is mounted
	# : means if your NFS is there then doing nothing
	# if its not then mount your NFS

	if df | grep -q 'blueserv:/mnt/raid1/Audio'
	then :
	else
		mount -t nfs blueserv:/mnt/raid1/Audio /media/Audio
	fi

	if df | grep -q 'blueserv:/mnt/raid1/Pictures'
	then :
	else
		mount -t nfs blueserv:/mnt/raid1/Pictures /media/Pictures
	fi

	if df | grep -q 'blueserv:/mnt/raid1/Video'
	then :
		exit 1
	else
		mount -t nfs blueserv:/mnt/raid1/Video /media/Video
	fi
fi

```

I had to change the **-e** commands to check the mountings because even if it is not mounted the directory still exists in **/media**.

Is this kosher?

Where would be the best place to put this script? Should I just copy it to **/etc/init.d/** and run:
```

sudo update-rc.d script_name defaults

```

I already made it executable.

Thanks again...

---

### Post by kast on 2007-10-27
looks good, i'm sure we can clean it up a bit,  but if it work, it works! 

as for where to put the script i put them in /usr/local/bin then use crontab to schedule when it should run

But your way might be better for your purpse.

---

### Post by blueorder on 2007-10-27
> **kast said:**
> looks good, i'm sure we can clean it up a bit,  but if it work, it works! 

as for where to put the script i put them in /usr/local/bin then use crontab to schedule when it should run

But your way might be better for your purpse.

The script works as advertised but when I used update-rc.d to include the script at bootup my mouse stopped working...hahaha

I'll mark it solved and thanks again for your help. Now to get the nfs-mounting and my mouse to play nice.

---

### Post by kast on 2007-10-27
glad to hear it! 

Ill be looking for a new post from you about your mouse :)

---

### Post by blueorder on 2007-10-27
> **kast said:**
> glad to hear it! 

Ill be looking for a new post from you about your mouse :)

UPDATE: stopped trying to use update-rc.d and just copied the script to **/usr/bin** and added the script to **/etc/rc.local**

Any difference between having it in **/usr/local/bin** or **/usr/bin**?

Everything good now...

---

### Post by kast on 2007-10-27
The Localists Fallacy

The problem is simply that in this day and age, /usr/local/bin suffers from the same problem that /usr/bin has. Anything you get from the net invariably installs to /usr/local/bin. At the time I wrote this article, my /usr/local/bin had 560 files in it- and most of them aren't really "local"- somebody else wrote them, I just installed them. When I upgrade, I usually have to upgrade those things also. So every argument against putting your home grown scripts in /usr/bin applies just as much to /usr/local/bin- same problems, same arguments.

Therefor, I suggest that you put your home grown scripts in your own directory structure: /usr/mystuff/bin or whatever, and further that you NEVER assume that it is in $PATH in calling scripts, but rather call it explicitly: /usr/mystuff/bin/whatever. This prevents the theft of "whatever" by another set of programs, and if some person upgrades the server years from now when you are long gone, and does not notice /usr/mystuff/bin, the calling scripts failure will immediately point them to the remedy.

Source 
[http://aplawrence.com/Opinion/religion.html](http://aplawrence.com/Opinion/religion.html)

---

### Post by blueorder on 2007-10-27
> **kast said:**
> The Localists Fallacy

The problem is simply that in this day and age, /usr/local/bin suffers from the same problem that /usr/bin has. Anything you get from the net invariably installs to /usr/local/bin. At the time I wrote this article, my /usr/local/bin had 560 files in it- and most of them aren't really "local"- somebody else wrote them, I just installed them. When I upgrade, I usually have to upgrade those things also. So every argument against putting your home grown scripts in /usr/bin applies just as much to /usr/local/bin- same problems, same arguments.

Therefor, I suggest that you put your home grown scripts in your own directory structure: /usr/mystuff/bin or whatever, and further that you NEVER assume that it is in $PATH in calling scripts, but rather call it explicitly: /usr/mystuff/bin/whatever. This prevents the theft of "whatever" by another set of programs, and if some person upgrades the server years from now when you are long gone, and does not notice /usr/mystuff/bin, the calling scripts failure will immediately point them to the remedy.

Source 
[http://aplawrence.com/Opinion/religion.html](http://aplawrence.com/Opinion/religion.html)

Interesting read. I've decided, after reading the above to create my own local bin and move th script there. It's owned by the root and I'm calling directly (not in PATH) from /etc/rc.local

I've still got quite a bit to learn about dealing with Linux after leaving the Windows world.

Thanks again...

---

### Post by kast on 2007-10-27
Your welcome! Good luck :)

---

