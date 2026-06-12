---
title: "I think my locale is messed up."
date: 2004-12-02
forum: General Help
---

### Post by snipes420 on 2004-12-02
when I try to install or upgrade my packages via apt-get upgrade all the packages say this:
[I]
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
LANGUAGE = "en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

[/I]
I think the problem is that I accidently set up the wrong locale or something.
My physical location is english speaking Canada and im using a us keyboard.
the GB in there looks like its out of place. any ideas?

Edit: and when I try to use "sudo dpkg-reconfigure locales" it outputs this:
[I]
snipes@nForce2:~ $ sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure: locales is broken or not fully installed
snipes@nForce2:~ $
[/I]

---

### Post by snipes420 on 2004-12-03
never mind. did a reinstall anyway. decided to free my machine once and for all. I deleted my windows partitions as well.

---

### Post by luiska on 2004-12-03
i have exactly the same problem, any ideas?

---

### Post by franky on 2004-12-10
[QUOTE=luiska]i have exactly the same problem, any ideas?[/QUOTE]
 I have the same problem too. I have a canadian-french keyboard, but I have installed ubuntu in english and my installation is the latest Warty. I am relatively new to the linux world and I would really appreciate some guidance regarding those language issues... Especially since they block me from using apt-get!
Where can we set those locales, and how must they be set to indicate we just want plain english?
I doubt a reinstall is the only solution and I'd like to understand what's going on.

Thank you in advance

---

### Post by cscc_leth on 2004-12-26
I had the same problem, but through some lucky guessing, I seem to have something that works.  I'm a relative linux newbie myself, but this worked for me.

I will denote commands typed at a command prompt by $

$ sudo gedit /etc/locale.gen

I changed this file to match that found here: [http://igor.tamarapatino.org/escritos/conf/ss250n/files/locale.gen](http://igor.tamarapatino.org/escritos/conf/ss250n/files/locale.gen) but only included those locales that I needed (the en_US and en_GB ones).  Save and exit.

$ sudo locale-gen

This generates the locales as you've specified in your newly adjusted file.

$ sudo gedit /etc/environment

I changed this file by adding the following to the beginning (after LANGUAGE="en_GB:en_US:en")

LANG=en_US
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US"
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=en_US


In other words, I forced it to use en_US for everything.  Save and exit. Then, I logged out and logged back in.  Everything seems to now work fine.  In order to clean things up, I ran

$ sudo dpkg-reconfigure locales

and

$ sudo dpkg-reconfigure localeconf

Finally, I removed the manual changes I made to /etc/environment by doing
$ sudo gedit /etc/environment

and removing the lines I had added before.

Everything seems to work brilliantly for me... since it seems that locale setting issues are relatively common, I hope this work around works for others (and that I didn't just get lucky!)

---

### Post by kasperbs on 2007-09-29
> I hope this work around works for others (and that I didn't just get lucky!)
Sorry to say it pal, but you did just get lucky.

I have been trying out your trick here and it doesn't work at all. I keep getting the locale at UTF-8

But thanks anyway for sharing

---

### Post by ntom-taylor on 2007-10-27
Yes, very lucky, still just listing all the utf-8 ones for me aswell, please help :(

---

