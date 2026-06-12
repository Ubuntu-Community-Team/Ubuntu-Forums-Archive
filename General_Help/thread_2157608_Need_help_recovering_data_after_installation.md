---
title: "Need help recovering data after installation"
date: 2013-06-26
forum: General Help
---

### Post by nikhilholla on 2013-06-26
Hi, 
I have installed ubuntu 13.04 on my system by erasing windows 7 which was previously installed.After install i am not able to find the D drive files wic was present in windows 7.
I need all those data and need help in recovering the data.
plz need help on this as i had lots of data in that drive and more over i am able to see the data present.
Thanks

---

### Post by varunendra on 2013-06-26
> **nikhilholla said:**
> I have installed ubuntu 13.04 on my system by erasing windows 7 which was previously installed.After install i am not able to find the D drive files wic was present in windows 7.

Welcome to the forums Nikhil !

There is nothing like D:, E: etc. drives in Linux. The concept of drives and partitions and their implementation is quite different here which you don't necessarily have to understand immediately (although it'll help you a lot).

Just open a file browser (the folder icon in the launcher in the left, or any folder anywhere), and if you are using the default Ubuntu, you will see all your partitions/drives in the left pane of the file browser. They will NOT show up as C:, D: etc. drives, but instead, by their Volume labels.

Just click on the drive icons and they will open up in the right pane (the main area of the file browser).

Unless you have wiped out all your partitions during the installation, your partitions, and the data in them should still be there. Post back if you don't see the drive icons in the left pane (that shows "Home, Documents, Downloads..." etc.)

---

### Post by Irihapeti on 2013-06-26
*Thread moved to **General Help**.*

---

### Post by varunendra on 2013-06-26
> **Irihapeti said:**
> *Thread moved to **General Help**.*

Thanks Irihapeti, and your signature says a lot about his problem :P

---

### Post by nerdtron on 2013-06-26
> **nikhilholla said:**
> Hi, 
I have installed ubuntu 13.04 on my system by erasing windows 7 which was previously installed.After install i am not able to find the D drive files wic was present in windows 7.
I need all those data and need help in recovering the data.
plz need help on this as i had lots of data in that drive and more over i am able to see the data present.
Thanks

How exactly did you install Ubuntu 13.04? Did you read carefully before you choose the "Erase Windows 7" option?

Anyway, open up the "Disks" utility and post the screenshot here. It'll give you an idea of the current partitions on you computer. Don't expect though, I think all is lost :(

---

### Post by Impavidus on 2013-06-26
You probably instructed the installer to erase windows and install Ubuntu on the entire drive. Unfortunately, windows uses the word "drive" in a confusing way both for the physical device and for the partitions on it. Linux doesn't, it consistently calls partitions "partitions". Therefore you probably thought the installer was only going to wipe the C partition, but in fact it formatted the entire drive. The thing windows called a D drive is probably gone, so you may be in for some file recovery: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). There's no guarantee it will work though.

Unless of course the "D drive" was indeed a different disk &#8211; windows wouldn't tell you &#8211; in which case you should be able to find it in the file browser.

---

### Post by varunendra on 2013-06-26
> **nerdtron said:**
> Don't expect though, I think all is lost :(

Not necessarily :)

Even if all the partitions are removed and recreated for Ubuntu, a fresh installation of Ubuntu is only about 4.5 Gb. Given the size of the modern disks, most of the data should still be there (unless of course it was less than 4GB and all in windows partition which is usually the first one).

In case the partitions are removed/overwritten, the only thing to be careful about now is to avoid doing anything that has the potential to 'Write' on the partitions. That further implies that if possible, even booting from hard disk should be avoided since at least many of the OS files are created/modified on each boot.

By the way, the [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) link Impavidus posted is a good one to understand the basic precautions in case of a potential data loss. Although, as is clear by OP's post, it may just be a (non-)issue of understanding the fundamental concepts, not necessarily a serious problem like we are discussing. :)

---

### Post by Mark Phelps on 2013-06-26
Folks have reported that the "replace" installer option, which they THINK will only overwrite the Win7 OS partition, in fact, overwrites other NTFS partitions as well.  That could be why so many folks think they're only replacing the Win7 OS to discover that they lost their Win7 data as well.

In my experience, Windows tools are best at recovering Windows filesystems; Linux tools in recovering Linux filesystems.

You want to take a look at the partitions on your drive to see if there is a Linux filesystem partition where the previous Windows "D" partition used to be.  IF that's the case, you may be able to use Windows partitioning tools to restore the Windows partition.

---

### Post by nikhilholla on 2013-06-27
hi thanks all for all the replies,
yes i tried to erase windows 7 thinking that ubuntu would be replaced on windows.
after install 4 gb of disk space was allotted for ubuntu os and rest disk space was kept and was transformed into raw files i guess.
i tried in ubuntu for this disk space, was not able to find.Then checked with windows 7 by plugging hard disk into another computer,
but the hard disk was not detected,then went to mange or device manager and check was disk management then i was able to find the disk space,
tried recovery with softwares but its coming in different names and format.
is there any way i can convert the files back to ntfs format.
thanks

---

### Post by varunendra on 2013-06-27
> **nikhilholla said:**
> is there any way i can convert the files back to ntfs format.

Be aware that you may be making it worse by trying random stuff without understanding the effects.

Everytime you use that disk, either with windows or linux, you are risking the chances of recovery.

That being said, here's your best chance to recover the earlier existing partitions :

Boot with a live USB, get connected to internet, install testdisk on it :
```
sudo apt-get update
sudo apt-get install testdisk
```

Then run it with -
```
sudo testdisk
```

..and follow this step-by-step guide to recover your previous partitions: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If even a deeper search doesn't show your previously existing ntfs partitions, post back here.

If you are tempted to try anything else, just make sure you don't do anything that has the potential to "Write" on the partitions, and mind you, this is something that windows absolutely doesn't care about. It may not even ask or inform you before doing further damage in attempt of 'repairing'. So, stay away from windows unless you have a very good understanding of what you are (or it is) going to do with the disk in question.

---

### Post by Mark Phelps on 2013-06-27
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

