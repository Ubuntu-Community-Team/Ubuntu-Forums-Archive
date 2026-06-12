---
title: "Ubuntu Software Center"
date: 2014-12-26
forum: General Help
---

### Post by Glkanter on 2014-12-26
Happy holidays to all!

I'm running 14.04 with Mate.

I tried following some instructions for 32 bit Google Earth, but got an error in the USC.

So I tried another solution, which involved WINE. And I got what I think is the same error message, attached.

A couple weeks ago, I had a USC problem that was mirror server related. I tried that, but I don't think that was working either.

I'd appreciate any help!

Thanks,

Garry

---

### Post by oldos2er on 2014-12-27
What instructions did you follow? 

If possible it might be simpler to install google earth using dpkg ```
sudo dpkg -i /path/to/google-earth.deb
``` You'll need to tailor that command to wherever the *deb file is located. Also if there are any errors given, ```
sudo apt-get install -f
``` should fix them.

---

### Post by Glkanter on 2014-12-27
Thanks. 

I'm more interested in the Software Center error than the Google Earth. My head is swimming with Google Earth "solutions".

---

### Post by sandyd on 2014-12-27
The error seems to be related to the policykit authentication agent not being started.
What version of Ubuntu are you running and are all updates installed?

Does running
```

/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
``` before starting USC stop the error?

---

### Post by Glkanter on 2014-12-27
I installed 14.04 about three weeks ago. I've been using - and loving! - MATE for about a week.
I install updates weekly, but I chose to skip yesterday's because of this error.
I've attached the results of running the code, and then attempting to install WINE.

Thanks so much!!

---

