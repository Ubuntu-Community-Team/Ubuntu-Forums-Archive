---
title: "Sudo problem"
date: 2014-05-07
forum: General Help
---

### Post by josephdaniel2 on 2014-05-07
I was trying to build [Atom]("http://github.com/atom/atom") and I failed but then I also screwed things up trying to build it.
Whenever I type any sudo command I get this "sudo: effective uid is not 0, is sudo installed setuid root?". 
How do I fix it ?
Any help will be appreciated 
Thank you!   

Additional info:
Ubuntu 13.10 32-bit

---

### Post by Impavidus on 2014-05-07
Something must be wrong with the ownership or permissions of sudo. Run```
ls -l /usr/bin/sudo
```to check. In my case it's```
-rwsr-xr-x 1 root root 155008 feb 10 20:16 /usr/bin/sudo
```If permissions or owner are different in your case, boot into recovery mode and fix it.```
#To mount the file system rw
mount -o rw,remount /
#To fix permissions (if applicable)
chmod 4755 /usr/bin/sudo
#To fix ownership (if applicable)
chown root:root /usr/bin/sudo
```

However, without knowing the cause of this problem, chances are that more can be broken. Better to check. Are there more files in /usr/bin with strange owner or permissions? These problem can quickly grow out of hand, making recovery almost impossible.

---

### Post by josephdaniel2 on 2014-05-07
I got this ```
 -rwsr-xr-x 1 grumpycat root 123328 Mar 11 17:56 /usr/bin/sudo
``` when I ran ```
[COLOR=#000000][FONT=Ubuntu Mono]ls -l /usr/bin/sudo[/FONT][/COLOR]
```. I am bit of a noob so how do I see if files in '[COLOR=#000000]/usr/bin[/COLOR]' have weird permissions ? I will now get into GRUB and try it and come back to you :)
Thank you!

---

### Post by josephdaniel2 on 2014-05-07
I tried the way you said and it still doesn't work :( But, sudo did work in the GRUB root terminal not quite sure why it doesn't work in the normal one :confused:

---

### Post by deadflowr on 2014-05-07
> **josephdaniel2 said:**
>  I am bit of a noob so how do I see if files in '[COLOR=#000000]/usr/bin[/COLOR]' have weird permissions ? 

Run
```
ls -l /usr/bin
```
will list all the files inside that directory, with both the permissions and ownership.
> **josephdaniel2 said:**
> I tried the way you said and it still doesn't work :( But, sudo did work in the GRUB root terminal not quite sure why it doesn't work in the normal one :confused:

When in root, sudo become moot, since sudo invokes root.

But in the recovery mode, did you follow the remount command?

---

### Post by josephdaniel2 on 2014-05-08
Yes, I did use ```
[COLOR=#000000][FONT=Ubuntu Mono]mount -o rw,remount /[/FONT][/COLOR]
``` I pasted what I got from "[COLOR=#000000][FONT=Ubuntu Mono]ls -l /usr/bin"[/FONT][/COLOR] [here]("http://pastebin.com/3kLDAQe4")

---

### Post by deadflowr on 2014-05-08
Your ownership problems seem to go beyond just the /usr.bin/sudo file.
That whole directory is owned by grumpycat.
(well except /usr/bin/sudo, ironically)

I wonder if it goes even further up the chain
What's the output of both
```
ls -l /usr
```
and
 ```
ls -l /
```

The permissions themselves, seem fine.
BTW

---

### Post by josephdaniel2 on 2014-05-08
I pasted the output [here]("http://pastebin.com/MqBWwVS4").

---

### Post by Impavidus on 2014-05-08
First of all,```
#From your post
-rw[COLOR=#ff0000]**s**[/COLOR]r-xr-x 1 grumpycat root        123328 Mar 11 17:56 /usr/bin/sudo
#From the long output
-rw[COLOR=#ff0000]**x**[/COLOR]r-xr-x 1 root      root        123328 Mar 11 17:56 sudo
```I see that you somehow also lost the setuid bit now. Have you tried chmodding the entire directory?

For some reason you chowned the entire /usr/bin directory. Luckily the groups are still correct and all files should be owned by root, so this can be fixed. Boot into recovery mode, remount the file system rw and run this command:```
chown -R root /usr/bin
```

This is not a full fix yet, as I see you now somehow lost your setuid and setgid bits. These have to be fixed manually and one by one.```
#To add the setuid bit
chmod 4755 /usr/bin/filename

#To set the setgid bit
chmod 2755 /usr/bin/filename

#To set both the setuid bit and the setgid bit
chmod 6755 /usr/bin/filename
```

On my system the following files in /usr/bin have the setuid bit:```
chfn
chsh
gpasswd
lppasswd
mtr
newgrp
passwd
pkexec
sudo
traceroute6.iputils
```The following have the setgid bit:```
bsd-write
chage
crontab
dotlockfile
expiry
mail-lock
mail-touchlock
mail-unlock
mlocate
ssh-agent
wall
```And this one has both (note the capital letter):```
X
```Your system however may be different.

You're getting close to the point where reinstalling is the fast way out.

As to the cause of all this, I see a file named Torrent-Video-Player, belonging to your group and created yesterday, so I think that you chowned the directory to give yourself write access to copy that file there. That's not the right way. Better is to give yourself temporary root access with sudo to get the right to copy the file. Or even better, don't copy things there manually, but leave the /usr/bin directory only for files installed via the package manager. If you want to install something manually, put it in /usr/local/bin/.

---

### Post by josephdaniel2 on 2014-05-08
Alright, I guess I will be re-installing Ubuntu then. Thank you for your time and effort both of you :p I will mark this thread as solved.

---

