---
title: "Playing Encrypted DVDs"
date: 2015-04-23
forum: General Help
---

### Post by craig10x on 2015-04-23
I recently upgraded to ubuntu 15.04...i haven't used encypted dvds on my system for a long time, but now i would like to be able to play some once in a while..
I know in the past, we were able to get libdvdcss2 (the file needed for encrypted dvds) from medibuntu, but that is no longer available....what is the easiest way to get and install it these days?
I would need the 64 bit version...

---

### Post by slickymaster on 2015-04-23
To play commercial DVDs in Ubuntu you need to install **libdvdcss** for recognizing them, **libdvdread4** for reading them and **libdvdnav4** for navigating them. These are not included by default, because Canonical would have to pay a royalty, making Ubuntu non-free. For personal use however, they are free for you to install.

In a terminal window run```

sudo apt-get install libdvdcss libdvdread4 libdvdnav4
```
Afterwards, and again in terminal run```

sudo /usr/share/doc/libdvdread4/install-css.sh
```
Rebooting might be necessary.

---

### Post by ajgreeny on 2015-04-23
Surely, there is no point in including the **libdvdcss** package in your first command as libdvdcss is not available as a package in the repos, but is called for installation (from videolan? direct) by the install-css.sh file, part of the libdvdread4 package.

I simply worry that a newer user will be unnecessarily concerned by the error message telling him that libdvdcss is not installable when running that first command of yours.

---

### Post by craig10x on 2015-04-23
I checked on ubuntu software center and it appears that libdvdread4 and libdvdnav4 are already installed (that probably was included in ubuntu restricted extras when i installed that)....so looks like i would only need libdvdcss2 for the encrypted ones...is there a 32 bit and 64 bit version for libdvdcss2?   And how would you install just the one file and make it work in the dvd players? (vlc and totem)...

edit: just saw ajgreeny's post...since the first 2 are already installed, does that mean i can already play the encrypted ones, or is there something else to do?
This is sure confusing ;)

---

### Post by ajgreeny on 2015-04-23
You need to run the command ```
sudo /usr/share/doc/libdvdread4/install-css.sh
``` which will download and install libdvdcss2 from (I think) the [http://download.videolan.org](http://download.videolan.org) site direct.  You should then be able to play any commercial encrypted DVDs.

---

### Post by slickymaster on 2015-04-23
> **ajgreeny said:**
> Surely, there is no point in including the **libdvdcss** package in your first command as libdvdcss is not available as a package in the repos, but is called for installation (from videolan? direct) by the install-css.sh file, part of the libdvdread4 package.
<---snip--->.
You're absolutely right ajgreeny, it was my bad there. [-(

Note to self, have a re-read at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) as soon as possible.

---

### Post by craig10x on 2015-04-23
Based on reading that link slickymaster, it sounds like they are saying that since i already have the libdvdread4 file (which ubuntu restricted extras installed) that all i would need to do is to open the terminal and enter:
    [COLOR=#333333][FONT=UbuntuMono]sudo /usr/share/doc/libdvdread4/install-css.sh  t
[/FONT][/COLOR]to make it work in vlc for the encrypted dvds...am i reading that right? And that i wouldn't need libdvdcss2 at all...or am i still confused? :confused:

It use to be so much easier when we had medibuntu...it was so easy to get it installed from there...

---

### Post by slickymaster on 2015-04-24
> **craig10x said:**
> Based on reading that link slickymaster, it sounds like they are saying that since i already have the libdvdread4 file (which ubuntu restricted extras installed) that all i would need to do is to open the terminal and enter:
    [COLOR=#333333][FONT=UbuntuMono]sudo /usr/share/doc/libdvdread4/install-css.sh  t
[/FONT][/COLOR]to make it work in vlc for the encrypted dvds...am i reading that right? And that i wouldn't need libdvdcss2 at all...or am i still confused? :confused:

<---snip--->
Yes, you're reading it correctly.

---

### Post by Keith_Helms on 2015-04-24
> **craig10x said:**
> Based on reading that link slickymaster, it sounds like they are saying that since i already have the libdvdread4 file (which ubuntu restricted extras installed) that all i would need to do is to open the terminal and enter:
    [COLOR=#333333][FONT=UbuntuMono]sudo /usr/share/doc/libdvdread4/install-css.sh  t
[/FONT][/COLOR]to make it work in vlc for the encrypted dvds...am i reading that right? And that i wouldn't need libdvdcss2 at all...or am i still confused? :confused:

It use to be so much easier when we had medibuntu...it was so easy to get it installed from there...

You do still need libdvdcss2.   It's just that instead of installing it either directly from the repository or as part of restricted extras the install is now "hidden" and the /usr/share/doc/libdvdread4/install-css.sh script is what goes and gets that library and installs it.  Once you've run that script, you'll see libdvdcss2 listed in synaptic or apt.

---

