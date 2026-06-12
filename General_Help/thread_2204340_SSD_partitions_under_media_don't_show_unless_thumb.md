---
title: "SSD partitions under /media don't show unless thumbdrive installed on boot"
date: 2014-02-07
forum: General Help
---

### Post by cigtoxdoc on 2014-02-07
The SSD on my Dell Vostro 3500 is partitioned as shown in the attached PDF file.  Folders under /media are not accessible unless I have a thumbdrive (not a special one) in a USB port when I boot.  If I don't out the thumbdrive in before booting, I cannot see/access /media/OS (Win XP Pro), /media/MyChemiatry (scientific data), and /media/MyDocuments (docments, PDFs, etc.).  Everything works fine in terms of getting to these directories if I have a thumbdrive in a USB port a time of boot.

What do I need to do to make sure these partitions are mounted at the time of boot ao I can get to my data files and documents?  I do much moving of files among the partitions (particularly taking files from the ntsf partition and adding them to /media/MyChemistry or /media/MyDocuments.  I use kdesuo with Dolphin or Konqueror to make these moves.  I have set files permissions so that I am the owner of the MyDocuments and MyChemistry folders and their subfolders and files.

Thank you,

John

---

### Post by tfrue on 2014-02-08
Would you post the output of:
```
cat /etc/fstab
```
and the output of:
```
sudo blkid
```
and:
```
lsblk
```

Thanks,
Chris

---

### Post by cigtoxdoc on 2014-02-08
Thank you, Chris.  The information you requested is shown in the attached PDF file.

John

---

### Post by tfrue on 2014-02-08
According to the /etc/fstab file, you do not have those mount points mounting at boot. That's why you can't access them at boot, but they still exist and you an mount them with the mount command, like this:
```
sudo mount -t ntfs-3g /dev/sda1 /media/OS
```
or
```
sudo mount -t ext4 /dev/sda3 /media/MyChemistry
```

Now if you want them mounted at boot, we will edit the /etc/fstab file so the boot script will mount them. When we edit the /etc/fstab file, we want to use the UUID of the disk so it will be more reliable incase /dev/sda2 is /media/OS the first time you boot, then changes to /media/MyChemistry the second time. Here is a link to a website that will give you plenty of info about editing the /etc/fstab file, but I will give you examples that will work.
(Remember that "#" are commented and ignored by BASH but should be inserted so we can look back at the file and know what we are editing.)
```
 sudo vi /etc/fstab
```
You will need to use the arrow key to scroll to the bottom and press 'o' and type:
```

# Win XP partition
UUID="06550BF50F315FAE" /media/OS ntfs-3g defaults 0 0

# MyChemistry partition
UUID="e7ac90b2-8959-4159-8ca4-9cc5a0018bf2" /media/MyChemistry ext4 defaults 0 0

# MyDocuments partition
UUID="a891270a-7acf-4eb0-8e20-1529af340c88" /media/MyDocuments ext4 defaults 0 0
```
Then we will save the file by type a ":" (colon) then type "wq" (ex. :wq) and then when you reboot you should have everything mount at boot. You could also hold "Shift" and type two(2) Z's.
After you edit the file you could type: ```
sudo mount -a
```
To mount everything in the /etc/fstab file.

Good luck, 
Chris

---

### Post by cigtoxdoc on 2014-02-09
Thank you very much, Chris.  Your solution worked and problem is solved.  If I told you the first time I used the vi editor, I would be dating myself (AT&T Unix on a Mattson Instruments FT-IR spectrophotometer).  It was much easier to type gksudo gedit and cut and paste from your post.

Problem solved.

John

---

### Post by tfrue on 2014-02-09
I forgot the link to the website LOL! Here it is incase you are wondering.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

But I'm glad that it worked for you and that I could help! 

Chris

---

