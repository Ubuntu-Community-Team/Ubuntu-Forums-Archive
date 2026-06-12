---
title: "LC_ALL locale issue"
date: 2024-03-25
forum: General Help
---

### Post by brazzmonkey on 2024-03-25
Hi there,
I've recently run into a LC_ALL locale issue on my 22.04 LTS.
I get:
```
$ locale
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE=fr_FR.UTF-8
LC_NUMERIC=gsw_FR.UTF-8
LC_TIME=en_GB.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=gsw_FR.UTF-8
LC_MESSAGES=POSIX
LC_PAPER=fr_FR.UTF-8
LC_NAME=fr_FR.UTF-8
LC_ADDRESS=fr_FR.UTF-8
LC_TELEPHONE=fr_FR.UTF-8
LC_MEASUREMENT=fr_FR.UTF-8
LC_IDENTIFICATION=fr_FR.UTF-8
LC_ALL=

```

Apart from the above error message, this LC_ALL issue causes problems with some programs (Hugin, for instance, won't work properly an displays "Cannot set locale to language "English (U.S.)" ).

Also I get:
```
$ sudo update-locale
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = "",
        LC_ADDRESS = "fr_FR.UTF-8",
        LC_NAME = "fr_FR.UTF-8",
        LC_MONETARY = "gsw_FR.UTF-8",
        LC_PAPER = "fr_FR.UTF-8",
        LC_IDENTIFICATION = "fr_FR.UTF-8",
        LC_TELEPHONE = "fr_FR.UTF-8",
        LC_MESSAGES = "POSIX",
        LC_MEASUREMENT = "fr_FR.UTF-8",
        LC_CTYPE = "fr_FR.UTF-8",
        LC_TIME = "en_GB.UTF-8",
        LC_NUMERIC = "gsw_FR.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").

```

As far as I know we're not supposed to set an LC_ALL value in /etc/default/locale, because it will override the other LC_** variables (I did so and ended with a system that's 100% American English, which is a no-go for me).

So what's wrong with my locale setup? How do I get rid of these LC_ALL issues?

Thanks ins advance for any guidance.

---

### Post by Xian on 2024-03-25
> **brazzmonkey said:**
> Hi there,
So what's wrong with my locale setup? How do I get rid of these LC_ALL issues?


Start here:

$ sudo dpkg-reconfigure locales

---

### Post by brazzmonkey on 2024-03-26
I tried that. It didn't help.
```
$ sudo dpkg-reconfigure locales
[sudo] password for sam: 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LC_ADDRESS = "fr_FR.UTF-8",
        LC_NAME = "fr_FR.UTF-8",
        LC_MONETARY = "gsw_FR.UTF-8",
        LC_PAPER = "fr_FR.UTF-8",
        LC_IDENTIFICATION = "fr_FR.UTF-8",
        LC_TELEPHONE = "fr_FR.UTF-8",
        LC_MESSAGES = "POSIX",
        LC_MEASUREMENT = "fr_FR.UTF-8",
        LC_CTYPE = "fr_FR.UTF-8",
        LC_TIME = "en_GB.UTF-8",
        LC_NUMERIC = "gsw_FR.UTF-8",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to a fallback locale ("en_US.UTF-8").
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales (this might take a while)...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.ISO-8859-1... done
  en_GB.ISO-8859-15... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IL.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.ISO-8859-1... done
  en_US.ISO-8859-15... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
  fr_BE.UTF-8... done
  fr_CA.UTF-8... done
  fr_CH.UTF-8... done
  fr_FR.ISO-8859-1... done
  fr_FR.UTF-8... done
  fr_FR.ISO-8859-15@euro... done
  fr_LU.UTF-8... done
Generation complete.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LC_TIME = "en_GB.UTF-8",
        LC_MONETARY = "gsw_FR.UTF-8",
        LC_CTYPE = "fr_FR.UTF-8",
        LC_ADDRESS = "fr_FR.UTF-8",
        LC_TELEPHONE = "fr_FR.UTF-8",
        LC_MESSAGES = "POSIX",
        LC_NAME = "fr_FR.UTF-8",
        LC_MEASUREMENT = "fr_FR.UTF-8",
        LC_IDENTIFICATION = "fr_FR.UTF-8",
        LC_NUMERIC = "gsw_FR.UTF-8",
        LC_PAPER = "fr_FR.UTF-8",
        LANG = "C"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en",
        LC_ALL = (unset),
        LC_TIME = "en_GB.UTF-8",
        LC_MONETARY = "gsw_FR.UTF-8",
        LC_CTYPE = "fr_FR.UTF-8",
        LC_ADDRESS = "fr_FR.UTF-8",
        LC_TELEPHONE = "fr_FR.UTF-8",
        LC_MESSAGES = "POSIX",
        LC_NAME = "fr_FR.UTF-8",
        LC_MEASUREMENT = "fr_FR.UTF-8",
        LC_IDENTIFICATION = "fr_FR.UTF-8",
        LC_NUMERIC = "gsw_FR.UTF-8",
        LC_PAPER = "fr_FR.UTF-8",
        LANG = "C"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
```

From the last lines I noticed LANG being changed from "en_US.UTF-8" to "C"? I don't know if this is relevant.

---

### Post by brazzmonkey on 2024-03-26
I don't make any progress, but I believe this is also related to LANG:
I tried to change LANG to fr_FR.UTF-8 in both /etc/default/locale and ~/.pam_environment. I logged out and even rebooted, and I still get the same messages with mentions to en_US.UTF-8.

So I suppose that:
- there is something forcing LANG to en_US.UTF-8, but I don't know what does that.
- en_US.UTF-8 is considered a fallback locale, but is unavailable according to the error messages, though it's installed and generated. This I don't understand either.

---

