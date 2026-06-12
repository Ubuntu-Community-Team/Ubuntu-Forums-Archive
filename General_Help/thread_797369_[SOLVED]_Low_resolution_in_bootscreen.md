---
title: "[SOLVED] Low resolution in bootscreen"
date: 2008-05-17
forum: General Help
---

### Post by _sAm_ on 2008-05-17
After going from Ubuntu 7.10 to 8.04 the resolution on the boot screen(you know, where you see the Ubuntu logo and that loading bar) is far to low and looks ugly. Its not important - just bugs me. 

I did try to follow a guide but it didn't work at all. Do you know of a safe guide to fix this?

Thanks

---

### Post by rubicon on 2008-05-17
What guide?

Maybe just try to change xres and yres in /etc/usplash.conf ? And &#8212; not necessarily &#8212; update-initramfs -u -k `uname -r`

---

### Post by _sAm_ on 2008-05-17
Thanks for answering my post:-) 

I tried "sudo nano /etc/usplash.conf" and this was the only info there; 
> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

Then I add the info you mentioned so it looked like this; 
> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=1024

But the resolution was the same when I did a reboot. 

Edit:
I tried "sudo dpkg-reconfigure usplash", after I had added the correct resolution. Now its ok.

---

