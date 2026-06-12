---
title: "hardy boot problem, won't start!"
date: 2008-05-03
forum: General Help
---

### Post by savethewabbit on 2008-05-03
i upgraded to hardy a couple of days ago... everything looked fine until i turned off my computer. 
since then, it's only a matter of luck whether my computer turns on or not. 
i can see the system start, and then, as it usually happened to me even with gutsy, my monitor goes black during loading and says "frequency too high". not a problem because it goes back to normal when the login appears. with hardy though, it can go on for 15 minutes with that message and no signs at all that the login screen has appeared. 
just to turn on my computer this morning i had to reboot manually a dozen (if not more!) times, only to leave it be for 10 minutes once, after which the login screen appeared. 
i don't know if it's a loading problem and if i really let the pc load for 20+ minutes the pc would start, but even if it was, it's not exactly an ideal timing. 

is there anything i can set up or something? i can't really see what goes on during startup given my "frequency too high" problem with my monitor (which doesn't really bother me much), so i don't know what's wrong.

anything would be helpful.

thanks.

---

### Post by Zorael on 2008-05-03
Try either booting into recovery mode, or hitting Ctrl+Alt+F1 when the graphical interface has started (likely when you're getting the frequency too high message).
[list][*]If recovery mode, pick 'go to root shell'.
[*]If Ctrl+Alt+F1, just login.[/list]
Then enter the following:
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
$ sudo dpkg-reconfigure xserver-xorg
```
Obviously, you'll need to write this down someplace.

---

### Post by savethewabbit on 2008-05-03
> **Zorael said:**
> Try either booting into recovery mode, or hitting Ctrl+Alt+F1 when the graphical interface has started (likely when you're getting the frequency too high message).
[list][*]If recovery mode, pick 'go to root shell'.
[*]If Ctrl+Alt+F1, just login.[/list]
Then enter the following:
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0805
$ sudo dpkg-reconfigure xorg.conf
```
Obviously, you'll need to write this down someplace.


thanks! i will try it out right now. just a newbie question though: do i have to write that $ symbol or do i just have to do sudo *code*? thanks a lot for replying so fast!

---

### Post by strabes on 2008-05-03
You don't have to do type the $. When you see a $ in front of a line it simply indicates that what follows is a command which you should enter into a terminal.

---

### Post by savethewabbit on 2008-05-03
> **strabes said:**
> You don't have to do type the $. When you see a $ in front of a line it simply indicates that what follows is a command which you should enter into a terminal.

oh, ok. thank you lots. i'm going to try now and let you know how it went.

---

### Post by savethewabbit on 2008-05-03
ok, i tried and while the first command didn't give any errors, with the second one (dpkg-reconfigure) it says:

```

Package `xorg.conf' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xorg.conf is not installed

```

not really a good thing i guess...

---

### Post by Zorael on 2008-05-03
Pah, my bad, it's supposed to be **xserver-xorg**. :<
```
$ sudo dpkg-reconfigure xserver-xorg
```

---

### Post by savethewabbit on 2008-05-03
ok, so the configuration started and i got at this point:
> 
For the X server to handle the keyboard correctly, a keyboard model must  &#8593; 
 &#9474; be entered.  Available models depend on which XKB rule set is in use.     &#9646; 
 &#9474;                                                                           &#9618; 
 &#9474;  With the "xorg" rule set:                                                &#9618; 
 &#9474;  - pc101: traditional IBM PC/AT style keyboard with 101 keys, common in   &#9618; 
 &#9474;           the United States.  Has no "logo" or "menu" keys;               &#9618; 
 &#9474;  - pc104: similar to pc101 model, with additional keys, usually engraved  &#9618; 
 &#9474;           with a "logo" symbol and a "menu" symbol;                       &#9618; 
 &#9474;  - pc102: similar to pc101 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - pc105: similar to pc104 and often found in Europe. Includes a "< >"    &#9618; 
 &#9474; key;                                                                      &#9618; 
 &#9474;  - macintosh: Macintosh keyboards using the new input layer with Linux    &#9618; 
 &#9474;               keycodes;                              
- macintosh_old: Macintosh keyboards not using the new input layer.      &#9618; 
 &#9474;  With the "sun" rule set:                                                 &#9618; 
 &#9474;  - type4: Sun Type4 keyboards;                                            &#9618; 
 &#9474;  - type5: Sun Type5 keyboards.                                            &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; Laptop keyboards often do not have as many keys as standalone models;     &#9618; 
 &#9474; laptop users should select the keyboard model most closely approximated   &#9646; 
 &#9474; by the above.                                                             &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; Experienced users can use any model defined by the selected XKB rule      &#9618; 
 &#9474; set.  If the xkb-data package has been unpacked, see the   
/usr/share/X11/xkb/rules directory for available rule sets.               &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; Users of U.S. English keyboards should generally enter "pc104".  Users    &#9646; 
 &#9474; of most other keyboards should generally enter "pc105".  
               <Ok>     

do i have to do something now? or do i just close the terminal window? also, will it just work as i reboot or do i have to enable the thing somewhere? thanks!

---

### Post by Zorael on 2008-05-03
Well, that's a guide, right? You'll be asked some questions about your input devices, timezone etc, then it'll generate your new xorg.conf. After which, just reboot X with Ctrl+Alt+Backspace.

---

### Post by savethewabbit on 2008-05-03
yeah, even though whatever i type in doesn't work (of all the options they give). i'm sorry i'm such a noob... i just can't understand what to type there. like if i type "pc105" nothing happens, i press enter afterwards nothing happens... or perhaps that's not where i should type those things? i'm sorry to bother, it's just that even if i press enter or type ok or anything it won't even go to the next page so i'm a little at a loss.

---

### Post by Zorael on 2008-05-03
Okay. Try entering those commands in one of the tty terminals. Hit Ctrl+Alt+F1; you should end up in a textual interface. Login and do the command again.
```
$ sudo dpkg-reconfigure xserver-xorg
```
Should work.

To return to the graphical interface, do Alt+F7.

---

### Post by savethewabbit on 2008-05-03
ok... tried as you said. 
the key to move on with the steps was to push the exit key btw :) it let me enter my keyboard option so i finished the configuration.
however i got the error: 
```
MDSSUM: /etc/X11/xorg.conf No such file or directory
```

so i basically inverted the first code you gave me and replaced xorg.backup0805 with xorg.conf. redid the configuration, it went through even though it said i might be overwriting some configured options or something... ignored that and rebooted, it started correctly at the first run.
so i don't really know what i did, but it seems to be working :) thanks a lot for the help and the patience!!

---

