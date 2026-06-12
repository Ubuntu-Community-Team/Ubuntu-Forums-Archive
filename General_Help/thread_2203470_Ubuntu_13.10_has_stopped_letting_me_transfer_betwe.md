---
title: "Ubuntu 13.10 has stopped letting me transfer between hard drives"
date: 2014-02-03
forum: General Help
---

### Post by Fsirett on 2014-02-03
Sorry to bother you again.

Due to some rather bad weather, I had two power outs that made things difficult, but not impossible. I thought I had everything going again when the machine began telling me I had low memory. Fine, I thought, I installed a new drive and put in two partitions which show up nicely, but now I want to move files from one drive to another and Ubuntu does not let me do this at all. 

I hasten to add that this worked just fine before. What I do is I open the disk in a window then open the target in a tab and drag the files across. No luck now!

I have numerous drives and this has stopped working between any of them. I have changed the ownerships and permissions on the files to ensure that was not the problem and it is not!

Does anybody have any idea what is going on?

Cheers

Frank Sirett

Now, I am playing around with things, I find that the new partitions are coming up under permissions as being "root" but when I go to them with gksudo I find they tell me they are mine. There are other disks that I am playing with but they all say I own them. Still will not let me move files, though.

F S

---

### Post by grahammechanical on 2014-02-03
What permission does Group and Others have in the Properties and Permissions of those partitions? Access Files? Or Create and Delete Files? You need to open Nautilus using gksu and then change the permissions for Group and Others to Create and Delete Files. When working as a standard user we need permission for Group and Others to be able to do more than just Read the files.

Do not move the files with File Manager (nautilus) that has been loaded using gksu as the files will now be owned by Root and you will not be able to write to the files as standard user.

Regards.

---

### Post by Fsirett on 2014-02-04
Thanks and good morning.

First of all, the permissions were all changed (using gksudo) to my permissions and this morning, when I turned it on, I had acess to moving files again, which I have been doing, but now one of my drives is not appearing on the left hand screen panel now. It is still available, but only through the "media" folder and does not accept automatically passed files.

I know this might seem like a new problem, but I strongly suspect it is the same problem in a new phase. Maybe it is a problem with my computer, but everything else seems to be working normally. 

What I did this morning is: 

I started the computer as normal and looked to se that all of the drives were up and mounted. I did this through the "home", as normal. 

I saw that a main drive was not showing on the list, so I went to the "computer" line on the "home screen, opened "media" and found it was listed there and that it opened.

I then opened my new partition (On another drive) and transferred a large quantity of files from that drive to the new one. 

I then noticed that I was getting warnings that my automatic downloads were not able to access the old (hidden) drive. Just a moment and I will tell you what the message says: It says there are permission problems , but the disk has been changed to my permissions and still shows that. The icon in the media folder shows two arrows on the icon in the lower right hand side, if that helps, none of the other icons do.

I use the disk to hold things I cannot get around to at the moment and I fear it might be failing, but I have never had a disk fail like this before

If this is an indication, it no longer appears in the devices listed in GParted's devices although it did when I first wrote yesterday. 

Every time I write to this forum I learn a huge amount to add to my survival kit, but the system seems to be intent on creating an expert in me one problem at a time.

---

### Post by Fsirett on 2014-02-08
After restarting the computer some three or four times ( in the normal course of things) the system readjusted to normal. How this happened is still a mystery to me. It would appear that Ubuntu fixed itself. I have no idea, but if anyone may know, or even suspect, please send me the answers! "Magic" is very unsatisfying  I want to change this to solved, but I am not certain how to do that

---

### Post by Fsirett on 2014-02-08
Another addendum. The file in question continued to plague me so I tried:  $ apt-get install --reinstall fglrx  to reinstall the gnome Desktop and everything has returned completely back to normal.  I hope this helps some other poor sod, like me, wh has similar problems

---

