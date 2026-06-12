---
title: "bootup : *incredible* lag between end of boot and start of GDM"
date: 2007-01-19
forum: General Help
---

### Post by Littleweseth on 2007-01-19
G'day;

I'm having a strange issue where for about forty or fifty seconds between when the scrolling boot messages disappear (i.e. the end of booting as logged by bootchart) and the appearance of the login screen, there is empty black nothingness (and the computer appears to be doing nothing.) I've combed through a few things and tried a few bootup optimisations (boot profiling, disabling unwanted services, etc.) but this giant idle period remains.

I get a distinct feeling that it's a timeout of some sort - either a disk mounting timeout (so faulty /etc/fstab), network timeout (i.e. waiting for an NTP server it's never going to find because i'm on dialup), or some other variety of bizzare wait. I'd disable GDM and see if was a delaay with that (and i'f i'd get faster login using a text login and 'startx'), but I don't know how.

I'm running a Dapper system that was built from a minimal server install, running the whole webserver kit. (so apache, postfix, etc.) I've charted my boot process with bootchart, and i infer that the delay is caused by a program that keeps running past where bootchart stops recording (i.e. appears on far right.) My most recent bootchart is here : [http://caradoc.jcu.edu.au/lws/bootchart.png](http://caradoc.jcu.edu.au/lws/bootchart.png) .

Any help appreciated.

---

### Post by dcstar on 2007-01-19
> **Littleweseth said:**
> G'day;

I'm having a strange issue where for about forty or fifty seconds between when the scrolling boot messages disappear (i.e. the end of booting as logged by bootchart) and the appearance of the login screen, there is empty black nothingness (and the computer appears to be doing nothing.) I've combed through a few things and tried a few bootup optimisations (boot profiling, disabling unwanted services, etc.) but this giant idle period remains.
......
Any help appreciated.

Do a forum search for "disable ipv6" and see if any of those solutions help.

---

### Post by Littleweseth on 2007-01-19
disabling ipv6 didn't help at all - i still timed a 39-second idle period.

Is there some kind of logfile detailing my boot process somewhere?

---

### Post by riven0 on 2007-01-19
Are you completely sure it's not your memory? How about doing a memtest just to be certain?

Also, you don't have Beagle installed, do you? This can cause massive slowdowns.

---

### Post by Littleweseth on 2007-01-19
i did a memtest a while back to test a feww sticks of dodgy ram (which all failed) and my current 512, which passed over and over in a period of about two hours.

No beagle :) 'locate' is good enough usually.

---

### Post by jocko on 2007-01-19
> **Littleweseth said:**
> G'day;
I'd disable GDM and see if was a delaay with that (and i'f i'd get faster login using a text login and 'startx'), but I don't know how.


To disable gdm you could rename the links to gdm in /etc/rc*.d:
```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/s13gdm
sudo mv /etc/rc3.d/S13gdm /etc/rc3.d/s13gdm
sudo mv /etc/rc4.d/S13gdm /etc/rc4.d/s13gdm
sudo mv /etc/rc5.d/S13gdm /etc/rc5.d/s13gdm
```
And to enable it again:
```
sudo mv /etc/rc2.d/s13gdm /etc/rc2.d/S13gdm
sudo mv /etc/rc3.d/s13gdm /etc/rc3.d/S13gdm
sudo mv /etc/rc4.d/s13gdm /etc/rc4.d/S13gdm
sudo mv /etc/rc5.d/s13gdm /etc/rc5.d/S13gdm
```

---

### Post by Littleweseth on 2007-01-19
Jocko : would using sysv-rc-conf do the same thing?

---

### Post by jocko on 2007-01-19
> **Littleweseth said:**
> Jocko : would using sysv-rc-conf do the same thing?

Yes, I think so. Just remember on which runlevels (2,3,4 and 5) it should be if you decide to revert.

---

### Post by Littleweseth on 2007-01-19
I disabled g/kdm and tried a bootup - nice fast text login. Type 'startx', twidle thumbs for about a minute while it idles. Something's wrong here?

---

### Post by markitect on 2007-01-19
I've seen a similar problem, with 2 monitors in twinview mode, in that case it was screwy resolutions/timing in my xconfig (on monitor had nice high timings and the other nice big resolution, so it took a while doing what seemed to be figuring out a common resolution/timing), that it was testing, and were failing.  

Check out your config and make sure that the first listed resolution is a valid one for your monitor, and make sure your timing range includes 60hz.

If you have a widescreen, dual screen or something like that its probably the problem.

---

### Post by Littleweseth on 2007-01-19
I have a single 1600x1200 19" CRT. Which config files am suposed to be digging around in here?

---

### Post by markitect on 2007-01-19
edit /etc/X11/xorg.conf (you will have to sudo to make changes)

go down to the Screen Section.  

Your DefaultDepth will probably be 24,

go to the subsection with the depth that matches and make sure the modes read something like

```
Modes "1280x1024" "1024x768" "800x600" 
```

try setting it to 1024x768 first in the list and try setting the DefaultDepth above to 16.  


if one of these things work, then x is having trouble setting the monitor to that resolution or depth

if that doesnt work look for a Monitor section and set the 
```

        HorizSync    30-107
        VertRefresh  48-120

```

This should allow some very low refresh rates so it should work better.


Most monitors can't run there max refresh rate at there max resolution so then X looks for a compramise between the too, which can cause your lag.

If you know what make and model you monitor is you can also try searching for a monitor section someone else uses for that paticular monitor

---

