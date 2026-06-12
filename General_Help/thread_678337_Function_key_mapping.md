---
title: "Function key mapping"
date: 2008-01-25
forum: General Help
---

### Post by Jeezus on 2008-01-25
I have a Toshiba Satellite A105 laptop, and I'd like to set up my function key to swap between my laptop, and an external monitor.
I'd like to know if there is a way to map to function key (Fn)+F5 a set of cyclical commands. Whereas you press it and it runs:

xrandr --output VGA --mode 1024x768
xrandr --output LVDS --off

and the next time you press it, it runs:

xrandr --output LVDS --mode 1280x800
xrandr --output VGA --off

so that I could just press Fn+F5 to swap from laptop monitor to external monitor, and vice versa.

---

### Post by diaa on 2008-01-26
Hi, You can map keys to commands using two methods[LIST=1]
[*][Configuring Gnome custom shortcut keys]("http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/")
[*][Using XBindKeys]("http://hocwp.free.fr/xbindkeys/xbindkeys.html")[/LIST]The first method is simpler to use but the second method is more powerful and more complex to use.
However there's a problem, you need to run different commands using the same shortcut, This can be done using a - Python - script to find out which commands need to be executed.
You need to find someone to do this for you since it needs someone with knowledge in programming(unless you have the time and can learn about it and do it yourself :) ).
scripts can be written in several languages:[LIST]
[*]Shell scripts
[*]**Python**
[*]Perl[/LIST]-- 
Diaa Sami

---

### Post by Jeezus on 2008-01-26
Thanks Diaa, I'll look it up. I haven't been able to find the keycode for the Fn key on my laptop though. As far as I understand, is that it's harwired into the system, and ubuntu doesn't recognize it, it only sees the event. I tried viewing the event with xev, but it doesn't seem to register anything. do you have any ideas?

---

### Post by diaa on 2008-01-27
> **Jeezus said:**
> Thanks Diaa, I'll look it up. I haven't been able to find the keycode for the Fn key on my laptop though. As far as I understand, is that it's harwired into the system, and ubuntu doesn't recognize it, it only sees the event. I tried viewing the event with xev, but it doesn't seem to register anything. do you have any ideas?

Do you mean that F5 and Fn+F5 generate events with the same *keycode* or generate the same key combination in *Preferences* > *Keyboard Shortcuts*?

As far as I can tell, Fn doesn't have a separate keycode, it's, like you said, hardwired into the keyboard and is transparent to Ubuntu, however pressing a key with Fn held(e.g Fn+F5) should generate a different key than pressing the same key alone(e.g. F5).

---

### Post by Jeezus on 2008-01-28
it doesn't even register in keyboard shortcuts dealy.
when I do it xev though I get this string:
KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  108 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
                 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

but I don't know what to do with it

---

### Post by diaa on 2008-01-29
> **Jeezus said:**
> it doesn't even register in keyboard shortcuts dealy.
when I do it xev though I get this string:
KeymapNotify event, serial 28, synthetic NO, window 0x0,
    keys:  108 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
                 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

but I don't know what to do with it

I'm not really sure, sorry.

---

### Post by Jeezus on 2008-01-29
yeah, me either... =)
I guess I just have to accept the fact that my laptop's Fn key is just not meant to be mapped. :p What'cha gonna do, right?
Thanks anyway though. =)

---

