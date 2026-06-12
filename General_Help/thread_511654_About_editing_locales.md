---
title: "About editing locales"
date: 2007-07-28
forum: General Help
---

### Post by satimis on 2007-07-28
Hi folks,

Ubuntu 7.04 desktop


On running;

$ sudo dpkg-reconfigure locales
Password:```

Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done

```

However on;

$ cat /etc/default/locale```

LANG="en_HK.UTF-8"

```

Only one line there.  What about the rest?


According to;
How to add locales to Ubuntu the command line way
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_locales_to_Ubuntu_the_command_line_way](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_locales_to_Ubuntu_the_command_line_way)

Ran
$ sudo su -

e.g.
# cat /usr/share/i18n/SUPPORTED | grep "en\|cn" > /var/lib/locales/supported.d/local
# dpkg-reconfigure locales```

Generating locales...
  ca_ES.UTF-8@valencia... up-to-date
  ca_ES.ISO-8859-15@valencia... up-to-date
  en_AU.ISO-8859-1... up-to-date
  en_AU.UTF-8... up-to-date
  en_BW.ISO-8859-1... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.ISO-8859-1... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.ISO-8859-1... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.ISO-8859-1... up-to-date
  en_GB.ISO-8859-15... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.ISO-8859-1... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.ISO-8859-15@euro... up-to-date
  en_IE.ISO-8859-1... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.ISO-8859-1... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.ISO-8859-1... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.ISO-8859-1... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.ISO-8859-1... up-to-date
  en_US.ISO-8859-15... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.ISO-8859-1... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.ISO-8859-1... up-to-date
  en_ZW.UTF-8... up-to-date

```

e.g.
To add "  en_GB.UTF-8"

# update-locale LANG=en_GB.UTF-8

But on
$ man update-locale```

EXAMPLE
       The command
               update-locale LANG=en_CA.UTF-8 LANGUAGE
       sets LANG to en_CA.UTF-8 and removes definitions for LANGUAGE.

```
What does it mean "...removes definitions for LANGUAGE"?


If I want to remove a locale on /etc/default/locale with command line, what it will be?

TIA


B.R.
satimis

---

