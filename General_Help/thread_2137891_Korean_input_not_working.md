---
title: "Korean input not working"
date: 2013-04-22
forum: General Help
---

### Post by anonymousthing on 2013-04-22
Hi,

I'm learning korean and I want to get my korean input working. I've enabled it all (installed Korean in Language Support, set to ibus, configured ibus settings) but whenever I swap to korean in ibus, it just types out in roman characters. I've also tried SCIM and Nabi, but those also don't work.

Help!

---

### Post by joe95 on 2014-03-27
I have exactly the same problem, I just cannot seem to get Korean text input working. Any help would be really appreciated.

---

### Post by monkeybrain20122 on 2014-03-28
I was setting up Chinese support for a friend and came across these links which may or may not be helpful. A poster in the second link said he had gotten Korean to work.

[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1241309](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/1241309)
[http://askubuntu.com/questions/360774/how-do-reactivate-ibus-after-upgrading-to-ubuntu-13-10](http://askubuntu.com/questions/360774/how-do-reactivate-ibus-after-upgrading-to-ubuntu-13-10)

According to my web search it seems that ibus is quite broken in 13.10 so I ended up installing fctix instead, it is widely recommended for Chinese (not sure about Korean)  and is the default for kylin-Ubuntu. I have no idea how well it works because I don't use Chinese input methods and don't know anything about pinyin, I will wait for my friend's feedback.

---

### Post by arm-c on 2014-04-05
Hi All, I hope that this helps.  I struggled for some time with this exact same problem.  I used to have no problem prior to Ubuntu 13.10.  I just upgraded to 14.04 and decided to figure it out again... got it this time and it is REALLY SIMPLE and WORKs... it just isn't too straight forward and there are misleading problems with the adding keyboard step... anyway... try he following and let me know if this works for you!!!

Summary:  How to set Ubuntu 14.04 to utilize Hangul.

Background:  Since Ubuntu 13.10, the ibus interface became difficult to setup for Hangul.  There were issues (most resolved by 14.04) with switching keys.  Primary issue appears to be if you want to set the Right Alt key to serve as the "Hangul" key to switch between input modes.  This is compounded by the fact that Linux utilizes many keyboard shortcuts and conflicts with modifiers persist.  In the past, the dialogs required for setting up IBus for Korean were much different.  Ubuntu is on the correct track with the Keyboard Language setup; however, it is confusing for those of us that utilized previous procedures due to lack of information.

Issues:
[] Ability to utilize the Right Alt key for selecting Hangul.
[] Zenity (the program that provides GUI interfaces for many scripts, doesn't display the im-config properly.  For that reason, recommend running from command promt (terminal) with -c option.
[] It is misleading for users of a clean install to be able to select "korean" keyboard from Text Entry prior to installing the correct package (or rather, that the selection doesn't trigger installation of the ibus-hangul package.

Process:
1.  Install ibus-hangul
```

sudo apt-get install ibus-hangul

```

2.  Run im-config to configure the IM client.  If your system is not a "COMPLETELY clean" install where everything is new (ie - did not remount an older "home" partition), recommend that you run im-config twice.  First run, delete the config in your home directory.  Second run, select ibus as the input method. From a terminal (CTRL+ALT+T)
```

im-config -c

```

3.  Setup "Text Entry Settings".  From Dash, type "Text" and select "Text Entry" option.  Alternatively, select system syettings (Power/Config icon top right of screen), then select "Text Entry" option.  Once in the screen, execute the following steps:
- In bottom left, click the + to add a keybaord.
- In new dialog box - filter list by typing "Korean"
-  You will SEE three options:
   Korean
   Korean (101/104)
   Korean (Hangul)
   
   SELECT "Korean (Hangul)" and click ADD.
   
4.  Configure Korean Keybaord -- Select "Korean (Hangul) in the "Input Sources to Use:" part of Text Entry.  Now, in bottom right of the "input sources to use" you will see a "configure" button right next tot he small "Keyboard" icon.  Select that to configure the Hangul input options.

5.  OPTIONAL:  You may wish to configure the keyboard switching options.  Default is "Super + Space".  I don't like that, so I default mine to an alternate key (currently the "menu" key which I rarely use).  Right Alt doesn't work (my preferred since that is the location for the "hangul" key normally.)

---

### Post by bb94 on 2014-04-29
> **arm-c said:**
> Hi All, I hope that this helps.  I struggled for some time with this exact same problem.  I used to have no problem prior to Ubuntu 13.10.  I just upgraded to 14.04 and decided to figure it out again... got it this time and it is REALLY SIMPLE and WORKs... it just isn't too straight forward and there are misleading problems with the adding keyboard step... anyway... try he following and let me know if this works for you!!!

Summary:  How to set Ubuntu 14.04 to utilize Hangul.

Background:  Since Ubuntu 13.10, the ibus interface became difficult to setup for Hangul.  There were issues (most resolved by 14.04) with switching keys.  Primary issue appears to be if you want to set the Right Alt key to serve as the "Hangul" key to switch between input modes.  This is compounded by the fact that Linux utilizes many keyboard shortcuts and conflicts with modifiers persist.  In the past, the dialogs required for setting up IBus for Korean were much different.  Ubuntu is on the correct track with the Keyboard Language setup; however, it is confusing for those of us that utilized previous procedures due to lack of information.

Issues:
[] Ability to utilize the Right Alt key for selecting Hangul.
[] Zenity (the program that provides GUI interfaces for many scripts, doesn't display the im-config properly.  For that reason, recommend running from command promt (terminal) with -c option.
[] It is misleading for users of a clean install to be able to select "korean" keyboard from Text Entry prior to installing the correct package (or rather, that the selection doesn't trigger installation of the ibus-hangul package.

Process:
1.  Install ibus-hangul
```

sudo apt-get install ibus-hangul

```

2.  Run im-config to configure the IM client.  If your system is not a "COMPLETELY clean" install where everything is new (ie - did not remount an older "home" partition), recommend that you run im-config twice.  First run, delete the config in your home directory.  Second run, select ibus as the input method. From a terminal (CTRL+ALT+T)
```

im-config -c

```

3.  Setup "Text Entry Settings".  From Dash, type "Text" and select "Text Entry" option.  Alternatively, select system syettings (Power/Config icon top right of screen), then select "Text Entry" option.  Once in the screen, execute the following steps:
- In bottom left, click the + to add a keybaord.
- In new dialog box - filter list by typing "Korean"
-  You will SEE three options:
   Korean
   Korean (101/104)
   Korean (Hangul)
   
   SELECT "Korean (Hangul)" and click ADD.
   
4.  Configure Korean Keybaord -- Select "Korean (Hangul) in the "Input Sources to Use:" part of Text Entry.  Now, in bottom right of the "input sources to use" you will see a "configure" button right next tot he small "Keyboard" icon.  Select that to configure the Hangul input options.

5.  OPTIONAL:  You may wish to configure the keyboard switching options.  Default is "Super + Space".  I don't like that, so I default mine to an alternate key (currently the "menu" key which I rarely use).  Right Alt doesn't work (my preferred since that is the location for the "hangul" key normally.)

I followed the first two steps, but the "Korean (Hangul)" option doesn't show for me.

---

### Post by Hal58 on 2014-08-26
Same problem here with AMD64 version of 14.04 configured with the 'retro' style.  I've followed the directions listed in this thread repeatedly (to clean up the ~/.xinputrc file), rebooting between steps to insure a clean X and many other things, but the keyboard entry modes never list the "Korean (Hangul)" selection, only "Korean" and "Korean (101/104 key compatible)".  The Icon on the status bar switches between "En" and "Ko" but all entry remains English.  Has anyone been able to get Korean entry to work with 64-bit 14.04?

---

### Post by Hal58 on 2014-12-06
There is an important item missing from the previous directions, and that is (at least in 14.04), you MUST log in with the default Ubuntu desktop and NOT the Retro or Classic. Since the default desktop (the 'new' common one with the dissappearing icons on the left column) has such a heavy CPU demand which causes my netbooks to stay at 100% and consequently heat up to the throttle point, I use the older Gnome Metacity desktop which is quite responsive even on an old Samsung Via Nano and an AMD C-60 based Acer Aspire One. The following steps have been tested with the 14.04 desktop after configuring to the lightweight desktop on an AMD64 system, Via Nano i386 system and a 64-bit Athlon with i686 upgraded from a 12.04 install.

1. log out, select the default Ubuntu desktop with the icon in the top-right of the password screen and log in
2. go to System Settings -> Language support and Add 'Korean'
3. go to System Settings -> Text Entry. Click on '+' in the bottom left of 'input source' window and select 'Korean (Hangul)'. Note that this entry will NOT be present if this is done in the Classic desktop. At this screen, you can also change the key sequence to switch between English and Korean if you desire.
4. log out, select the alternate desktop of your choice (I use the Metacity one) at the login screen and log back in.

At this point, you should be able to select Hangul text entry by pressing the key sequence from the screen in step 3 above, or by left-clicking on the keyboard entry on the top bar (by default, a box displaying 'En') and choosing the tri-color circle for Hangul. The square box then becomes the tri-color circle. Reverse it to return to English.

NOTE: If this works, by going to System Settings -> Text Entry, there will only be the English entry and NO Korean entry!  If it does work, however, it ain't broke so don't fix it!  That must be up to the developers or integrators (sigh!).

---

