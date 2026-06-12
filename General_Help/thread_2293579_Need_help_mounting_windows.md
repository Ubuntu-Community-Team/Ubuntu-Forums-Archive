---
title: "Need help mounting windows"
date: 2015-09-05
forum: General Help
---

### Post by sean102 on 2015-09-05
when i try to view the contents of my computer(ubuntu is on my external hard drive) with the file manager i get this error
"Error mounting /dev/sda4 at /media/sean/Windows: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/sean/Windows"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option."

Can someone please help me fix this as i intend to use ubuntu as a rescue disk that scans my pc with antivirus?

---

### Post by yancek on 2015-09-05
The problem is stated explicity in the output you posted.

> The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting)

The standard with new windows is to have it default to hibernate rather than to shut down so it seems to boot faster.  Do a full shutdown as instructed.

---

### Post by sean102 on 2015-09-06
K thank you, i will try that.

---

### Post by sean102 on 2015-09-06
I tried shutting it down and now get this error
"Error mounting /dev/sda4 at /media/sean/Windows: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/sean/Windows"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option" its not in hibernation

---

### Post by yancek on 2015-09-06
You might try searching the forums here for similar problems as I've seen numerous similar posts.  In addition to rebooting there are several options such as fast boot that also need to be disable in the BIOS/setup.  Also look for any options relating to hibernation.  I don't use windows 8 or later so??

---

### Post by sean102 on 2015-09-06
I got it to shut down fully by typing "shutdown -s -t 0" in command prompt

---

### Post by chemist931 on 2015-09-07
I believe that this command will mount the drive in a read only state:

sudo mount -t ntfs-3g -o ro /dev/sd?? /media/windows

You will have to first make sure that the /media/windows folder exists.  I have also only used this command once, you may want to double check that for legit.

---

