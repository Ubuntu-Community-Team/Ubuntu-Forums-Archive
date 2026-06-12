---
title: "system will not boot"
date: 2019-05-09
forum: General Help
---

### Post by stompin-tom on 2019-05-09
I have Xubuntu 18.04 on my old dell desk top. It will not boot up. This is the message I get- /dev/sdal contains a file system with errors, check forced. /dev/sdal: Inodes that were part of a corrupted orphan linked list found, /dev/sdal: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. (ie., without -a or -p options) fsck exited with status code 4  The root filesystem on /dev/sdal/ requires a manual fsck  Busy Box V1.27.2 (Ubuntu 1:1.27.2-2ubuntu 3.2) built in shell (ash) Enter 'help' for a list of built-in commands      I am not very savvy with any of this. I have xubuntu 18.04 on a flash drive, if that will help. Thank you. Tom.

---

### Post by CatKiller on 2019-05-09
Booting from your flash drive and running fsck to check your hard drive is the thing to do.

You might be fortunate and the errors are fixable but, if they came on suddenly, you'll have to face the prospect that your disc has failed.

---

### Post by Rubi1200 on 2019-05-09
Just to help us get a clearer picture of the situation, what happened prior to this?

Was everything working normally? Were there some updates or other changes to the system?

fsck needs to be run on an unmounted partition, so as CatKiller mentioned, boot with a live CD/USB and then open a terminal to run the command:

```
sudo fsck /dev/sdxx
```

Where xx represents the drive and partition.

If you are unsure run this first:

```
sudo fdisk -l
```

This will display the drives and partitions.

I recommend first running fsck without any parameters to see what it returns in terms of types of errors.

Post the output here if you want us to take a look and offer advice.

Thanks.

---

### Post by stompin-tom on 2019-05-09
It will not boot from the flash drive.

---

### Post by stompin-tom on 2019-05-09
It will not boot from the flash drive, so i can't enter any commands, except maybe on the error page that came up, which is what i have copied to the original thread.

---

### Post by Rubi1200 on 2019-05-10
If it is an older machine then you probably have legacy BIOS?

At startup are you able to get into BIOS at all? I think Dell uses F2 or F12.

If you can get in then make sure boot order is set to use a flash drive as first priority and then see if you can get into the live media after rebooting.

If yes, we can work from there.

If not, then when it comes back to BusyBox type exit. If it drops you to a shell with initramfs type exit then post back here if errors were mentioned.

Edit: in your first post you write /dev/sdal but surely you mean /dev/sda1?

If yes, when you get back to BusyBox type this:

```
sudo fsck /dev/sda1
```

Let us know what it returns as errors.

---

### Post by stompin-tom on 2019-05-10
It will not boot from flash drive when I go into bios with F12 and select usb. You are correct, it should be /dev/sda1 - I am transcribing this onto paper, then onto forum. When I type sudo fsck /dev/sda1 into BusyBox, it says- sudo: not found. When I type in help after (initramfs) A list of Built-in commands 8 lines long come up. Any help appreciated. Thanks. Tom.

---

### Post by Rubi1200 on 2019-05-10
My mistake, it has been so long since I was there (if you know what I mean).

I think just running fsck should be enough:

```
fsck /dev/sda1
```

Post back errors or other messages here.

---

### Post by stompin-tom on 2019-05-12
Thank you Rubi- when I entered fsck /dev/sda1  a list of errors and fixes came up. There are still some problems, but it is working again.

---

### Post by Rubi1200 on 2019-05-12
After the command ran did it force the fixes?

Working again, I assume this means you can log in and use your system normally?

If there are other problems, not related to the file system, please let us know so we can try and help you sort it out.

In any event, I am pleased to hear you can work normally again.

If you think the problem is resolved then mark this thread Solved using thread tools at the top of the first post.

Best of luck.

---

