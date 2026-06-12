---
title: "Suspend/Hibernate/Resume/Thaw - Scripts"
date: 2013-06-25
forum: General Help
---

### Post by stbluesrul on 2013-06-25
I need to run a script on a Suspend/Hibernate and on a Resume/Thaw.  Now, I know the place to put the script is /etc/pm/sleep.d/ but this doesn't seem to work for a script requiring access to the network as the network is either already down or not up yet when it runs.  Is there another place I need to put my script so it has access to the network before the network is shutdown on a suspend and after the network is up on a resume?

Basically, I just need to send out a UDP broadcast like:

echo -n "Resumed" | socat - udp-datagram:192.168.5.255:5100,broadcast

I'm running ubuntu 11.10.

---

### Post by Toz on 2013-06-26
Hello and welcome to the forums.

Have a look at the /etc/network/if-up.d directory. These scripts run after the interface comes up.

---

### Post by stbluesrul on 2013-06-26
Thanks for the reply.  I'll give that a try.  

What about for a suspend, before the network is brought down?

---

### Post by Toz on 2013-06-26
> **stbluesrul said:**
> What about for a suspend, before the network is brought down?
I believe that when the system resumes and the network interface is brought back up, the same scripts in /etc/network/if-up.d will be re-run.

---

### Post by stbluesrul on 2013-06-28
[FONT=arial]Ok, the script in /etc/network/if-up.d worked great when it boots up or resumes.

Now I just need to know where to put a script so I can send out a network message that the PC is being Suspended or Hibernated.

