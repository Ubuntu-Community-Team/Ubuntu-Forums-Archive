---
title: "Malformed man pages and locale setting"
date: 2007-11-21
forum: General Help
---

### Post by sonicbuddha on 2007-11-21
I've had some difficulty with the settings for the formatting of the man pages in Ubuntu 7.10.  With the default locale setting of en_US.UTF-8 apostrophe's and other punctuation are malformed: ```
man is the systemâ€™s manual pager
```
If I change the locale setting to "C" or "Posix", the punctuation properly displays but some pages choke, like the samba man pages:
```

Manual page smb.conf(5) line 1/tmp/zmanjzv6Yw:3613: warning: numeric expression expected (got `a')
/tmp/zmanjzv6Yw:3650: warning: numeric expression expected (got `m')
```
Oh, I've tried various pagers via update-alternatives - its definitely an unicode/locale/lang issue.

Any help?

---

### Post by bingoUV on 2007-11-22
2 suggestions :

1. Use pinfo instead of man. Colourful, navigatable and good rendering.
2. For me, this works
```

export LANG=en_US

```

---

### Post by sonicbuddha on 2007-11-22
Thanks for the suggestion, although it seems "en_US" is not an acceptable value for locale (or LANG, which is set from the locale).  If I set my locale to "en_US" my man pages are fixed but LANGUAGE and LC_ALL are then unset, as per the error messages when installing pinfo:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
```

A moment of more investigation and I've found this only occurs when ssh-ing into the machine; local logins do not suffer from this encoding problem with man pages.  This is a server install and I rarely log in at the console.  ;)

---

### Post by sonicbuddha on 2007-11-22
AH HA!  Ok, it was the ssh element that gave me something new to look at.  A little searching found this thread and this article:

[http://ubuntuforums.org/showthread.php?t=545176&highlight=locale+ssh](http://ubuntuforums.org/showthread.php?t=545176&highlight=locale+ssh)
[http://jean-christophe.dubacq.fr/index.php?post/2007/05/09/Openssh-and-the-transmission-of-the-locale-setting](http://jean-christophe.dubacq.fr/index.php?post/2007/05/09/Openssh-and-the-transmission-of-the-locale-setting)

If I can boil it down, there is an issue with sshd utilizing pam to set the locale settings, specifically transmitting locale settings from the ssh client.  The author of the article offers a patch to sshd or you can do what the thread suggests and just comment out "UsePam yes" from the sshd_config file.  Currently I've opted for the latter over patching and recompiling sshd although I'm concerned about what security I may be compromising.

---

