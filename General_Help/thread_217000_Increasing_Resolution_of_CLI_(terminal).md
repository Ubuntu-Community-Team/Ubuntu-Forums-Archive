---
title: "Increasing Resolution of CLI (terminal)??"
date: 2006-07-16
forum: General Help
---

### Post by rohan! on 2006-07-16
There is a tutorial on linux planet which describes how to use the terminal instead of a conventional windows manager, and in it it tells you how to increase the resolution of your CLI. ( [http://www.linuxplanet.com/linuxplanet/tutorials/6206/3/](http://www.linuxplanet.com/linuxplanet/tutorials/6206/3/) ) 

But I can't find the file that it refers to -- /boot/grub/grub.conf -- is this the same as /boot/grub/menu.lst ??

When I add the comment video=1024x768-32@85 to the end of the line of my kernal there is no effect... 
[B]
What I'm trying to ask is if anyone knows how to make the text smaller in my command line??[/B]

---

### Post by blitzd on 2006-07-16
> **rohan! said:**
> There is a tutorial on linux planet which describes how to use the terminal instead of a conventional windows manager, and in it it tells you how to increase the resolution of your CLI. ( [http://www.linuxplanet.com/linuxplanet/tutorials/6206/3/](http://www.linuxplanet.com/linuxplanet/tutorials/6206/3/) ) 

But I can't find the file that it refers to -- /boot/grub/grub.conf -- is this the same as /boot/grub/menu.lst ??

When I add the comment video=1024x768-32@85 to the end of the line of my kernal there is no effect... 
[B]
What I'm trying to ask is if anyone knows how to make the text smaller in my command line??[/B]

menu.lst is the file you're looking for. The line should look something like this:

```
kernel /boot/vmlinuz root=/dev/sda5 vga=0x317
```
...where 0x317 is hex that corresponds to a video mode. I believe 0x317 is 1024x768, I have a page with a list of them somewhere but it's not loading at the moment. I'll post back when I find it.

*Edit: There is a lost of other modes here at the bottom under Framebuffer Resolutions* [http://wiki.sourcemage.org/HOWTO-Bootsplash](http://wiki.sourcemage.org/HOWTO-Bootsplash)

---

### Post by rohan! on 2006-07-16
wicked, will try this as soon as i get an oportunity to turn my computer off!

ta, chuck (that's thankyou in the yorkshire dialect btw) :)

---

### Post by ayoli on 2006-07-16
If you want to change resolution for ttys edit /boot/grub/menu.lst as root and find this block:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash [COLOR="Red"]vga=791[/COLOR]

```
and add vga=XXX where XXX is the resol you want. that will be a default option and will not change even after a kernel upgrade.
here is some codes:
vga=788 for 800 x 600 - 16 bits
vga=791 for 1024 x 768 - 16 bits
vga=794 for 1280 x 1024 - 16 bits
vga=834 for 1400 x 1050 - 16 bits

regards.

---

### Post by mrazster on 2006-07-16
Sound interseting...going to try this.

Is it possible to run at 1921200 24bit in CLI...if so, waht would the code be then..?

---

### Post by blitzd on 2006-07-16
> **mrazster said:**
> Sound interseting...going to try this.

What would the code be for 1920x1200 ..??

You can do higher modes, but I think you may have to recompile your kernel to get any higher than 1280x1024 (I haven't done it in a looong time, but I know I had some pretty high resolutions working under Gentoo).

There is a tool around called vbetest that will help you determine the hex/decimal number of the modes supported on your machine, and I believe there are some instructions on using it here:

[http://gentoo-wiki.com/HOWTO_fbsplash](http://gentoo-wiki.com/HOWTO_fbsplash)

I can't be sure though because it's not loading at the moment.

Supposedly it's possible to do 1680x1050 (native res of my monitor) but I haven't got it working yet with Ubuntu.

---

