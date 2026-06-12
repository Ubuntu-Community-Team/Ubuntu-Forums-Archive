---
title: "Compose key for special characters not working after upgrade"
date: 2007-10-23
forum: General Help
---

### Post by wkleu on 2007-10-23
Hello there

I recently upgraded from 7.04 to 7.10 without any major problems. The only problem I have noticed is that my compose key isn't working any more to create special characters (with ^ or " on top, etc.). This used to work in 7.04 and I am not sure what  changed.

I have gone into System->Preferences->Keyboard and set the compose key and tried a variety of keyboard models without any luck.

The computer is a HP Compaq nc8430. Anyone know what specific keyboard model must be selected?

I want to set my right alt (It is marked as "alt gr") to be my compose key.

Any help/tips/random guesses will be appreciated.

Thanks.

---

### Post by mac.ryan on 2008-01-04
Any luck with this? I have the same problem...

---

### Post by der_joachim on 2008-01-05
Is your /etc/xorg.conf configured correctly? Open it in your favourite text editor and make sure that your keyboard section looks somewhat like this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
	Option         "XkbOptions" "grp:alt_shift_toggle,**compose:ralt**,eurosign:5,altwin:super_win"
EndSection

```
The bold part is the setting for mapping your right alt to compose and that should be hdo only thing you should paste into your own xorg.conf file.

---

### Post by mac.ryan on 2008-01-16
Thanks for the suggestion, and sorry for the belate answer. I checked that option and if I manually change it, when I boot the computer the following time I get a message notifying me that X11 and Gnome have different settings, and asking me what I would like to use.

Alas, whatever I choose, the compose key would still not work.

An additional thing I noticed - however - is that if I assign the compose key to CAPS_LOCK (via the menu in System/Preference/Keyboard), caps lock will stop working as a toggling key for the case of the characters. 

This let me guess that the problem is not about not assigning the "compose call" to a given key, but about not being able to process the keyboard input correctly, returning the desired character... I noticed that there are a number of bugs from feisty in which people complains about certain combinations not working... I wonder if that has something to do with the locale settings.

I am using EN_GB (United Kingdom)... any suggestion on how to investigate further is more than welcome.

---

### Post by der_joachim on 2008-01-16
Hmmm... I am a KDE user, so I cannot help you with your Gnome problem. I've heard your problem mentioned before though. Make sure that the layout that you have configured in your xorg.conf file is the same as in your Gnome keyboard applet. 

Just a thought: does the Gnome keyboard applet allow you to set any custom XKB options? I know that the KDE settings manager does. My xorg.conf has slightly different settings, compared to KDE. Works perfectly.

---

### Post by mac.ryan on 2008-01-17
In my understanding the Gnome KB applet modify the xorg.file automatically and the other relevant setting of XKB...

I tried to follow the communty help ([https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)), and I even tried to implement the XIM module method... but with no avail :-/

I will try to install KDE (a daunting task with a 2 Kb/sec connection) and see if this will help...

Thanks for the suggestions, anyhow. :)

---

### Post by 0x656b694d on 2008-03-10
Hi,

the same problem here. Any update on this?


Thanks,

-Mike

---

### Post by nashattan on 2008-03-12
I never tried it on 7.04, but I can´t get the compose key working on 7.10 either.  Dead keys work fine, but I have the exact same results with compose as listed above.  The assigned key stops doing what it was previously assigned to do but does not let me type special characters.

---

### Post by 0x656b694d on 2008-03-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/202650](https://bugs.launchpad.net/ubuntu/+bug/202650) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

---

### Post by Toscho on 2008-04-05
I had the same problem. Installing SCIM and rebooting the computer helped. Now it works fine.

---

### Post by 0x656b694d on 2008-04-07
Toscho, that is the scim method, which is too much for me. BTW, i lose my keyboard sometimes in Qt applications with scim enabled.

I would like to see X method working. I have my own ~/.XConfig file with some useful combinations, just wonder why it has stopped working.

-Mike

---

### Post by MemoryDump on 2008-05-09
> **der_joachim said:**
> Is your /etc/xorg.conf configured correctly? Open it in your favourite text editor and make sure that your keyboard section looks somewhat like this:
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
	Option         "XkbOptions" "grp:alt_shift_toggle,**compose:ralt**,eurosign:5,altwin:super_win"
EndSection

```
The bold part is the setting for mapping your right alt to compose and that should be hdo only thing you should paste into your own xorg.conf file.
does this work in for using the right ALT key to insert special characters? such as accents.. ex: ALT plus 130 (on the keypad) give you a "é". This is something I need.. which I actually miss from windows. (so does my wife)

