---
title: "Need Accents With Urgency!!!"
date: 2008-03-12
forum: General Help
---

### Post by arashiko28 on 2008-03-12
I need a solution NOW!!!! I've searched this forum upside down looking for a solution and still I am far from it. I installed Ubuntu Ultimate Edition 1.7, it's gutsy based, I used gutsy without any kind of problem related to this. I changed the keyboard layout to write on spanish, english and japanese. Now, on spanish, I need special characters such as Ñ, ñ, and words with accents, these are essentials. But even if I can write the Ñ, I don't get the accents, which are made by combining ´ and a vowel, instead, I get ´a.

I have reconfigured Xorg, changed the layout about a 100 times, restarted and more. I have been looking for a qwerty spanish file that someone referred to look at, and it's blank. This has a mix between GNOME and KDE, so I have checked both configurations, still no good. I need a real solution ASAP, someone who uses KDE since as I've read, this is common in KDE, also I wanted to uninstall all of KDE based, but there is no core, nothing that can really make a difference in a Keyboard.

Please, help!! There are a lot of people with this problem. I desperately need those accents and the character map it's not a solution.:(

---

### Post by kyphi on 2008-03-13
Go System then Preferences then Keyboard.  Coose Layout Options and scroll to Compose Key Position.  Choose a Compose Key.  Using the Compose Key with the accent of choice and the letter you can make all sorts of accents.

à, á, ã, ä, â, .....

---

### Post by arashiko28 on 2008-03-14
No good, this as far as I've read, is a KDE very common problem. So please, someone with KDE please help. I can't find a way to remove all of KDE, because even being a lot of kde applications, the kde core and stuff like that are uninstalled.

UPDATE:

Ok, so as far as I've searched, there are some references about checking the xkb rules, so I tried, but :O found out that that file does not exist, neither any file inside the /usr/share/X11/xkb, has an "es" extension :s... So now it all focuses con finding how to find and download the xkb rules file. Again this is a very common KDE problem, please KDE users, help!!!!

---

### Post by arashiko28 on 2008-03-15
Well... that's it, i've had it. I'm going back to the normal Ubuntu 7.10, even if I love how U.E. looks, it's not functional for me. See ya in a couple of minutes. BTW, none of my friends who are experimented KDE users found a solution. But it still being a very common KDE users problems, so I think it should be taking into account for the 8.04 version :)

---

### Post by der_joachim on 2008-03-16
I have no experience with UE whatsoever. However, I do have some experience with configuring xorg. My right alt is configured to act like a compose key and it works flawlessly. 

How to configure xorg:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbLayout" "us(intl)" # replace this with your own layout.
Option        "XkbModel" "pc104" #if applicable: replace with own keyboard model
Option         "XkbOptions" "compose:ralt"
EndSection

```
Configuring KDE is not so difficult. Fire up your keyboard config utility and select the tab 'Advanced'. This tab enables you to play and experiment with XKB settings.

---

### Post by arashiko28 on 2008-03-17
I'm back to regular Gutsy. I can't believe this course is following me!!! I mean, I used gutsy from all 4 months now and NEVER had this problem, not I installed back amarok and voila, $%"% up keyboard again! I changed it to us intl and was working fine, but now, none!!! I need this accents!!! I'm truly desperate, I uninstalled almost everything related to KDE, the language packs, amarok, all of it!!! Where's this coming from? Please help!!!:confused::confused::confused::confused::confused:

---

