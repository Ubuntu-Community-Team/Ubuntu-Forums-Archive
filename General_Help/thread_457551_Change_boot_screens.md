---
title: "Change boot screens"
date: 2007-05-28
forum: General Help
---

### Post by Kuoi on 2007-05-28
Hello ,

After installing and uninstalling UbuntuStudio , I had a problem.

Everytime I was logging out or logging off , I did get the UbuntuStudio logoff screen instead of the Ubuntu default logoff screen.

After some searching on the internet and this forum , I couldn't find a way to change the boot screens or logoff screens.
So , I've opened Synaptic and deleted all repos referring to UbuntuStudio.
Now I don't have any boot screen anymore , I mean only the one where you have to login , but no other than that.
Log in = all text , logout = all text.

**How can I get my boot screens back ?**

And now I wander why I can't fix this myself ? :-k

Kuoi

---

### Post by Psicolonia on 2007-05-28
search google for a debian package called "start-up manager"

make a copy of /boot/grug/menu.lst just in case because sometimes it changes your entries.

However you can reactivate your usplash easily.

Tell me if you got any problems with this.

---

### Post by loathsome on 2007-05-28
> **Psicolonia said:**
> search google for a debian package called "start-up manager"

make a copy of /boot/grug/menu.lst just in case because sometimes it changes your entries.

However you can reactivate your usplash easily.

Tell me if you got any problems with this.

start-up manager caused my Feisty boot to crash completely.

I recommend you remove all «usplash»-packages, and then reinstalling «ubuntu-artwork-usplash» (or w/e it's called)

---

### Post by strabes on 2007-05-28
[http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/](http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/)

The ubuntu usplash package is called "usplash-theme-ubuntu"

---

### Post by Kuoi on 2007-05-29
I've uninstalled every usplash package , reinstalled the ubuntu usplash theme , but that didn't work.

Then I've found the following , tried it , and now I have a logoff screen , but still no bootup screen.
> open terminal
sudo nautilus
go to /usr/lib/usplash/

find file usplash-artwork.so and see if the link is broken.
if the link is broken, delete file.

right click on the file usplash-theme-ubuntu.so and make link.

rename the new link usplash-artwork.so

reboot and see if that works for you.

Looking further to get the default boot screens back.

Kuoi

---

### Post by Kuoi on 2007-05-29
> **strabes said:**
> [http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/](http://strabes.wordpress.com/2007/02/17/change-bootsplash-images-in-ubuntu/)

The ubuntu usplash package is called "usplash-theme-ubuntu"

I did the 2 first commands and after more then 1 reboot , and do the commands again , now everything is fine.

Thanks for the help everybody , Kuoi

---

### Post by rubengs on 2007-05-30
Not my solution, copied and translated from [http://www.espaciolinux.com/foros-tema-t26526.html](http://www.espaciolinux.com/foros-tema-t26526.html) : 

To chose usplash theme:
```
sudo update-alternatives --config usplash-artwork.so
```


Then update initramfs with:
```
sudo update-initramfs -u
```

To test the new usplash theme:
```
sudo usplash -c
```

To go back to your session press Ctrl+Alt+F7.

---

