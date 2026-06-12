---
title: "postgresql not working"
date: 2007-03-30
forum: General Help
---

### Post by Weaseal on 2007-03-30
Hi all,
I have installed postgresql-server-dev and enabled PostgreSQL server in the Services menu.  However, I find no server running on my system, and "ps ax | grep sql" returns nothing.  Any ideas?

---

### Post by acormack on 2007-03-31
Check if running using

sudo /etc/init.d/postgresql status

then start with

sudo /etc/init.d/postgresql start

---

### Post by Weaseal on 2007-04-02
I ran your start command:```
ecorazeni@c8:~$ sudo /etc/init.d/postgresql-8.1 start
 * Starting PostgreSQL 8.1 database server  * perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Error: The server must be started under the locale en_US.UTF-8 which does not exist any more.
```Not sure what to do to resolve this...

---

### Post by acormack on 2007-04-02
This is more of a question for postgres list than this one.

My guess would be that you have installed just the regional settings for four own region en_GB and that postgress is starting with a different setting en_US in the /etc/init.d/postgresql file

I can't help as I have only ever run MySql.

You could maybe  look here for help

  [http://www.oryx.com/ams/postgresql.html](http://www.oryx.com/ams/postgresql.html)

---

### Post by nikhilk on 2007-04-02
> **Weaseal said:**
> Not sure what to do to resolve this...
Run these commands and then try starting postgres again
```
sudo locale-gen
sudo dpkg-reconfigure locales
```

---

### Post by Weaseal on 2007-04-04
```
$ sudo locale-gen
Password:
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  ro_RO.UTF-8... up-to-date
Generation complete.
ecorazeni@c8:~$ sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... up-to-date
  en_BW.UTF-8... up-to-date
  en_CA.UTF-8... up-to-date
  en_DK.UTF-8... up-to-date
  en_GB.UTF-8... up-to-date
  en_HK.UTF-8... up-to-date
  en_IE.UTF-8... up-to-date
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... up-to-date
  en_PH.UTF-8... up-to-date
  en_SG.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
  ro_RO.UTF-8... up-to-date
Generation complete.
Current default timezone: 'Europe/Chisinau'.
Local time is now:      Wed Apr  4 11:23:14 EEST 2007.
Universal Time is now:  Wed Apr  4 08:23:14 UTC 2007.
Run 'tzconfig' if you wish to change it.
ecorazeni@c8:~$ sudo /etc/init.d/postgresql-8.1 start
 * Starting PostgreSQL 8.1 database server  * perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Error: The server must be started under the locale en_US.UTF-8 which does not exist any more.
                                                                         [fail]
```So...what now?

---

### Post by exhuma.twn on 2007-08-04
I am experiencing the **exact** same error. Please help.
After a week of trying to get it to work I am completely lost.

---

### Post by Weaseal on 2007-08-05
Never got a reply to this one; I started from scratch with 7.04 and the problem never returned.

---

### Post by exhuma.twn on 2007-08-10
It's a shame. Really.
But as this is a server machine I might end up installing a different distro alltogether, now that I have to rei-install. I find ubuntu to be a bit bloated for a server-box. Even if you pick the server-installation.

But it installs lightning fast ;)

---

### Post by exhuma.twn on 2007-08-11
I *finally* got it working. And it was easier that I thought.

I simply **purged** the locales bu issuing
```
# aptitude purge locales
```

This seemed to have automatically reinstalled the locales. But to make sure:
```
# aptitude reinstall locales
```

maybe just re-installing locales is enough. But this is what I did.

After that "/dev/null" was not writable by everyone (what gives?!?!?). Well easy to solve:
```
# chmod a+w /dev/null
```

done.

hth

---

