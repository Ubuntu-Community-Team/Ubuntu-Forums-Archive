---
title: "How to manually download and install a different version of kernel headers ?"
date: 2018-05-09
forum: General Help
---

### Post by dgosborn on 2018-05-09
I need to do a memory dump on a system without rebooting.

I was going to use fmem.

It won't compile because /usr/src/ only has a subfolder /usr/src/linux-headers-3.13.0-24-generic/

but it seems I am running (or uname -r thinks I am running) 3.16.0-34-generic

/lib/modules/ includes both -24 and -34 versions

Synaptic has been updated but only includes -24 version of the headers.

Is there any way to manually download and install -34 version of the headers?

update:
I found the following link but still not sure how to go about it:
[https://packages.ubuntu.com/trusty-updates/linux-headers-3.16.0-34](https://packages.ubuntu.com/trusty-updates/linux-headers-3.16.0-34)

---

### Post by Impavidus on 2018-05-09
Which Ubuntu release? Because no fully updated Ubuntu release should use kernel 3.16 nowadays. 14.04 without HWE is at 3.13.0-147, all others at least at 4.4.

But if you're on 14.04, headers 3.16.0-34 are available using```
sudo apt-get install linux-headers-3.16.0-34
```But keep in mind that that kernel is obsolete.

---

### Post by dgosborn on 2018-05-09
I tried it. Here is the terminal...

**[COLOR=#000000]Reading package lists... Done[/COLOR]**
**[COLOR=#000000]Building dependency tree       [/COLOR]**
**[COLOR=#000000]Reading state information... Done[/COLOR]**
**[COLOR=#000000]Note, selecting 'linux-headers-3.16.0-34-generic' for regex 'linux-headers-3.16.0-34'[/COLOR]**
**[COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]**

/usr/src still shows only the original header folders and not the new ones(0-34).

Any ideas? Thanks for the advice you have already given.

---

### Post by monkeybrain20122 on 2018-05-09
You haven't answered the question. Which version  of Ubuntu is it?

---

### Post by poorguy on 2018-05-09
> **monkeybrain20122 said:**
> You haven't answered the question. Which version  of Ubuntu is it?
Hey dgosborn,

[I][B]Open terminal

[/B][/I]***copy and paste this command ***

***[COLOR=#0000ff]lsb_release -a[/COLOR]***

***press enter*** 

***copy and paste the output*** 

Others who know what to do will be able to give better assistance.

---

### Post by Impavidus on 2018-05-10
> **dgosborn said:**
> I tried it. Here is the terminal...

**[COLOR=#000000]Reading package lists... Done[/COLOR]**
**[COLOR=#000000]Building dependency tree       [/COLOR]**
**[COLOR=#000000]Reading state information... Done[/COLOR]**
**[COLOR=#000000]Note, selecting 'linux-headers-3.16.0-34-generic' for regex 'linux-headers-3.16.0-34'[/COLOR]**
**[COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]**

/usr/src still shows only the original header folders and not the new ones(0-34).

Any ideas? Thanks for the advice you have already given.
Not the output I was expecting, not even if you're not on 14.04.

Can you show the output of these commands:```
sudo apt-get update
dpkg --list | grep linux-
```That should tell us a bit more about what your system thinks is available and what is installed. And it should tell us what release you're really using.

---

