---
title: "Can't boot to 16.04. Only get Grub rescue prompt. Boot repair not fixed"
date: 2018-04-25
forum: General Help
---

### Post by nitram1963 on 2018-04-25
After starting my Ubuntu PC on Sunday morning it only bootsto grub rescue prompt (it's not dual boot). There was a serious electrical storm the night beforeand the PC was on. Maybe a coincidence.

The attempted fix: I have been booting to a live version of Ubuntu froma CD (same as the installed version - 16.04) and have run the boot-repairprogram several times. Both the downloaded version / auto fix option, 3 or 4times plus the manual terminal window method, mounting the system to a temp2 folder and manually installing anew version of grub following guides I found on this site.

Nothing seems to work although the live install mounts mydrive and I can see all my files.

I have a 64gb SSD drive
/dev/sda1 - *Boot 51gb
/dev/sda2 - Extended drive 8gb
/dev/sda5 - SWAP file 8gb 

If I type in the grub prompt: &#8220;ls (HB0)&#8221; it returns &#8220;error HB0not found

I could do a rebuild but I don&#8217;t really want to when itseems that there is little wrong and it&#8217;s a common issue.

I did a &#8220;paste bin&#8221; but when I go to it, it doesn&#8217;t work (don&#8217;tknow why &#8211; deleted?) so will try again tonight:

[http://paste.ubuntu.com/P/3d3kB6Tvb/]("http://paste.ubuntu.com/P/3d3kB6Tvb/")

What should I try next?

---

### Post by yancek on 2018-04-25
> [FONT=Calibri][COLOR=#000000][SIZE=3]*There was a serious electrical storm the night beforeand the PC was on*[/SIZE][/COLOR][/FONT]

Best to shut down the computer and unplug it in situations like that.
Best thing to have done with the bootinfoscript is to select the option to Create BootInfo Summary.  Trying the repairs when you don't know the problem isn't helpful so I would suggest running it again and trying to post a link here.  There are a number of members who are very knowledgeable about boot problems.

 > [FONT=Calibri][COLOR=#000000][SIZE=3]If I type in the grub prompt: “ls (HB0)” it returns “error HB0not found[/SIZE][/COLOR][/FONT]

That is correct and expected behavior, the command is:  ls   OR ls (hd0)  Try running ls first.  The H and D are for Hard Drive, need to be lower case letter.
From the info you posted, you seem to have a Legacy install so you could try the commands below and if the Grub files are not corrupted, it should boot.  Make a note of specifically what happens if it fails and post back.  Enter each line separately at the grub> and hit Enter after writing in each line:

> set root=(hd0,msdos1)  (hit the Enter key)
chainloader +1  (hit the Enter key)
boot  (hit  the Enter key)  

If that fails, you will need to get the actual kernel names.

---

### Post by nitram1963 on 2018-04-25
[COLOR=#000000]*set root=(hd0,msdos1) (hit the Enter key).    This was ok but other 2 commands were unknown*[/COLOR]
[COLOR=#000000]*chainloader +1 (hit the Enter key)*[/COLOR]
[COLOR=#000000]*boot (hit the Enter key)*[/COLOR]

I then tried again using a live CD as follows and with the same results - grub rescue
HELP

```
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev &&
> sudo mount --bind /dev/pts /mnt/dev/pts &&
> sudo mount --bind /proc /mnt/proc &&
> sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
root@ubuntu:/# grub-install --recheck /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-119-generic
Found initrd image: /boot/initrd.img-4.4.0-119-generic
Found linux image: /boot/vmlinuz-4.4.0-116-generic
Found initrd image: /boot/initrd.img-4.4.0-116-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# exit &&
> sudo umount /mnt/sys &&
> sudo umount /mnt/proc &&
> sudo umount /mnt/dev/pts &&
> sudo umount /mnt/dev &&
> sudo umount /mnt
exit
```

---

### Post by yancek on 2018-04-25
Your initial post indicates that you have an Extended partition which contains one logical partition with swap.  With Linux systems, it is possible to have a Legacy/MBR system with gpt so change the line:

> set root=(hd0,msdos1)

TO:

> set root=(hd0,gpt1)

and then repeat the other two lines.  I've used this method with both GPT and MBR and it works.  If this fails, post the results.  You might try from the Live CD then to mount sda1 to see if you have the necessary files.

---

### Post by deadflowr on 2018-04-25
Please use code tags when posting terminal output.
It retains the proper formatting.

---

### Post by nitram1963 on 2018-04-25
Thanks Yancek, but the grub rescue still does not recognise the commands 2 & 3.

I have run a live session again and posted the output from it here. Maybe this will throw some light on the issue?

[http://paste.ubuntu.com/p/6ZBJF4fwwj/](http://paste.ubuntu.com/p/6ZBJF4fwwj/)

---

### Post by oldfred on 2018-04-25
Have you tried running fsck on your / partition?

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by yancek on 2018-04-25
I have used those commands with success in the past but I just booted an external MBR drive and used those commands to try to boot a Legacy Linux system on the first partition and got an 'invalid signature' error.  What you could try is directly booting the kernel.  When you are at the grub>, do:

```
ls (hd0,msdos1)/boot/
``` 

If you do have an MBR system, that should show the Grub directory and a number of files including the kernel, a file beginning with vmlinuz.  It should also show an initrd file.  Then do the following commands, hit the Enter key after each line.  You will need to rename your vmlinuz and initrd files to what you got with ls as the below is just an example from an older system.  If that doesn't work, I don't know what else to try.

> set root=(hd0,msdos1)
linux /boot/vmlinuz-3.13.0-24-generic root=/dev/sda1
initrd /boot/initrd.img-3.13.0-24-generic
boot

If the above fails due to multiple disks and naming of disks changing, you could use the UUID on the Linux line which you can get with the command:  sudo blkid
Replace the UUID shown below with the one you get for sda1 from the blkid command:

> linux /boot/vmlinuz-3.13.0-24-generic root=UUID=02607a3a-05c4-41ed-8212-8e259326f4f0i

---

### Post by nitram1963 on 2018-04-26
Fixed. So thanks very much to you both but oldfred gets the stars &#11088;&#65039;.

ran [COLOR=#000000]sudo e2fsck -f -y -v /dev/sdb1 

but then had to remove the -p as it didn&#8217;t like the auto response. As it happens there were several disk errors, not too many and within a few minutes it was finished.

Rebooted and got then grub screen but no Ubuntu.

Booted again into live Cd session again, ran boot-repair (recommended option) reboot and all fixed.

Very happy, thanks a lot. I do suspect it was the storm caused some kind of blip or corruption.[/COLOR]

---

