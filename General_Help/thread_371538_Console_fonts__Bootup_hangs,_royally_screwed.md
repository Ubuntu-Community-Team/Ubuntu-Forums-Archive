---
title: "Console fonts?  Bootup hangs, royally screwed"
date: 2007-02-27
forum: General Help
---

### Post by Shrodinger on 2007-02-27
My laptop installation of Ubuntu is royally screwed.  I was trying to upgrade to feisty, and had the rediculously common problem of python versioning...  the fixes didn't work for me, and I was trying and trying, I think eventually making some progress.  I eventually had to stop part way through (ie, shutdown), and now the machine won't boot up!

Again with the last working kernel, with "Single user mode," (same as if I had quiet removed from the line of the usual grub entry, I guess) I see as the last words:



* Activating swap...                [ OK ]
* Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
                                               [ OK ]
* Mounting local filesystems...
* Configuring network interfaces...
* Setting up console font and keymap...


Did this give up at mounting local filesystems?  There are no OKs intentionally in the above recreation.  I have booted with rescue disks (the RIP disk, since I couldn't use reiserfsck on the ubuntu rescue), and checked my filesystem on /dev/hda3, it's all good.  I mounted it and looked around, it seems fine.  I tried to set the last digit of my root directory's entry in fstab to 0, but that didn't make a difference.  I doubt apt would have taken off some package without replacing it with an upgrade, right?

Can someone please let me know what I should do?  This is basically a killer blow to me, I need my lappy to live, and I don't have anything set up on Windows for it (although I kept the out-of-the-box installation on a tiny partition), so I am pretty screwed :(  Thanks in advance for any tips.

---

### Post by Shrodinger on 2007-02-27
Actually, I just found a bit of an issue!  On my drive, I don't have /dev/hda3, nor anything in /dev/disks, the latter of which appears in fstab.

How do I regenerate these devices?!

Thanks

---

### Post by vhhareesh on 2007-03-07
> **Shrodinger said:**
> My laptop installation of Ubuntu is royally screwed.  I was trying to upgrade to feisty, and had the rediculously common problem of python versioning...  the fixes didn't work for me, and I was trying and trying, I think eventually making some progress.  I eventually had to stop part way through (ie, shutdown), and now the machine won't boot up!

Again with the last working kernel, with "Single user mode," (same as if I had quiet removed from the line of the usual grub entry, I guess) I see as the last words:



* Activating swap...                [ OK ]
* Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
                                               [ OK ]
* Mounting local filesystems...
* Configuring network interfaces...
* Setting up console font and keymap...


Did this give up at mounting local filesystems?  There are no OKs intentionally in the above recreation.  I have booted with rescue disks (the RIP disk, since I couldn't use reiserfsck on the ubuntu rescue), and checked my filesystem on /dev/hda3, it's all good.  I mounted it and looked around, it seems fine.  I tried to set the last digit of my root directory's entry in fstab to 0, but that didn't make a difference.  I doubt apt would have taken off some package without replacing it with an upgrade, right?

Can someone please let me know what I should do?  This is basically a killer blow to me, I need my lappy to live, and I don't have anything set up on Windows for it (although I kept the out-of-the-box installation on a tiny partition), so I am pretty screwed :(  Thanks in advance for any tips.

Hi

I was trying to install 6.10 edgy on a compaq v6000 series laptop (AMD Turion 64x2 2G RAM nvidia Go6150 graphics), I go the same error.  The machine virtually hangs.

Please help

Thanks

Hareesh

---

### Post by Shrodinger on 2007-03-07
As far as I know, this has something to do with the drive manager...  I ended up using a rescue CD to secure-copy over my important stuff to a different machine, and then reinstalled :(

Good luck...

---

### Post by froghopper on 2007-03-12
I had this problem after a edgy to feisty upgrade.

I fixed it by booting from a liveCD. In a console window I typed:

sudo mount /dev/hda2 /mnt/hda2 <- change hda2 to your partition
sudo chroot /mnt/hda2 su
dpkg -i --force-all /var/cache/apt/archive/console-setup<some version number>.deb
dpkg --configure -a

Obviously something wasn't install properly or in the correct order. It will at least boot after that.

---

### Post by CoolkcaH on 2007-03-15
I'm having this problem too upgrading edgy to feisty...trying to solve it  now.

dpkg -i --force-all /var/cache/apt/archive/console-setup<some version number>.deb crashed with a "Soft crash detected on CPU#0" or something like that and I had to force shutdown.

I didn't find any bug report on this anywhere except this thread, shouldn't we open a bug at launchpad? Anyone has experience on bug reporting?

---

### Post by Loonux on 2007-03-31
I have the same problem. My Machine crashed when upgrading from Edgy to Feisty and now it hangs at the SETTING UP CONSOLE FONT AND KEYMAP part of the boot process.

Did anyone find a definitive solution to this after?

Thanks

---

### Post by uzd4ce on 2007-03-31
I was able to do what was suggested above, boot with the LiveCD, mount your hard drive, then chroot to it.

sudo mount /dev/hda2 /mnt/hda2 <- change hda2 to your partition
sudo chroot /mnt/hda2 su

But then I just ran 
sudo update-manager -c -d

and it gave me an error about something wasn't complete.  I forget what it told me to do, but whatever that command was, it restarted the install process from the point my original install had crashed.

After it finished, I rebooted and everything was fine.

---

