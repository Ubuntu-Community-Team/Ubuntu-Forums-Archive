---
title: "Data recovery after formatting my disk for Ubuntu install"
date: 2013-04-13
forum: General Help
---

### Post by con1980 on 2013-04-13
The unthinkable has happened. Had a Windows XP PC, 1 hard disk containing 2 partitions (C:\ and D:\ ), I spent one week backupping all important data to the D:\ partition, because I was planning to change it to Kubuntu. It's a rather old PC which I wanted to give a second life on Kubuntu. I installed Kubuntu and seem to have formatted the second partition too... Yes I almost shot myself in the face.

The disk contains different files, movies, music, photos and e-mail.

After reading many posts on this and other forums I came to understand that there may be some ways to recover my data, especially since the formatted data might (not sure at all) be stored on the exterior of the hard disk. My PC has been turned off since I noticed the D:\ partition is gone so very little data has been added since the format, if any.

Now I'm wondering which software to use, which tools I need etc. Is there any step by step guide?

The formatted disk is a Maxtor DiamondPlus 9 120GB hard disk (ATA). Could a 3,5" USB enclosure be useful? I noticed they cost about 15$ so that's really worth it.

I have another Ubuntu laptop and a Windows 7 laptop which could come in handy for the recovery process. If so, let me know.

Especially the e-mail and address book information are quite important to me... The photos are of "only" emotional value.

PS: Somewhere on the net I found a post of someone in the same situation who had the guts to re-install Windows XP and who did recover every "formatted" file. Sadly not a lot of detail. I guess I should not try this.

Thank you in advance for your information!!

---

### Post by Mark Phelps on 2013-04-13
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

