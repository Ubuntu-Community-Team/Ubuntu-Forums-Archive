---
title: "Weird Bootup Pictures"
date: 2006-08-02
forum: General Help
---

### Post by tonyr1988 on 2006-08-02
You know the picture that is shown when you startup / shutdown Ubuntu? It has the Ubuntu logo on top, the progress bar, and all the actions with "ok" next to them?

I installed KDE the other day so that I could switch between Gnome and KDE before logging in.

Now, when I load up and shut down, it shows the Kubuntu logo / color scheme.

Some facts:

1) I originally had Gnome from installation.
2) Gnome is, and always had been, my default.
3) I didn't shut down from KDE - I simply logged out and logged back into Gnome.
4) I use GDM, not KDM (I think those are the right acronyms).

It's not a big deal, I'm just curious why it did that, and if there's anything I can do to fix it.

---

### Post by darrenm on 2006-08-02
> **tonyr1988 said:**
> You know the picture that is shown when you startup / shutdown Ubuntu? It has the Ubuntu logo on top, the progress bar, and all the actions with "ok" next to them?

I installed KDE the other day so that I could switch between Gnome and KDE before logging in.

Now, when I load up and shut down, it shows the Kubuntu logo / color scheme.

Some facts:

1) I originally had Gnome from installation.
2) Gnome is, and always had been, my default.
3) I didn't shut down from KDE - I simply logged out and logged back into Gnome.
4) I use GDM, not KDM (I think those are the right acronyms).

It's not a big deal, I'm just curious why it did that, and if there's anything I can do to fix it.

Been trying to find the answer to this myself for ages. Its not the splash because thats the small bar that displays when you log into gnome.

I know its something to do with the initrd (well I think at least) because when you look at /boot/grub/menu.lst it shows that its passing 'splash' as an option to the kernel as it loads. But where it gets the splash image from I really don't know.

---

### Post by siplus on 2006-08-02
This happened to me as well when I installed 'kubuntu' packages via synaptic.

I haven't changed it back, but I googled this:

[http://ubuntuforums.org/archive/index.php/t-77290.html](http://ubuntuforums.org/archive/index.php/t-77290.html)
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Hope it helps!

---

### Post by darrenm on 2006-08-02
woohoo! [quote=https://help.ubuntu.com/community/USplashCustomizationHowto]
5. Regenerate the initramfs:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
[/quote]
I love it when I take a wild guess and happen to be right ;)

---

### Post by tonyr1988 on 2006-08-03
> **darrenm said:**
> woohoo! 
I love it when I take a wild guess and happen to be right ;)
hmm....that didn't work for me.

I'll try it again in a little bit, reboot, and see if it works.

---

### Post by Ramses de Norre on 2006-08-03
Do ```
sudo update-alternatives --config usplash-artwork.so
``` and choose the non-kubuntu entry.
I don't know why it changes but it always does so..

---

### Post by tonyr1988 on 2006-08-03
Well, the shutdown image is back to Ubuntu, but the loading image is still Kubuntu. Do I need to change another one?

---

### Post by darrenm on 2006-08-04
Did you did this: ```
sudo dpkg-reconfigure linux-image-$(uname -r)
``` afterwards?

---

### Post by tonyr1988 on 2006-08-05
> **darrenm said:**
> Did you did this: ```
sudo dpkg-reconfigure linux-image-$(uname -r)
``` afterwards?
That did it!

I'm back to the normal "ubuntu" logo for bootup and shutdown.

Thanks a ton!

---

