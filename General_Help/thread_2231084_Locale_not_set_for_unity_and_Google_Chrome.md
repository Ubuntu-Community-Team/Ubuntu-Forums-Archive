---
title: "Locale not set for unity and Google Chrome"
date: 2014-06-23
forum: General Help
---

### Post by d-lhoest-y on 2014-06-23
Hello, 

On Ubuntu 14.04 using a French Belgian Keyboard with my locale being set as UTF-8 fr_BE, accents or special keys are not recognised either in Chrome or in Unity but well in all other programmes (Terminal, Gedit, ...).

For instance, hitting the keys from 1 to 0 should give & é " ' ( § è ! ç à
In Chrome it gives : &2"'(67!90
In Unity (Dash) I have & " ' ( !

I tried reconfiguring locales, my system is configured with the French Belgian Keyboard, I tried deleting the configuration files, cache of IBus and rebooted to no avail.
```
[COLOR=#333333][FONT=Menlo]rm -rf .cache/ibus .config/ibus .config/dconf[/FONT][/COLOR]
```

For Google Chrome, the only usefull solution I found was to start the browser in a terminal with ```
LANG=fr_BE.utf8 google-chrome



``` but I couldn't get it working by changing the Google Chrome unity launcher.

Any help would greatly be appreciated!

---

### Post by d-lhoest-y on 2014-06-24
[COLOR=#000000]Some results : 

```
sudo dpkg-reconfigure locales[/COLOR][COLOR=#000000]Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
  fr_BE.UTF-8... up-to-date
  fr_CA.UTF-8... up-to-date
  fr_CH.UTF-8... up-to-date
  fr_FR.UTF-8... up-to-date [/COLOR][COLOR=#000000]  fr_LU.UTF-8... up-to-date
```

```
[/COLOR][COLOR=#000000][FONT=Consolas]$ locale[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LANG=en_IN[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LANGUAGE=en_IN:en[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_CTYPE="en_IN"[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_NUMERIC=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_TIME=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_COLLATE="en_IN"[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_MONETARY=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_MESSAGES="en_IN"[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_PAPER=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_NAME=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_ADDRESS=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_TELEPHONE=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_MEASUREMENT=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_IDENTIFICATION=fr_BE.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=Consolas]LC_ALL=[/FONT][/COLOR][COLOR=#000000]
```


[/COLOR]

---

### Post by d-lhoest-y on 2014-06-24
Problem solved with the following command :

```
sudo dpkg-reconfigure keyboard-configuration 
```

---

