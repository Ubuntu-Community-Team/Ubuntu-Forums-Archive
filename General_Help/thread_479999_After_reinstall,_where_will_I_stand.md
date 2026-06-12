---
title: "After reinstall, where will I stand?"
date: 2007-06-20
forum: General Help
---

### Post by tuco penguin on 2007-06-20
Running Feisty, I had Open Office decide to stop running for me... neither the Ubuntu version nor the official release over on the oo.org web site will start any longer.  (see this thread:  [http://ubuntuforums.org/showthread.php?p=2826944](http://ubuntuforums.org/showthread.php?p=2826944))

Have also not been able to get the nvidia-glx drivers working, although my graphics card is a pretty standard XFX-5200 from GeForce.  Probably related to the way I tried to perform the upgrade, and reading several forum threads seem to indicate reinstalling ubuntu is the only solution.  I can work with the nv driver--eye candy is not that critical for me.  But not being able to update my resume or utilize my financial spreadsheets is a big deal, so my open office problems have me contemplating a fresh Feisty install from CD, and the nvidia issue adds some weight to the idea.

My question is:  what can I expect to lose when I do this, and what should persist through the reinstallation?  (And do I need to backup and copy my /home directory into the new installation, or does it persist itself during the installation if I don't reformat my partitions?  Of course I would backup critical data anyway!)
1.  Firefox bookmarks?
2.  Desktop wallpaper, panel layouts, and other user preferences?
3.  Installed non-standard programs like MythTV Frontend?
4.  Thunderbird address book and mailbox?
5.  fstab for several network drives that mount during startup?

There's more too, I'm sure.  I stand to create a lot of work for myself to reconfigure my system if it doesn't go well, so I really need to know what to expect.  That will help me decide whether to dive in and reinstall or keep beating my head against OpenOffice directly.](*,) which I have removed and installed at least six times now.

---

### Post by phidia on 2007-06-20
It appears that you have a seperate home partition? Is that correct? If you do and you don't format that partition then most of your settings will be saved. If you don't have a seperate home partition then you do need to save that. If you save and sucessfully restore your home most of your settings e.g firefox, thunderbird, ect will be saved. You may want to give the system rescue cd a look [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by tuco penguin on 2007-06-20
Thanks for the info and recue cd link.

I believe my separate home partition (hda3) is a logical partition, not a physical one.  Does that make any difference?

---

### Post by merlinus on 2007-06-20
Not at all.  Just remember NOT to format it.

-merlin

---

