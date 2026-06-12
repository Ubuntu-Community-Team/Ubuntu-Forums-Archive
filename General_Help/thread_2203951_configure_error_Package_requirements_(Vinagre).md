---
title: "configure: error: Package requirements (Vinagre)"
date: 2014-02-06
forum: General Help
---

### Post by jaybie_18 on 2014-02-06
Good day Everyone! i'm using Ubuntu 12.04 with version of Vinagre 3.4.2, as per their site latest version is already 3.11.5. I download the tar file extract & configure I got this error: much appreciated all help!

```
configure: error: Package requirements (glib-2.0 >= 2.28.0 gio-unix-2.0 >= 2.28.0 gthread-2.0 >= 2.0.0 gtk+-3.0 >= 3.9.6 libsecret-1 libxml-2.0 >= 2.6.31   ) were not met:

No package 'glib-2.0' found
No package 'gio-unix-2.0' found
No package 'gthread-2.0' found
No package 'gtk+-3.0' found
No package 'libsecret-1' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables VINAGRE_CFLAGS
and VINAGRE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by monkeybrain20122 on 2014-02-06
It tells you exactly what are missing. You have to install the developmental files for those packages in order to compile
```
sudo apt-get install libglib2.0-dev libgio2.0-cil-dev libgtk-3-dev  libsecret-1-dev libxml2-dev
```

Install synaptic, it would be convenient to search and find the exact packages when this happens next time.

---

### Post by jaybie_18 on 2014-02-06
@[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403") thanks so much! for assistance, what i did is install Synaptic then only this one is missing, can't find at Synaptic 

libsecret-1-dev

---

### Post by jaybie_18 on 2014-02-06
... up

---

### Post by monkeybrain20122 on 2014-02-06
I am on 13.10, apparently libsecret is not in Precise's repo. [https://launchpad.net/ubuntu/+source/libsecret](https://launchpad.net/ubuntu/+source/libsecret)
On this same link it lists some ppas where you can find libsecret, there are more if you click "other untrusted versions.."

---

### Post by jaybie_18 on 2014-02-06
done installing from other untrusted version. but i got this kind of error, :-(

```
configure: error: Package requirements (glib-2.0 >= 2.28.0 gio-unix-2.0 >= 2.28.0 gthread-2.0 >= 2.0.0 gtk+-3.0 >= 3.9.6 libsecret-1 libxml-2.0 >= 2.6.31   ) were not met:

Requested 'gtk+-3.0 >= 3.9.6' but version of GTK+ is 3.4.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
```

---

### Post by monkeybrain20122 on 2014-02-06
Hi, again the error message tells you exactly what went wrong. The version of gtk3 (libgtk-3-dev)in 12.0.4 is too old. It needs version 3.9.6 or higher but the version in 12.0.4's repo is 3.4.2. The version in Saucy is 3.8.6 so even that is not high enough to compile your applications. Unfortunately I couldn't find any ppa to upgrade that package in Precise to high enough version, there are probably some compatibility issues. 

I couldn't find a ppa for a more updated version of Vinagre for Precise either.  So I think your only option is perhaps to try to compile an older version which is still more updated than Precise's  (3.11.5 is not even in Trusty)  and hopefully the the gtk3 requirement can be met.  Here are the Vinagre versions in different Ubuntu releases for your reference [https://launchpad.net/ubuntu/+source/vinagre](https://launchpad.net/ubuntu/+source/vinagre)

Outdated software is the downside of using LTS. :)

Edited: If you are pro you probably can compile gtk from source and all its dependencies in /home( doubt that the repo versions of all of those will be high enough)  so that they will not interfere with with the system's versions and then compile Vinagre with it. But that is a lot of work and will bring more frustrations along the way..

---

### Post by jaybie_18 on 2014-02-06
Thank you. Speaking of downside, anyway will stick to this version until LTS on April release, your effort and time is really appreciated. Do we have Thank You button here? :)

---

