---
title: "Missing Keyboard Layouts"
date: 2006-11-07
forum: General Help
---

### Post by iceman504 on 2006-11-07
i just noticed this problem when trying to change my keyboard layout. When i go to my keyboard preferences unknown is in the keyboard model box and when i click on add 
no layouts are there. and when i try to change my accessibility options i get a warning saying i don't have the xkb extenstion. I tried kcmshell keyboard_layout and when i click apply i get:
ERROR: X server XKB extension 0.0 != 1.0
DCOP aborting call from 'anonymous-21079' to 'kxkb'
ERROR: Communication problem with kxkb, it probably crashed.

I also tried some other commands people mentioned on this thread but none of them have worked for me so far. 
Any ideas on how to fix this?

---

### Post by iceman504 on 2006-11-08
so nobody knows how to fix my problem also i just noticed this after i installed xgl/compiz

---

### Post by Into The Pit on 2006-12-05
I'm having the same problem too in edgy :(

---

### Post by strabes on 2006-12-05
run gnome-settings-daemon

that should fix your problem; if it does, you should add it to startup programs in gnome-session-properties

if not, add it to startup anyway and then restart your x session with ctrl+alt+backspace, and then if it still doesn't fix your problem, remove it. This should also allow you to use custom gtk and icon themes while using xgl/compiz.

---

### Post by grinias on 2006-12-09
I have the same problem. I think we are talking about kubuntu/kde and not gnome. The problem began (I think) and for me after installing xgl/beryl and using it as one more session option, since I have fglrx installed for my ATI 600X card. At least in KDE session, I can change from US to Greek. This cannot be done in xgl/beryl session, however.

---

### Post by grinias on 2006-12-09
I have the same problem. I think we are talking about kubuntu/kde and not gnome. The problem began (I think) and for me after installing xgl/beryl and using it as one more session option, since I have fglrx installed for my ATI 600X card. At least in KDE session, I can change from US to Greek. This cannot be done in xgl/beryl session, 

I hope that someone will post the answer.

---

### Post by FenrisAbraxas on 2006-12-30
Check:

[This post :)]("http://ubuntuforums.org/showthread.php?p=1946677#post1946677")

---

### Post by iceman504 on 2007-01-18
ok Thanks everyone who responded i figured out the problem after looking at [this]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#.22I_have_no_keyboards_listed_in_gnome-keyboard-preferences.3F.22")
except i added the load "xkb" line to my xorg.conf file b/c i didn't have it and i removed the "-kb" line in my gdm.conf-custom file b/c it was present.
and just pressing ctrl+alt+backspace won't do it for some reason i had to fully restart my computer for it this start working

---

