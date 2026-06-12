---
title: "Downloading Ubuntu 14.04"
date: 2016-04-28
forum: General Help
---

### Post by ChristmasPi on 2016-04-28
Where can I download a pristine copy of Ubuntu 14.04 64-bit from?  The download page now shows Ubuntu 16.04.

---

### Post by howefield on 2016-04-28
Should be able to get it at [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by vasa1 on 2016-04-28
> **ChristmasPi said:**
> Where can I download a pristine copy of Ubuntu 14.04 64-bit from?  The download page now shows Ubuntu 16.04.

What do you mean by *pristine*? The reason I'm asking is that the first release of LTS versions including 14.04 differs from later releases: see [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack).

If you don't want to go the HWE route, you may want to install from here: [http://old-releases.ubuntu.com/releases/14.04.0/](http://old-releases.ubuntu.com/releases/14.04.0/) and then update that as usual.

---

### Post by ajgreeny on 2016-04-28
Or from the same site that vasa1 mentions you could save a little bit of updating and download the **14.04.1** version which does not have any of the Hardware-enablement-stack packages and will retain support until 2019 without any problems related to that.

Do not download the 14.04.2 point version as the Hardware-enablement-stack packages in that (vivid) have already lost support, and 14.04.3 (wily) soon will.

---

### Post by ChristmasPi on 2016-04-29
I think I made this a bit more complicated for myself when I said pristine.

I'm just a rookie at this stuff :( , all I really need is a copy of Ubuntu 14.04 that I can install on my desktop.  I'm not really sure what stacks are and if I need them.

I did look at the url [http://releases.ubuntu.com/](http://releases.ubuntu.com/) and I see there are two versions of Ubuntu 14.04 with the folder names as follows:

Ubuntu 14.04
Ubuntu 14.04.04

Which one should I be downloading or will Ubuntu 14.04 just update to Ubuntu 14.04.04?

Thank you

---

### Post by ajgreeny on 2016-04-29
Unless you have very new hardware I recommend that you stick to the straight 14.04, not 14.04.4 as that will lose support for the hardware enablement updates in July and you will then need to upgrade those packages to the xenial versions.

After running normal updates the system.will tell you that it is 14.04.4, and eventually 14.04.5 but it will.still be using the 3.13 kernel series, etc etc, which will retain support until 2019.

---

### Post by ChristmasPi on 2016-05-02
> **ajgreeny said:**
> Unless you have very new hardware I recommend that you stick to the straight 14.04, not 14.04.4 as that will lose support for the hardware enablement updates in July and you will then need to upgrade those packages to the xenial versions.

After running normal updates the system.will tell you that it is 14.04.4, and eventually 14.04.5 but it will.still be using the 3.13 kernel series, etc etc, which will retain support until 2019.

Hello Algreeny

Any chance you might be able to provide me with a link to the exact ISO file I need to download for Ubuntu 14.04 64-bit for i386 desktop PCs?

Over the weekend, I thought I would rebuild my PC and went to the link ( [http://releases.ubuntu.com/](http://releases.ubuntu.com/)[COLOR=#000000]  ) that I listed upstream.  There are two folders there, one called 14.04 and the other 14.04.04 but when I go into each of these folders, the only option for download is Ubuntu 14.04.04.
[/COLOR]
Thank you

---

### Post by howefield on 2016-05-02
If you are looking for 14.04 as suggested by ajgreeny, you should find it here...

[http://old-releases.ubuntu.com/releases/14.04.0/](http://old-releases.ubuntu.com/releases/14.04.0/)

---

### Post by marcello7 on 2016-05-02
here link to the ISO for [COLOR=#000000]Ubuntu 14.04 64-bit - i386 desktop PCs
[/COLOR]
[http://old-releases.ubuntu.com/releases/14.04.0/ubuntu-14.04.1-desktop-i386.iso](http://old-releases.ubuntu.com/releases/14.04.0/ubuntu-14.04.1-desktop-i386.iso)

Cheers

---

### Post by ChristmasPi on 2016-05-04
Thanks all, I think I figured out where my issue was.

I saw the AMD64 version on the download page and assumed it was for PCs with an AMD processor.  On the same page, it said the i386 version was "[COLOR=#000000][FONT=Ubuntu]For almost all PCs" which is why I went with that.

Long story short, I now know AMD64 refers to 64-bit processor and it worked perfectly on my PC.  Thanks again, hopefully this will help someone else as well.[/FONT][/COLOR]

---

