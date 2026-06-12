---
title: "Cannot move the window buttons to the right"
date: 2012-10-28
forum: General Help
---

### Post by squenson on 2012-10-28
Hello,

I just did a fresh install of 12.04. Here are the characteristics of my machine:
Release 12.10 (quantal) 64-bit
Kernel Linux 3.5.0-17-generic
GNOME 3.6.0

I try putting back the maximize, minimize, close buttons to the right of the window. I used gconf-editor and modified the entry /apps/metacity/general/button_layout to :minimize,maximize,close. I must mention that it also says in the Key Documentation area that "This key has no schema".

I have rebooted and still the buttons are on the left. Any idea? Thanks in advance!

---

### Post by flint5 on 2012-10-28
Have you tried with Ubuntu Tweak??

---

### Post by squenson on 2012-10-28
I have not found any option in Ubuntu Tweak that allows me to change the position of the window buttons. May be I should install an add-on for this, do you know which one?

---

### Post by flint5 on 2012-10-28
Open Ubuntu Tweak => Tweaks => Window, you will see Window control button position,
than choose left or right.

---

### Post by squenson on 2012-10-28
I don't see any Window icon or option in the tweak panel...

---

### Post by flint5 on 2012-10-28
I thing you have a old version of Ubuntu Tweak, my version is 0.8.0.
If your version is older than 0.7.3 try to upgrade, with adding the ppa:

sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak

---

### Post by squenson on 2012-10-28
Thank you for your help flint5, but I have a more recent version than yours, the 0.8.1.

---

### Post by black veils on 2012-10-28
i think ubuntu uses dconf instead of gconf now, maybe that will help?

---

### Post by pkadeel on 2012-10-28
open dconf
Select org > gnome > desktop > wm > preferences
Set preference named "button-layout"

---

### Post by squenson on 2012-10-28
Thank you pkadeel, that does the trick! I now have my buttons on the right.

---

### Post by flint5 on 2012-10-28
or open the terminal and try use this command:

gsettings set org.gnome.desktop.wm.preferences button-layout ':minimize,maximize,close'

than log out and log in

---

### Post by Jetro on 2012-11-01
> **pkadeel said:**
> open dconf
Select org > gnome > desktop > wm > preferences
Set preference named "button-layout"
Brilliant, thanks!

All 'solutions' I found googling just turned up the old "install gconf-edtitor" and do the same there. Which has no effect on 12.10.

---

### Post by mrpauldriver on 2013-09-09
Thank you [COLOR=#000000]@pkadeel - that was a big help[/COLOR]

---

