---
title: "[Kubuntu] Chrome/Chromium displays in English despite system set to other"
date: 2014-05-22
forum: General Help
---

### Post by Skyflier on 2014-05-22
Hi there,

I'm having an issue with Google Chrome and Chromium in Kubuntu 14.04. I use my system in Portuguese language and all KDE apps and menus display right from the start. But Google Chrome is the only application that insists to display in English. I tried changing system language from pt_PT to en_US and ended up with mixed languages which I eventually fixed but Chrome retains its menus in English.

What is the problem here? How does Chrome or Chromium check which language it should display in?

---

### Post by startas on 2014-05-22
open chrome -> Settings -> show adanced settings -> language and input settings -> select language and press "display google chrome in this language".

---

### Post by slickymaster on 2014-05-22
If you launch chrome and open "**chrome://settings**" and click the "**Show advanced settings...**" link at the bottom of the page and then click on '**Language and Input settings**' button, you'll be presented with the 'Languages' dialog, where add languages or drag to order them based on your preference.

Also, see this [https://support.google.com/chrome/topic/3434349?rd=1](https://support.google.com/chrome/topic/3434349?rd=1)

---

### Post by Skyflier on 2014-05-22
I already checked that menu and it seems to be set correctly but display language is still English

[ATTACH=CONFIG]253361[/ATTACH]

---

### Post by slickymaster on 2014-05-22
That's odd indeed. See if [http://www.google.com/support/chrome/bin/answer.py?answer=95416](http://www.google.com/support/chrome/bin/answer.py?answer=95416) can somehow help you.

---

### Post by Skyflier on 2014-05-22
That page informs that in Linux you should verify the system's language support as Chromium sets his language from that.

Here's the output of these two commands, if they can help:

```
$ locale
LANG=pt_PT.UTF-8
LANGUAGE=pt:en
LC_CTYPE="pt_PT.UTF-8"
LC_NUMERIC=pt_PT.UTF-8
LC_TIME=pt_PT.UTF-8
LC_COLLATE="pt_PT.UTF-8"
LC_MONETARY=pt_PT.UTF-8
LC_MESSAGES="pt_PT.UTF-8"
LC_PAPER=pt_PT.UTF-8
LC_NAME=pt_PT.UTF-8
LC_ADDRESS=pt_PT.UTF-8
LC_TELEPHONE=pt_PT.UTF-8
LC_MEASUREMENT=pt_PT.UTF-8
LC_IDENTIFICATION=pt_PT.UTF-8
LC_ALL=

```
```
 
$ locale -a
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
pt_BR.utf8
pt_PT.utf8

```

---

### Post by startas on 2014-05-22
Once again, you are wrong. As you can see (i hope so), you have only "[COLOR=#333333][FONT=Segoe UI]**This language is used for spell checking**" when you select your language, but you also must have "[/FONT][/COLOR]**[COLOR=#333333][FONT=Segoe UI]Google Chrome is displayed in this language[/FONT][/COLOR]**[COLOR=#333333][FONT=Segoe UI]".[/FONT][/COLOR]

---

### Post by Skyflier on 2014-05-22
> **startas said:**
> Once again, you are wrong. As you can see (i hope so), you have only "[COLOR=#333333][FONT=Segoe UI]**This language is used for spell checking**" when you select your language, but you also must have "[/FONT][/COLOR]**[COLOR=#333333][FONT=Segoe UI]Google Chrome is displayed in this language[/FONT][/COLOR]**[COLOR=#333333][FONT=Segoe UI]".[/FONT][/COLOR]
But I don't see any option to set that, what you see is that dialog box in the screenshot.

Btw, this is Chromium that I am using right now.

---

### Post by startas on 2014-05-22
Well, when you download chrome, you can choose your language, and then the whole browser is in that language, so [http://www.google.com/intl/pt-PT/chrome/browser/](http://www.google.com/intl/pt-PT/chrome/browser/) would be in your language, but this is chrome, not chromium. You should check if you have "[COLOR=#333333][FONT=Ubuntu]chromium-browser-l10n[/FONT][/COLOR]" installed, it's languages package for chromium, i dont know if its installed by default in ubuntu.

---

### Post by Skyflier on 2014-05-22
> **startas said:**
> Well, when you download chrome, you can choose your language, and then the whole browser is in that language, so [http://www.google.com/intl/pt-PT/chrome/browser/](http://www.google.com/intl/pt-PT/chrome/browser/) would be in your language, but this is chrome, not chromium. You should check if you have "[COLOR=#333333][FONT=Ubuntu]chromium-browser-l10n[/FONT][/COLOR]" installed, it's languages package for chromium, i dont know if its installed by default in ubuntu.
It is not like that. Google Chrome comes in an universal multilingual package, it doense't matter from which local website you download, it will display in the system's language. 
I have that "chromium-browser-l10n" package installed already. This is something related to the system or KDE itselft that is telling Chromium to show the interface in English. I just don't know what it is.

---

### Post by Skyflier on 2014-05-24
Problem solved!

This is actually a bug in KDE, don't know if specific to Kubuntu or present in other distros too.

There is a line in the "setlocale.sh" file that has this:

```
LANGUAGE=pt:en
```

And after some investigation I changed it to this:

```
LANGUAGE=pt_PT:en
```

And voila! Google Chrome now shows up in Portuguese (Portugal) and all other apps too. 

So in the end, the bug is that KDE generates a wrong "setlocale.sh" file for the pt_PT locale, pretending it is just "pt" and maybe this applies for other locales as well. Maybe it should be reported in lauchpad with the fix for other users who find this issue in Kubuntu.

---