Like:
[/FONT][COLOR=#000000]echo -n "Hibernating" | socat - udp-datagram:192.168.5.255:5100,broadcast

I see there are other scripts in /etc/network.  I tried /etc/network/if-down.d but that didn't work.  Anything else I can try?[/COLOR]

---

### Post by Toz on 2013-06-28
> Now I just need to know where to put a script so I can send out a network message that the PC is being Suspended or Hibernated.

You could put that in /etc/pm/sleep.d as 01_socat (before the network is taken down). The file should look like:
```

case $1 in
     suspend|suspend_hybrid|hibernate)
	echo -n "Hibernating" | socat - udp-datagram:192.168.5.255:5100,broadcast
        ;;
     resume|thaw)
	# Do nothing, handled by /etc/network/if-up.d
        ;;
esac
```
Make this file executable.

---

### Post by stbluesrul on 2013-06-28
This doesn't seem to work as the network is already taken down.  I verified that the script is in fact working by just having it create a directory on the desktop but it doesn't send out the broadcast.

echo -n "Hibernating" | socat - udp-datagram:192.168.5.255:5100,broadcast

works correctly when I run it in my other script and through the terminal.

Is there a place that lists exactly what is executed when a hibernate or suspend is done?

---

### Post by Toz on 2013-06-28
> Is there a place that lists exactly what is executed when a hibernate or suspend is done? 

/var/log/pm-suspend.log will show it. Perhaps you can post the log back for a look:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by stbluesrul on 2013-06-29
Here is the link:

[http://paste.ubuntu.com/5811441/](http://paste.ubuntu.com/5811441/)

I even tried putting the socat command into /usr/lib/pm-utils/sleep.d/000kernel-change as it seems this is the first script that is ran on a suspend but again the network is already down when it executes.

---

### Post by Toz on 2013-06-29
The earliest place you could put this during a suspend cycle would be before 000kernel-change, say 0000socat. If that doesn't work, then the suspend scripts can't be used because the network is unavailable at the time those scripts are being run.

I came across this code in /etc/NetworkManager/dispatcher.d/01ifupdown:
```
# pre-up/pre-down not implemented. See
# https://bugzilla.gnome.org/show_bug.cgi?id=387832
#    pre-up)
#	export MODE="start"
#	export PHASE="pre-up"
#	exec run-parts /etc/network/if-pre-up.d
#	;;
#    pre-down)
#	export MODE="stop"
#	export PHASE="pre-down"
#	exec run-parts /etc/network/if-down.d
#	;;

```
This would be ideal for you (pre-down) but as you can see, the code is commented out and if you read the bug report, there is some reluctance to include that functionality.

---

### Post by stbluesrul on 2013-06-29
Do you know what is first called when you click "Suspend"?  Or is there another set of scripts I could look in, since it looks like suspend scripts aren't going to work for me?

And looking at the log there is:
```

Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.
```

Where NetworkManager tries to put the interfaces to sleep but fails becauses the network is already down.  Is there something else that is taking down the network?  Since it doesn't seem to be NetworkManager that is doing it.  Likewise, the same thing happens when it resumes.  NetworkManager tries to wake the interfaces but they have already been brought up.

```

Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.
```

---

### Post by Toz on 2013-06-29
I get those error messages as well, along with a shopt error as of 13.04 (there is a bug report for it). Doesn't seem to affect the sleep process though.

[Here is a link]("https://help.ubuntu.com/community/HibernateWhatHappens"), a little dated, but explains the process from clicking hibernate/suspend to actualy hibernate/suspend. I don't see another layer in that process that you can hook in to.

However, here is a suggestion. Ultimately, /usr/sbin/pm-suspend is called. You could rename /usr/sbin/pm-suspend to /usr/sbin/pm-suspend.real and create your own /usr/sbin/pm-suspend that first runs your script, then calls /usr/sbin/pm-suspend.real to continue with the suspend process:
```

#!/bin/bash
echo -n "Hibernating" | socat - udp-datagram:192.168.5.255:5100,broadcast
sleep 1   # in case you need to pause the process - tailor as needed
/usr/sbin/pm-suspend.real
```

The one thing to keep in mind is that if the pm-utils package every gets updated, this file will get replaced and you'll need to re-create it.

---

### Post by stbluesrul on 2013-06-30
Ok, I've tried this and it's hit and miss, mostly miss.  Something else takes down the network.  However, /usr/sbin/pm-suspend.real doesn't seem to run.  This got me to thinking, though.  What if I just restart the network services.  So I did this:

```
#!/bin/bash


sleep 3
sudo service network-manager restart 
sleep 4
echo "OFF" | socat - udp-datagram:192.168.5.255:5100,broadcast
sudo service network-manager stop


/usr/sbin/pm-suspend.real

```

This works, however, again I have the same problem of /usr/sbin/pm-suspend.real isn't getting ran.  I also tried changing it to the actual script which is /usb/lib/pm-utils/bin/pm-action which also doesn't seem to get called.

---

### Post by Toz on 2013-06-30
Are entries being made into /var/log/pm-suspend.log? If so, /usr/sbin/pm-suspend.real is being run, just not successful.

Also, try without the last network-manager stop command, it will be done automatically:
```
#!/bin/bash

sleep 3
service network-manager restart 
sleep 4
echo "OFF" | socat - udp-datagram:192.168.5.255:5100,broadcast

/usr/sbin/pm-suspend.real
```
Note: sudo is not needed in the script because it will be run as root.

---

### Post by stbluesrul on 2013-07-05
Ok, so I've finally got a solution.


In /etc/pm/sleep.d/ I have a script do the following:
```

case "$1" in
        hibernate|suspend)
        sleep 3
        service network-manager restart
        sleep 3
        echo "HIBERSUSP" | socat - udp-datagram:192.168.5.255:5100,broadcast
                ;;
        thaw|resume)
        service network-manager restart
        echo "RESUMETHAW" | socat - udp-datagram:192.168.5.255:5100,broadcast
                ;;
        *)
                ;;
esac

exit $?

```


It brings the network back up and sends out a broadcast message when the PC is going down for a suspend or hibernation.  On a resume or thaw it brings up the network and sends a broadcast that the PC is back online.


Next I added a login and logout script:
The login and logout scripts are on the desktop. Then in /etc/lightdm/lightdm.conf add the following:
```

session-cleanup-script=/home/xbmc/Desktop/00socatlogout
session-setup-script=/home/xbmc/Desktop/00socatlogin

```
The logout script looks like the following:
```

echo "LOGOUT" | socat - udp-datagram:192.168.5.255:5100,broadcast

```
Login script:
```

echo "LOGIN" | socat - udp-datagram:192.168.5.255:5100,broadcast

```


Now when the PC shutdown, suspended, or hibernated a broadcast message is sent out. Likewise, when the PC is started up, resumed, or coming out of hibernate another message is sent out that it is back online.

---

### Post by Toz on 2013-07-05
Great. Thanks for sharing. This can potentially be useful information for others. Can you please mark this thread solved using the istructions from the link in my signature so that it is easier for others to find?
Thanks.

---

### Post by stbluesrul on 2013-07-05
Just did.  Many thanks for the quick replies and help!

---

