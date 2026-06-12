---
title: "Problems with accented vowels"
date: 2014-05-06
forum: General Help
---

### Post by marciano#1 on 2014-05-06
Hello,

Last year I installed on my wife's laptop a 2013 version of lubuntu.
Under configuration first language was Spanish and then English.
I added a top bar with some icons, one of them was the used language.
It always displayed "US" despite the real lang was "ES" or "SP" (I don't know if this icon should be used to change the language like other OS, no option but set a country flag, font size...)
She recently upgrade to 14.04 and the keyword worked sometimes. I fixed that changing kb input method from iBus to None.
At this time she is able to write Spanish chars like á ó and ñ BUT in Chromium Gmail.
Strangely the ñ or Ñ work fine but the accent key seems not, no way to write accented vowels.
Gmail has a menu with some Spanish options aside the configuration wheel.  
I tried changing to other options but it is the same thing.

Thanks for any help

---

### Post by bapoumba on 2014-05-06
If you right click on the icon, it brings up the Keyboard Layout Handler Settings. You can choose your keyboard variant there.

In Chromium, I have to **ibus exit** to be able to write characters.
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1307648)

---

### Post by marciano#1 on 2014-05-06
Thanks bapoumba for your reply
[ATTACH=CONFIG]252930[/ATTACH]
Both languages are installed, first Spanish, second and last English

$ ibus exit
"Cannot connect to ibus"

Remember I had to switch keyb input from iBus to None to get it work

---

### Post by bapoumba on 2014-05-07
My first button says "Add" which I believe is yours saying "Anadir". The Spanish keyboard layout is within the S letter range, and not the E, do not ask me why :)
You can click on the little arrow to have more options.

---

### Post by marciano#1 on 2014-05-07
Yes, Añadir means Add but  all this this section of the window was greyed, unable to make changes until... next snapshot.
Anyway "es" language is already displayed in my previous attachment while "US" is displayed in the top bar.
Now I've unchecked 'Keep system distribution' and the left side is enabled, so I added "en-us".
Now "ES" is displayed in top bar.
But the problem still remains.  
This is strange, on some programs accented vowels are displayed (accent key works) and in others they do not.
I remember when I installed the previous OS last year (clean install) setup guides me to set the correct keyboard setting.
Is it possible that this setting was change during recent upgrade? If so, how can I correct this?
In this snapshot I see Keyboard model pc105. I don't know if it would be useful to change that.
[ATTACH=CONFIG]252957[/ATTACH]

---

### Post by bapoumba on 2014-05-07
> **marciano#1 said:**
> 
This is strange, on some programs accented vowels are displayed (accent key works) and in others they do not.


Now that can be the font you are using.

---

### Post by marciano#1 on 2014-05-07
Common fonts are used like Sans-serif, Verdana all without problems with accented vowels.
I insist, can this be a keyb config issue?
Merci

---

### Post by bapoumba on 2014-05-07
Yes, that can be. All I can find around (because I've already used all I had to go through to set up my own French keyboard that was stuck on a US layout) are older threads that invoke lxkeymap. It's not installed by default here, and not sure how it could fuss around with other config files. I'll have a deeper look.

I tried changing my own French layout for one with no dead keys and see what it would do, but my session froze and I had to reboot, nothing would allow me back either on a working desktop or to log back in again.

---

### Post by bapoumba on 2014-05-07
I have been looking around and crashed my session several times trying out things :)

Here are some links that may help you, although all I did to set up the compose key failed and completely froze my desktop. Had to reboot from one of the virtual terminals as restarting LightDM brought me to a very funny desktop with funny and unusable panel.

[http://rlog.rgtti.com/2014/05/01/how-to-modify-a-keyboard-layout-in-linux/](http://rlog.rgtti.com/2014/05/01/how-to-modify-a-keyboard-layout-in-linux/)
[http://ubuntuforums.org/showthread.php?t=2207779](http://ubuntuforums.org/showthread.php?t=2207779) < this one crashed me
[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey) < this one too

I used to use the compose key, had not set it yet, and wanted to have it back anyway.

---

### Post by marciano#1 on 2014-05-08
Thanks for your time, I appreciate this.

The file to be edited does not exist in my system [http://rlog.rgtti.com/2014/05/01/how-to-modify-a-keyboard-layout-in-linux/](http://rlog.rgtti.com/2014/05/01/how-to-modify-a-keyboard-layout-in-linux/)

I was thinking about the problem happens in some apps. LibreOffice display well accented vowles.

So I installed Firefox (problems with Java here, I'll have to dig on it) and voilà! Facebook and gmail accept all Spanish chars.

The problem is with Chromium and this lubuntu upgrade 14.04.

---

### Post by bapoumba on 2014-05-08
OK, sorry I was on two things at the same time yesterday and forgot to add that the file was in /usr/share/X11/xkb/symbols for me. Had a look at my own stuff and got distracted by the freezes :)

I do have several problems with Chromium too, the most important one being in the bug report I linked to previously.

So I guess this is a temp fix and workaround for you, cheers !

---

