---
title: "I've broken my linux OS"
date: 2008-04-10
forum: General Help
---

### Post by miansaab on 2008-04-10
Hi,

I think I have done irreparable damage to my OS (Gutsy). I was following the instructions found on the following links to change drive permissions after which my **internet** and **sudo** stopped working. 

[http://ubuntuforums.org/showthread.php?t=543477](http://ubuntuforums.org/showthread.php?t=543477)

[http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

Before I tried the following remedies to no success, I was getting an error 'sudo: must be setuid root' whenever I tried sudo:

chown root:root /usr/bin/sudo
chmod 4111 /usr/bin/sudo
chmod 4755 /usr/bin/sudo
chmod 0440 /etc/sudoers

After trying these I get the following message when I try sudo:

sudo: /etc/sudoers is owned by uid 1000, should be 0

atif@Brisbane:~$ sendmail: fatal: open /etc/postfix/main.cf: No such file or directory.

When I type in 'ls -l /usr/bin/sudo' I get:

-rwsr-xr-x l atif atif 91776 2007-06-15 08:49 /usr/bin/sudo

Please help! I have tried alot of the things posted on forums but have had no success.

Thanks

---

### Post by Rocket2DMn on 2008-04-10
OK we'll try and repair what you've done in those four commands.  
First I want you to post the output of these commands:
```
ls -l /usr/bin/sudo
ls -l /etc/sudoers
```
Then reboot into the recovery kernel from the GRUB menu (second entry).  Then run
```
chown root:root /usr/bin/sudo
chown root:root /etc/sudoers
reboot
```
Give that a try to see if it gets you back on track, otherwise post back with as much error output as you can, including the command you issued.

---

### Post by kevin1780 on 2008-04-11
I'm in a similar situation. I chowned /usr when trying to install Java (which I still can't do).

I type: ls -l /usr/bin/sudo
I get:    ---s--x--x 1 kevin root 122560 2008-02-25 06:28 /usr/bin/sudo

I type:  ls -l /etc/sudoers
I get:    -r--r----- 1 root root 470 2008-04-07 00:19 /etc/sudoers

When I try:  chown root:root /usr/bin/sudo
I get:   changing ownership of `/usr/bin/sudo': Operation not permitted

This is when I restart in "fail safe GNOME"

Please help.

---

### Post by Rocket2DMn on 2008-04-11
kevin, try rebooting into the recovery kernel (the second option at the GRUB menu) and running the following commands
```
chown -R root:root /usr
chmod 4755 /usr/bin/sudo
```
Then you can reboot normally
```
reboot
```
Hopefully that will fix your problem, otherwise post back with more errors.  Your executables may have gotten screwed up when you ran the chown command.  You may have to reinstall, but we'll try our best to avoid that.

---

### Post by ryanhaigh on 2008-04-11
There is a way to copy only the permissions of files and apply those to a matching set I did it once when I screwed up a debian install, it got me back to a usable system and I recovered my data/configs but after using it for a while it was just easier to reinstall.

---

### Post by miansaab on 2008-04-11
> **Rocket2DMn said:**
> OK we'll try and repair what you've done in those four commands.  
First I want you to post the output of these commands:
```
ls -l /usr/bin/sudo
ls -l /etc/sudoers
```
Then reboot into the recovery kernel from the GRUB menu (second entry).  Then run
```
chown root:root /usr/bin/sudo
chown root:root /etc/sudoers
reboot
```
Give that a try to see if it gets you back on track, otherwise post back with as much error output as you can, including the command you issued.

Hey Rocket I tried what you stated and I get the following messages before doing the chown commands:

For ```
ls -l /usr/bin/sudo
```

```
-rwsr-xr-x 1 root root 91776 2007-06-15 08:49 [COLOR="Red"]/usr/bin/sudo[/COLOR]
```

For ```
ls -l /etc/sudoers
```

```
-r--r----- 1 atif atif 496 2008-02-23 05:41 /etc/sudoers
```

After I tried your suggested diagnostic, I get:

For ```
ls -l /usr/bin/sudo
```

```
-rwxr-xr-x 1 root root 91776 2007-06-15 08:49 [COLOR="Lime"]/usr/bin/sudo[/COLOR]
```

And for ```
ls -l /etc/sudoers
```

```
-r--r----- 1 root root 496 2008-02-23 05:41 /etc/sudoers
```

Now when I try to do a sudo command, say ```
sudo apt-get update
```, I get:

```
sudo: must be setuid root
```

And when I try ```
su
```, then I get:

```
setgid: Operation not permitted
```

I should also mention that when I was following the guide on the above two links I put in hdb1 (or hdb3, can't remember)into the ```
/dev/hda5 /storage ext3 defaults 0 0
``` command and my hdb1 (or hdb3) was actually my root drive, the one with Ubuntu installed. Also I cannot acccess my other drive anymore. Other partitions are visible in My Computer but I guess they do not mount because when I click them I get directed to my root drive. So I guess I can't mount my other drive either now alongside my internet which is not working.

Hope this gives you more insight on the problem.

---

### Post by Rocket2DMn on 2008-04-11
OK, you shouldn't be using sudo from the recovery kernel for starters.  Permissions are wrong on /usr/bin/sudo so run (from the recovery kernel)
```
chmod 4755 /usr/bin/sudo
```
I'm unclear about your othe problem, did you change the mount point in fstab of the root filesystem?

---

### Post by miansaab on 2008-04-11
Rocket, I tried the diagnostic suggested in your last post and finally sudo is working again. Thanks.

Also my other drive mounts now so that is good. But my internet is still not working. I also cannot access su from my account in terminal.

When I type ```
su
``` I get ```
setgid: Operation not permitted
```

Please help me get my internet back.

Lastly, below is the exact readout of my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd2
UUID=169404a8-0b52-454f-9715-2c4803f1a8f9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd1
UUID=E4707ED5707EADC4 /media/hdd1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdd3
UUID=0845ccad-ced7-43f1-a5b7-56877e4a89fc none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Again, thanks for helping me get sudo working.

---

### Post by Rocket2DMn on 2008-04-12
For su, try running (from a normal boot, since sudo is working)
```
sudo chmod 4755 /bin/su
```

I'm not really sure what to do about your internet, let's just see if it works after this.  You're lucky that your system is still working at all.  If troubleshooting your wireless doesn't work out very well, it may be easier to just back up your data and do a reinstall of Ubuntu (since it worked before, right?).
Is your internet connection wired or wireless?

---

### Post by miansaab on 2008-04-12
I tried sudo ```
chmod 4755 /bin/su
``` but su is still not back, I am getting the same message ```
setgid: Operation not permitted.
```

My computer is wired to my router and I have cable internet. It works if I put in live CD but it still isn't working on my hard disk install.

---

### Post by Rocket2DMn on 2008-04-12
> **miansaab said:**
> I tried sudo ```
chmod 4755 /bin/su
``` but su is still not back, I am getting the same message ```
setgid: Operation not permitted.
```

My computer is wired to my router and I have cable internet. It works if I put in live CD but it still isn't working on my hard disk install.

I think it would be easiest to just reinstall.  You may consider waiting for Hardy which will be release in less than two weeks, but it's up to you.  I'm afraid that even if we fix su and the internet, more problems will surface because of what you initially did to screw up the system.

---

### Post by jocko on 2008-04-12
When you changed permission on your drives, do you mean you changed permission on your entire "/" partition? In that case a reinstall is your only simple option. A reinstall takes maybe 20-40 minutes (plus installing extra programs you want), while figuring out exactly how to fix the permissions for every individual file would probably take weeks...
Just make a backup of your home directory (including hidden files) first if you want to be able to restore your personal settings for every program (or even better make a separate /home partition)

---

### Post by miansaab on 2008-04-13
Yeah, I was also thinking that I should wait for Hardy. Anyways thanks for all your help guys.

---