---

### Post by 0x656b694d on 2008-05-09
> **MemoryDump said:**
> does this work in for using the right ALT key to insert special characters? such as accents.. ex: ALT plus 130 (on the keypad) give you a "é". This is something I need.. which I actually miss from windows. (so does my wife)

No, it doesn't, sorry.
It works in a bit cooler way. Look at me, who never use diacritics and don't remember the code for "e acute". But it took just a 2 seconds for me to figure out that i can type "Compose, apostroph, e" to get é.
Also, i put custom combinations into my ~/.XCompose file to get arrows (&#8594;), and even smileys &#9786;.
Those combinations are pretty simple to remember (Compose, s, o = §). Note, that they are commas, not + (not simultaneous).

BTW, you don't need to change anything in the xorg.conf. Everything is done by the standard tool via System&#8594;Preferences&#8594;Keyboard&#8594;Layouts&#8594;Layout options.

---

### Post by 0x656b694d on 2008-05-09
Forgot to mention that they changed the standard layout with dead keys in Hardy. So now you may want to choose the "USA International (AltGr dead keys)" for example.
I have that one plus Russian Winkeys. I set "right Alt is Compose" option for both and so can use the Compose sequences in both layouts.

---

### Post by MemoryDump on 2008-05-09
> **0x656b694d said:**
> No, it doesn't, sorry.
It works in a bit cooler way. Look at me, who never use diacritics and don't remember the code for "e acute". But it took just a 2 seconds for me to figure out that i can type "Compose, apostroph, e" to get é.
Also, i put custom combinations into my ~/.XCompose file to get arrows (&#8594;), and even smileys &#9786;.
Those combinations are pretty simple to remember (Compose, s, o = §). Note, that they are commas, not + (not simultaneous).

BTW, you don't need to change anything in the xorg.conf. Everything is done by the standard tool via System&#8594;Preferences&#8594;Keyboard&#8594;Layouts&#8594;Layout options.
ahh.. thanks for the explanation! I just have to print out a handy little chart so my wife and I can refer to it easily.
Know of any good ones? I've see a bunch, but most don't look that good.
thxs again
-MD

---

### Post by 0x656b694d on 2008-05-09
oh, well, the whole list of the combinations are in the 
/usr/share/X11/locale/en_US.UTF-8/Compose file.

This page is not so bad:
[http://cyberborean.wordpress.com/2008/01/06/compose-key-magic/](http://cyberborean.wordpress.com/2008/01/06/compose-key-magic/)

You're actually may want to make a list of symbols you personally use more often and make a table by yourself. Because the whole list is too huge.

---

### Post by MemoryDump on 2008-05-12
> **0x656b694d said:**
> oh, well, the whole list of the combinations are in the 
/usr/share/X11/locale/en_US.UTF-8/Compose file.

This page is not so bad:
[http://cyberborean.wordpress.com/2008/01/06/compose-key-magic/](http://cyberborean.wordpress.com/2008/01/06/compose-key-magic/)

You're actually may want to make a list of symbols you personally use more often and make a table by yourself. Because the whole list is too huge.

great thanks! it's mostly for the French accents that my wife and I need these reference sheets. :)
still weird that the ALT-keynumber combo can't be used in a similar fashion as in windows. oh well

---

