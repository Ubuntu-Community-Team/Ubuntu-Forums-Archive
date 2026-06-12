---
title: "browser for japanese/ english"
date: 2008-05-04
forum: General Help
---

### Post by scientist1971 on 2008-05-04
a user of my computer regularly uses both english and japanese when browsing
firefox does not support all the japanese characters and epipheny only lets japanese be typed and will not switch to english when the relevant key is pressed (this makes it impossible to type web site addresses)
anyone got any ideas for a browser that will enable both japanese and english to be used?

---

### Post by Zorael on 2008-05-04
Okay, this is what I did to get Japanese support in all and any applications. I hear Gnome has a graphical interface with which you can do most of this, so parts of this guide may be redundant. See [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM).

So consider this an alternative approach.


[list=1][*]Install the following packages.
[list][*]scim (if Gnome)
[*]skim (if KDE)
[*]scim-tables-ja
[*]scim-anthy[/list]
[*]Hit Alt+F2 to spawn a run box and run '**scim**'. An icon should pop up in your systray. Obviously, make this '**skim**' for KDE.
[*]Go into Scim's configuration, either through the tray icon right-click menu, or by running '**scim-setup**'. Use the tray icon for KDE, I don't know the command.
[INDENT]If KDE, go to General SCIM -> Other tab, pick '**scim-panel-kde**' as panel program and '**kconfig**' as config module.
A similar option may be needed for Gnome as well, I'm not sure.[/INDENT]
[*]Set keybinds as you please. I disabled everything except one keybind for trigger since I only plan to use Japanese (toggled on) and Swedish (toggled off), but the "Show input method menu" is sort of handy if you have several methods enabled.
[*]Unmark "Other".
[*]Expand "Japanese" and make sure "Anthy" is enabled. You don't need the others since Anthy has kana modes (as well as rômaji modes) you can toggle, but do as you please. I didn't like the "Nippon" one at all.


