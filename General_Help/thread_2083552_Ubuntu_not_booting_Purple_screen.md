---
title: "Ubuntu not booting Purple screen"
date: 2012-11-12
forum: General Help
---

### Post by gasperg on 2012-11-12
**Disclaimer**

First off I'd like to state that I am not a big user of forums.  I'll do a post somewhere once in a blue moon and get yelled at for multiple things.  Please refrain from that and if I do something wrong please be patient.

I have spent 3 hours searching on fixes to the problem and have not found a problem quite the same as mine, nor a fix to a similar one that worked for me.

Now onto my problem..

**My Problem:**

I have run Ubuntu and Windows Vista dual boot fine for 2 years now.  Today while working on an assignment for school in the terminal (C coding) I compiled my work and ran it against a grading script.  At that point my screen froze and my mouse froze.  I gave it some time.  Tried a few hotkeys that often get me out of the problem to no success.

At this point I restarted my computer, chose Ubuntu (instead of windows vista, like usual) and my computer went to a purple screen and after about 2 seconds my caps lock and scroll lock lights on my laptop began flashing and continued doing so. My normal ubuntu login screen never showed up and after many efforts the same results continue.

**Edits:**

1. Worth noting I used WUBI to install ubuntu
2. Not sure what version of Ubuntu I have but I think its 12.04
3. I have no access to any command line in Ubuntu, like I said it doesn't go past me choosing ubuntu from start up.

**Key things to note so far:**
1. Purple screen
2. Caps lock and screen lock flashing
3. I did NOT do any sort of upgrade or update prior to this happening


**What I have tried:**

I have tried holding shift in attempt to open up the "grub".  Needless to say that didn't work.  It's also worth mentioning I don't know what the grub is and nothing of what I've read about it has ever shown up.  Generally I choose ubuntu when I start my computer the ubuntu loading screen shows up for a couple seconds, than my login screen appears and I enter the ubuntu OS.

I have tried running dskchk and this has not worked.

Nothing else I've done is relevant to getting my install to work..

**So here are my current thoughts:**

I would like either of 2 things:

1. Fix my boot so that I can log in normally again to continue my work.

2. Find a way to extract the needed files from my damaged Ubuntu so that I can just use my newly downloaded virtual box on windows with ubuntu to continue.

Obviously I am at a dead end with number 1.  

**Here is what I have done to try and extract my ubuntu files:**

I have downloaded something called ext2Read which should allow me to look at files on my Ubuntu from windows.  This installed fine and I went into C/ubuntu/disks where my root.disk is to look inside of it.  Of course I cannot do that either, I get the error message that it is corrupted and cannot be read.


**Conclusion**

So any help for either 2 scenarios will be of alot of assistance.  I will readily accept help at any time, but I will be up all night working on the project and will just start from scratch once my ubuntu on virtual box is done installing (which at this rate will be awhile).

And again if I'm doing something wrong about the placement of the thread or if for some reason you think that this question has been answered please refer me to the thread (however I promise I tried to look for something and was unable to).

Also if I should change or add better tags I could use that advice to.

Thanks!

---

### Post by oldfred on 2012-11-13
Wubi relies on the NTFS file system and is one large file. If chkdsk sees an issue it can then cause major issues.

Do you have a LiveCD of the same version of Ubuntu?

How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by gasperg on 2012-11-13
Sorry for the ignorance, but what do you mean by LiveCD?

Do you mean a physical disk copy of Ubuntu? 

EDIT: Looked at your link and no I don't have a live CD.

Also, I am not missing root.disk, but would it be ok to try and give that troubleshoot a shot? Or would that potentially wipe my files away.

END EDIT.


I have read some of the Wubi guides and FAQ's with no success so far.  Interesting note that Wubi wasn't intended for a full time installation though.

Thanks.

---

### Post by oldfred on 2012-11-13
The standard Desktop install CD or USB is a liveCD which can run the full Ubuntu on your system. Of course you cannot write to a CD so anything you do is lost. But you need a liveCD for Ubuntu to make repairs and should also have the Windows repairCD that Windows lets you make. The Windows Repair CD now costs $10 to download, it also used to be free. So make that Windows disk while you can.

If you install the USB flash drive version and add persistence, you can save some data from the live version.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Have not used wubi. But those links seem the best on trying to recover data.

---

