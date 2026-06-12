---
title: "Deactivating Swap Failed, system will not shut down"
date: 2007-08-12
forum: General Help
---

### Post by Romanus81 on 2007-08-12
When I shut down my computer it will not power down unless I do a hold the power button for a couple seconds.
It gives me this message: 
Deactivating Swap [fail]
System will now shut down
[some numbers] Power Down
and then it does nothing, and I have to hold the power button until it shuts down.
I tried putting Ubuntu on it's own partition using LVPM, but the error remained

---

### Post by ago on 2007-08-13
Hmm never seen that before.

Try to deactivate swap by rename the swap.virtual.disk file to noswap.virtual.disk. You can use a free partition for swap as well (you will need to change the entry in fstab)

---

### Post by Romanus81 on 2007-08-17
I renamed the file and made a new partition with gparted and formatted it as swap, but I'm not sure if I got the fstab right. I haven't noticed any system problems, and the shutdown screen doesn't say "Deactivating Swap: Fail" anymore, but my system still won't shut down. I'm thinking this might not be a Wubi problem.

---

### Post by leondoes on 2009-10-29
I've wubi, i've recently upgraded to 9.10 and found the same problem. I'm a new user and I don't ready to get involved in setting partitions yet, there's ohter way to fix it? 
Thank you.

---

### Post by grar05 on 2009-10-31
The same as leondes. Sure it may be a solution without reinstalling nor doing partitions, and all with wubi. What do you think?

---

### Post by ncmncm on 2009-11-04
Up up up!

Anyone? shutdown hangs during deactivation of  swap partition.

---

### Post by rubins88 on 2009-11-07
I have the same problem with kubuntu 9.10 with wubi i can't shutdown the system..... Finally i find the solution!!! :popcorn:


Go to system settings -> advanced -> login manager -> shutdown

In commands write to halt line:

```
sudo shutdown -h now
```

and in reboot line write
  
```
sudo shutdown -r now
```

YOU CAN FINALLY SHUTDOWN THE SYSTEM

sorry for my english!

> l'italia sta avanti

---

### Post by Terrycymru on 2009-11-09
There is a solution at #19 of this bug report:

