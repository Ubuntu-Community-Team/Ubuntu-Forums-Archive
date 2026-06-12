---
title: "changing Xorg settings"
date: 2007-10-21
forum: General Help
---

### Post by Angelbeast on 2007-10-21
Okay i'm a little nervous about messing with system config files. Can someone tell me the easiest, most idiot proof way to change the xcorg settings so that my screen stops going blank every ten minutes?Thanks in advance...

---

### Post by Angelbeast on 2007-10-21
Someone? Purdy please? :-)

---

### Post by Angelbeast on 2007-10-21
*bunpety bump bump*  :-)

---

### Post by Angelbeast on 2007-10-22
c'mon man.. just want a little help from the HELP forum *LOL* ... 

seriously...i'm afraid of messing something up and i've seen a few ways and i just want to know the easiest, safest way...

---

### Post by Nunu on 2007-10-22
Sorry for getting your hopes up man. i have no idea how to change what you want to change all i can say is backup... what ever you change have a backup ready. but cant you change your display power setting in the through the desktop settings window??

---

### Post by Angelbeast on 2007-10-22
> **Nunu said:**
> Sorry for getting your hopes up man. i have no idea how to change what you want to change all i can say is backup... what ever you change have a backup ready. but cant you change your display power setting in the through the desktop settings window??

well from what other posts i've found  the xcorg keeps it's own set of setings and it seems to over ride the power management...and even the screen saver...the way it is now my screen goes blnk every ten minutes if i'm watching a video haha

---

### Post by Nunu on 2007-10-22
That sucks some... does the screen just go blank or does it go into standby mode (amber power LED)

---

### Post by Angelbeast on 2007-10-22
> **Nunu said:**
> That sucks some... does the screen just go blank or does it go into standby mode (amber power LED)

it just goes black...not really into standby proper

---

### Post by Nunu on 2007-10-22
So it's more of a screen saver then power managment then? Still find it quite wierd that the XORG overites your personal settings. 

Sorry i can't be of more help though

---

### Post by rsambuca on 2007-10-22
Did you try changing the settings in your "System -> Preferences -> Screensaver" section.  You can also enter the power management section from there as well.

---

### Post by Angelbeast on 2007-10-22
> **Nunu said:**
> So it's more of a screen saver then power managment then? Still find it quite wierd that the XORG overites your personal settings. 

Sorry i can't be of more help though

nooo don't be sorry man...at least you took time to say something *LOL* ... 

i dunno...i must have been black listed or something haha

---

### Post by Nunu on 2007-10-22
> **rsambuca said:**
> Did you try changing the settings in your "System -> Preferences -> Screensaver" section.  You can also enter the power management section from there as well.

It must be some form of conspiracy going :)  any way i tried what rsambuca said and compared the the XORG before and after the changes and it definitely went through on my side. have you had a go with it on your system? i would be interested to see if your machine allows the changes or not.

---

### Post by Rumpty on 2007-10-22
I don't think anything in xorg.conf will make the screen go blank after 10 minutes.

Try the screensaver <system-prefs-screensaver> setting, and move the slider for "regard the computer as idle after..." to the right to alter the setting to, say, 30 mins. See if that makes any difference.

---

### Post by Angelbeast on 2007-10-22
my screensaver never even gets a chane to come on

---

### Post by Nunu on 2007-10-22
In South Africa we have a wonderful saying that will explain issues like this. 

"Eish" meaning  "What the ...."

---

### Post by jocko on 2007-10-22
I guess you run Xgl with DISPLAY=:1?
It seems that xorg is set to go into blank mode after 10 minutes if no program tells it otherwise, and gnome-power-preferences only affects the display it is being run in (:1).

To get rid of this, add these lines to your /etc/X11/xorg.conf:
```
Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection

```

---

### Post by Angelbeast on 2007-10-22
> **jocko said:**
> I guess you run Xgl with DISPLAY=:1?
It seems that xorg is set to go into blank mode after 10 minutes if no program tells it otherwise, and gnome-power-preferences only affects the display it is being run in (:1).

To get rid of this, add these lines to your /etc/X11/xorg.conf:
```
Section "ServerFlags"
    Option        "blank time" "0"
    Option        "standby time" "0"
    Option        "suspend time" "0"
    Option        "off time" "0"
EndSection

```

Thank you thnk you thank you!

now doi need to add these lines in a certain place or just anywhere?

---

### Post by jocko on 2007-10-22
> **Angelbeast said:**
> Thank you thnk you thank you!

now doi need to add these lines in a certain place or just anywhere?

If you already have a section named "ServerFlags", just add the lines starting with "Option" to that section, otherwise add the entire section anywhere.

---

### Post by Angelbeast on 2007-10-22
> **jocko said:**
> If you already have a section named "ServerFlags", just add the lines starting with "Option" to that section, otherwise add the entire section anywhere.

okay i changed the file...thanks for your help...  :-)

---

### Post by Angelbeast on 2007-10-22
> **jocko said:**
> If you already have a section named "ServerFlags", just add the lines starting with "Option" to that section, otherwise add the entire section anywhere.

looksl ike it didn't work...do i need to restart for the changes to take effect?

---

### Post by jocko on 2007-10-22
> **Angelbeast said:**
> looksl ike it didn't work...do i need to restart for the changes to take effect?

You'll have to restart xorg (Ctrl+Alt+Backspace).

---

