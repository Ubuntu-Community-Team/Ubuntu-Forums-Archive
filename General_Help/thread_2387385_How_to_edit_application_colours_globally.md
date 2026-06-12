---
title: "How to edit application colours globally"
date: 2018-03-18
forum: General Help
---

### Post by Sleepy-zz-John on 2018-03-18
In an attempt to make different application borders displayed on my 16.04 LTS Unity desktop more distinguishable so I could more easily see which application I was clicking on,  I've carelessly managed to make some global change that I can't remember how to undo.

Some applications have been affected by this change;  others not.   

My Libre Office for example,  now comes up in orange with a black background on all its setting fields like this

[https://1drv.ms/f/s!AnlYFOhVtJPGiyydOVAD4K2aqCMM](https://1drv.ms/f/s!AnlYFOhVtJPGiyydOVAD4K2aqCMM)

How can I globally change the orange and black here back to more usable colours?

---

### Post by again? on 2018-03-18
Most likely made a customization to gtk2 theming.
Look @ **~/.gtkrc-2.0** or in **~/.config/gtk-2.0**

---

### Post by Sleepy-zz-John on 2018-03-18
P'raps it's worth adding that I've been trying to correct this issue with experimental edits to 

/usr/share/themes/Radiance/gtk-3.0/apps/unity.css
  and
/usr/share/themes/Ambiance/gtk-3.0/apps/unity.css

but neither of these have any effect on the orange or black that are making all my LibreOffice and my GIMP so hard to use 

Haven't had any success with Unity Tweak Tool or dconf editor either.

---

### Post by again? on 2018-03-18
Test in a new user account or the guest session.
If the colour change does not happen in a new user account and using a theme you haven't tampered with, then it's a config in your normal user's home folder.

P.S. I think by default libreoffice is a gtk2 app in 16.04 so you should be looking at gtk2 theming.
```
apt policy libreoffice-gtk*
```

---

### Post by Sleepy-zz-John on 2018-03-19
Thanks for your useful suggestions guber2.   Haven't quite got there yet but here's what I've found so far:

Firstly for both my themes/Ambiance and my themes/Radiance,  all the .rc files in my gtk-2.0 apps folders and  file gtkrc
 predate the time when I made my careless changes by several months  so that appears to rule out my problem being in themes/Ambiance/gtk-2

Secondly,  when I log-in on a guest session,  those rogue colours don't appear.  LibreOffice shows up with normal colours.

So I agree with you it  must be a config in my normal user's home folder. 

I'm currently looking for any files/folders in my /home/.config folder with dates that might coincide with the time I originally made my careless changes, but only gnome-control-center/backgrounds//last-ediited.xmll  comes up as a suspicious candidate and all that seems to do is define my desktop background picture.

So I still haven't identified the source of the rogue colours my LibreOffice and Gimp are displaying,  but thanks to your suggestions I think we're getting a bit nearer.:smile

---

### Post by again? on 2018-03-19
Something else you can try...
Use gcolor2 to find the colour shown in libreoffice.

Then search for that colour using silversearcher-ag
example...
```
ag --hidden '#FF8324'
```

ag is a lot faster than grep with saner defaults.
To install...
```
sudo apt install silversearcher-ag
```

---

### Post by again? on 2018-03-19
Ok... don't forget ~/.gtkrc-2.0

---

### Post by Sleepy-zz-John on 2018-03-20
Thanks again Guber2.    Haven't yet identified the source but still looking.  

gcolor2 displays with the same rogue yellow and black as LibreOffice.  Could be lucky,  but I doubt if it will be accurate enough to exactly find match my hidden colours wherever they're stored.

You wrote: [COLOR="#0000FF"]* Ok... don't forget ~/.gtkrc-2.0*[/COLOR]

Well the only file in my home/.config/gtk-2.0 folder is gtkfilechooser.ini and there aren't any colour entries there.   Must be somewhere else my rogue colours are lurking.  -  I'll keep looking

---

