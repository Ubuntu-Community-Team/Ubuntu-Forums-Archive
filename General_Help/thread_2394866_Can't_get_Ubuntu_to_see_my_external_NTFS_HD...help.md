---
title: "Can't get Ubuntu to see my external NTFS HD...help please!"
date: 2018-06-22
forum: General Help
---

### Post by darkcyber on 2018-06-22
I am running Ubuntu 14.04 LTS and I have a Western Digital 4 TB NTFS external hard drive I am trying to get Ubuntu to see and so far I'm having no luck. I thought this version has the built in ability to see NTFS drives. I have checked under the dolphin file manager and all I see is my internal hard drive. Any help to get it to see my external NTFS drive would be appreciated.

---

### Post by ajgreeny on 2018-06-22
There could be a number of different things causing the problem.

Is the drive formatted as a single partition or are there multi-partitions on the disk?
Did your Windows system create partitions or did Windows format the full unpartitioned drive? The latter will never be seen in Linux as far as I'm aware.
A 4TB drive will have to use a GPT partition table for it to be detected and usable if I remember correctly.
Also remember that if you did not "Remove safely" from Windows the disk will still be in use as far as Linux can detect, so you will need to attach it again to a Windows OS then remove it properly

---

### Post by darkcyber on 2018-06-22
Actually, I think I just started using it straight out of the box...exactly as it came. I don't remember me formatting it. When hooked to my Windows 10 PC it shows NTFS and 3.63 TB of total space. No big deal about having to get this one single drive to work. I just have a ton of music from my Windows computers I need to get on this Ubuntu computer. I have other smaller external hard drives. I have been able to get the NTFS drives to show up in CentOS, but not successful on Ubuntu.


> **ajgreeny said:**
> There could be a number of different things causing the problem.

Is the drive formatted as a single partition or are there multi-partitions on the disk?
Did your Windows system create partitions or did Windows format the full unpartitioned drive? The latter will never be seen in Linux as far as I'm aware.
A 4TB drive will have to use a GPT partition table for it to be detected and usable if I remember correctly.
Also remember that if you did not "Remove safely" from Windows the disk will still be in use as far as Linux can detect, so you will need to attach it again to a Windows OS then remove it properly

---

### Post by yancek on 2018-06-22
You can check the partitions, filesystems and whether it is GPT using the command below as root (sudo):

```
parted -l
``` 

Check to see if you have ntfs-eg installed.

---

### Post by vanadium on 2018-06-23
I would suggest first connecting it to you Windows machine, have it checked with the Windows drive checking tools, then unmount it properly from the Windows machine (or shut the Windows system fully down - no hibernate). That should ensure that the NTFS volume is in a consistent state, and even a version as old as Ubuntu 14.04 (you should be using 16.04) should mount a clean ntfs volume automatically.

If that does not work, then it will be time for some diagnostics, and to try to mount it manually to learn from the error messages what might be the issue.

---

### Post by darkcyber on 2018-06-23
I will check on that. I thought from what I read that ntfs-3g was installed in the OS itself, on 14.x.

> **yancek said:**
> You can check the partitions, filesystems and whether it is GPT using the command below as root (sudo):

```
parted -l
``` 

Check to see if you have ntfs-eg installed.

---

### Post by vanadium on 2018-06-23
> **darkcyber said:**
> I will check on that. I thought from what I read that ntfs-3g was installed in the OS itself, on 14.x.

There is no doubt about that. The problem will not be there.

---

### Post by darkcyber on 2018-06-23
OK, since this version cannot see an NTFS drive, then let me ask the question differently. I have a ton of .wav music files I have on my Windows 10 computer. How can I get them onto the Ubuntu 14.04 computer?

> **vanadium said:**
> There is no doubt about that. The problem will not be there.

---

### Post by yancek on 2018-06-24
Windows partitions on internal/external drives are usually accessible under /media/user by UUID.  Have you checked there?  Substitute you actual user name.  Do the partitions show using parted -l or fdisk -l?  If so, you should be able to manually mount them and copy from them.

---

### Post by vanadium on 2018-06-25
Does your partition show up in the output of "lsblk"? If yes, note the device name and try to mount the partition using the terminal. If tat fails, the error message may provide an indication as to what is wrong. If not, do the following to see if/how the system recognizes the drive or what it tries to do with it:

- plug it out (perhaps best while system is shut down)
- Open terminal
- Plug the drive in
- Look at the last kernel output with the command "dmesg | tail 30" to see the last 30 lines. These lines might give a clue about what is going wrong.

---

### Post by sp40140 on 2018-06-25
Try different USB cable.
Just a while back, I got 8 TB WD drive. It came with Micro AB USB 3.0 SS cable (same port as samsung galaxy s5). The cable was bad. I used regular micro USB and it worked fine. 
The thing is micro usb is very slow compared to micro AB SS, so I got new cable and things have been fine.

Ubuntu doesn't have issue with NTFS. However, my 8TB came with ExFat.

---

