---
title: "[SOLVED] Problem with Themes"
date: 2008-06-02
forum: General Help
---

### Post by mel_phil@flashmail.com on 2008-06-02
Hi

I installed gnome-theme-extras and liked the darklook theme. I set Gnome to use this theme & it looks cool but when I reboot it reverts to another theme & I have to manually change the theme back to darklook. Is there a way to save that theme so it is there after a reboot. Using the latest Ubuntu 8.04. The themes that came with the original unstall all work OK after reboot it is only on the newly added themes. Have tried to reinstall the package again....no luck there


Cheers

PS :):):):):).

---

### Post by Forlong on 2008-06-02
Sounds like a setup issue. Did you by any chance run something as root (sudo) you shouldn't need?

Try this (just copy and paste those into your terminal):
```
sudo chown -R $USER:$USER $HOME
```
```
chmod -R u+rwx $HOME
```
That will make sure, you are the owner of all the files in your home directory.

---

### Post by mel_phil@flashmail.com on 2008-06-02
Hi

Many thanks for the quick reply :)

I entered the first command into the terminal & get the following
[COLOR="Red"]
chown: cannot access `/home/p/.gvfs': Permission denied[/COLOR]

The second one runs OK

I did notice though that the darklook theme is still selected in the appearance settings it just looks different.

Many thanks again :):):)

---

### Post by mel_phil@flashmail.com on 2008-06-02
Hi,

Also I tried to create a new user with a "reset" gnome desktop & still get the same result

Cheers

PS

---

### Post by mac143_01 on 2008-06-03
What is a Theme? Can I customize Ubuntu's Theme? please tell me the step by step procedures... THaNKS!!

---

### Post by mel_phil@flashmail.com on 2008-06-03
Hi,

Also I tried to create a new user with a "reset" gnome desktop & still get the same result

Cheers

PS

---

### Post by mel_phil@flashmail.com on 2008-06-03
Hi 

I did a format of my hard disk & re-installed a clean copy of Ubuntu 8.04 to see if it was anything I had done. The first thing I did was using Synaptic installed gnome-theme-extras. It inststalled ok with no interuptions or errors. I changed the theme to darklooks and it changed ok. Did a restart & the same problem occured again (the theme darklooks was still selected in the Theme Manager but does not display properly). I then downloaded all available updates to see if there was maybe a fix there. No change problem still there. Possibly a bug? because this was a clean install with nothing added first up except the theme package & then only the updates after that.

Cheers

PS :):):):):)

---

### Post by Skiesare on 2008-06-04
Try this;

Edit the theme file:

cd /usr/share/themes/Darklooks/gtk-2.0/

edit gtkrc, changing lines 181 and 182 from:

bg[NORMAL] = @tooltip_bg_color
fg[NORMAL] = @tooltip_fg_color

to:

bg[NORMAL] = @tooltips_bg_color
fg[NORMAL] = @tooltips_fg_color

note the change from tooltip to tooltips

I found this at 
[http://opencomputing.blogspot.com/2008/05/using-dark-theme-in-ubuntu.html](http://opencomputing.blogspot.com/2008/05/using-dark-theme-in-ubuntu.html)

Hope it helps.

---

### Post by mel_phil@flashmail.com on 2008-06-06
The solution worked. Thank you very very much guys


PS :):):):):)

---

