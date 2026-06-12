---
title: "Locked out!"
date: 2007-07-26
forum: General Help
---

### Post by bahistagitarista on 2007-07-26
hi guys! i need your help... for some weird reason, I can't log in as root or as my sudo user. I don't know how it happened or why it happened. I didn't do anything before I shut down the pc, and Im the only one who uses my laptop....

can anybody help me please?

---

### Post by NeuralEskimo on 2007-07-26
No problem.

1) Boot from the Kubuntu/Ubuntu CD you used to install.
2) Once booted, mount your root (/) partition
3) Open /etc/passwd in a text editor (nano for example)
4) Find the entry for the root user. It will be of the form "root:x:...."
5) Delete the "x", so the line reads "root::..."
6) Reboot and remove the install CD
7) Login as root and reset all your passwords (run passwd from the commandline)

Hope this helps...

---

### Post by bahistagitarista on 2007-07-27
THanks so much for your help! this is what is coming out now: **GDM could not wite to your authorization file. Thi could mean that you are out of disk space or that your home directory could not be opened for writing. In anycase it is not possible to log in. PLease contact your system admin.** but I have 27gb free space still... im sorry, but im a noob. I just switched from windows 2 weeks ago to try linux... and im no programer....

---

### Post by RAH66 on 2007-10-10
got the same issue

---

### Post by anaconda on 2007-10-10
How about just booting to recovery more (select from grub) and then giving your user a new password and making sure he is in the admin group.

to change the password from recovery terminal type:
```
passwd yourusername
```
and give the new password

then to check that the user is in admin group type:
```
more /etc/group
```
there will be a line starting with "admin" check that yourusername is also in that line.
if not you can add yourusername to admin with:
```
adduser yourusername admin
```

Good luck

---

### Post by RAH66 on 2007-10-10
this worked for me seein as you have such a small drive like me... well I found out that ubuntu needs 5% free space for some system stuff anyway if you can get 5% free then you are good to go

try:    sudo apt-get clean  (all I needed to do)

---

### Post by sarc on 2008-02-05
I got the same issue and it's because somehow my Home folder is FULL!  How do I empty it and how do I stop it from happening?

---

### Post by jken146 on 2008-02-05
Well, delete something.  Try emptying the trash for a start.  Try booting in recovery mode to do this.

---

### Post by sarc on 2008-02-06
Thanks I deleted files from console then I could reboot.  Now I'd like to make sure it does not happen again... if Linux is filling my hard drive with backup and spare files, it sounds suspiciously like something Windoze would do!!!

What to clen up?  How?  How to know what it's time to do it?

BTW Nautilus does not have an option to show folder size unless I right click on each folder, how do I find out where are the big useless files?

THANKS!

---

