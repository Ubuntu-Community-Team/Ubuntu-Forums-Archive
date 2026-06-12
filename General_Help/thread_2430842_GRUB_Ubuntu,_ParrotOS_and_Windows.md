---
title: "GRUB Ubuntu, ParrotOS and Windows"
date: 2019-11-08
forum: General Help
---

### Post by malwin1234 on 2019-11-08
Hello,
 i have an encrypted lvm of ubuntu and one of parrot os. I just installed Parrot OS and i chose my Ubuntu boot partition for Parrot too. Now my grub is overwritten and i dont know how to boot into Ubuntu.

Any help is appreciated.

---

### Post by yancek on 2019-11-08
> I just installed Parrot OS and i chose my Ubuntu boot partition for  Parrot too. Now my grub is overwritten and i dont know how to boot into  Ubuntu.
Any help is appreciated. 		

You will need to clarify the above comment because as stated, if you chose to install Parrot OS to the same partition on which you had Ubuntu, you will have overwritten the Ubuntu install and it is not there to boot.  Can you boot Parrot?  If so, open a terminal and run this command and post the output here:

```
sudo parted -l
```

---

### Post by ajgreeny on 2019-11-08
With an lvm installation of Ubuntu you will have had, as you implied, a separate /boot partition so you may not have overwritten your Ubuntu root partition as feared by yancek.

However, let's see exactly where you've got to at the moment.

See **Boot-Repair** in my signature below and follow the instructions there just to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the **pastebin** link you get which will show us a lot more about your system and its current setup.

---

### Post by yancek on 2019-11-08
I think I misread the original post.  Question is, now that you have installed Parrot, can you boot it?  If so, you should be able to run grub-mkconfig to update grub to include Ubuntu.  Best to post the boot repair output if you have not resolved this issue.

---

### Post by oldrocker99 on 2019-11-08
I make two / partitions, and install each OS on one of them. Set it to boot from the first partition, and you'll get a menu on boot, from which you can select one or the other. That's how I dual-boot Manjaro and Ubuntu; each has some features the other doesn't.

It's pretty easy to do.

There are 2 kinds of people: Three Stooges fans, and women.
There are 10 kinds of people: Those who understand binary, and those who don't.

---

### Post by malwin1234 on 2019-11-10
Hello, i already used Boot Repair, but here's my Boot Info Summary: [https://paste.ubuntu.com/p/SCxbpFVmDS/](https://paste.ubuntu.com/p/SCxbpFVmDS/)

Thanks for the replies

---

### Post by yancek on 2019-11-10
Look at lines 559-561 in boot repair shown below, specifically the line beginning with search which shows the UUID for the Ubuntu partition, beginning with e355...:

> menuentry "Ubuntu du Fotze" {
search --fs-uuid --no-floppy --set=root e3554851-1997-4e4b-8388-343ab08dce99 
chainloader (${root})/efi/EFI/ubuntu/grubx64.efi

Then look at any of the grub.cfg menuentry lines for Parrot OS, beginning with line 325.  On lines 333 and 335, you see the UUID above which was the Ubuntu partition as the UUID for the install of Parrot.  That is /dev/sdc2 on the 238GB drive and you have installed Parrot over the previous Ubuntu install.  The only sign of Ubuntu in the boot repair output is lines 543-549, the EFI entry info which is on the EFI partition and will remain there but can't be used as Ubuntu no longer exists.

---

### Post by malwin1234 on 2019-11-10
So what can i do now?

---

### Post by yancek on 2019-11-10
> So what can i do now? 		

You need to reinstall Ubuntu completely as it is gone, overwritten by your Parrot install which is using the entire drive.  You need to resize/shrink one of the partitions to create space on which to install Ubuntu if you want to use the same drive.  You are using encryption, LVM and RAID, none of which I am familiar with so wait for someone else to post or start a new thread on installing Ubuntu on the same drive with another Linux OS and LVM, or keep searching online.

---

### Post by malwin1234 on 2019-11-11
It is not the same drive, I think you misunderstood

---

### Post by yancek on 2019-11-12
> It is not the same drive, I think you misunderstood 		

What's not the same drive?  You're being a little cryptic if you want help.  What drive is not the same and the same as what?  Other than the EFI entries, there is no sign of Ubuntu.  So please be more detailed.

---

