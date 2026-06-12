---
title: "Ubuntu broken after latest update 13/02/13"
date: 2013-02-13
forum: General Help
---

### Post by Romeo9 on 2013-02-13
I just now updated my Ubuntu 12.10 computer with the latest updates and restarted my machines after the updates as requested.

As the computer restarted I realised that where I use to have a splash screen at the right resolution I now have a check-list with a very large resolution.

As I enter the desktop I can only view my background and nothing else still in a resolution which seems to be too big for my 19" Display.

Some of the items in the update list which I can remember included at very large amount of X.org updates and a Linux firmware update.

I would really appreciate it if someone can help me out, I really am not looking forward to re-installing my OS. My mouse is limited to the parameters of my screen even though it appears as though my desktop has been stretched beyond the parameters of my screen. As a result I can't access anything I can only see the centre of my desktop wallpaper that's it.

---

### Post by dino99 on 2013-02-13
boot into recovery mode, and watch if you still have a /etc/X11/xorg.conf

as now the kernel directly deal with X, xorg.conf is not needed. And a borked one often break the video or like you, boot in low mode.

then you can also watch the upgrade history errors (dpkg.log)

---

### Post by Romeo9 on 2013-02-14
Thanks for the reply dino

I did everything you suggested but none of it worked.

However as I was booting I loaded up the grub again and where the default is Ubuntu with Linux 3.7.0.7 (Generic) I decided to boot up Ubuntu using the one just below that, Linux 3.5.0.23 (Generic) and it booted perfectly. Right resolution, my navigation bars where all working, with 3.7 the navigation bars at the top of the windows where gone. So I'm guessing the latest Linux firmware update isn't compatible with my install of Ubuntu 12.10.

I would just like to know how do I set my computer to boot using the 3.5 kernel instead of the 3.7 kernel by default?
Alternatively if someone knows why my OS is breaking in this strange way when using the 3.7 kernel please let me know.

Here's a list of all the updates I did right before my Ubuntu install broke: [Link]("http://ubuntuone.com/7bBlIQwJlmq6FpPEEOVNjb")

---

