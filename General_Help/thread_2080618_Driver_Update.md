---
title: "Driver Update"
date: 2012-11-04
forum: General Help
---

### Post by 7ewis on 2012-11-04
Can someone please help me update a driver for my USB Wi-Fi adapter.

This post here:
[http://ubuntuforums.org/showthread.php?t=1215251](http://ubuntuforums.org/showthread.php?t=1215251)

Is exactly what I want to do, but I get stuck at one point of the update.

If you look at post #3, I have the same problem as him. The OP says that he must be running a too old kernel, what does that mean?

He then says that he should remove the line with the BUILD EXCEPTION, which I have done. But it still doesn't seem to work for me.

This is the error:

root@bt:~# sudo dkms build -m rt73-k2wrlz -v 3.0.3

Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which
does not match this kernel/arch.  This indicates that it should not be built.

After I got that message I deleted everything and started again, but when I did this command:

root@bt:~# sudo dkms ldtarball --archive=rt73-k2wrlz-3.0.3-dkms.tar.gz

Loading tarball for module: rt73-k2wrlz / version: 3.0.3

Warning! Source for rt73-k2wrlz-3.0.3 already exists.  Skipping...

DKMS: ldtarball Completed.

It says the source already exists? I deleted everything in my home directory, so I don't know what it means, or if that contains the file that is stopping it working.

Someone please explain what to do, my main OS is Ubuntu 12.10, and I am trying to do this in BackTrack 5 R3, but I am fairly new to Linux, and this forum. 

Thanks!

---

### Post by ibjsb4 on 2012-11-04
Your trying use a fix developed for ubuntu 9.04 and your running 12.10.  Im not a wifi expert, but I think its safe to say no way will this ever fly.

Why do you think that patch is what you need.  Will your wifi work at all?

The little bit of exploring I did indicates the rt73usb driver is what you need.

[http://ubuntuforums.org/showthread.php?t=2040350](http://ubuntuforums.org/showthread.php?t=2040350)

More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Ralink+RT73+USB+Wifi+Driver&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Ralink+RT73+USB+Wifi+Driver&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by 7ewis on 2012-11-04
I'm using it for BackTrack, as I don't think my built in Wi-Fi card can be in promiscuous mode.

I think I need that one because my adapter is a:

D-Link DWL-G122 Ver. C

And that's what I found other people had been using on Backtrack-linux forums.

I'll have a look at that though, thanks!

Do you know what the error I mentioned is though?

---

