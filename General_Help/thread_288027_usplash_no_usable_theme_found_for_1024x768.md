---
title: "usplash: no usable theme found for 1024x768"
date: 2006-10-29
forum: General Help
---

### Post by Starlight on 2006-10-29
Hi! I get that error every time I boot... the result is that I can't see any messages while Ubuntu is loading, and I have no idea what's going on. I have usplash-theme-ubuntu installed, and I even tried reinstalling it, but it didn't change anything.

---

### Post by Starlight on 2006-11-04
bumping the thread... it still doesn't work... I tried reinstalling the themes, reinstalling usplash, changing the resolution, reconfiguring usplash.... and still nothing! If it can't be fixed, then maybe there's a way to disable usplash... I don't really like looking at a blank screen for a few minutes while Ubuntu is booting...

---

### Post by autocrosser on 2006-11-04
Search for threads about usplash-switcher--I've got it installed & another theme from gnomelook.org--switcher "might" open your options up--

Also--you could edit /boot/grub/menu.lst & remove the "quiet" from quiet splash in your kernel line.

---

### Post by Jivicin on 2006-11-08
I am getting this error as well only my resolution is 1280 by 1024.

Any solutions?

---

### Post by autocrosser on 2006-11-09
Ok--You could try adding: vga=794 in your /boot/grub/menu.lst list--open /boot.grub/menu.lst with sudo gedit--

<sudo gedit /boot/grub/menu.lst>
and look for the line:
# defoptions=quiet splash

and add your framebuffer resolution code, e.g. (for 1280x1024)

# defoptions=quiet splash vga=794

Save the file, then execute

sudo update-grub

Of course, if you want info while booting--remove the "quiet" from quiet splash

give that a try---

---

### Post by Jivicin on 2006-11-09
Yup, I had that in there already.  No change.

---

### Post by autocrosser on 2006-11-09
Tell me what is in your /etc/usplash.conf file---and look at /usr/lib/usplash to see what is in there---

---

### Post by huwnet on 2006-11-09
I had the same problem as you after an upgrade.

Installing usplash-theme-ubuntu fixed the problem although running "update-grub" still says there is no usplash present.

---

### Post by jpyanowski on 2006-11-11
> **autocrosser said:**
> Search for threads about usplash-switcher--I've got it installed & another theme from gnomelook.org--switcher "might" open your options up--

Also--you could edit /boot/grub/menu.lst & remove the "quiet" from quiet splash in your kernel line.

I want to THANK YOU for this advice. \\:D/ I was disappointed by the lack of text in the boot process in Edgy (I was spoiled by Dapper). Deleting "quiet" in the menu.list file has returned my text!!! I just have to change the color from blue to white and things will be sweet.  :D

---

