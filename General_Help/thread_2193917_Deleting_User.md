---
title: "Deleting User"
date: 2013-12-15
forum: General Help
---

### Post by Quarkrad on 2013-12-15
I need to delete a user on my pc but have forgotten the password - have googled and written down procedure via rescue mode at startup, but for some reason rescue mode freezes; all I can do is launch to desktop.  Is there another way to delete this user - **dad2**?   There is nothing stored in the dad2 profile - I just would like this user to be removed from my pc (at the moment pc boots to **dad2** so I have log-off and re log-on to the user I want: **dad**.

---

### Post by bapoumba on 2013-12-15
Removing a user and its files is not a problem. You need to change the auto-login into that user first. But if you have forgotten the password, it will need a little more work. Let me look and try or wait for someone who will know for sure. You do have admin rights to dad, correct ?

Edit : which ubuntu flavor and environment are you using ?

---

### Post by Quarkrad on 2013-12-15
Thanks - I'm using 13.04 and the Unity environment.

---

### Post by bapoumba on 2013-12-15
OK, from the dad account, have a look at the link below and please paste the output to **cat /etc/lightdm/lightdm.conf**
If the file looks similar to the one in the link below or to mine, you can proceed. Do not hesitate to post it here first, before going further. Of course, I do not have autologin, so I'm missing the last line :
```
bapoumba_lxde@SonyBlue:~$ cat /etc/lightdm/lightdm.conf
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter

```

The process will be :
If the last line says autologin-user=dad2, first backup the file :
```
sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm_old.conf 
```
Remove dad2 from the line :
```
sudo nano /etc/lightdm/lightdm.conf 
```
Save and exit : 
ctrl o (letter o) to save
ctrl x to exit.
Logout, and see if you can choose the user dad from the login screen.

[http://askubuntu.com/questions/106428/how-to-disable-automatic-login](http://askubuntu.com/questions/106428/how-to-disable-automatic-login)

Then from the user dad, you can remove dad2 : [https://help.ubuntu.com/10.04/serverguide/user-management.html](https://help.ubuntu.com/10.04/serverguide/user-management.html)

---

### Post by Quarkrad on 2013-12-15
Sorry - I'm going to have to pick this up tomorrow, but I appreciate your help so far.   I have this output from my terminal:

[B]dad@dadubuntu:~$  cat /etc/lightdm/lightdm.conf
[SeatDefaults]
autologin-guest=false
autologin-user=dad2
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter[/B]

I had the **autologin-user=dad2** element so I carried on then got:

[B]dad@dadubuntu:~$ sudo cp /etc/lightdm/lightdm.conf /etc/lightdm/lightdm_old.conf
[sudo] password for dad: 
dad is not in the sudoers file.  This incident will be reported.[/B]

---

### Post by bapoumba on 2013-12-15
This is why I asked if you had admin rights with the dad account.

Is there another account with admin rights on this computer ?

I think that for now, you need to consider the autologin and removal of the dad2 account less of an issue than not having a user with admin rights. So leave the autologin for now, even if it is not going to be of much use if you do not remember the password.

There are ways to change the dad user privileges, but it is not that simple. I would like to make sure you are indeed the owner of both accounts. Please do not get upset, I have no way of knowing if your request is indeed legitimate. I'm not saying it is not, I'm just wondering and would not like to bump some other user outside of their account and give another one admin privileges.

How were the dad and dad2 accounts created ?

---

### Post by Quarkrad on 2013-12-16
I am a home user with a single PC - I have used Ubuntu since 8.04 and evolved to 13.04.  I have always used** dad** as my user name (see my past history on this forum) and still regard myself as a newbie re Linux/Ubuntu admin.  Despite my limited ability admin wise I have convinced about 12 family and friends to convert to Ubuntu - mainly because I use to look after their Windoze machines and in the end got feed up keep having to do re-builds every few years.   All these machines are basically used for email and surfing so 'looking after them' is within my limited capability.  The cause of this present problem was again my ignorance with Ubuntu.  I use a product called Teamviewer to remotely  access these friends/family machines and last week had a problem with different versions (I have Teamviewer v7 and the machine I needed to access had v6).  Because most of the remote machines have v7  I did not want to go down to v6 on my pc so my brain wave was to create another user on my machine (**dad2**) and install v6 on it.  (The remote machine that has v6 on it is the only Windoze machine left &#8211; I put Teamviewer on it a year or so ago).  I created **dad2** using  the gui, System Settings/User Accounts and followed the prompts using my password to unlock where necessary.  All went well (with respect to the issue on the remote pc) and then I found my machine boots to **dad2**.  (I dual boot with Windoze (iTunes only) and use grub/Burg).  I (**dad**) have always been able to do things like **gksudo nautilus** or **sudo su** to get root access after entering my password but now I find **dad** is not in the sudoers file.  This is very frustrating because I'm usually a bit overboard documenting passwords (i.e. the one for dad2) which I didn't this time and I now realise I could have installed Teamviewer V6 and V7 in my **dad** instance and chosen which one to use via the Dash.

---

### Post by Quarkrad on 2013-12-16
Hmm....  I've remebered the password I created for** dad2** so I can now log-off either account and log-on to the other one.  Problem is - whether I'm in dad or **dad2** using their respective passwords I cannot **sudo su** or say, **gksudo nautilus**.  A message comes up about not being in the sudoers file and contacting the system administrator - which is me, **dad**.  Now I'm really stuck.

---

### Post by steeldriver on 2013-12-16
have a look here --> [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Quarkrad on 2013-12-16
Thanks - but for some reason I cannot boot into recovery mode.  It seems to get half way through and then the screen freezes.  So I'm stuck within the Desktop environment or using LiveCD.

---

### Post by bapoumba on 2013-12-16
Quite unfortunate you cannot boot into recovery mode (and thanks for the explanation).

Basically, you will need to use a live cd, mount your root partition, chroot into it (and this is the part I wont like as the last time I had to do it, some many years ago in a particular situation, I failed miserably), and add your users to the admin group (ubuntu 10.04). You'll probably also have to check the sudoers file to make sure it is not corrupted by the Teamviewer manipulations.

Pasting here my sudoers and own groups :
```
 #
# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults	env_reset
Defaults	mail_badpass
Defaults	secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo	ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

```
bapoumba_lxde@SonyBlue:~$ groups
bapoumba_lxde adm sudo lpadmin sambashare
```

Your users have to be in their own groups (the username) and admin group as you are on 10.04 if your profile is correct. They must be in the sudo group for later ubuntu releases

1- Boot from the LiveCD
2- Locate your root partition
```
sudo fdisk -l
```
2- Mount the partition and chroot into it [COLOR="#B22222"]and this is where I'd like someone to step in for the mount options and chroot.[/COLOR]
3- Add both users to the admin group (if you are on 10.04)
```
sudo adduser dad admin
sudo adduser dad2 admin
```
4- Verify the sudoers file
```
sudo cat /etc/sudoers
```
And edit with visudo if needed.

Before you go through all the process, please backup your important files.

---

### Post by Quarkrad on 2013-12-16
Thanks - I did change my profile after you pointed it out in an earlier post - my now reads that I am on 13.04.  I will do dome digging about the mount options and chroot as this will be new to me.  Hopefully somebody might respond with some help.

---

### Post by Quarkrad on 2013-12-16
Is this the right sequence of actions?

Boot to Live CD
launch terminal
run:  sudo fdisk -l  (identify what partition has my 13.04 os - say sda1)
run:  sudo mount /dev/sda1 /mnt
run:  sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
run:  sudo chroot /mnt

This should leave me with something like root@ubuntu:  from where I can follow your previous post

---

### Post by bapoumba on 2013-12-16
On 13.04, users should be in the sudo group, not the admin group (so same as my own groups).

I'm not sure you need to mount the other files (such as sys and proc). The sudoers file is in /etc, I'm not sure you need to mount parts of the root directory tree at a different mount points (that is the bind option). These are needed to repair grub as grub-install needs them mounted that way, close or identical to what a real system is. One additional thing, you may want to 
```
sudo mkdir /mnt/sda1
```
and mount sda1 there rather than directly into /mnt and chroot into it to run adduser.

Now I'll really appreciate someone chiming in. I've reported the thread to my fellow staffers. I know some of them and regular members could chroot and code circles around me without me noticing :)

---

### Post by Quarkrad on 2013-12-18
Bump   I hate bumping but I'm in a mess now.  I have an issue where I need to install some software to do something urgently and I do not have sudo access because I'm not in the sudoers file.  I've had a look around with the liveCD (cannot boot to recovery mode for some reason) but I need help.  Guess I'm going to have to rebuild by close of play because of urgent work.  First time ubuntu has let me down - just through adding an extra user(!).

---

### Post by steeldriver on 2013-12-18
Is anyone a sudoer? what does

```
getent group sudo
```

say? If you absolutely don't have any sudo options AND can't get into recovery mode, then I agree with the previous posters - you will need to 'chroot' from a live disk / USB. We can walk you through that.

---

### Post by Quarkrad on 2013-12-18
Thank you.  The output of that command is:

[B]dad@dadubuntu:~$ getent group sudo
sudo:x:27:
dad@dadubuntu:~$ [/B]

---

### Post by Quarkrad on 2013-12-18
Put in that symbol somehow.  It should have read

sudo:x:27:

---

### Post by Quarkrad on 2013-12-18
Hmm...  the symbol bit is:

:x

---

### Post by Quarkrad on 2013-12-18
Ok,

sudo  colon x  colon 27 colon

---

### Post by steeldriver on 2013-12-18
Yeah the bulletin board software treats things like :x as smilies - you have to go the Miscellaneous Options and check the 'Disable smilies in text' box (or enclose the text in CODE tags)

Regardless it shows your sudoers group is empty so yes its recovery mode or chroot

---

### Post by Quarkrad on 2013-12-18
My pc will not boot into recovery mode so I will have to use a liveCD.  Can you help me - I'm booting to liveCD and reading this forum on a spare laptop.

---

### Post by steeldriver on 2013-12-18
bapoumba has outlined the steps - first thing once you are booted into the live environment is to find out how your installed system is partitioned so you know what bits to mount for the chroot

```
sudo fdisk -l
```

It will produce a bunch of 'stuff' - all you are really interested in at this stage is the bit that looks like

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   117223423    58610688    7  HPFS/NTFS/exFAT
/dev/sda2       117225470   195371007    39072769    5  Extended
/dev/sda5       117225472   149223423    15998976   83  Linux
/dev/sda6       149225472   187367423    19070976   83  Linux
/dev/sda7       187369472   195371007     4000768   82  Linux swap / Solaris

```

---

### Post by Quarkrad on 2013-12-18
Below is a picture of my output

---

### Post by steeldriver on 2013-12-18
OK based on that it looks like your root partition is on /dev/sdb2 - so the steps would be

1. create mount points for the chrooted environment (some of these may not be essential but it won't do any harm to create them all). The choice of 'sdb2' for the root mountpoint is arbitrary - call it whatever you like.
```

ubuntu@ubuntu:~$ sudo mkdir -p /mnt/sdb2/{dev,proc,run,sys}

```

2. mount the root block device of your HDD to the root mountpoint that you created in step (1)
```

ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt/sdb2

```

3. bind mount the additional directories for the chrooted environment
```

ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/sdb2/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/sdb2/proc
ubuntu@ubuntu:~$ sudo mount --bind /run /mnt/sdb2/run
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sdb2/sys

```

4. chroot into the HDD filesystem
```

ubuntu@ubuntu:~$ sudo chroot /mnt/sdb2

```

5. let's just check we are in the correct filesystem and confirm that group 'sudo' is messed up
```

root@ubuntu:/# getent group sudo
sudo:x:27:

```

6. now let's do the actual fix by adding our user to the 'sudo' group
```

root@ubuntu:/# gpasswd --add steeldriver sudo
Adding user steeldriver to group sudo

```

7. check that it worked
```

root@ubuntu:/# getent group sudo
sudo:x:27:steeldriver

```

8. OK we're done here - we can exit from the chroot environment
```

root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ 

```

9. back in the live disk environment - we should cleanly unmount the chrooted filesystem
```

ubuntu@ubuntu:~$ sudo umount /mnt/sdb2/{dev,proc,run,sys}
ubuntu@ubuntu:~$ sudo umount /mnt/sdb2/

```

10. now you can exit from the live environment and boot back into your regular system

---

### Post by Quarkrad on 2013-12-18
Wow - that did it.  I have my machine back.  Many thanks for all your work - I appreciate what you did this afternoon.

---

### Post by bapoumba on 2013-12-20
So many many thanks steeldriver. I'm not comfortable with the chroot environment as my previous encounters were miserable fails and was not sure you had to bind other files for adding a user to the sudo group. I had no time to test it (and believe it or not, I should not even take the time to answer here..).

Very glad you got it fixed, Quarkrad.

This little story reminded me why I _always_ keep an additional user with admin privilege _and_ the last working kernel on any system I use (Linux or MacOS) or feel responsible for (kids..). Not even talking about backups.

---

