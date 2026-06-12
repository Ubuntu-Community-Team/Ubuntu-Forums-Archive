---
title: "how to convert windows hard disk file system to ubuntu's?"
date: 2017-06-06
forum: General Help
---

### Post by ronjjjg8885 on 2017-06-06
my system is on ssd
but i've an hd too.
i want to convert the hd that was being used by windows to linux file system [U]without losing data.

thanks[/U]

---

### Post by LastDino on 2017-06-06
First and most logical thing would be to do here is to copy your data to some other HD/Disk

Without doing that you will not be able to turn entire disk in one go to Linux partition systems. By the way, Linux reads NTFS just fine, if installing is the problem, you just need one partition which is ext4 for your "/".

Be clear on what you want to do, and convey same here.

---

### Post by Impavidus on 2017-06-06
I'm not aware of any tools that can convert NTFS into ext4 in place. The file systems are very different. And even if it exists, you'd need backups first as a power failure during the conversion would destroy the entire partition. So I suggest you copy all data to a backup drive, then delete the NTFS partition, create an ext4 partition and copy everything back.

Ubuntu can read and write NTFS, but not fix it. It's better not to rely on NTFS if you don't have Windows to fix it.

---

### Post by ronjjjg8885 on 2017-06-06
i already have a backup but the backup is encrypted with veracrypt as a whole device and not a container.

i will have to be sure that the backup is working.

after that i just need to format the volume with "Disks" and make an ex4 partition?
anything else i need to know about?

---

### Post by LastDino on 2017-06-06
After making sure backup is functioning (As I've no experience with veracrypt), using Linux tools like Gparted to handle the partitioning is best and recommended way to go.

Most people here will swear by using Linux tools for Linux partitioning, otherwise there have been issues. If you have Ubuntu on SSD, it should be easy, if not, boot in live USB or DVD.

---

### Post by ronjjjg8885 on 2017-06-06
thanks

what should i do if ubuntu does not recognize my encrypted external HDD?

i've found that:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

but it seems much more complicated to mount a drive than what i've thought.
will it work with encrypted drive if at last i succeed with it?

---

### Post by LastDino on 2017-06-06
Either get rid of the encryption and try or there is Varacrypt available for Linux too, right? 

I've never used encrypted drives across platforms, so you'll have to check this on your own or probably wait someone else to come along.

---

### Post by ronjjjg8885 on 2017-06-06
i think that there is a chance that i've tried to mount the wrong device.
i'm saying this because it is seems that the external hard drive is not even recognized as a drive by my linux.

are you actually saying that if it is encrypted there is this chance of not being able to even mount the device to ubuntu?

i got very confused by how mounting devices work on ubutnu

---

### Post by LastDino on 2017-06-07
I'm not aware of the specific functionality of your crypt software but no, you can mount encrypted devices fine. Usually you will see it in you gui file manager.

---

