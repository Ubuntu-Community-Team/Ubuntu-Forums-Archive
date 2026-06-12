---
title: "After 5 months of use, Kubuntu (6.06) suddenly does not boot (from HD)"
date: 2006-12-05
forum: General Help
---

### Post by usr16 on 2006-12-05
I'm very new to linux\kubuntu but my system had been running well for a couple of months until yesterday:

It hangs just before (probably) the login prompt (displays the kubuntu progress bar screen as empty) after all the "Ok"s (but I can still manage an alt ctrl del shutdown)

I tried the recovery mode and find a terminal mode which I'm not used to but I find thankfully see my files (which obviosly I need to rescue)in my home dir. 
I place a 1Gb USB flash drive which it seems to detect (sda1?) but alas not present in /media (or in df , /etc/fstab or mtab apparently).
And I dont know how to a DVD in terminal mode (certainly not with KE3). Is there a way to get any sort of GUI at this stage?

Started to be a bit of a hassle so I gave up and and tried the Kubuntu live CD which seemed to work fine but this time I cant access my hard drives (I can see them in /media but fails to mount them and cant find them in fstab or mtab). Starts to be a bigger hassle...

The first question is: How do I get my files out?

I have searched around but found really nothing (yet) directly useful. 

Would appreciate any advice!

Thanks

---

### Post by AusIV4 on 2006-12-05
You may be jumping the gun a bit trying to get your files out. First, I'd try hitting ctrl-alt-f1 when you boot. This time instead of seeing that it's through all the OK's, you'll see a more detailed description of what it's doing.

If you can get some more detail, post it here and we'll try to give some more help.

If you can't, here's how I would go about saving my data (bare in mind I usually just use the commandline when I have a problem).

Plug in your external drive. Make a directory to mount it. Ex:

# mkdir external

Then mount it.

# sudo mount /dev/sda1 external

If you're using the Live CD, your other disks won't be in fstab, because it's the Live CD's fstab. Because your USB device was called /dev/sda, I'm going to assume your root filesystem is on /dev/hda.

# mkdir fs
# sudo mount /dev/hda1 fs

Personally, I keep my home directory on it's own partition, so if I have to reinstall my OS, it stays untouched, and getting my computer back to normal is just a matter of searching through the repositories to install everything I need.

---

### Post by usr16 on 2006-12-05
Thanks for your quick reply.

The only error message I noticed during the boot process after alt ctrl f1 was under restricted drivers:
something like codec_read: codec 0 is not valid 

Then the same stuck kubuntu screen appears again after that but with alt-crtl-f1 again I got the login prompt and have access to the system (so I assume the GUI is not working for some reason).

Again I'm not handy with the console but at least I managed to mount (that was the missing step) the flash drive but had some problems writing to it. But also managed to mount  my hard disk with the live CD (it was hdc1) and have access to it apparently read only (could this be changed? As it makes it difficult to create a archive/zips that way as I do have quite a bit (~70Gb) of data and files (almost all of it work related, believe or not) I should backup). Also have not tried DVD burning (since I feel it should be a little difficult with a live CD and no spare HDs?!)

Yes, the partition idea would have been good to start with (or seperate HDs which I usually do with windows) but I didnt remember to do that with Kubuntu this time, and I have just run out of hard disks...  

Any ideas what might be the problem with the GUI?

Thanks again,

---

### Post by usr16 on 2006-12-05
Ok, I got it working somehow, I used a somewhat awkward display configuration script through the console (sorry I can't remember exactly what it was, something like Xorg -configuration etc. I tried quite a few things) then the GUI/ KDE just started working next time I rebooted.

---

