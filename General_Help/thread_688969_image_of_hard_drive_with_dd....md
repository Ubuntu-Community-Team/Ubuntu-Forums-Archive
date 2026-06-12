---
title: "image of hard drive with dd..."
date: 2008-02-05
forum: General Help
---

### Post by Mia_tech on 2008-02-05
I just made an image of my hd with this code I came across, but I need to restore the image and don't know the code to decompress and put it back on the hd... little help!

On the destination machine:
nc -l -p 5000 | gunzip | dd of=/dev/sda bs=100K

On the source machine:
dd if=sda bs=100K | gzip --fast| nc 1.2.3.4 5000

---

### Post by bodhi.zazen on 2008-02-05
I have not seen it done that way, link ?

This is a nice link on dd, hope it helps : 

[http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)

---

### Post by Mia_tech on 2008-02-06
Thanks for the link....here's a much nicer way and less complicated way to do it

to create the image

# dd if=/dev/hda | gzip > /mnt/hdb1/system_drive_backup.img.gz

to restore the image

# gzip -dc /mnt/hdb1/system_drive_backup.img.gz | dd of=/dev/hda

---

### Post by hyperair on 2008-02-06
Firstly, it's not compressed. Notice that on the source machine, you've piped your output through "gzip --fast" which compresses it, then on the destination machine, you've piped your input through "gunzip" which decompresses it.

Secondly, to restore the image, just swap the commands. The one you ran on the source machine now runs on the destination machine, and vice versa. 

NB: This is only possible because both file names are the same. If they aren't then you swap the commands but keep the file name.

---

### Post by Mia_tech on 2008-02-08
I use this commands to create and restore my image and after rebooting the system all I got is a blank screen and a  blinking cursor.... am I missing something here?

o create the image

# dd if=/dev/hda | gzip > /mnt/hdb1/system_drive_backup.img.gz

to restore the image

# gzip -dc /mnt/hdb1/system_drive_backup.img.gz | dd of=/dev/hda

---

### Post by bodhi.zazen on 2008-02-08
Can you tell us more ?

Are you doing this from a live CD ? (I hope so)

what is the size of system_drive_backup.img.gz ? (did the initial dd / gzip work ?)

What is the contents of hds (can you mount it with a live CD an take a peek ?)

I doubt it, but did the uuid change on the partition ?

---

### Post by Mia_tech on 2008-02-08
well to answer some of your questions, yes it was done from a live cd, knoppix in this case, and the image was created of about 800M on a network share, and it was from a VM windows xp,  but when I tried to restore it.... it is not booting anymore... I'll have to boot again and take a look on the hd and see what's it's content....I'll get back at you with that answer

---

### Post by Mia_tech on 2008-02-08
sudo mount -t ntfs /dev/hda /mnt/disk
Failed to mount '/dev/hda': Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
made to NTFS by this software.

---

