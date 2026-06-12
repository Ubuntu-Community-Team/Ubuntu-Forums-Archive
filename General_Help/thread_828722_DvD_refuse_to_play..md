---
title: "DvD refuse to play."
date: 2008-06-14
forum: General Help
---

### Post by fedex1993 on 2008-06-14
Okay in about 3 days i am going on vaction and of course taking my laptop with me to play dvds surf the next and other stuff. My problem is i just bought about 15 new dvds and wanted to watch them while on the trip. I can not get any of them to play at all even after install ubuntu-restricted-drivers, i tried on VLC Mplayer and also Kaffeine. Please help before 3 days is up.

---

### Post by cariboo on 2008-06-14
have you got libdvdcss2 installed? if no go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and do what it says for your version (you didn't specify)

Once you've finished, open Synaptic and search for libdvdcss2 and mark it for installation, while you are there make sure libdvdread3 is installed, if not install it too.

Jim

---

### Post by ad_267 on 2008-06-14
From: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

> If you are using Ubuntu 8.04 "Hardy Heron" (AMD64):

    *

      Open a terminal and type

      sudo apt-get install build-essential debhelper fakeroot

      press the enter key.
    *

      Then type

      sudo /usr/share/doc/libdvdread3/install-css.sh

      press enter again
    *

      When it asks you, press enter to continue and it will build and install libdvdcss2


---

