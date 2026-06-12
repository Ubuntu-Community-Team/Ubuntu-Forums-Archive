---
title: "glmatrix screensaver on 15.04?"
date: 2015-06-22
forum: General Help
---

### Post by NoLifeDGenerate on 2015-06-22
Ok, I know glmatrix is part of the xscreensaver-gl package, which is used by both gnome-screensaver and xscreensaver. What I don't know is how to get it to show up in 15.04 when I install that package. The screensaver dialog in 15.04 is IDENTICAL to 10.04's Gnome screensaver settings. Yet, I can't find either of those services running. What am I missing here?

---

### Post by Dennis N on 2015-06-22
In my Ubuntu, I use xscreensaver and disable gnome-screensaver:  I remove gnome-screensaver from startup applications, and add xscreensaver to my startup applications, with the command **xscreensaver -no-splash**

Under those conditions, glmatrix works fine here.

---

### Post by NoLifeDGenerate on 2015-06-22
> **Dennis N said:**
> In my Ubuntu, I use xscreensaver and disable gnome-screensaver:  I remove gnome-screensaver from startup applications, and add xscreensaver to my startup applications, with the command **xscreensaver -no-splash**

Under those conditions, glmatrix works fine here.

I had issues with xscreensaver and my dual screens when I tried it on Mint. I prefer gnome-screensaver, and this is supposed to work with it. I used it on 10.04 that way for years. [https://launchpad.net/ubuntu/vivid/amd64/xscreensaver-gl](https://launchpad.net/ubuntu/vivid/amd64/xscreensaver-gl)

---

### Post by NoLifeDGenerate on 2015-06-23
Really. Nobody knows?

---

### Post by Dennis N on 2015-06-23
Since 2011 or 2012, gnome screensaver doesn't run animated screensavers.

[http://askubuntu.com/questions/292995/configure-screensaver-in-ubuntu](http://askubuntu.com/questions/292995/configure-screensaver-in-ubuntu)

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/994612](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/994612)
read posts #5 and #6 there.  Restoring this dialog is on "wishlist" status (post #6, and "Importance" at top) and there's no indication here that Gnome has changed its collective mind, or of further activity.  

> "The screensaver dialog in 15.04 is IDENTICAL to 10.04's Gnome screensaver settings."

Please explain how to access the screensaver dialog you're referring to in Ubuntu 15.04. Thanks.

---

### Post by NoLifeDGenerate on 2015-06-23
> **Dennis N said:**
> 
Please explain how to access the screensaver dialog you're referring to in Ubuntu 15.04. Thanks.

System > Preferences > Look and Feel > Screensaver

---

### Post by Dennis N on 2015-06-23
> **NoLifeDGenerate said:**
> System > Preferences > Look and Feel > Screensaver

Are you using Ubuntu Unity 15.04?

I ask because the path you give doesn't exist in my Ubuntu Unity 15.04, starting at "System Settings" on the launcher. There are no "Preferences" or "Look and Feel" subcategories in "System Settings". And no "Screensaver" anywhere under "System Settings". So I can't get any further with that information. To be clear, xscreensaver has not been installed on this particular system.  

Well, since there is no gnome-screensaver preferences dialog anymore, what do you think you are could be looking at? Do you have xscreensaver installed along with xscreensaver-gl? If so, it could be the dialog for that - which goes by the name 'Screensaver' under System Settings when it is installed.

---

### Post by NoLifeDGenerate on 2015-06-23
> **Dennis N said:**
> Are you using Ubuntu Unity 15.04?

I ask because the path you give doesn't exist in my Ubuntu Unity 15.04, starting at "System Settings" on the launcher. There are no "Preferences" or "Look and Feel" subcategories in "System Settings". And no "Screensaver" anywhere under "System Settings". So I can't get any further with that information. To be clear, xscreensaver has not been installed on this particular system.  

Well, since there is no gnome-screensaver preferences dialog anymore, what do you think you are could be looking at? Do you have xscreensaver installed along with xscreensaver-gl? If so, it could be the dialog for that - which goes by the name 'Screensaver' under System Settings when it is installed.

Hell no. I'm a Unity hater. I'm using 15.04 Mate.

---

### Post by Dennis N on 2015-06-23
> **NoLifeDGenerate said:**
> Hell no. I'm a Unity hater. I'm using 15.04 Mate.

Then you are looking at mate-screensaver, not gnome-screensaver. I'm not sure it will run glmatrix. I will check, as I have several Ubuntu MATE installations here.

---

### Post by Dennis N on 2015-06-23
I tried a couple of the gl screensavers (including glmatrix) and they work in the full screen preview of mate screensaver. So it looks good there, but something is not right in real usage - at the set time, my screen dims, but then goes back to the normal screen before the screensaver appears. Why I'm not sure. Nothing is being touched. I tested in MATE 14.04 and will try it in 15.04 and see if that matters.

---

### Post by NoLifeDGenerate on 2015-06-23
> **Dennis N said:**
> I tried a couple of the gl screensavers (including glmatrix) and they work in the full screen preview of mate screensaver. So it looks good there, but something is not right in real usage - at the set time, my screen dims, but then goes back to the normal screen before the screensaver appears. Why I'm not sure. Nothing is being touched. I tested in MATE 14.04 and will try it in 15.04 and see if that matters.

Thanks. Let me know what you figure out.

---

### Post by Dennis N on 2015-06-23
Lucky for us the gl screensavers work fine in 15.04. But there is a problem where screensavers from xscreensaver-gl don't show up in the mate-screensaver dialog. To fix that run these two commands (one at a time) in the terminal. You may want to copy and paste the second line to avoid errors.
```

cd /usr/share/applications/screensavers
sudo perl -p -i -e 's/OnlyShowIn=GNOME;/#OnlyShowIn=GNOME;/g' *.desktop

```
Now open the dialog and they will all appear!

---

### Post by NoLifeDGenerate on 2015-06-24
> **Dennis N said:**
> Lucky for us the gl screensavers work fine in 15.04. But there is a problem where screensavers from xscreensaver-gl don't show up in the mate-screensaver dialog. To fix that run these two commands (one at a time) in the terminal. You may want to copy and paste the second line to avoid errors.
```

cd /usr/share/applications/screensavers
sudo perl -p -i -e 's/OnlyShowIn=GNOME;/#OnlyShowIn=GNOME;/g' *.desktop

```
Now open the dialog and they will all appear!

That's awesome! Thanks

---

### Post by wint2 on 2015-09-30
> **Dennis N said:**
> Lucky for us the gl screensavers work fine in 15.04. But there is a problem where screensavers from xscreensaver-gl don't show up in the mate-screensaver dialog. To fix that run these two commands (one at a time) in the terminal. You may want to copy and paste the second line to avoid errors.
```

cd /usr/share/applications/screensavers
sudo perl -p -i -e 's/OnlyShowIn=GNOME;/#OnlyShowIn=GNOME;/g' *.desktop

```
Now open the dialog and they will all appear!

Awesome, thank you!

---

### Post by cyberia on 2015-10-02
> **Dennis N said:**
> Lucky for us the gl screensavers work fine in 15.04. But there is a problem where screensavers from xscreensaver-gl don't show up in the mate-screensaver dialog. To fix that run these two commands (one at a time) in the terminal. You may want to copy and paste the second line to avoid errors.
```

cd /usr/share/applications/screensavers
sudo perl -p -i -e 's/OnlyShowIn=GNOME;/#OnlyShowIn=GNOME;/g' *.desktop

```
Now open the dialog and they will all appear!


THX Denis. &#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086; &#1073;&#1086;&#1083;&#1100;&#1096;&#1086;&#1077; !

---