[*]*(Not necessary if you're only going to rely on the toggle keybind in the Global Setup tab.)*
Having Anthy selected, hit Edit Hotkeys and add a hotkey, unless you plan to use the next/previous input method in the earlier tabs. I use Ctrl+Alt+period, for instance.


[*]*(Not available in the KDE (Skim) config app, so run '**scim-setup**' manually for this step. Make sure to apply settings before exiting the other one.)*
Go to the Anthy tab (IMEngine -> Anthy) and set it up as you please. Here you can set keybinds for toggling kana modes etc. Notably "Circle input mode".
I also suggest you remove any keybinds you aren't going to use, so they don't conflict with other running programs. (Ctrl+D to delete instead of just Del seems dumb.)
If the rômaji standard you're not used to isn't supported by any of the default tables under the Romaji typing tab, hit Customize and add stuff. (like, if you want sya to be sha, etc. I also needed to add the Japanese version of ~ since I like to use it. Plenty.


[*]Check the GTK tab and see if there are any options you'd like to alter.


[*][list][*]**HARDY**: Open up a terminal and enter this command.
```
$ sudo update-alternatives --config xinput-all_ALL
```
You should get a menu with some ~4 alternatives. Hopefully '**scim**', '**scim-bridge**' and/or '**skim**' is listed there. I chose **skim** and it works in KDE, but your mileage may vary.
**NOTE:** For me, this was enough for all programs except Firefox 3.0b5, which further required the below Gutsy procedure. Opening FF3 without having done that *broke* scim until next start of kdm.


[*]**GUTSY (and Hardy + FF3)**: The Hardy solution *may* work. Else: [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM). Scroll down to *"Additional configuration if you're not using a CJK session"* and follow the steps there. I doubt that mentioned scim-bridge app works (since I don't seem to be able to switch input modules in firefox, for instance), so you're likely better off editing that file.[/list]


[*]Save your work, restart X with Ctrl+Alt+Backspace.[/list]

Let me know if it didn't work.

---

### Post by scientist1971 on 2008-05-05
thanks for the response
busy this afternoon but will try later and tell you if it worked

---

### Post by scientist1971 on 2008-05-05
I followed your instructions as best I could and use the scim input method setup from the system tray
I tried to setup my japanese keyboard and use the han kaku zen kaku key provided on japanese keyboards for toggling between japanese and english (as the japanese user does in XP) but it did not work and the input for this user is hiragana and english for me (i.e. cannot switch between the languages)
I will continue to try with your instructions and the link you gave me
also as a side effect my desktop appearence preferences > visual appearence is stuck on none where I usually use advanced desktop settings to customise it - when I try to do this I am given a message saying effects could not be enabled - have no idea why this happened
will keep trying though

---

### Post by Zorael on 2008-05-05
I'm using a Swedish keyboard so I don't have the hankaku, zenkaku and similar keys, though I'm able to switch between full-width/half-width hiragana/katakana/romaji with the keybind in the Anthy settings.

A telltale sign to know if you've succeeded is if you can toggle scim or Japanese on and off when you're in, say, Firefox. If it worked, you've managed to set scim as your default input, then you can toy around with the bindings and get everything the way you want it.

A similar sign would be if the scim panel pops up. If it did; success.

As as side note, you may want to try scim-bridge instead of scim when doing the update-alternatives command, if all else fails. Again, I'm on KDE so skim did the trick for me.

---

### Post by scientist1971 on 2008-05-05
ok thanks will try that
btw you encouraged me to try kubuntu
looks very good - something else to play around with :)

---

### Post by scientist1971 on 2008-05-06
I stopped trying to use the hankaku, zenkaku key and changed it to something else and it worked like a treat thanks

---

### Post by Zorael on 2008-05-06
Awesome, have fun. :>

---

### Post by scientist1971 on 2008-05-06
I have a further problem unfortunately
the other user of my computer had other issues such as not being able to play  you tube videos etc which my user login did not have plus as her english is much better than my japanese rather than change her settings I deleted her as a user (including her home directory) and asked her to use my login (we are family so sharing a login is no problem)
the problem is that scim will now not function at all despite me reinstalling it, following you instructions, and restarting several times... nothing
any further help appreciated

---

### Post by Zorael on 2008-05-06
Curious. None of this should be user-specific.

Do you get the tray icon? If so, it could be your keybinds acting up.

If no tray icon, please enter the terminal output of the following command.
```
$ ps -A | grep im
```

---

### Post by scientist1971 on 2008-05-06
richard@richard-laptop:~$ ps -A | grep im
 6914 ?        00:00:00 scim-launcher
 6918 ?        00:00:00 scim-helper-man
 6919 ?        00:00:00 scim-panel-gtk
 6921 ?        00:00:00 scim-launcher
richard@richard-laptop:~$

---

### Post by scientist1971 on 2008-05-06
no launcher though...

---

### Post by Zorael on 2008-05-06
What if you enter this in a terminal, then?
```
$ scim &
```

---

### Post by scientist1971 on 2008-05-06
richard@richard-laptop:~$ scim &
[1] 6238
richard@richard-laptop:~$ Smart Common Input Method 1.4.7

Launching a SCIM process with x11...
Loading socket Config module ...
Creating backend ...
Loading x11 FrontEnd module ...
SCIM has exited abnormally.
scim &scim &

---

### Post by Zorael on 2008-05-06
Weird; if it worked once it should work every time, or so you'd think.

Have you tried the Gutsy approach, editing that file in /etc/X11/xinit/xinput.d/?

Also, you could enter this for good measure, though I'm not sure it'll help at all.
```
$ sudo dpkg-reconfigure scim scim-launcher scim-bridge
```

---

### Post by scientist1971 on 2008-05-06
you won't believe this but my password has WA in it and the only place on the whole system that this is being recognised as hiragana is in the terminal!?!
therefore any instructions you give me will have to wait until I have changed my password
thanks for all the help BTW much appreciated

---

### Post by Zorael on 2008-05-06
Reading the man page for scim, I see this:
```
EXAMPLES
       To  use scim in XIM mode, execute the following commands in an X termi&#8208;
       nal (assuming Bourne style shell):
              XMODIFIERS="@im=SCIM"
              export XMODIFIERS
              GTK_IM_MODULE="xim"
              export GTK_IM_MODULE
              scim -d
              <program>
       Now you can press Ctrl-space to activate scim in the program  you  just
       started from X terminal.  To avoid the inconvenience of having to start
       the  program  from  X  terminal,  make  sure  you  set  XMODIFIERS  and
       GTK_IM_MODULE before starting your X session.

       To use scim in GTK IM mode, just start any GTK+ application, then right
       click in the application, choose "Input Methods -> SCIM  Input  Method"
       in  the  pop-up  menu,  and  scim should automatically start.  Alterna&#8208;
       tively, you can use the following commands to set scim as  the  default
       GTK IM module (again assuming Bourne style shell):
              GTK_IM_MODULE="scim"
              export GTK_IM_MODULE
              <gtk-program>
       Here  scim  will also automatically start when you start your GTK+ pro&#8208;
       gram.  However, it’s still a good idea to start scim explicitly even if
       you  use  GTK  IM mode, because if only one application is using GTK IM
       mode, scim will automatically stop  when  you  quit  this  application.
       Then  when you start a new application, scim will start again, this can
       cause quite long delay for application start and  quit,  giving  people
       the impression of "everything slows down when using scim".

       The following command starts scim in daemon mode, using the simple con&#8208;
       figure module, Pinyin IM engine module, X11 frontend module:
              scim -c simple -e pinyin -f x11 --no-socket -d
```

Basically, opening any GTK+ program and right-clicking an entry field should pop up a meny wherein you can choose input method. If scim is listed there you know it sort of works, but perhaps the keybinds are messed up in scim-setup or it simply doesn't autostart correctly. If you try the first command and it works, you know something similar is wrong.

---

### Post by Zorael on 2008-05-06
> **scientist1971 said:**
> you won't believe this but my password has WA in it and the only place on the whole system that this is being recognised as hiragana is in the terminal!?!
therefore any instructions you give me will have to wait until I have changed my password
thanks for all the help BTW much appreciated

eheh. :>

---

### Post by scientist1971 on 2008-05-06
zorael
It appears to be working :)
need to adjust the toggle keys but I can select hiragana, katakana or english by selecting with the mouse :)
cannot thank you enough for spending time helping me with these problems
richard

---

### Post by Zorael on 2008-05-06
Cheers.

If you're using Anthy (and not the Hiragana, Katakana or Nippon input method services), the keybind you want to set to toggle between kana/romaji modes is the "Circle input mode" one, in Anthy's settings.

Anyway, have fun. :>

---

