---
title: "Does only running a tty save a lot of battery life?"
date: 2013-02-10
forum: General Help
---

### Post by blackbird34 on 2013-02-10
Does only running a tty save a lot of battery life?

In other words, if I do ctrl+alt+f1 at the login screen, that only loads a command prompt, so no cpu cycles are wasted on a DE and startup applications etc? How much (in %, roughly) do you think this would save?

This is purely out of curiosity, a way of listening to music /taking notes for long periods of time. Web browsing or Films would be out of the question without X at least. Or can you watch a film in a tty with mplayer too?

If its a lot, i'll test taking notes with nano in class to see my neighbours' faces :popcorn: (oh sh**, have to take a look at nano :D )

Thanx

---

### Post by thermion on 2013-02-10
I don't think there will be any difference at all. Simply switching to tty1 won't stop your X-Server and DE.
And when listening to music: Keep in mind that any program used for playback of audiofiles (rhythmbox, amarok or whatever) will stop when switching to tty1-6.

---

### Post by Cheesemill on 2013-02-10
The main suspects for power usage are your screen backlight, hard drive and CPU usage.

Generally speaking CLI programs will use less resources than a GUI program for any given task.

> **blackbird34 said:**
> Web browsing or Films would be out of the  question without X at least.

What gave you this idea?

There are several browsers and media players that will happily run without X.

VLC and mplayer will both run in framebuffer mode. For browsers have a look at links.

---

### Post by Mark Phelps on 2013-02-10
> **blackbird34 said:**
> Does only running a tty save a lot of battery life?

Basically -- NO. While text based usage places less demand on the graphics, that's not going to save a LOT of battery power.  You still will have the hard drive running, and (presumably) still be running apps.

---

### Post by pqwoerituytrueiwoq on 2013-02-10
if you want to save battery edit [FONT=Courier New]/etc/init.d/ondemand[/FONT]
[[IMG]http://www.zimagez.com/miniature/screenshot-02102013-103917am.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-02102013-103917am.php")
change ondemand on that line to conservative
also you want to set your screen brightness to as low as possible (unless off is a option)
anyway in [FONT=Courier New]/etc/lightdm/lightdm.conf[/FONT] add this line
```
greeter-setup-script=sh -c "xbacklight -set 0"
```if xbacklight does not work for you you may want to try backlightx
[http://pastebin.com/F3LDQ6cB](http://pastebin.com/F3LDQ6cB)

[s]i just noticed xbacklight does not work for me with the 3.8 kernel it worked with 3.6 though[/s] xbacklight uses a percentage not a level

for me backlightx does not work in lightdm.conf but xbacklight does
in the desktop session i use backlightx since it does not lag on increase/decrease

---

### Post by nothingspecial on 2013-02-10
> **blackbird34 said:**
>  Web browsing or Films would be out of the question without X at least. Or can you watch a film in a tty with mplayer too?



Of course you can

[IMG]http://i.imgur.com/BevSM9X.png[/IMG]

And take screenshots too :p

---

### Post by tgalati4 on 2013-02-10
On an old Dapper Drake (6.06) machine running on a 1 GHz Celeron, I estimated that running the X-Windows server used ~9% of the CPU cycles.  Depending on your graphics card, running no graphics may save a few a watts, but the lack of productivity is not worth the trade off.

You would have to do some testing with your hardware.  If you are running an Intel processor, you can run powertop and see how many watts are being used and how often the processor gets poked from low-power idle.

You can also recompile your kernel and pull out stuff that you don't need or support for hardware that you don't have.  Running gentoo with a custom-compiled kernel can improve CPU cycle performance by 2% by some measures.

---

### Post by Impavidus on 2013-02-10
Not to mention switching off any wireless technology. Under some circumstances it saved me 20% (really, although this is way more than the power transmitted by the antenna, which is legally limited to (I think, in Europe) 2 W. It must be because of energy losses in the RF amplifier and the extra power to the cooling fans).

Besides, you can still be quite productive without a GUI, as long as you are just typing. I spend half of my computer time writing TeX files in vim (and, incidentally, vim is an even better way of impressing your neighbour than nano). I never tried that with the screen off however, but I could try once.

---

