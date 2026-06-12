---
title: "HELP... I've messed up Sudo"
date: 2006-12-03
forum: General Help
---

### Post by funk19 on 2006-12-03
In my wisdom I chmod -R 0755 /home/myhomefolder/ and in the process messed a lot of things up.

When I tried to login again to unbuntu (6.10) I was warned that my /.dmrc file needed to be set to 644 and that my home folder needed to be writable only by the user.

I fixed the chmod issue on /.dmrc and set my user/home folder to Write/Read/Read recursively.

I can now login without any warnings but I can no longer user sudo.

If I try and run any sudo command all I get is the following error:-
sudo: must be setuid root

Any ideas on how I can:
a) set my permissions on my folders back to the way they were before I ran the chmod?
b) get sudo back to normal operation?

Short of re-installing I am not sure what to do now... ](*,)

---

### Post by soaring747 on 2006-12-03
Well you definitely don't need to reinstall Ubuntu.

You may want to try booting in single-user mode (recovery mode option on grub) and then running apt-get -install --reinstall sudo. Then you want to make sure to add your user to the sudoers file.

[http://www.ubuntuforums.org/showthread.php?t=9890](http://www.ubuntuforums.org/showthread.php?t=9890)

Make sure you have a command line text editor to use. I believe Vim comes pre-installed, so know how to use basic vim commands [http://www.pixelbeat.org/vim.tips.html](http://www.pixelbeat.org/vim.tips.html)

Make certain that you don't mispell anything in the sudo configuration file!

---

### Post by funk19 on 2006-12-04
> You may want to try booting in single-user mode (recovery mode option on grub)

Problem with this is that I am running 6.10 on PPC. It looks like it loads yaboot and not grub and my only options at boot time is a) l for GNU/Linux or b) c for CDROM boot.

I tried also logging in using a failsafe terminal session but I can't su to root to do anything.

> apt-get install --reinstall sudo

This command works without using sudo which is fantastic however now I can't connect to the internet to download the 172kb for this command to complete. 

I am using pppoe to connect to the internet but I need to once again connect as root in order for me to establish a connection to the internet.

On a side note have a look at the following list of files...

.bashrc
.bash_profile
.bash_logout
.bash_history

All of these files are current set to my user and group instead of root:root. They also have 777 as the permissions set. Are these not contributing to this sudo issue?

---

