---
title: "how to install firefox 2.0 rc3 from .tar.gz ?"
date: 2006-09-27
forum: General Help
---

### Post by syxbit on 2006-09-27
i don't want to install from the repo's, as i want the update feature to work, and i hear it's better(faster) than the repo's one anyway.

i downloaded this file "firefox-2.0.en-GB.linux-i686.tar.gz"
untar'd, but don't know how to proceed
i was gonna compile it, but i didn't get the source.
could someone help

---

### Post by tuxcantfly on 2006-09-27
how about you cd to the directory you extracted to, and do a ./configure? do it as sudo unless you want to install into your home directory. as for source, it's here: [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0rc1/source/firefox-2.0rc1-source.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0rc1/source/firefox-2.0rc1-source.tar.bz2)

---

### Post by Fully216 on 2006-09-27
It would be more helpful if you placed a link to the file that you downloaded, showed the commands you tried, and the corresponding error messages if any.

When I go to the mozilla ftp site, I can only find release canidate 1 for firefox 2.0 instead of rc3.  There is a linux-i686 version and a source version available, so I am curious which one you chose, if any at all.  Btw, you will need the source package.  You can find them here

[ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0rc1](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0rc1)

---

### Post by Fully216 on 2006-09-27
On a side note, anything compiled from source will not work with the update feature.  You will be responsible for maintaining the package on your own.

---

### Post by tuxcantfly on 2006-09-27
there is no rc3. only rc1 has been released. look at the announcement on mozilla.org:

[http://en-us.www.mozilla.com/en-US/firefox/2.0/releasenotes/](http://en-us.www.mozilla.com/en-US/firefox/2.0/releasenotes/)

---

### Post by tuxcantfly on 2006-09-27
by the way, what's wrong with using edgy's version? it'll update with apt.

---

### Post by Fully216 on 2006-09-27
I don't think there is anything wrong.  It is what I use, although I have the 64-bit amd flash issues, so I run the 32-bit version if need be.

---

### Post by tuxcantfly on 2006-09-27
you can run the 32 bit firefox under amd64. howto here: [http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)
for best flash and plugin compatibility, just run the windows version of firefox under wine. it's the only way to get flash 9, shockwave, and stuff like that

---

### Post by dpicker on 2006-09-27
Once you have extracted the original "firefox-2.0.en-GB.linux-i686.tar.gz" you downloaded, go into the firefox folder and just double click on the "firefox" script. Gnome will ask you if you want to run it or view it, Click run.

Btw It won't open properly if you already have another version of firefox open/running.

---

### Post by syxbit on 2006-09-27
sorry, guess i meant rc1
i untar, cd to the dir and type
./configure (i've tried "sudo ./configure" aswell)
and get this
```
sudo: ./configure: command not found
```

i don't see a firefox script either

these are the files in the firefox DIR
```
syxbit@SyXbiT-X:~/Desktop/firefox$ ls
browserconfig.properties  libnspr4.so         libxpistub.so
chrome                    libnss3.so          mozilla-xremote-client
components                libnssckbi.so       plugins
defaults                  libplc4.so          readme.txt
extensions                libplds4.so         README.txt
firefox                   libsmime3.so        removed-files
firefox-bin               libsoftokn3.chk     res
greprefs                  libsoftokn3.so      run-mozilla.sh
icons                     libssl3.so          searchplugins
libfreebl3.chk            libxpcom_compat.so  updater
libfreebl3.so             libxpcom_core.so    updater.ini
libmozjs.so               libxpcom.so         xpicleanup
```

any ideas ?

---

### Post by dpicker on 2006-09-27
The firefox script is there. Just double click on the file called "firefox".

It says command not found when you type in ./configure because the .tar.gz you downloaded is not the source, it's the binary. I wouldnt recommend compiling as it would take a long time and there would be lot's of dependencies.

---

### Post by syxbit on 2006-09-27
well, thanks for the help guys
before running the script, i managed to ruin my firefox install.
it wouldn't work anymore, and reinstalling wouldn't fix (the repo version that is)
i ran the script, and BAM!
now i just linked my old firefox shortcut to the script, and it works like a charm.
i don't really know what i did (i think i moved the old firefox location or something) but it works now anyway.

btw. bon echo is a big improvement. i love the spell checker
so many times in gmail i'd just forget to spell check. but having it spell check as you type is perfect.

thanks again guys

(ps. i guess i didn't know it was a script cause it didn't have the extension ".sh")

---

### Post by amubu on 2006-10-19
now i have to delete the old firefox... ? i write firefox at the terminal and  the old firefox appears

---

