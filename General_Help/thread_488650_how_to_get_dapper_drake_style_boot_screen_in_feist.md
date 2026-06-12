---
title: "how to get dapper drake style boot screen in feisty ?"
date: 2007-06-30
forum: General Help
---

### Post by ashwin_cse on 2007-06-30
Hi,

I like the dapper style boot screen where it shows the current services it starting & it results (ok or failed) below the progress bar in nice graphical way. The kind of boot screen can be found at [http://i37.photobucket.com/albums/e53/nemesis4u/2.png](http://i37.photobucket.com/albums/e53/nemesis4u/2.png) . It has also been attached for your reference (named 2.png ). How do i make this my boot screen in my ubuntu feisty fawn ?

---

### Post by omschaub on 2007-06-30
Coming from the Gentoo world, this is certainly something that I miss.  I find it nice for the 'noobs' to hide this info, but for the novice to intermediate user that I am, I enjoy seeing it.  Especially if a disk is being scanned because of the number of mounts.. the computer just kind of sits there until some timeout, then it show me what is going on.

I have no answer for you.. but I do have a big "ME TOO" .... I would love this info!  So I will sit back and watch this thread for an answer.

:popcorn:

---

### Post by strabes on 2007-06-30
you simply have to remove the "quiet" option in the kernel line in your /boot/grub/menu.lst: ```
sudo gedit /boot/grub/menu.lst
```

Mine looks like this:
> title		kubuntu, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9447cb7b-af50-4fc6-806e-bd72714c7c99 ro **quiet** splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

---

### Post by omschaub on 2007-06-30
> **strabes said:**
> you simply have to remove the "quiet" option in the kernel line in your /boot/grub/menu.lst:

THANKS! :D

---

### Post by speeddemon8803 on 2007-06-30
yeah, thanks! I was wondering about that, I went through all configuration files, I didnt even think to check that one!

---

### Post by ashwin_cse on 2007-06-30
**Thank You strabes . It works!**

---

### Post by ashwin_cse on 2007-07-02
how do i suppress the lot of text messages that flows before the GUI starts & after the grub menu ? I have been searching the net for some time now & i dont find any article explaining the usplash. From my search i understand that the detailed boot is to do with usplash & noit grub as i initially understood. But the problem is i dont find any good documentation on what parameters the usplash accepts, so instead of passing unquiet boot to kernel, we can say to usplash to boot with messages on.

---

