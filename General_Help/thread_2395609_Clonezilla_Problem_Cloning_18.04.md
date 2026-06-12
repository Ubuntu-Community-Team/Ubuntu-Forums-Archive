---
title: "Clonezilla Problem Cloning 18.04"
date: 2018-07-04
forum: General Help
---

### Post by mountainman70 on 2018-07-04
I am dual booting W10 & Ubuntu & have been using Clonezilla to clone my Hard Drives without any problems. I have just installed Ubuntu 18.04 along side of W10 and have it set to my specs. I am trying to clone it but keep getting this error:

extfsclone.c: bitmap error at 1 group

I do not know how to correct this. Any simple suggestions will be appreciated. Thanks.

---

### Post by howefield on 2018-07-04
Are you using a current version of Clonezilla ?

---

### Post by mountainman70 on 2018-07-04
> **howefield said:**
> Are you using a current version of Clonezilla ?

Thanks for replying howefield. 
The version I was using is 2.1.1-7. I remembered that I had made a new copy several weeks ago & had used it to clone my dual boot w10 7 16.04 without any problems. I found it & tried it but it would not boot. I D/Led Clonezilla-live-20180620-bionic-amd64 & burned it to a dvd. However when I try to run it I get this error: Failed to load ldlinux.c32 & when I press a key it goes back to desktop. I am about ready to go back to 16.04.

---

### Post by VMC on 2018-07-04
[Read This]("https://sourceforge.net/p/clonezilla/discussion/Help/thread/de8ea4fe/")

---

### Post by mountainman70 on 2018-07-04
> **VMC said:**
> [Read This]("https://sourceforge.net/p/clonezilla/discussion/Help/thread/de8ea4fe/")

I had read that but if it is saying to use shell command prompt then I do not know what commands to enter. I just use the basic of Clonezilla. I did a live usb of 18.04 & ran sudo fsck /dev/sda5 & it said it was clean.

---

### Post by sudodus on 2018-07-04
How did you install Clonezilla?

Did you clone Clonezilla from the iso files to a USB pendrive and/or create a DVD disk with a reliable tool?

Did you check the md5sum of the iso files?

Did you check that it works correctly in another computer?

[hr][/hr]
Did you check that the drive hardware is good? You can check the S.M.A.R.T. information with Disks (alias gnome-disks),

[S.M.A.R.T. information of HDD and SSD](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors-what-should-i-do-now/972983#972983)

If there are sectors on the drive, that are difficult but not impossible to read, **ddrescue** may help you read them, and if there are bad sectors (impossible to read), it can at least clone what can be read (and skip over the bad sectors in a controlled way), so that everything, that can be read will be cloned.

There may also be problems, if the file system is damaged.

[Repair the partition table and file system of a pendrive](https://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

Scroll down to 'Advanced repair of a partition table, file system and/or recovery of files'

---

### Post by mountainman70 on 2018-07-04
Sorry to be so long replying, but been enjoying the 4th of July with family. Hope all of you have had a wonderful 4th of July. 
I have found my problem. I have had a bad internet connection causing bad downloads. I went back & deleted all Clonezilla D/Lds & then D/Led new ones and made sure they were from sourceforge. I made a usb drive of 2.5.5-38 & one of bionic. Both cloned my HD's without any problem. I then made a cd of 2.5.5-38 & it cloned without any problem. I will try to make a DVD of bionic tomorrow. Right now I am going to watch fireworks.

Thanks to all who replied. It made me think of possible solutions to my problem which turned out to be corrupted downloads.

---

