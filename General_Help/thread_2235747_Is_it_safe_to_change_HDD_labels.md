---
title: "Is it safe to change HDD labels?"
date: 2014-07-22
forum: General Help
---

### Post by ***J*** on 2014-07-22
I've been thinking about changing the label of one of my internal hard drives that I use for storage and have found that these four tools should do the job:


GParted
Disk Utility
e2label
tune2fs


What I want to know is if these are safe to use and will my data still be intact. I was initially going to use GParted 0.18.0 to change the label but a warning popped up just when it was about to commence which got me thinking about this. The hard drive has important data on it and unfortunately I don't have an empty one to experiment with. 


Which of the above four tools are the safest to use?
Should I unmount the drive first?
Are there any drawbacks to having spaces in the label? 
Any other precautions I should take?


I'm inclined to take the if it ain't broke don't fix it approach but if there is no risk in changing the label I'd go through with it.

---

### Post by mcduck on 2014-07-22
At least both e2label and tune2fs should be fine, and can be used for this purpose even if the drive is mounted. I'd advice against having a space in the label (not sure if that's even allowed or not), and keep in mind the max length is 16 characters. Otherwise small changes like this should not cause any issues (I've used tune2fs for much more complicated tweaks even with mounted filesystems without any problems), but if your drive is mounted using fstab, you might want to make sure it's done using UUID instead of device name or label before making the chance.

---

### Post by Dennis N on 2014-07-22
I use e2label. You don't need to unmount the partition to use it.

See existing label (if any)
```
dmn@Zotac:~$ sudo e2label /dev/sda3
Xubuntu_14.04
```
If none exists, you get no message.

Change label to New_Label
```
dmn@Zotac:~$ sudo e2label /dev/sda3 New_Label
```
Which I aborted since I like the existing label.

I consider it safe.

---

### Post by oldfred on 2014-07-22
I try to remember to include label when I create partition with gparted. So I often use Disks or Disk Utility to add label later. Once or twice I have used command line, so any of the methods should be fine.

If you manually mount partitions with Nautilus, it will use the label if it exists. So in that case it may be a bit safer to unmount first.

Almost no one uses labels to mount partitions(including me), but it is a good way to mount as then you provide your own consistency. It is mentioned usually almost as a footnote in the fstab instructions.

---

### Post by ***J*** on 2014-07-22
[FONT=arial]Thanks for the tips guys. I finally mustered up the courage to do this and it worked like a charm without even having to unmount. I opted for [COLOR=#000000]e2label and changed the label to 1.5TB_Seagate. All my data was left intact so I'm marking this as solved. Googling this I found a lot of suggestions on how to change the label but whether the data would be left intact or not constantly failed to be mentioned. I really didn't need to lose data because of me having to fool around with labels so I'm glad this worked out. [/COLOR];)[/FONT]

---

