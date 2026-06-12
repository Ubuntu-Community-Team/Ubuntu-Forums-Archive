---
title: "Lubuntu Downloads Missing?"
date: 2021-11-16
forum: General Help
---

### Post by rich332 on 2021-11-16
For some reason I can't find the proper download for my Atom box.  I can only find the AMD64 version.  

```
$ sudo wget http://cdimage.ubuntu.com/lubuntu/releases/19.04/release/lubuntu-19.04-desktop-amd64.iso--2021-11-16 16:24:09--  http://cdimage.ubuntu.com/lubuntu/releases/19.04/release/lubuntu-19.04-desktop-amd64.iso
Resolving cdimage.ubuntu.com (cdimage.ubuntu.com)... 91.189.91.124, 91.189.88.248, 91.189.91.123, ...
Connecting to cdimage.ubuntu.com (cdimage.ubuntu.com)|91.189.91.124|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2021-11-16 16:24:09 ERROR 404: Not Found.


##### Tue Nov 16 16:24:09 rich@sniff  ~/build
$ sudo wget http://cdimage.ubuntu.com/lubuntu/releases/18.10/release/lubuntu-18.10-desktop-i386.iso
--2021-11-16 16:24:51--  http://cdimage.ubuntu.com/lubuntu/releases/18.10/release/lubuntu-18.10-desktop-i386.iso
Resolving cdimage.ubuntu.com (cdimage.ubuntu.com)... 91.189.91.123, 91.189.88.247, 91.189.91.124, ...
Connecting to cdimage.ubuntu.com (cdimage.ubuntu.com)|91.189.91.123|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2021-11-16 16:24:51 ERROR 404: Not Found.
```

I also have the AMD64 installer, but it won't boot on my machine.

Any insight appreciated.  Cheers

---

### Post by GhX6GZMB on 2021-11-16
Sorry, but no cigar.
Last Lubuntu 32-bit version is 18.10
After that it's only amd64.
I think Debian still supports i386.

---

### Post by tea for one on 2021-11-16
[https://distrowatch.com/](https://distrowatch.com/)  > Find/Submit Distro > Search for Distro > Architecture

Plenty of other options on the same page to refine your search.

---

### Post by guiverc on 2021-11-16
You didn't use a Lubuntu or Ubuntu site I bet for your links

Lubuntu's web site is [https://lubuntu.me/](https://lubuntu.me/)

Lubuntu's download page is [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/) and includes only supported releases of Lubuntu.

If you're unsure of which of the many sites google will offer for download of Lubuntu (which include *legitimate*, *fan *& *fake* sites), don't use google (unless you can peruse what it offers & pick *legit* from *fake**/fan*) and use ubuntu.com, ie. [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) will send you to the correct site for each.

Both Lubuntu team, and Ubuntu only control Ubuntu and official sites.

(Lubuntu 18.10 & 19.04 are EOL & thus don't exist for download anymore; Lubuntu 19.04 in *i386* ISO was never officially released with ISO generation being disabled end-2018 whilst still in *alpha* thus existed only where QA daily ISOs exist.  Old ISOs do exist but I'd not recommend using an EOL version so I won't provide a link; *but I added one on a wiki page if I recall correctly...*   yeah I just checked & the ISO exists for *cosmic* in i386 & amd64, but not *disco*).

Do yourself a *favor* and only use legitimate sites (*not fan or fake*), and supported releases.

---

### Post by rich332 on 2021-11-17
Moved on to proper Ubuntu.  But to let you know, I did use the legit lubuntu site.

---

### Post by ActionParsnip on 2021-11-17
I suggest something like Puppy Linux or something equally light. 32bit support is about but is fading away slowly. Is there no scope to upgrade the CPU to a 64bit one or is it hard welded to the motherboard?

---

### Post by guiverc on 2021-11-17
> **rich332 said:**
> Moved on to proper Ubuntu.  But to let you know, I did use the legit lubuntu site.

The link you mentioned was removed 23-January-2020 on the official Lubuntu site; so you should have mentioned the *time-warp*, or actually look again in your history; as what you considered the *legit* site I bet was a *fan* or *fake* site.

Lubuntu has used [https://lubuntu.me/](https://lubuntu.me/) since 2015 (access to a *fan* site continued after that date, but that relatioship had ended by 2018 & only [https://lubuntu.me/](https://lubuntu.me/) was used from 2018).

---

### Post by oldos2er on 2021-11-18
If I might ask, why are you running wget with sudo?

---

### Post by TheFu on 2021-11-18
Each of the posts above makes valid points.
32-bit support for ubuntu releases ended a few years ago. 20.04 doesn't have any 32-bit installer for x86 CPUs.

End-of-Life releases get removed from downloads and official sources when support ends. Non-LTS releases have only 9months of support from the date released. The intent is that people using those would move to the next release 6 months later. If you don't want to move to a new release every 6 months, stick with only LTS releases which get 3 yrs of support for the DE versions (with 1-2 exceptions) and 5 yrs of no-hassle support for servers.  After 5 yrs, ESM (i.e. paid) support is available for server and the main, Gnome3 version of Ubuntu Desktop. There are ways to get free ESM support for LTS releases for a few systems. You can research that.  Non-LTS releases don't get ESM.

sudo used with wget is almost always a bad idea. Use a different system or different account to put files off the internet, then extract them somewhere else with that same account, and finally use sudo to install/place them into the final position desired, only if sudo is required to make that happen.  Sudo abuse is bad.  OTOH, if you have 5+ yrs Unix experience and fully understand the risks - go for it. It is impossible for us, to know you or your Unix skills. All we know is that you are new here.

For some reason, I thought almost all Atom CPUs supported 64-bit OSes, unless they are really old like the N270/N280 which is pre-2010.
N2xx, E6xx, Z2xxx (4 numbers) and all Zxxx (3 numbers) seem to be the only ones without Intel 64 (aka x86-64) support.  Z3xxx and later have it as do the Sxxxx and Cxxxx.

---

