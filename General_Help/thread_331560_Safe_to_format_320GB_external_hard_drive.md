---
title: "Safe to format 320GB external hard drive?"
date: 2007-01-04
forum: General Help
---

### Post by QwUo173Hy on 2007-01-04
I have a 320GB USB external hard drive. I've only just learned that vfat cannot handle some characters and therefore I cannot backup all my files. If I format the drive to ext2 or ext3 will this solve my problem? Perhaps there is a more suitable workaround that someone could help me with (without renaming these file, this is a no no for me).

Thanks for any help, the drive is sitting idle since I got it and I'd be thrilled to get it going.

Regards,
Jarlath

---

### Post by Ocxic on 2007-01-04
yes re-formatting your drive will prolly solve your probleme, may i suggest XFS or ResierFS filesystems. the are slightly faster. personally i use XFS but its up to you.

---

### Post by rattking on 2007-01-04
Hi
you could also tar your files before backup. that would help with the filename / permission problems with vfat.. your drive would still be accessable from windows if need be

tar cpf /media/vfatdrive/backup.tar * 
as an example
tar cpzf /media/vfatdrive/backup.tar.gz * 
to add gzip compression
hope that helps
edit.. ohh i guess you could use a gui app for that too.. but thats hardly as fun :)

---

### Post by QwUo173Hy on 2007-01-04
Thanks Ocxic. Iif I want to use a format that windows users can access when I loan them the drive what should I choose? I'm guessing XFS would be the most compatible but I don't know.

---

### Post by rattking on 2007-01-04
> **jarlath said:**
> Thanks Ocxic. Iif I want to use a format that windows users can access when I loan them the drive what should I choose? I'm guessing XFS would be the most compatible but I don't know.

XFS or ResierFS are probably the least compatible filesystems with windows
ext2 I think would be the most compatible.. but still need a extra app or driver for access

---

### Post by QwUo173Hy on 2007-01-04
Thanks rattking, I didn't know that you could do that with tar, that's very useful.

I would prefer not to compress the files so that I can access them quicker. The capacity of the drive allows me to do this, but the format doesn't unfortunately. A filesystem that is compatible with both OSes and also supports the full charset would be ideal, if such a filesystem exists.

---

### Post by dannyboy79 on 2007-01-04
you can add utf8 or whatever to the mount option for you vfat partition can't you? I don't have any issues with filenames for my 250gb vfat hard drive. check out man mount and you can read all about it.

---

### Post by khedron on 2007-01-04
Unfortunately, filesystem compatibility is quite lacking between Windows and Linux. I'll run through some of the options that I think should be considered, and that I am considering for my backup drive.

1. Does NTFS support the characters you need? To write to an NTFS partition on Linux you would need the ntfs-3g package. I have heard it is quite stable, but I have not used it too much.

2. Partition your drive so that it has a large ext2 (or whatever) partition and a smaller FAT (or NTFS) partition. Your friends can use the FAT partition, and if you want them to access the backup, they can install the ext2 driver (see option 3, below).

3. ext2 + Windows driver: this seems like a good option if your friends don't mind installing a new driver on their system. I think it was quite easy - just unzip, copy the driver files to C:/Windows/system32/drivers and reboot, I think.


4. Re tar: I seem to remember something like if you tar the files you will only be able to access them sequentially, like on an old tape backup. That would scupper any plans you have of tarring the files, since in order to access a file at the end, you would have to read through the whole tar file. 

On a quick Google it seems that compressing them with bzip2 might make an index of the tar file for easy file seeking, but I'm not sure (my Google-foo isn't great this time of night). You will have to play around with it to see if it is faster. Use bzip2 --fast for the quickest and least compression.

---

### Post by QwUo173Hy on 2007-01-05
Thanks Dannyboy79, would you mind posting your fstab entry please?

khedron, thankyou for that. I will rule out the tar option as I want to be able to access the data easily. Nothing annoys my girlfriend more than me typing in a load of commands so we can watch a movie I have on another drive (although I get great pleasure from it :))

I think I willl also rule out NTFS because I want something that is quite reliable, since I will be storing so much data.

If dannyboy79s fstab entry helps me then I'll go with that. Otherwise I think ext2 would be a wise choice. And to be honest, it would give me peace of mind knowing that all that data is journalled.

---

### Post by dannyboy79 on 2007-01-19
sorry it took me so long to post back, here ya go:
/dev/hdb1       /home/daniel/fat32      vfat    rw,uid=1000,gid=1000,iocharset=utf8,umask=0000  0       0

---

