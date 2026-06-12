---
title: "How can I permanently remove or delete the zh_CN.UTF-8 Chinese locale?"
date: 2014-10-27
forum: General Help
---

### Post by mckayc on 2014-10-27
Many of the programs on my computer show up half in English and half in Chinese because of the zh_CN.UTF-8 locale. This is driving me nuts and any help to get zh_CN.UTF-8 locale removed from my computer would be greatly appreciated.

From searching various forums, I have found the way to remove it (supposedly) is by running the command:
```
sudo localedef --delete-from-archive zh_CN.utf8
```

After I do that, I run the command
```
sudo locale-gen
```
After I do this, it spits out the following in the command line:
```
Generating locales...
  en_AG.UTF-8... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NG.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZM.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  zh_CN.UTF-8... done
Generation complete.
```

All of the locales except the last one (Chinese) say "up-to-date," but it pauses for a bit on zh_CN.UTF-8. It seems to be installing it again right after I removed it. Why on earth is it doing this?

Some more background:
[LIST]
[*]I am living in China and have my timezone set to Shanghai.
[*]All locale settings are set for US English.
[*]I have gone into Synaptic (apt-get) and removed anything Chinese that I can find.
[*]I have gone into usr/share/locale and manually deleted every Chinese locale I could find, but they always seem to reappear after I install a program on my computer.
[/LIST]

Thanks in advance. I will love your forever if you can help me with this (unless you don't want any of my love, then I will just love ice cream forever).

---

### Post by bapoumba on 2014-10-27
What do you have in Language Support ? Not sure where the menu currently is as I am running lubuntu.

---

### Post by mckayc on 2014-10-27
> **bapoumba said:**
> What do you have in Language Support ? Not sure where the menu currently is as I am running lubuntu.

I am using Kubuntu. To access the language settings I go to System Settings/Locale/Languages  In preferred language I have it set to "American English." There is a long list of available languages, but these cannot be deleted. For country I have it set to "United States of America."

If there is an additional  way to set a language aside from this, I am unaware of how to do it in KDE.

---

### Post by bapoumba on 2014-10-28
Please see if you have the option to remove languages as I do by clicking on install/remove languages if you have that option. My system language is in English, locales in French.

---

