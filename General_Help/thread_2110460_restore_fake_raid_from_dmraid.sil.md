---
title: "restore fake raid from dmraid.sil"
date: 2013-01-30
forum: General Help
---

### Post by sdpagent on 2013-01-30
Dear all,
Can someone please let me know if it is possible that:

[LIST]
[*]a fake raid device could have been used to set up fake raid (mirroring) on two discs, but later unplugged with the drives re-plugged into the motherboard and still be used like raid? (I still saw the raid volume without the raid card)
[/LIST]

[LIST]
[*]if the previous point is true, perhaps later unplugging the drives and rebooting could cause the raid to fail/become unrecognized at boot? (I cant get the machine up again with the drives plugged in, they have to plug in after boot)
[*]whether the raid could be restored using the dmraid.sil folder found in the home directory (without needing to get the fake raid card back)
[*]whether having used the fake raid is the reason I get input/output errors whenever I try to interact with the drives, yet I can run successfully run extended smart scans on the drives showing **no errors**. Does this mean I have to get that fake raid card back to 'restore' the drives. Also of note is that the input/output errors occur if I use another seperate computer so its not the cables or that specific controller, but maybe I need to get the fake raid controller back? (How did it work for a while without the fake raid controller?)
[/LIST]
At the time, I had thought I had successfully configured the drives NOT to use fake raid and had set up software raid with mdadm, but having doubts after looking through config files and seeing the dmraid.sil folder.

This all relates to this [really long ask ubuntu post]("http://askubuntu.com/questions/247981/software-raid-mdadm-re-find-my-array") which is a) too long now b) no longer fresh

---

### Post by ronparent on 2013-01-30
> a fake raid device could have been used to set up fake raid (mirroring) on two discs, but later unplugged with the drives re-plugged into the motherboard and still be used like raid? (I still saw the raid volume without the raid card
Yes - I have actually done it! 
> if the previous point is true, perhaps later unplugging the drives and rebooting could cause the raid to fail/become unrecognized at boot? (I cant get the machine up again with the drives plugged in, they have to plug in after boot)
You should be able to at least get the raid activated after boot by typing - 
> sudo dmraid -ay
In any case you are probably operating in a situation beyond the scope of the programmer and the oucomes are unpredictable.
> whether the raid could be restored using the dmraid.sil folder found in the home directory (without needing to get the fake raid card back)
Answered above.
> whether having used the fake raid is the reason I get input/output errors whenever I try to interact with the drives, yet I can run successfully run extended smart scans on the drives showing no errors. Does this mean I have to get that fake raid card back to 'restore' the drives. Also of note is that the input/output errors occur if I use another seperate computer so its not the cables or that specific controller, but maybe I need to get the fake raid controller back? (How did it work for a while without the fake raid controller?)

At the time, I had thought I had successfully configured the drives NOT to use fake raid and had set up software raid with mdadm, but having doubts after looking through config files and seeing the dmraid.sil folder.
If you are mixing fakeRAID set up at boot by dmraid and Linux software raid administered by mdadm you are really asking for problems. You could erase your fakeRAID metadata and use mdadm to build a true software raid, but, that would destroy your partition table and force you to rebuild from scratch. I would be inclined to first try to undo the mdadm setup and run the raid using dmraid. 

In any event the fakeRAID may well run without the original MD chipset since the fakeRAID metadata is already on the drives but the results are unpredictable.

---

### Post by sdpagent on 2013-01-30
Thank you. I feel I should raise these points:

[LIST]
[*]I didn't  intentionally setup software raid on top of hardware raid. I plead  accidental stupidity (if this is indeed what has happened)
[*]I  havent set up a /boot partition on the drives (as far as I am aware) as  I boot from a seperate drive and was just using these for data.
[*]Running sudo dmraid -ay just results in input/output error messages.
[*]I cant rebuild the software raid through mdadm so far as 'no superblock found'
[/LIST]
Is there any way to 'reset' the drives (to get the hardware back not the data). At the moment I cant format or even run an hdpaarm security erase on the drives (input / output errors)

---

### Post by sdpagent on 2013-01-30
Ok so it turns out the drives were locked! I unlocked them with an hdparm command and now the drives can be seen by gparted! Unfortunately all is not well.  I tried auto mounting with dmraid -ay, and with mdadm --assemble --scan, neither of which picked up the raid. There are some fat red exlamation marks with this output:

[IMG]http://img1.uploadscreenshot.com/images/orig/1/2921405516-orig.png[/IMG]
[IMG]http://www.uploadscreenshot.com/image/1860789/3430041[/IMG]
I have managed to mount the md device. Is it possible to unplug one drive, format it to a normal drive and copy the data to that? Ive had enough 'fun' with raid and am going to go down an automated backups route with rsync I think. I want to ask before I do anything that may cause data integrity issues.

---

### Post by ronparent on 2013-01-30
It is. Just remember that the metadata is persistent and must be erased to completely clear the raid. That would be done prior to uninstalling dmraid.

In a live cd session, open a terminal and type > sudo dmraid -Er sda
Do that for each disk. That will rid you of the fakeRAID. Incidently, because it is a mirriring array, you should have still access to the data even after the raid metadata is erased. Good luck.

---

