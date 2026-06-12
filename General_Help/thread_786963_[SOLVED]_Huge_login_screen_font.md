---
title: "[SOLVED] Huge login screen font"
date: 2008-05-08
forum: General Help
---

### Post by jimbob on 2008-05-08
How do I adjust the font size on the login screen window in Hardy?
Each character entered is HUGE - two of them fill up the entire Username window (at least as much of them as you can see).

---

### Post by jimbob on 2008-05-12
Surely someone else out there has seen this.  It happens with both the Hardy live/install CD and the alternate CD.

This is on a Toshiba laptop with an Intel 82852/855GM Integrated Graphics Device.

---

### Post by nick_h on 2008-05-12
I seem to remember reading a thread similar to this before.

The only thing I can think of at the moment is to add a -dpi option to the line that starts the standard X server in your /etc/gdm/gdm.conf file.

---

### Post by jimbob on 2008-05-19
I do not know where to put a .dpi option in the gdm.conf file.

Can anyone help with this?

If I change the login window to something other than the default and then reboot, the new login screen comes up just as huge as the font.

---

### Post by greeneagle99 on 2008-05-19
I have the same problem, too. Very low resolution of login window with huge font. After login the display switches to correct resolution. This occurs on my desktop-computer with an ATI 9200 card. On my notebook (Lenovo T60) everything is OK...

---

### Post by jimbob on 2008-05-19
That's really weird because my desktop with Nvidia 6600GT is just fine.

It's the laptop that is messed up.

Well, here I go again with my fourth re-install of Hardy on the laptop. I messed up gdm so badly that I can no longer start it up.

---

### Post by havchr on 2008-05-19
I had this on my laptop, but it went away after I enable the restricted graphics drivers (ati mobility card)

---

### Post by nick_h on 2008-05-19
> I do not know where to put a .dpi option in the gdm.conf file.

Can anyone help with this?

In your /etc/gdm/gdm.conf file you will see a section like the following:
```
[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 **-dpi 96**
```

You can add a dpi option here (96 dpi in my example).

---

### Post by jimbob on 2008-05-20
> You can add a dpi option here (96 dpi in my example).

Thanks for that.  I set it at 200 dpi and it cut it down to manageable size but not enough to be normal. ( [SIZE="6"]semi-huge[/SIZE] )

I tried 600 then 400 but no smaller could be achieved.  How does one know the correct value here?  What put you onto 96 dpi?

---

### Post by nick_h on 2008-05-20
> What put you onto 96 dpi?

96 dpi is the resolution Windows uses by default.  When I first switched to Ubuntu I didn't like the font rendering and I thought the screen resolution might be part of the problem.  Now I use it because it reduces the font in my gdm login screen slightly, but my font is only slightly too big to begin with.

---

### Post by Jaiinus on 2008-05-20
Just had a similar problem which I fixed in this way:

```
gconftool-2 --type float -s /desktop/gnome/font_rendering/dpi 75
```

I don't know if this will fix the login screen but it fixed my fonts from being super humongous.

---

### Post by greeneagle99 on 2008-05-20
Are you sure that the problem is just the font-size? I installed Hardy on 2 machines (Notebook and Desktop). On the notebook everything works fine. On the desktop-machine gdm-resolution is quite low and of course the font seems quite huge if the resolution is so low.

Normally this behaviour can be fixed by editing xorg.conf (First specified resolution should be taken by gdm) but unfortunately this seems not to work in my environment. It seems that the 'Modes'-entries in xorg.conf are ignored....

I also cannot believe that it is a driver-problem because when I have logged in everything is OK.

---

### Post by housam on 2008-05-20
try this ( it happened with me in Gutsy and fixed ) sys > pref. >> appearance >> fonts >> window title font >> scale it to 1 or 2 .

---

### Post by Zacariaz on 2008-05-20
I had the same problem, also on a toshiba laptop.
All i did to get it working, was to install in "secure graphical mode" (or something similar) and the problem was no longer a problem. I have a working installation now.

---

### Post by jimbob on 2008-05-20
> All i did to get it working, was to install in "secure graphical mode" (or something similar) and the problem was no longer a problem. I have a working installation now.

I couldn't find anything resembling "secure graphics mode" but did find the boot parameter "vga=771" (I'm using the alternate install CD) which seemed to select the native mode of the Toshiba (1280x800) immediately. Installing again now so will see if this makes any difference.

---

### Post by mali2297 on 2008-05-20
Another solution might be to add the line
```
	
Option  "DDC" "No"

```
in *Section "Device"* in the file **/etc/X11/xorg.conf**. This works at least for me with the open source radeon driver.

You can edit the file from the terminal with nano,
```

sudo nano -B /etc/X11/xorg.conf

```

---

### Post by jimbob on 2008-05-21
> Option  "DDC" "No"
This seems to have done the trick - thank you so much!   I guess I need to look up that option to see exactly what it does.

I'm marking this thread as solved.

---

### Post by nick_h on 2008-05-21
> I guess I need to look up that option to see exactly what it does.
DDC allows the X server to determine the supported video modes for the monitor.  It obviously doesn't work too well in your case.

[http://en.wikipedia.org/wiki/Display_Data_Channel](http://en.wikipedia.org/wiki/Display_Data_Channel)

There is also a brief mention in the xorg.conf manual page.
```
man xorg.conf
```

---

### Post by denver38 on 2008-06-20
> **mali2297 said:**
> 
```
	
Option  "DDC" "No"

```


Thanks, solved the problem on my kubuntu machine

---

### Post by gatorbrit on 2008-06-23
> **mali2297 said:**
> Another solution might be to add the line
```
	
Option  "DDC" "No"

```
in *Section "Device"* in the file **/etc/X11/xorg.conf**. This works at least for me with the open source radeon driver.

You can edit the file from the terminal with nano,
```

sudo nano -B /etc/X11/xorg.conf

```


Just a note, this solved the problem on huge login fonts for me on my toshiba satellite A105.

---

### Post by houba on 2008-06-24
> **mali2297 said:**
> Another solution might be to add the line
```
	
Option  "DDC" "No"

```
in *Section "Device"* in the file **/etc/X11/xorg.conf**. This works at least for me with the open source radeon driver.

You can edit the file from the terminal with nano,
```

sudo nano -B /etc/X11/xorg.conf

```

Hey, thanks a lot, it helped me too on my fsc amilopro v3505 (intel integrated graphics)!!!!

bye

---

### Post by metallicamaster3 on 2008-07-27
also solved the problem for me on my older Dell Inspiron 6000!

---

### Post by muckv on 2008-07-27
good work

---

### Post by KOTeek on 2008-07-29
It seems that  - Option  "DDC" "No" - helps solve huge font problem on toshiba laptops =) It works on Satellite MX40X184.

---

### Post by Cardoso on 2008-08-08
Thanks to Mali2297. This works also on a LG S1 Pro Express Dual, with Ubuntu 8.04.

---