[https://bugs.launchpad.net/wubi/+bug/468589](https://bugs.launchpad.net/wubi/+bug/468589)

I haven't tried it yet but several people have reported it works!

**LATER: THIS PROBLEM HAS NOW BEEN SOLVED BY AN UPDATE TO KARMIC 19/11/2009. There is now no need to do this workaround.**

---

### Post by Terrycymru on 2009-11-10
> **Terrycymru said:**
> There is a solution at #19 of this bug report:

[https://bugs.launchpad.net/wubi/+bug/468589](https://bugs.launchpad.net/wubi/+bug/468589)

I haven't tried it yet but several people have reported it works!

Yes, this worked for me!

---

### Post by minimo on 2009-11-12
I'm a bit new to this and really don't understand what I need to do to get it to shut down correctly...

Any help with the basics of what you guys are talking about in post #19

Thanks loads...

---

### Post by Terrycymru on 2009-11-13
> **minimo said:**
> I'm a bit new to this and really don't understand what I need to do to get it to shut down correctly...

Any help with the basics of what you guys are talking about in post #19

Thanks loads...

minimo: First of all this fix is intended for users who have upgraded a WUBI install of 9.04 to 9.10 and have the shutdown problem. You need to edit the file /etc/rc6.d/s40umountfs .

In terminal type sudo gedit
Enter password when asked for it

When gedit is displayed select File          

Click on File System (in the Places panel)

Double Click on etc

Double Click on rc6.d

Highlight s40umountfs and click on Open

You can now edit the file

Scroll down until you see # Unmount local filesystems

replace

fstab-decode umount -f -r -d $WEAK_MTPTS

with

fstab-decode umount -r -d $WEAK_MTPTS

and

fstab-decode umount -f -v -r -d $WEAK_MTPTS

with

fstab-decode umount -v -r -d $WEAK_MTPTS

(In other words you need to remove the "-f". There are 2 occurrences of each so you need to edit 4 lines.)

Click on Save then close gedit.

Close terminal and try to reboot.

---

### Post by minimo on 2009-11-13
Terrycymru...

It totally worked, only I didn't have to edit 4 lines only the 2 that were mentioned in your post and the original post.

There were two lines in there:

fstab-decode umount -f -r -d $REG_MTPTS

and 

fstab-decode umount -f -v -r -d $REG_MTPTS

[COLOR="Red"]Those I did not touch[/COLOR] and it still reboots just fine now.

Thanks a bunch Terrycymru:

-----------------------

Now for those having a tough time like me. I can explain what I did in greater detail.

As Terrycymru said, this fix is for people who can't seem to shut down or reboot Ubuntu 9.10. This fix is intended for users who have upgraded a WUBI install of 9.04 to 9.10 and have the shutdown problem. WUBI is the windows installer for Ubuntu. I have mine on a duel boot with windows vista.

So when you have Ubuntu 9.10 open. You have to go to the start menu in the lower left corner of the screen. Scroll your cursor to accessories and then open Terminal.

In terminal type: 
sudo gedit

Enter password when asked for it. (unlike windows, you will not see the cursor move or little boxes when you are typing your password, so don't freak out)

When gedit opens, you will see something very similar to note pad in windows. I'm sure it's a lot beefier than note pad, as you can see, it seems to be password protected.

So having your gedit window open you now need to find the file you have to edit.

So like in windows, you go to the pull down menu.
Click file,
scroll down and click open. (or single click the open button both work fine) 

A new windows opens up and you will see something similar to file explorer on windows. On the left side panel named Places click on File System.

Now on the right side panel where you see all the files. double Click folder:
etc

scroll down until you find the folder named:
rc6.d
Double click that folder

Now look for the file named:
s40umountfs

Open it by double clicking it or highlight it and press the open button on the bottom right. (either way)

Now you should see the file open in your gedit (note pad-ish) you will need to find two lines of code.

fstab-decode umount -f -r -d $WEAK_MTPTS

and

fstab-decode umount -f -v -r -d $WEAK_MTPTS

When you find them, what you need to do is remove the -f from those and only those lines. You can get the cursor just before the -f on those lines and hit back space 3 times to remove the -f and the extra space that is not needed.

Or you can just replace the lines as was previously suggested.

Now remember, you are just dealing with those to lines of code. Not the lines above it or below it.

Once you have those two lines changed. Hit the Save button on the gedit (note pad like application) and close gedit. Then just reboot your system and it should work fine. It did for me.

Thanks again for this. I hope my writing doesn't confuse but helps those who need to be walked through the process.

---

### Post by Terrycymru on 2009-11-19
This problem has now been solved by an update to Karmic. 

The file /etc/rc6.d/s40umountfs has been replaced by a symlink to /etc/init.d/umountfs . The revised umountfs does not cause the shutdown problem.

---

### Post by ncmncm on 2009-11-23
Worked  for me too! 
Thanks !

---

### Post by ganeshmallyap on 2009-11-30
Hello all,

I am using Ubuntu Karmic AMD64 OS and from the past 2 days I am facing this issue.  Each time while shutting down my desktop freezes after flashing the message "deactivating swap".  The only thing I can do is to power off the machine.  For once I did a swapoff and then swapon using Gparted and this problem disappeared momentarily.  But in no time this trouble started again.

I did a clean install on the very first day of release of Karmic and so far there were no issues.  I tried to follow the steps mentioned in this message, but what I noticed was -f flag was not there in the file mentioned in my computer.  So not sure what is causing this problem.  I have logged a bug report in launchpad and it is still in new/unassigned state.

---

### Post by Dedi Landsman on 2009-12-02
Hello all, I'm facing this problem with the shut down. the difference is that i have a Wubi Ubuntu 9.04
and the solution given at here
>  is a solution at #19 of this bug report:
[https://bugs.launchpad.net/wubi/+bug/468589](https://bugs.launchpad.net/wubi/+bug/468589)
is meant for those upgraded from 9.04 to 9.10. I.E. it is not applicable to me.
please, help me solve this issue. Thanks

---

### Post by ahus98 on 2010-01-09
It is frustrating for new users but try the simple Graphical Solution

Problem at shutdown failure at deactivating Swap.... Solved on Karmic Ubuntu
 After over a month, desperately searching the INTERNET launchpad and wherever the search engines took me. I found the solution for my system. It is so simple I'm surprised none of the experts of the many many forums ever suggested it.

 I forced my system off, i restarted to bios and power it off from there, tried to modify scripts and power down using various commands, yet it all failed, the hours & hours wasted. After almost giving up & waiting for the next major update to Lucid Lynx meaning months to shutdown my system properly (silly but well what can i say)
 OK to the point.... which really really doesn't make me happy.... because of its simplicity.

 I decided to find some shutdown tools in the hope that an advanced tool might help... So I Entered Synaptic Package Manager
 Did a search... typed shut (& of course the results had a few tools for shutting down) or you can search initscripts which is my solution
 1. I right clicked (sweet no command line)
2. Mark for re-installation (sweet so simple)
3. Apply & let the task complete

 4. Reboot / perhaps shutdown & your computer powers off itself (You must love technology that turns off when you tell it to)
 As a new user, why of why didn't anyone say i could have reinstalled that, i was thinking how to reinstall shutdown but didn't know the term i needed. I'd be interested to know, does this solve a

---

### Post by boyang on 2010-01-12
Thanks for ahus98 at #17.

It is indeed working when you use Synaptic Package Manager to reinstall the initscripts.
I also try the methods other people solve their problems successfuly, but these methods are not working in my machine. After reinstall these scripts and reboot the system, everything is ok.:KS

> **ahus98 said:**
> It is frustrating for new users but try the simple Graphical Solution

Problem at shutdown failure at deactivating Swap.... Solved on Karmic Ubuntu
 After over a month, desperately searching the INTERNET launchpad and wherever the search engines took me. I found the solution for my system. It is so simple I'm surprised none of the experts of the many many forums ever suggested it.

 I forced my system off, i restarted to bios and power it off from there, tried to modify scripts and power down using various commands, yet it all failed, the hours & hours wasted. After almost giving up & waiting for the next major update to Lucid Lynx meaning months to shutdown my system properly (silly but well what can i say)
 OK to the point.... which really really doesn't make me happy.... because of its simplicity.

 I decided to find some shutdown tools in the hope that an advanced tool might help... So I Entered Synaptic Package Manager
 Did a search... typed shut (& of course the results had a few tools for shutting down) or you can search initscripts which is my solution
 1. I right clicked (sweet no command line)
2. Mark for re-installation (sweet so simple)
3. Apply & let the task complete

 4. Reboot / perhaps shutdown & your computer powers off itself (You must love technology that turns off when you tell it to)
 As a new user, why of why didn't anyone say i could have reinstalled that, i was thinking how to reinstall shutdown but didn't know the term i needed. I'd be interested to know, does this solve a

---

### Post by Xpf on 2010-01-19
> **ahus98 said:**
> It is frustrating for new users but try the simple Graphical Solution

Problem at shutdown failure at deactivating Swap.... Solved on Karmic Ubuntu
 After over a month, desperately searching the INTERNET launchpad and wherever the search engines took me. I found the solution for my system. It is so simple I'm surprised none of the experts of the many many forums ever suggested it.

 I forced my system off, i restarted to bios and power it off from there, tried to modify scripts and power down using various commands, yet it all failed, the hours & hours wasted. After almost giving up & waiting for the next major update to Lucid Lynx meaning months to shutdown my system properly (silly but well what can i say)
 OK to the point.... which really really doesn't make me happy.... because of its simplicity.

 I decided to find some shutdown tools in the hope that an advanced tool might help... So I Entered Synaptic Package Manager
 Did a search... typed shut (& of course the results had a few tools for shutting down) or you can search initscripts which is my solution
 1. I right clicked (sweet no command line)
2. Mark for re-installation (sweet so simple)
3. Apply & let the task complete

 4. Reboot / perhaps shutdown & your computer powers off itself (You must love technology that turns off when you tell it to)
 As a new user, why of why didn't anyone say i could have reinstalled that, i was thinking how to reinstall shutdown but didn't know the term i needed. I'd be interested to know, does this solve a

For me work to tanks for the help :KS

Para mim funcionou também muito obrigado pela ajuda :KS

---

### Post by jcneto on 2010-01-30
> **ahus98 said:**
> It is frustrating for new users but try the simple Graphical Solution

Problem at shutdown failure at deactivating Swap.... Solved on Karmic Ubuntu
 After over a month, desperately searching the INTERNET launchpad and wherever the search engines took me. I found the solution for my system. It is so simple I'm surprised none of the experts of the many many forums ever suggested it.

 I forced my system off, i restarted to bios and power it off from there, tried to modify scripts and power down using various commands, yet it all failed, the hours & hours wasted. After almost giving up & waiting for the next major update to Lucid Lynx meaning months to shutdown my system properly (silly but well what can i say)
 OK to the point.... which really really doesn't make me happy.... because of its simplicity.

 I decided to find some shutdown tools in the hope that an advanced tool might help... So I Entered Synaptic Package Manager
 Did a search... typed shut (& of course the results had a few tools for shutting down) or you can search initscripts which is my solution
 1. I right clicked (sweet no command line)
2. Mark for re-installation (sweet so simple)
3. Apply & let the task complete

 4. Reboot / perhaps shutdown & your computer powers off itself (You must love technology that turns off when you tell it to)
 As a new user, why of why didn't anyone say i could have reinstalled that, i was thinking how to reinstall shutdown but didn't know the term i needed. I'd be interested to know, does this solve a


Ha! Worked for me too!!! Thanks a lot!

---

