---
title: "Night Light on Lubuntu 21.04"
date: 2021-06-02
forum: General Help
---

### Post by lx431 on 2021-06-02
Hi there, 
I would to switch to Lubuntu and I ask for if there is a built in tool to change the color temperature (night light, blue light and so on...). Because of the new Wayland server most of them do not work anymore (redshift, f.lux and many others).

Thank you

---

### Post by guiverc on 2021-06-02
LXQt & Lubuntu use X11 so there is no need to worry.

Yes in the future LXQt will be able to use Wayland ([https://github.com/lxqt/lxqt/issues/10](https://github.com/lxqt/lxqt/issues/10)) however that's not currently available.

Redshift has a `redshift-gtk` GUI front-end for GTK, but a front-end was been created for Qt for Lubuntu ([https://launchpad.net/~hmollercl/+archive/ubuntu/redshift-qt;](https://launchpad.net/~hmollercl/+archive/ubuntu/redshift-qt;) it hasn't been re-packaged for more recent releases, but it still works on releases up to and including my *impish*)

(*Redshift works the same on LXQt as it did on LXDE years ago*)

---

### Post by ajgreeny on 2021-06-02
And of course, redshift will work without the gtk or qt GUI packages.

It's configured with a simple text file so very easy to use.

---

### Post by lx431 on 2021-06-02
Xubuntu also uses still X11 but upgrading from 20.10 to 21.04 Redshift doesn't work anymore: why?

---

### Post by ajgreeny on 2021-06-02
Does running it from terminal show you anything useful?

I do not have 21.04 at all but do have a VM of Xubuntu-21.10 using KVM/QEMU where redshift like in your 21.04 does not seem to work at all.
I have set manual location and the info from clicking the redshift-gtk icon in my panel suggests that the colour temp is working as it should but what I see on screen shows that it certainly is not.

This is something I can not explain at present; maybe it is a result of running as a VM but I will try to investigate further and come back.

---

### Post by guiverc on 2021-06-02
I'm convinced it's working for me on my impish box  (it kicked in when I wrote my prior post on this thread; alas day time now so I can't test).

I booted a recent QA-test install of *impish* and note

> Could not connect to wayland display, exiting.
Failed to start adjustment method wayland.
Trying next method...


which is why it likely isn't working for you, not for me on this ~fresh QA-install of impish.
Yet is is on my older (very much modified) primary box that is running the same packaged version?    (I have comparison boxes anyway to explore this)

Possibly a backend-package change has occurred, so I'll have to look.   Redshift Package 1.12-3 (Dec 2020) added Wayland support I see..    I'll explore this

(*note: this will be  easier to test at night... the program uses GeoIP to say if day/night; I flipped the QA-test install box to London/England timezone so time reports night, but program still said day using my GeoIP... i tried disconnecting box from network & it reports inability to get Day/Night detail & program just exits... [I don't want to have to setup a NTP server just to test this]*)

FYI:  I just got a report on IRC of a hirsute/21.04 user using it successfully (I asked)

---

### Post by guiverc on 2021-06-02
I've had a play.. it works on all boxes I normally use (including *hirsute* or 21.04)

However I have a **redshift.conf** I created I used back in 14.04/*trusty* days, and I just copy that to my boxes as part of my setup.  

Once I added that file to the QA-test box mentioned in the prior post; it worked (a*las was going day/dark regularly but I ignored as I'd made many changes to timezone in play etc*).. I logged out & back-in and it was great & working perfectly !

FYI:  *it's manually set currently to use UTC time for day/night instead of my local time, so I can play & test effects*.

I'd suggest creating a **~/.config/redshift.conf** file

See [https://help.ubuntu.com/community/Redshift](https://help.ubuntu.com/community/Redshift) for how.


FYI: The *helpful hirsute* user on IRC doesn't use a *conf* file I'm suggesting here though 

> <remline> guiverc: No conf. I eventually got to prefer a constant gamma shift throughout the day, so I just use one-shot manual mode. (e.g., redshift -P -O 4500)

---

### Post by ajgreeny on 2021-06-03
I was also using an imported configuration file, from my 20.04 Xubuntu install, using manual location settings  with lattitude and longitude.

I edited the normal daytime colour temp right down to 2500 to make it obvious but it simply did not work, even though the command ***redshift -p*** showed all working properly,  it obviously wasn't, the screen being normal colour.

Possibly a VM problem; I just do not know about that as I don't usually run redshift in VMs.

---

### Post by Dennis N on 2021-06-03
I used to control redshift with the application's command options in startup applications. My notes:
> Put in startup applications with adjusted numbers for location and desired color:
```
reshift -l 25:-122 -t 6500:3700
```
 -l is the latitude:longitude. use '-' if west or south. -t is the "warmth" 6500 is normal, 3700 is a redder night setting.
-l can be followed by geoclue, which finds your approximate location. If you try geoclue, the settings are for dusk to dawn.

---

### Post by lx431 on 2021-06-05
on my Xubuntu 21.04 I run redshift at boot but it go on for some seconds and after go off for several seconds and so on. I've made a redshift.conf file. It is annoying to see the screen first yellow then white then yellow again etc...

---

