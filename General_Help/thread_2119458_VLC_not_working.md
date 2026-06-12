---
title: "VLC not working"
date: 2013-02-23
forum: General Help
---

### Post by BigD77 on 2013-02-23
Hello,

   I am running Lubuntu 12.04 on a 2003 vintage Dell Inspiron 1100.
   When I ran previous versions Ubuntu (9.10, and 10.10) VLC ran perfectly.  Yet, now when I pop a DVD in, it will acknowledge the DVD, give the title for a second or two, then just stop.  I am running the latest version from the Lubuntu Software Store.
   Is there a conflict somewhere, or am I doing something wrong?

---

### Post by steeldriver on 2013-02-23
Did you install the restricted extras / css packages?

[https://launchpad.net/ubuntu/precise/+package/lubuntu-restricted-extras](https://launchpad.net/ubuntu/precise/+package/lubuntu-restricted-extras)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by CaptinGoogle on 2013-02-23
Do you have ubuntu-restricted-extras and libdvdcss installed?

---

### Post by BigD77 on 2013-02-24
I installed all the available files from Synaptic.  Synaptic didn't have libdvdcss as a seperate file.  I also installed libdvdread4. still nothing.

---

### Post by andrew.46 on 2013-02-24
> **BigD77 said:**
> I installed all the available files from Synaptic.  Synaptic didn't have libdvdcss as a seperate file.  I also installed libdvdread4. still nothing.

Try the following in a terminal window:

```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

and then try your dvd...

---

### Post by BigD77 on 2013-02-24
> **andrew.46 said:**
> Try the following in a terminal window:

```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

and then try your dvd...

Andrew,

That worked!  Thanks a bunch!  Now I can watch DVD's.  :popcorn:

I wonder why this time I had to load that when before it just ran "out of the box" with previous versions of VLC and Ubuntu.

---

### Post by andrew.46 on 2013-02-24
Good to hear your issue has been resolved :). Now if there were only some decent DVD movies around these days....

---

