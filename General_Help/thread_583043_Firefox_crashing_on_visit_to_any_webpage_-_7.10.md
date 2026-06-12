---
title: "Firefox crashing on visit to any webpage - 7.10"
date: 2007-10-20
forum: General Help
---

### Post by Ryura on 2007-10-20
On any none-admin account, Firefox will crash randomly when visiting any page. Here's the error:
> ** Message: GetValue variable 1 (1) 
** Message: GetValue variable 2 (2) 
** Message: GetValue variable 1 (1) 
** Message: GetValue variable 2 (2) 
** Message: GetValue variable 1 (1) 
** Message: GetValue variable 2 (2) 
** Message: GetValue variable 1 (1) 
** Message: GetValue variable 2 (2) 

(gecko:9278): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Tahoma 8.25' 
Segmentation fault (core dumped) 

Please help :(

---

### Post by UK-Wobbie on 2007-10-20
> **Ryura said:**
> On any none-admin account, Firefox will crash randomly when visiting any page. Here's the error:


Please help :(

Have you had a go on unstilling firefox and then restill it?
That may fix it :)

Download [http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580](http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580)

---

### Post by Ryura on 2007-10-20
> **UK-Wobbie said:**
> Have you had a go on unstilling firefox and then restill it?
That may fix it :)

Download [http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580](http://sourceforge.net/project/showfiles.php?group_id=202789&package_id=241580)

Thanks for your response,

What is the easiest way to uninstall Firefox without harming any other files/applications?

---

### Post by subvertigo on 2007-10-20
The problem is Tahoma.

I had the same problem. I don't understand why upgrading from Feisty to Gutsy, Tahoma font went broken.

For now delete Tahoma font from /usr/share/fonts/...

I'm searching for a solution .... i need Tahoma!

---

### Post by questpro on 2007-10-20
Same problem for me as well. Its not just one font. Its happening to me for every website I am trying to visit and every time it is crashing on different font.


EDIT: AMD64 here as well.

---

### Post by Joshua Swink on 2007-10-20
Here is the bug:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/152609](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/152609)

It has the title "firefox crash on loading website w MS Core Fonts", but I'm not sure the ms core fonts are actually responsible. Anyway, I'm looking for a workaround because Firefox is completely broken for me in Gutsy.

---

### Post by tcsedc on 2007-10-21
Almost the same problem for me.  Firefox is completely dead after upgrading to 7.10

I have the AMD64 version of both Ubuntu and Firefox.

---

### Post by Beebock on 2007-10-21
Hi,

Same problem here. pretty much every website is dying out on me.
I'm running Gutsy 64Bit AMD. Just upgraded....

Re-installed flash (no solution) looking around now...

richard

---

### Post by arabxptyltd on 2007-10-21
I have the same problem. my font was tahoma 8.5
 Attempting the discussions on removing stuff, as tahoma is no a file found on my machine

---

### Post by a grain of Alt. on 2007-10-21
I was having the same issue as you guys- ultimately just did a clean install. Was it an upgrade to Gutsy or a fresh install?

I've heard some murmerings of nspluginwrapper causing problems (the script that installed 32 bit flash on 64 bit firefox).  I'd try uninstalling that and firefox, then reinstalling firefox from the repos- 

Hope ya'll have better luck than me.

---

### Post by markfinn on 2007-10-24
In my case the message was about the Tahoma font, which I had just installed.  I changed the permissions on the tahoma fonts to -rw-r--r-, and firefox stopped crashing.  YMMV

---

### Post by Joshua Swink on 2007-11-14
> **a grain of Alt. said:**
> I was having the same issue as you guys- ultimately just did a clean install. Was it an upgrade to Gutsy or a fresh install?

It was an upgrade. I also have a system with a fresh install, where Firefox works ok.

Another workaround is to add "export MOZ_DISABLE_PANGO=1" to /etc/profile. See [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/152609](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/152609).

---

### Post by blee1170 on 2007-11-26
I am having a issue with firefox crashing with a Segment Fault (core dumped) message.  I have tried reinstalling firefox, the flash plugin, and even placing "export MOZ_DISABLE_PANGO=1" in the profile.  That did slow it down a bit, but it still crashes on me a lot.  Anyone have another idea to try?

My system is just a 32bit fresh install of Ubuntu.

---

### Post by wavesound on 2007-12-14
Hi
I did a clean install and keep getting this on my 64bit system.
It seems to connected with add website.
Slashdot is the worse!
The screen goes grey and seems to hang the system till I close the browser.

Doulbeclick seems to hang the web page if it's slow loading the content. :(

cheers
Bob

---

