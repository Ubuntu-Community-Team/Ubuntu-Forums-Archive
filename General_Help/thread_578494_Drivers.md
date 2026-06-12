---
title: "Drivers"
date: 2007-10-17
forum: General Help
---

### Post by DaveCampbell on 2007-10-17
I am brand new to this forum and can't find a category where an answer to my question would be, so I'm posting it here.

I have a new laptop (Acer 4520-5803) with Vista.  I was planning on replacing Vista with XP until I stumbled upon Ubuntu for the first time.  I'd sure like to try my hand at installing it.  I've down loaded and created an installation disk.  Before I run it though, I want to resolve my concerns about hardware drivers.

In the past I've been able to download drivers for XP, but I've never seen such a thing for Ubuntu.  How do I insure computability of Ubuntu with this laptop?

---

### Post by renzokuken on 2007-10-17
you cant 100%. almost all drivers for hardware are built into the kernal and so should "just work"

the only things people struggle with are wireless and grafix drivers, but there are very easy ways to deal with these thanks to ubuntu's Restricted Drivers Manager.

best bet is to whack in a live cd, check everything works, then consider installing

---

### Post by DaveCampbell on 2007-10-17
> **renzokuken said:**
> 
best bet is to whack in a live cd, check everything works, then consider installing

Since I'm a little bit on the dense side, and before I do anything drastic, what do you mean by whacking a live cd?  It seems you're implying, "try before you commit".

---

### Post by alien21010 on 2007-10-17
So when you download the Ubuntu cd from one of the mirrors, what you are downloading is a LIVECD.  A LiveCD allows you to actually test drive Ubuntu (or any Linux distribution that comes in the form of a LiveCD) without actually installing anything on your hard drive.  It's pretty cool, and will allow you to go ahead and see if you like Ubuntu before making the plunge.  To use the LiveCD all you have to do is burn the ISO Image that you downloaded off of the internet to a CD, and make sure that your computer is set to boot from CD before hard drive (usually in the BIOS).  Then watch as Ubuntu boots up.  Obviously, since the distribution is running off of the CD it will be MUCH slower than it will be when you install, but it will allow you to gain some insight into what potential problems you will encounter.

I have an Acer laptop, and I can tell you right now that there are some minor issues with Acers that you can work around.  All in all, if everything goes as planned, it should take a little less time to fix the minor issues than it would to install all the drivers on Windows XP.

However, if you boot up the liveCd and everything works, then you'll know that you are compatible.  Give it a shot.

If you're feeling really adventurous, open a Terminal window by going into the Applications -> Accessories -> Terminal.  Then type "lspci" without the quotes, and paste the output into this window.  It will allow us to give you a better idea of what hardware might have conflicts.  

Most drivers are built into the kernel...

---

### Post by gOLdenHaWK3D on 2007-10-17
> **DaveCampbell said:**
> Since I'm a little bit on the dense side, and before I do anything drastic, what do you mean by whacking a live cd?  It seems you're implying, "try before you commit".

Yes, LiveCD is a cool way to know whether Ubuntu will work on your PC or not, or maybe with minor modifications. And guess what, a LiveCD boots & works normally without being having installed on the hard disc! :)

---

### Post by DaveCampbell on 2007-10-17
> **alien21010 said:**
> So when you download the Ubuntu cd from one of the mirrors, what you are downloading is a LIVECD.  A LiveCD allows you to actually test drive Ubuntu (or any Linux distribution that comes in the form of a LiveCD) without actually installing anything on your hard drive.  It's pretty cool, and will allow you to go ahead and see if you like Ubuntu before making the plunge.  To use the LiveCD all you have to do is burn the ISO Image that you downloaded off of the internet to a CD, and make sure that your computer is set to boot from CD before hard drive (usually in the BIOS).  Then watch as Ubuntu boots up.  Obviously, since the distribution is running off of the CD it will be MUCH slower than it will be when you install, but it will allow you to gain some insight into what potential problems you will encounter.

I have an Acer laptop, and I can tell you right now that there are some minor issues with Acers that you can work around.  All in all, if everything goes as planned, it should take a little less time to fix the minor issues than it would to install all the drivers on Windows XP.

However, if you boot up the liveCd and everything works, then you'll know that you are compatible.  Give it a shot.

If you're feeling really adventurous, open a Terminal window by going into the Applications -> Accessories -> Terminal.  Then type "lspci" without the quotes, and paste the output into this window.  It will allow us to give you a better idea of what hardware might have conflicts.  

Most drivers are built into the kernel...


Thank you for your kind help.  It's going to make the difference between an early surrender and making a go of giving this an earnest try.  I was able to do as you say, and I must say, this Ubuntu is quite impressive.  My major road block now is in getting the wireless adapter to see my router, or for that matter, I guess a cable connection too.

I did as you said and copied out the log file.  I would sure appreciate hearing what you have to say about the log file contents.

---

### Post by renzokuken on 2007-10-19
after a quick peruse of your lspci, it looks like most/all things should work out of the box.

wireless, though, has a habit of not working on a livecd but being ok on an install (and vice versa). but you atheros chip is well documented with ubuntu so you should have no trouble getting it to work with a bit of human intervention. there are guides littered all over the forums.

you could run a "dual boot" system, where you have vista AND ubuntu on your laptop, allowing you to choose which one on boot.

---

