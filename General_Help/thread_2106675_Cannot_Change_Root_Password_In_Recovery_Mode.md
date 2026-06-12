---
title: "Cannot Change Root Password In Recovery Mode"
date: 2013-01-19
forum: General Help
---

### Post by revzalot on 2013-01-19
I've just upgraded from 11.04 to 11.10 and luckily I'm still able to login via ssh keys.  However, my root password no longer works to gain control of the machine.  

I rebooted the machine, went into recovery mode, then chose "remount" to mount the filesystems.  Finally I choose "root: Drop to root shell prompt" but it asks me for root password or CTRL D to continue.  Thus I cannot get into the the shell to do a passwd change.  

How can I bypass it from asking me for my root passwd in recovery mode?

---

### Post by westie457 on 2013-01-19
Hi reset your password using this guide.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by revzalot on 2013-01-19
> **westie457 said:**
> Hi reset your password using this guide.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)


Yeah I followed that guide step by step but when I pick the "drop to root shell prompt," it'll ask me for a root password to do maintenance or CTL D to continue.   Any advice how to bypass this so I can get into the root shell?

---

### Post by sudodus on 2013-01-19
> **revzalot said:**
> I've just upgraded from 11.04 to 11.10 and luckily I'm still able to login via ssh keys.  However, my root password no longer works to gain control of the machine.  

I rebooted the machine, went into recovery mode, then chose "remount" to mount the filesystems.  Finally I choose "root: Drop to root shell prompt" but it asks me for root password or CTRL D to continue.  Thus I cannot get into the the shell to do a passwd change.  

How can I bypass it from asking me for my root passwd in recovery mode?
The security philosophy of Ubuntu excludes logging in as root. It is possible that your tweak to do so was lost with the upgrade to a new version.

Are you able to log in with your normal user account? In that case I suggest that you try using sudo to obtain root privileges. The advantage of sudo is that you get only temporary root privileges. This reduces the risk to destroy the system or delete important user data.

If you have problems to log in at all or to use sudo, I was going to suggest the following link.

[[COLOR="Red"]http://www.psychocats.net/ubuntu/resetpassword[/COLOR]]("http://www.psychocats.net/ubuntu/resetpassword")

But I'm late and now I know that you already tried that.

***Is your home directory encrypted?***

---

### Post by revzalot on 2013-01-19
> **sudodus said:**
> The security philosophy of Ubuntu excludes logging in as root. It is possible that your tweak to do so was lost with the upgrade to a new version.

Are you able to log in with your normal user account? In that case I suggest that you try using sudo to obtain root privileges. The advantage of sudo is that you get only temporary root privileges. This reduces the risk to destroy the system or delete important user data.

If you have problems to log in at all or to use sudo, I was going to suggest the following link.

[[COLOR="Red"]http://www.psychocats.net/ubuntu/resetpassword[/COLOR]]("http://www.psychocats.net/ubuntu/resetpassword")

But I'm late and now I know that you already tried that.

***Is your home directory encrypted?***

After the upgrade, I cannot login normally with login and password thus I cannot sudo as well.  Yes I was able to sudo before I upgraded.  Now I really need to change my password in the recovery console but I cannot since it keeps asking for root password or CTL D to continue.   Luckily, I login via ssh keys and I tried to change my passwd when I logged in but no go.  I tried those steps in the links many times.  I've also tried using the UBuntu Live CD and I could not chroot into my mounted filesystems.  I'm running out of ideas trying to change my password.  Please help anyone.

PS.  My home directory is not encrypted but it's using LVM.

---

### Post by revzalot on 2013-01-19
SOLVED!
Here's how I did it.  

1.  Use an Ubuntu Live CD and Load it.
2.  Click on try Ubuntu to get into Live CD Desktop.
3.  Open a terminal
4.  Since I'm having trouble mounting my LVM filesystem:
  apt-get install lvm2
5.  pvscan   # scan the physical volumes 
6.  vgscan   # find the volume groups
7.  vgchange -a y  #  activate volume groups all
8.  lvscan  # make sure their all activated
9.  mount /dev/VolGroup00/LogVol00 /mnt      #  mount the lvm filesystem
10.  passwd root   # change new password for root 
11.  reboot   

Voila!   I'm now able to log in.  

On my next upgrade, I'm going to update a password after all the upgrades and right before rebooting to avoid this mess.  :()

---

