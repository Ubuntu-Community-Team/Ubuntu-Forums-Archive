---
title: "Looking for a disk cloning utility"
date: 2017-11-02
forum: General Help
---

### Post by orthoducks on 2017-11-02
I'm looking for a utility that:

[LIST]
[*]Will clone a hard disk: boot track and all partitions. 
[*]Can handle a mix of Linux and NTFS partitions. 
[*]Has a "just do it" mode that clones a specified source to a specified destination without making me set a multitude of options. 
[/LIST]
If it runs under Linux, under Windows, or stand-alone, fine. As long as it works.

So far I've looked at Clonezilla (extremely complex) and Redo Backup and Recovery (can't actually clone a disk; it only backs a disk up to a file and restores it from a file). What else is there that may fit my needs?

---

### Post by litlesam on 2017-11-02
> **orthoducks said:**
> I'm looking for a utility that:

[LIST]
[*]Will clone a hard disk: boot track and all partitions. 
[*]Can handle a mix of Linux and NTFS partitions. 
[*]Has a "just do it" mode that clones a specified source to a specified destination without making me set a multitude of options. 
[/LIST]
If it runs under Linux, under Windows, or stand-alone, fine. As long as it works.

So far I've looked at Clonezilla (extremely complex) and Redo Backup and Recovery (can't actually clone a disk; it only backs a disk up to a file and restores it from a file). What else is there that may fit my needs?

There's a few but [Clonezilla]("http://clonezilla.org/downloads.php") seems to handle my needs.

---

### Post by raleigh3 on 2017-11-02
Clonezilla is what I and many others use and it's not that complicated once you use it a few times.

No program I have ever seen has a "just do it" setting. Cloning a disk has to be done carefully.

Their website has tons of help.

If you have any questions about using it, I would be happy to help.

---

### Post by sudodus on 2017-11-03
> **raleigh3 said:**
> Clonezilla is what I and many others use and it's not that complicated once you use it a few times.

No program I have ever seen has a "just do it" setting. Cloning a disk has to be done carefully.

Their website has tons of help.

If you have any questions about using it, I would be happy to help.

+1 for Clonezilla.

[http://clonezilla.org](http://clonezilla.org)

Download an iso file and create a boot USB pendrive or boot CD disk. Boot live to run Clonezilla.

You can either clone directly to a drive of at least the same size as the original drive, or you can create a compressed image (a directory with a number of files).

---

### Post by jambyc on 2017-12-27
Hi,

Clonezilla is a fantastic piece of software... I have managed to clone entire disk but for some reason all my system data hasn't been cloned. At the first boot from new disc ubuntu going to guest login instead to my main one.
Any advice how to fix it?

---

### Post by sudodus on 2017-12-27
0. Were there some error outputs from Clonezilla?

1. Did you select cloning of the whole drive or did you specify all the partitions separately?

2. Did you clone from a bigger drive to a smaller drive?

3. Are the sector sizes the same in the original drive and the target drive? (They may differ if the target drive is much bigger or much newer or of a different brand name.) You can check with the command

```
sudo parted -ls
```

4. Was you home partition on the same or on a separate drive?

---

### Post by Autodave on 2017-12-27
I have used *Redo *many times w/o a problem.

---

### Post by HermanAB on 2017-12-27
The ultimate 'Just Do It' utility would be Data Definition:
# dd if=/dev/sda of=/dev/sdb bs=1M

Careful RTFMing is recommended though.

---

### Post by ian-weisser on 2017-12-27
> **HermanAB said:**
> Careful RTFMing is recommended though.

+1 RTFM: dd is an awesome tool. Awesomely powerful, awesomely fast...and with a single human typo, awesomely destructive. No handrails.

---

### Post by jambyc on 2017-12-29
> **sudodus said:**
> 0. Were there some error outputs from Clonezilla?

1. Did you select cloning of the whole drive or did you specify all the partitions separately?

2. Did you clone from a bigger drive to a smaller drive?

3. Are the sector sizes the same in the original drive and the target drive? (They may differ if the target drive is much bigger or much newer or of a different brand name.) You can check with the command

```
sudo parted -ls
```

4. Was you home partition on the same or on a separate drive?

0. No errors

1. Cloned whole drive

2. Smaller (350GB) to bigger (2TB)

3 & 4. I have seen system structure through file manager but no personal data as I could only login as Guest. Due to guest limitation I cannot access terminal. Partition structure was fine when I checked with Gparted live. All system data is on this drive nowhere else.

---

### Post by sudodus on 2017-12-29
> **jambyc said:**
> 0. No errors

1. Cloned whole drive

2. Smaller (350GB) to bigger (2TB)

3 & 4. I have seen system structure through file manager but no personal data as I could only login as Guest. Due to guest limitation I cannot access terminal. Partition structure was fine when I checked with Gparted live. All system data is on this drive nowhere else.

This is strange. It seems you have done everything right (if the sector sizes are the same on the source and target drives).

But maybe there is another problem: I know that things work directly, if you clone a drive with an MSDOS partition table. But if there is a GUID partition table (GPT), there is a bac&#7729;up partition table at the tail end of the drive, and I am not sure, if it will be treated correctly by Clonezilla. If this is the problem, you can repair it with **gdisk**.

On the other hand, it is strange that things work well enough for the guest session but not with the regular user IDs. This makes me think that there is something wrong with the **/home** directory (which might be in a separate partition).

---

### Post by jambyc on 2017-12-30
I have cheeked again and two partitions had about 900gb each + swap partition (about 8gb) so entire disk was used. Partitions are not the same then

When login as guest, server name is correct as per old disk.

What do you mean to repair it with gdisk? Resize partitions?


New disk
[ATTACH=CONFIG]277967[/ATTACH]

old disk
[ATTACH=CONFIG]277968[/ATTACH]
old disk
[ATTACH=CONFIG]277969[/ATTACH]

---

### Post by sudodus on 2017-12-30
You have an MSDOS partition table, so you need not fix any backup table at the tail end of the drive.

Did you do this only with Clonezilla, or did you do something else afterwards?

Which version of Clonezilla did you use? There seems to be some new features, that I have not used.

[hr][/hr]
When there are this kind of problems with cloning, it might work better (faster and more likely to succeed) to make a fresh installation, and copy your personal data afterwards. You can install program packages when you need them (instead of trying to install everything that was installed in your old system).

---

### Post by jambyc on 2017-12-30
Latest stable clonezilla-live-2.5.2-31-i686-pae

---

### Post by jambyc on 2017-12-30
Ok 

I have cloned again and this time clonezilla said

[ATTACH=CONFIG]277971[/ATTACH]

---

### Post by sudodus on 2017-12-30
> **jambyc said:**
> Latest stable clonezilla-live-2.5.2-31-i686-pae

My newest iso file is clonezilla-live-2.5.0-25-amd64.iso (downloaded May 21 2017).

> **jambyc said:**
> Ok 

I have cloned again and this time clonezilla said

[ATTACH=CONFIG]277971[/ATTACH]

I think the yellow line indicates an error. (I have not seen this error before and don't know what is wrong with the partition.)

---

### Post by jambyc on 2017-12-30
[sudodus]("https://ubuntuforums.org/member.php?u=1499021")[COLOR=#000000][FONT=Ubuntubeta] 

[/FONT][/COLOR]Thank you for you support. I have asked on clonezilla forum. I will see what they come up with and post link for any future support to anyone.

---

