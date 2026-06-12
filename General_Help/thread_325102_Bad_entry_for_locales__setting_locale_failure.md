---
title: "Bad entry for locales / setting locale failure"
date: 2006-12-25
forum: General Help
---

### Post by xsism on 2006-12-25
I believe after i installed LIVeS and LMMS, one of the dependent packages reconfigured something.

My suspect is libc6. My main issue is that VLC began telling me:
```
Cannot set locale to ''.
```

which when run from terminal gives:
```
VLC media player 0.8.4 Janus

(process:7234): Gdk-WARNING **: locale not supported by C library

(.:7234): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

```


So I investigated the problem and began seeing similar errors all leading to **locales.** I searched high and low on google and ubuntu forums and tried many attempts to sovle the problem, but I couldn't figure it out.

I finally did this:
```
$/usr/lib/locale/en_US$ sudo dpkg-reconfigure --force locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US",
        LC_ALL = "en_US",
        LANG = "en_US"
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
Error: Bad entry 'en_US '
  en_US.ISO-8859-1... up-to-date
Error: Bad entry 'en_US.UTF-8 '
  en_US.UTF-8... up-to-date
Error: Bad entry 'en_US.utf8 '
  en_ZA.UTF-8... up-to-date
  en_ZW.UTF-8... up-to-date
Generation complete.
Current default timezone: 'America/Monterrey'.
Local time is now:      Mon Dec 25 00:18:38 CST 2006.
Universal Time is now:  Mon Dec 25 06:18:38 UTC 2006.
Run 'tzconfig' if you wish to change it.
```


I do not know what bad entry means nor how I can fix it. I rebooted and still got the same errors about locales being wrong. I use perl to test and I get variations of:
```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_US",
        LC_ALL = "en_US",
        LANG = "en_US"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```


I've tried en_US, en_US.UTF-8, en_US.utf8 and all gave the same errors.

I looked into removing libc6 and locales so that I could get a fresh install of them, but they are used by far too many packages.

I finally got nvidia drivers working after many reboots and hours of reading forums, i'm so tired of this crap randomly breaking or not working. I'm desperate, please help!

---

### Post by NeoLithium on 2006-12-25
Is your time zone set correctly from your install? I just noticed the ```
Current default timezone: 'America/Monterrey'.
```
Just asking cause I had that issue once where my tz was conflicting with the locale

---

### Post by xsism on 2006-12-25
it's the only GMT-6 i could find on the stupid TZ map. I live in Texas.


Remember too, I never had these issues until today, when I installed LMMS and LIVeS.

I think the issues is LIVeS. I got the DEB from [http://www.getdeb.net/app.php?name=lives](http://www.getdeb.net/app.php?name=lives) since there is no official pack.

I've since removed both LMMS and LIVeS, but that didn't help.

[B]
Is there ANY way to see what packages have been installed recently?[/B]

EDIT: synaptic hs a history, but doesn't show when I installed the LIVeS deb pack, how can I figure out what packs it installed? It was like 21 packs iirc.

better yet, how do I just fix the locales conflicts?

---

### Post by xsism on 2006-12-25
SOLVED (so it appears)
--------------------------------

I edited /etc/belocs/locales-gen.conf ...
```
PURGE=yes
```

then did...
```

export LC_ALL="C"
sudo dpkg-reconfigure --force locales
```

Everything was reset and I don't have those pesky errors. After I logged out and then back in, VLC no longer gave the errors either.

My /etc/environment file now looks like this
```
LANG="C"
LANGUAGE="C"
LC_ALL="C"
```

I'm going to try en_US.UTF-8 now, but I know for sure it works with C
EDIT----
Ok, Nothing else works besides C, but I discovered that the only thing that needs to be C is LC_ALL, so you can do
export LC_ALL="C"

this is my working enviroment
```
$ locale
LANG=en_US:en
LANGUAGE=en_US:en
LC_CTYPE="C"
LC_NUMERIC="C"
LC_TIME="C"
LC_COLLATE="C"
LC_MONETARY="C"
LC_MESSAGES="C"
LC_PAPER="C"
LC_NAME="C"
LC_ADDRESS="C"
LC_TELEPHONE="C"
LC_MEASUREMENT="C"
LC_IDENTIFICATION="C"
LC_ALL=C

```
END EDIT-----


Here are some pages I used in my journey...
[http://www.ubuntuforums.org/showthread.php?t=159177](http://www.ubuntuforums.org/showthread.php?t=159177)
[http://forums.vpslink.com/showthread.php?t=286](http://forums.vpslink.com/showthread.php?t=286)
[http://www.ubuntuforums.org/showthread.php?p=1057783](http://www.ubuntuforums.org/showthread.php?p=1057783)
[http://oriya.sarovar.org/docs/getting_started/node16.html](http://oriya.sarovar.org/docs/getting_started/node16.html)
[http://www.ubuntuforums.org/showthread.php?t=83315](http://www.ubuntuforums.org/showthread.php?t=83315)

---
if anyone needs help i'll try to assist best I can. This was on a Ubuntu 6.06 Dapper LTS install on HD with nvidia kernel compile.

Remember that packages get updated over time adn that can cause some weirdness.

:)

---

### Post by mahasmb on 2008-01-10
THANK YOU!

Thank you ever so much!

This worked. I've been struggling for days on this problem.

---

