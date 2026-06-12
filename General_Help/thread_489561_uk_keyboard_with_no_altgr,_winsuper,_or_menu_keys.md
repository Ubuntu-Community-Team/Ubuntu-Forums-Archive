---
title: "uk keyboard with no altgr, win/super, or menu keys"
date: 2007-07-01
forum: General Help
---

### Post by d_yat on 2007-07-01
Where to start?
Well firstly I've been searching the forums for a while now trying things out with no luck (probably did it wrong or something being n00b like to Linux). Oh yea the problem being that stated in the title.
xmodmap produces this

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Mode_switch (0x71)
mod2        Num_Lock (0x4d)
mod3      
mod4      
mod5        Scroll_Lock (0x4e)

I played about with xev to find, umm, I'll attach it to the bottom if you wanna look. Basically AltGr key is Mode_switch (what ever that is), and the other 3 have 'no symbol'.

I found a post somewhere saying go to the keyboard preferences and under layout options change the alt/win key behavior to alt and meta. That however gave me error messages (also attached). This error happens if I try to change anything in there! Very weird.

I only noticed this lack of keys after installing sri lankan fonts for my parents (&#3520;&#3540;! woo!). It works, except there's some letters than can only be accessed by the AltGr key. ([http://sinhala.sourceforge.net/](http://sinhala.sourceforge.net/) have the instructions to do this, if you need to know). I don't think that changed anything on the keyboard tho, as i have noticed the AltGr key not working before.

Anyway, not sure what to do now. Any suggestions?

---

### Post by d_yat on 2007-07-03
no suggestions/ideas at all? =(

---

### Post by d_yat on 2007-07-04
bump...

---

### Post by d_yat on 2007-07-06
ok, got bored, tried some other things. still no luck tho.
Anyway i tried reinstalling the bugs from above (and now below)
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

didn't work.
tried what was said here [http://ubuntuforums.org/showthread.php?t=472825](http://ubuntuforums.org/showthread.php?t=472825) (reinstall xkb-data)
but that didn't work (I noticed my tty sessions didnt work either, and they still don't. They did once, because I remember using them.)

please, anyone, help!
or else i'll be very sad. (go on say aww)

---

### Post by zmike1 on 2007-07-08
Sorry I can´t help... but you´ve got my sympathy.  I´ve been trying to find a solution to a keymapping problem for many days.  
Maybe look at xorg.conf file if it applies to your set up.  I´m more of a noob than you so I can´t offer much.
Good Luck

---

### Post by d_yat on 2007-07-10
thanks zmike, but tried that before, and just for the hell of it, tried it again. changed a few things, but no luck.
Althought I get that "X.Org Foundation 
70200000" error/bug thing on startup now (login in).

I wonder if reinstalling (ubuntu) would work? and if I did, does it matter that my /home directory is on the same partition as ubuntu is on. -> in other words will I lose all of the settings/programs after the reinstall? or have I had too many bad memories with reinstalling windows and loosing stuff when I shouldn't!?

---

### Post by d_yat on 2007-07-26
for anyone who cares, after reinstalling ubuntu, the alt gr key worked again. (I thought it would as during the 1st install I tested the keyboard for the € key, and it worked.)

so i'm guessing that at some point in time after some fiddling, I messed up the keyboard config somehow.
lesson ->fiddling and tinkering is fun, but sometimes it will mess with things in an annoying way.
not that I will stop mind you.

---

