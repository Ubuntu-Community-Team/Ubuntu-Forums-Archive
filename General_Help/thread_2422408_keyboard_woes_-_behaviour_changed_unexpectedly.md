---
title: "keyboard woes - behaviour changed unexpectedly"
date: 2019-07-07
forum: General Help
---

### Post by engine on 2019-07-07
Main problem: ctrl + shift + u has stopped working for me

Up until a week or so back, I was happily using ctrl + shift + u and four-digit codes to enter unicode characters ... now this has stopped working :-{

language settings tab shows
[INDENT]language: English, UK, UTF-8 -- which is what I want
region: German, Belgium, UTF-8 -- but I live in Flanders, not in German-speaking Belgium!
system locale: language English UK, region English UK -- why a different region?[/INDENT]

Also, the comma (bottom right on the numeric keypad) has started entering a comma instead of a full stop: this is not what I want, and how how it used to be!

keyboard preferences, layouts is still Belgian, generic 105-key

Simple advice on what to correct will be appreciated! Thanks in advance.

---

### Post by engine on 2019-08-05
People who know more than I do suggested I should check locale ... I did.
**result**
```
LANG=en_GB.UTF-8
LANGUAGE=
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC=en_GB.UTF-8
LC_TIME=en_GB.UTF-8
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY=en_GB.UTF-8
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER=en_GB.UTF-8
LC_NAME=en_GB.UTF-8
LC_ADDRESS=en_GB.UTF-8
LC_TELEPHONE=en_GB.UTF-8
LC_MEASUREMENT=en_GB.UTF-8
LC_IDENTIFICATION=en_GB.UTF-8
LC_ALL=
```

Aha - no value for LANGUAGE! I'll try
```
sudo update-locale LANG=LANG=en_GB.UTF-8 LANGUAGE
```

**response from system**
```
*** update-locale: Error: invalid locale settings:  LC_NUMERIC=en_GB.UTF-8 LC_ADDRESS=en_GB.UTF-8 LC_PAPER=en_GB.UTF-8 LANG=LANG=en_GB.UTF-8 LC_MONETARY=en_GB.UTF-8 LC_TIME=en_GB.UTF-8 LC_MEASUREMENT=en_GB.UTF-8 LC_NAME=en_GB.UTF-8 LC_TELEPHONE=en_GB.UTF-8 LC_IDENTIFICATION=en_GB.UTF-8
```

So - what's invalid? how do I correct it? All hints and tips welcome.

---

### Post by Bashing-om on 2019-08-05
engine; Hello -

syntax ?
"LC_NUMERIC=en_GB.UTF-8 LC"
try as :
```

lang=en-GB

```
replacing the underscore with a hyphen.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by engine on 2019-08-06
Well, you indirectly prompted me to check ```
locale -a
``` again: and there, I notice, the option is labelled not ```
en_GB.UTF-8
``` but ```
en_GB.utf8
``` ... So I tried ```
sudo update-locale LANGUAGE=en_GB.utf8
``` and guess what: no error message!

But, running locale immediately afterwards still returns
```
LANG=en_GB.UTF-8
LANGUAGE=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC=en_GB.UTF-8
LC_TIME=en_GB.UTF-8
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY=en_GB.UTF-8
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER=en_GB.UTF-8
LC_NAME=en_GB.UTF-8
LC_ADDRESS=en_GB.UTF-8
LC_TELEPHONE=en_GB.UTF-8
LC_MEASUREMENT=en_GB.UTF-8
LC_IDENTIFICATION=en_GB.UTF-8
LC_ALL=

```
as though I had done nothing at all. Baffled and unimpressed ... but thanks for answering, anyway.

---

### Post by Bashing-om on 2019-08-06
engine; Hummm

My results:
```

sysop@x1804mini:~$ locale -a
C
C.UTF-8
en_AG
en_AG.utf8
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IL
en_IL.utf8
en_IN
en_IN.utf8
en_NG
en_NG.utf8
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZM
en_ZM.utf8
en_ZW.utf8
POSIX
sysop@x1804mini:~$ 

sysop@x1804mini:~$ locale
LANG=en_US.UTF-8
LANGUAGE=en_US
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
sysop@x1804mini:~$

```

Maybe of value:
```

sudo dpkg-reconfigure keyboard-configuration

```
to reset the keyboard.

 The keycodes are in the file "/usr/share/X11/xkb/keycodes/evdev"  Maybe switch the keycodes with the 'xev' tool as the guide.

to see all the current key mapping:
```

xmodmap -pke

```


With resetting the keyboard, does unicode now work ?

[INDENT]try'n to help
[/INDENT]

---

### Post by engine on 2019-08-07
And Hm again, unfortunately ... I tried ```
sudo dpkg-reconfigure keyboard-configuration
``` - now there's an interface that took me back a few years! - and watched patiently. After a while, it threw up the message ```
Warning: No support for locale: en_GB.utf8
``` -- so much for the output (reported earlier) from ```
locale -a
```

Strikes me that something is fundamentally out of order, if a command that refers to a config file doesn't recognise the values the system has included in that config file.

---

### Post by #&amp;thj^% on 2019-08-07
I've been watching this since yesterday, and suddenly dawned on me.
I've fixed this with:
```
sudo locale-gen --purge --no-archive
```
This command purges (deletes) the archive file and replaces it with the .utf8 files.
See if this helps.

---

### Post by engine on 2019-08-26
<sigh> Thanks for all the advice, but I'll have to add ```
sudo locale-gen --purge --no-archive
``` to the list of suggestions that haven't resolved the problem :-{

---

### Post by tea for one on 2019-08-26
Are you able to boot up a live session to see if **ctrl + shift + u** still misbehave?

---

