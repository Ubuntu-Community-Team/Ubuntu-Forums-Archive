---
title: "Polish letters in English Ubuntu 13.04"
date: 2013-06-28
forum: General Help
---

### Post by jet-san on 2013-06-28
Hi there,


I use English versions on both of my systems: Win XP & Ubuntu and I believe I have a similar problem.
I could not see Polish letters in notepad on XP, which means I wasn unable to see Polish letters in subtitles for movies as a consequence.
I went to Contro Panel => Data, time, languages => Regional options => Advanced => set non-Unicode to Polish.
I reboot the computer and now it is ok and my notepad looks as shown below.
[[img]http://s21.postimg.org/pzgrxg9n7/image.jpg[/img]](http://postimg.org/image/pzgrxg9n7/)

On Ubuntu I have...
[[img]http://s21.postimg.org/yt7oejwlv/Ubuntu.jpg[/img]](http://postimg.org/image/yt7oejwlv/)

Anyone knows how to fix it?


Regards
jet

---

### Post by Vaphell on 2013-06-28
if the subs are from windows (and they are), most likely they are using codepage cp1250/windows 1250. Set that encoding in preferences of your player. BTW, what is this, Star Trek? :)


Same deal with text editor. If your text file is using win1250 then you need to open it with that encoding.
In gedit in the open file window there should be option to change encoding. Remember that if you want to preserve original format, you need to save as win1250 as well.

Gedit also tries to guess which codepage is used by trying various options in listed order. By default the list is set to utf8 only.
That order can be tweaked in gconf/dconf (equivalent on regedit in win), eg i set mine to iso8859-2, utf8 for work reasons.
If you need to edit and share text files between backwards XP and linux, i don't envy you :) utf8 is the way to go.

---

### Post by jet-san on 2013-06-30
Hehe, yes - this is Star Trek (The Next Generation)!:D

I keep my movies (with subs) on Win XP drive and watch it on Ubuntu - is that a bad idea?

I cannot find that option there:(
[[IMG]http://s13.postimg.org/t3ib29wsj/Subs.jpg[/IMG]]("http://postimg.org/image/t3ib29wsj/")

---

### Post by Impavidus on 2013-06-30
You can find it in the lower left of the file open dialog box, and also in the save as box.

---

### Post by Vaphell on 2013-06-30
> **jet-san said:**
> Hehe, yes - this is Star Trek (The Next Generation)!:D

I keep my movies (with subs) on Win XP drive and watch it on Ubuntu - is that a bad idea?
no, it's fine. Once you set your video player to proper encoding it works just fine.

I just advise against editing text files from both systems, it's easy but also very annoying that you have to keep track of the encoding all the time.
> I cannot find that option there:(

[http://ubuntuforums.org/showthread.php?t=1291039](http://ubuntuforums.org/showthread.php?t=1291039)
about arabic but the procedure is the same.

---

### Post by jet-san on 2013-07-07
Spot on, thanks!

Central European (WINDOWS-1250) works for Polish fonts.

Just don't know how to set it as default,
so far I need to open with above encoding and save...

---

### Post by Vaphell on 2013-07-08
you need to look in gconf-editor/dconf-editor depending on the ubuntu version and look for gedit prefs
10.04 gconf-editor:
/apps/gedit-2/preferences/encodings -> auto_detected

13.04 (in VM) dconf-editor:
org.gnome.gedit.preferences.encodings -> auto_detected

WINDOWS-1250 needs to be first if you want it to be the default setting.

---