### Post by #&amp;thj^% on 2024-03-26
I'll always back-up first ie:
```
less /etc/locale.gen >locale.txt

```
That file will be in your home directory.
You can set locale manually using update-locale:
```

sudo update-locale LANG=fr_FR.UTF-8 UTF-8 LC_MESSAGES=POSIX
```

Read the man page for more information.

Alternatively, you can manually change your system's locale entries by modifying the file /etc/default/locale.

For example, on a German system, to prevent system messages from being translated, you may use:
```

LANG=de_DE.UTF-8
LC_MESSAGES=POSIX
```

Note: changes take effect only after a fresh login.
Good Luck

---

### Post by brazzmonkey on 2024-03-26
Thanks for trying to help.
Unfortunately, as stated in my previous post I already tried to change LANG manually but it didn't help...

---

### Post by #&amp;thj^% on 2024-03-26
Yes I see now you have multiple locales now, and is confusing your system.
There used to be a way to set it also in "/etc/environment" but I've never had to use it.

Also in your ".bashrc" i can add locales as these examples:
```
export LANGUAGE=en_US.UTF-8
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
export LC_CTYPE=en_US.UTF-8
```

---

### Post by brazzmonkey on 2024-03-26
Basically you ask me to set everything in american English, which I already tried.
As stated in my very first post, a simple ```
 export LC_ALL=en_US.UTF-8
``` overrides everything and doesn't produce any error thereafter.
Unfortunately 100% american English is not something I can live with.
I have been using mixed locales on this system for a while (more than 5 years), and suddenly something's wrong... I'm clueless.

---

### Post by #&amp;thj^% on 2024-03-26
> **brazzmonkey said:**
> Basically you ask me to set everything in american English, which I already tried.
As stated in my very first post, a simple ```
 export LC_ALL=en_US.UTF-8
``` overrides everything and doesn't produce any error thereafter.
Unfortunately 100% american English is not something I can live with.
I have been using mixed locales on this system for a while (more than 5 years), and suddenly something's wrong... I'm clueless.

LOL...Those were examples only, and you should change to your preferred Lang

---

### Post by #&amp;thj^% on 2024-03-26
Disregard the above post, and remove those suggestions in post #6
And add this to "/etc/environment" I just did this and it still works:
```
LANGUAGE=fr_FR.UTF-8
LC_ALL=fr_FR.UTF-8 

```
Proof:
```
locale
LANG=C.UTF-8
LANGUAGE=fr_FR.UTF-8
LC_CTYPE="C.UTF-8"
LC_NUMERIC="C.UTF-8"
LC_TIME="C.UTF-8"
LC_COLLATE="C.UTF-8"
LC_MONETARY="C.UTF-8"
LC_MESSAGES="C.UTF-8"
LC_PAPER="C.UTF-8"
LC_NAME="C.UTF-8"
LC_ADDRESS="C.UTF-8"
LC_TELEPHONE="C.UTF-8"
LC_MEASUREMENT="C.UTF-8"
LC_IDENTIFICATION="C.UTF-8"
LC_ALL=C.UTF-8

```
```
Jeu de paramètres régionaux actif par défaut*:                                    &#9474; 
  &#9474;                                                                                   &#9474; 
  &#9474;                                  Aucun           &#8593;                                &#9474; 
  &#9474;                                  C.UTF-8         &#9646;                                &#9474; 
  &#9474;                                  en_US.UTF-8     &#9618;                                &#9474; 
  &#9474;                                  fr_FR.UTF-8     &#9618;                                &#9474; 
  &#9474;                                  en_AG           &#9618;                                &#9474; 
  &#9474;                                  en_AU.UTF-8     &#9618;                                &#9474; 
  &#9474;                                  en_BW.UTF-8     &#9618;                                &#9474; 
  &#9474;                                  en_CA.UTF-8     &#8595;                                &#9474; 
  &#9474;                                                                                   &#9474; 
  &#9474;                                                                                   &#9474; 
  &#9474;                      <Ok>                          <Cancel>                       &#9474; 
  &#9474;                                                                       
```

---

### Post by brazzmonkey on 2024-03-26
Sorry if we misunderstood...
I'm used to have a computer in English (american), with metric system, euros currency, and swiss number formats.
I haven't had any issue so far... until last week.

Good news is that I eventually narrowed it down to some sort of conflict or incompatibility between system locales, and most likely KDE locales.
KDE provides many "exotic" locales, and using them with "classic" system locales now generates warnings and errors. I have no idea why.
In my case, the gsw_FR.UTF-8 entries were the culprit. As an workaround I now use de_LI.UTF-8. Hopefully this will get better with 24.04.

Thanks for trying to help me, much appreciated.

---

### Post by #&amp;thj^% on 2024-03-26
> **brazzmonkey said:**
> Hopefully this will get better with 24.04.

Thanks for trying to help me, much appreciated.
It dose get better:
```
locale
LANG=fr_FR.UTF-8
LANGUAGE=en
LC_CTYPE="fr_FR.UTF-8"
LC_NUMERIC="fr_FR.UTF-8"
LC_TIME="fr_FR.UTF-8"
LC_COLLATE="fr_FR.UTF-8"
LC_MONETARY="fr_FR.UTF-8"
LC_MESSAGES="fr_FR.UTF-8"
LC_PAPER="fr_FR.UTF-8"
LC_NAME="fr_FR.UTF-8"
LC_ADDRESS="fr_FR.UTF-8"
LC_TELEPHONE="fr_FR.UTF-8"
LC_MEASUREMENT="fr_FR.UTF-8"
LC_IDENTIFICATION="fr_FR.UTF-8"
LC_ALL=

```
```
PRETTY_NAME="Ubuntu Noble Numbat (development branch)"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04 (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

```

Sorry i could not be of more help to you. :)

---

