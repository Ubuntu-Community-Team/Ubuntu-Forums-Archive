---
title: "Syntax help ..."
date: 2015-12-02
forum: General Help
---

### Post by asearle on 2015-12-02
Hallo Everyone,

My Ubuntu refuses to boot and gives me the "BusyBox" message ...

BusyBox ...
Enter 'help' for a list of built-in commands.
(initramfs)

I found a solution (on another forum) ...

[http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox]("http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox")

... which seems very promising.  But I have a syntax problem:

I need to pick up a list of superblocks using this command ...

```
sudo dumpe2fs /dev/sda2 | grep superblock
```

... with, I image, the list being written to the file "superblock" which, arrgghh, I cannot find.  I tried a few permutations but then got a blank output file.  I then removed the "grep" part of the command and the list of superblocks appeared but quickly scrolled off the screen.

Can anyone help me here?  How do I get either a.) the screen to not scroll or b.) the command to write to a file that I can find.  I'm sure there's a Linux guy out there who can tweak my syntax for me or give me a little tip(?)

Many thanks,
Alan

---

### Post by btindie on 2015-12-02
No, wrong, it doesn't write it to a file.

dumpe2fs writes a load of information about the file system to a PIPE that is passed to the grep command and that filters the results for lines that contain the word 'superblock'. The results will be displayed on the screen.

If it scrolls off the screen I think you should be able to scroll back up using "Shift+PageUp". Alternatively you can redirect the output to a file by appending '> /tmp/output' which will create a file called 'output'.... Or you can pipe it to a pager. I think busybox is limited to 'more' so you can pipe the output by appending ' | more' to your command.

---

### Post by asearle on 2015-12-02
Many thanks: That explains it.  I re-ran the command (with your explanation I now understand how it should work) but somehow no superblock was found.  I'll investigate and post my results.  Many thanks, Alan

---

### Post by btindie on 2015-12-02
Have you got the correct partition? /dev/sda2 is what they used in their example but for you it could be different.
```
sudo fdisk -l /dev/sda
```
will list the partitions on your first harddisk.
It may be that you want to instead use /dev/sda1 if you've just installed it all to a single partition. Or if you're using LVM then it'd be something like /dev/mapper/vg_system-lv_root (depending on your volume group name).

---

### Post by asearle on 2015-12-02
Yes, I ran it with the correct partition ( /dev/sda1 ) and, indeed, without the grep statement, a whole lot of information is delivered.  But nothing with "superblock".

This is a bit of a shame because the solution that I wanted to implement (for my BusyBox / non-boot problem) seemed very promising ...

[http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox](http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox)

I'll keep investigating ... or maybe you have a tip/suggestion?

Many thanks,
Alan

---

