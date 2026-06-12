---
title: "Laptop Seems to shut down during boot"
date: 2014-06-03
forum: General Help
---

### Post by kneeki on 2014-06-03
Details: 11" MacBook Air, Ubuntu GNOME 14.04
Symptom: Will not boot into desktop, seems to "shut down" after the gnome screen appears. The power button must be pressed and held twice for roughly 5 seconds to restart the PC.
Additional Notes:

Hi Everyone!

I've installed a fresh copy of Ubuntu Gnome along side my 11" MacBook Air and it went without issues. Yesterday I followed the [top things to do after installing ubuntu]("http://www.unixmen.com/top-things-installing-ubuntu-14-0413-1013-0412-1012-04/") and as though I didn't install everything they suggested, everything I did choose went very well and without a hitch. I even finished my day installing Office 2010 and completing a couple projects for school and printing them out. This morning however, my Ubuntu install won't boot. It seems to boot as usual, then shut down in the middle of the booting process.

I've included a video in this post which shows the issue in action. I did notice a new screen flash during one of my booting attempts showing something about gnome, fsck, and my hard drives. Unfortunately the screen went black before I was able to fully read (and take a picture with my phone). I've not seen the same screen happen again. Any ideas what I could do to further diagnose the issue or fix it all together?

The computer failing to boot: [http://youtu.be/egaNNbrZQyY](http://youtu.be/egaNNbrZQyY)
Failing to boot to FailSafeX: [http://youtu.be/siUJ1GVvoW8](http://youtu.be/siUJ1GVvoW8)

---

### Post by kneeki on 2014-06-03
So I noticed in the advanced boot options for Ubuntu a check disk application named fsck. I attempted running fsck and regardless of how long I leave the PC, it seems to remain just as the image shows until I CTRL+C out.

[[IMG]http://i.imgur.com/PWwg0iZ.jpg[/IMG]](http://imgur.com/PWwg0iZ)

---

### Post by kneeki on 2014-06-04
I'm still continuing to work on this issue. Although fsck isn't working exactly as it should with the recovery mode option, my laptop wasn't actually shutting down during boot. After pressing CTRL+ALT+F2 I was able to login to the command line and issue the command 'startx'. BOOM! DESKTOP!

Now I'm looking into why the Xorg server isn't starting with boot. Any tips would be greatly appreciated.

---

