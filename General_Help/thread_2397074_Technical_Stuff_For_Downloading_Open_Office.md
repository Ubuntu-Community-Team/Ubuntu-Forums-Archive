---
title: "Technical Stuff For Downloading Open Office"
date: 2018-07-25
forum: General Help
---

### Post by skyesharica on 2018-07-25
Hi Linux Friends,
I am writing a book.  I've had trouble with LibreOffice Writer and so I want to try Open Office.  ([https://www.openoffice.org](https://www.openoffice.org))  It's a free word etc program.
They ask me about these Linux specifications.:
System Requirements

[LIST]
[*]Linux kernel version 2.6 or higher, glibc2 version 2.5 or higher
[*]X-Server with 1024 x 768 pixel or higher resolution with at least 256 colors   (16.7 million colors recommended)
[/LIST]
I have no idea what those things mean.  Does anyone have an easy answer.
Then, to download the right version, I have to state whether I have:
Linux 64-bit (x86-64) (DEB) ... or
Linux 64-bit (x86-64) (RPM)
All I know for sure, is that I have 64 bit.  Is there an easy answer please?  :KS

---

### Post by Irihapeti on 2018-07-25
Any current Ubuntu version (including flavours) will be suitable.

You'll need to download the DEB version for 64 bit.

Remove LibreOffice first, if you haven't already done so, before installing.

---

### Post by Holger_Gehrke on 2018-07-25
LibreOffice and OpenOffice are not all that different, they share a lot of source code. A short history: the German company Star Division developed a multiplatform Office Suit named StarOffice. Sun bought them, but they wanted the developers, not the product and renamed it to OpenOffice and relicensed it under a free and open license. Oracle bought Sun, which led to a fork named LibreOffice, because there's quite some dislike of Oracle in the Open Source community. Then Oracle gave OpenOffice to the Apache Foundation.

So if you have problems using one of these two, the other won't be any better for you since they come from a common source. Most of the differences between the two are purely cosmetic or differences in default settings.

The listed requirements are so low that any PC built in the last 10 years and any Linux distribution published in the same time frame should work (for different values of "work").

RPM and DEB are different ways of packaging programs for Linux distributions. RPM is the Red Hat Package Manager, while DEB files were developed for Debian. Ubuntu is derived from Debian and uses DEB packages.

Holgeer

---

### Post by skyesharica on 2018-07-25
> **Irihapeti said:**
> Remove LibreOffice first, if you haven't already done so, before installing.

Thankyou for that.  Are you sure I have to remove LibreOffice.  How do I do that?  :p

> **Holger_Gehrke said:**
> Most of the differences between the two are purely cosmetic or differences in default settings.

Thanks Holger.  I want to try it because my line spacing is faulty in LibreOffice Writer.  No matter how much I mess with the settings I get no result, or an inconsistent result.  I'm writing a book and formatting like double spacing is extremely important or the editor will ignore you.  So I thought it would be worth trying the Open Office, even though, as you say, they are very similar.

---

### Post by Irihapeti on 2018-07-25
Actually, I'm not 100% sure you have to remove LibreOffice first, though I've understood that it's good practice to do so.

I use synaptic for package management, and I used to go through and mark for removal anything that looks like LibreOffice. These days, I use LibreOffice, so my memory of the process is a bit hazy.

You might find it useful to get further information from the OpenOffice forums [https://forum.openoffice.org/en/forum/](https://forum.openoffice.org/en/forum/) They do also allow questions about LibreOffice.

---

### Post by TheFu on 2018-07-25
LibreOffice is a "fork" from OpenOffice, from back when Oracle controlled it.  There were some bad feelings at the time, so most of the main developers left.

Those 2 requirements are met by almost every system running Linux desktop made today. Some laptops might have only 720p resolution.  That "requirement" isn't really a requirement, I'm positive.

You can check your kernel version using 'uname -a', but any Ubuntu the last 10+ yrs is running newer than v2.6.
X/Windows is the thing that controls the display.  All currently supported Ubuntu releases use X/Windows by default. It is possible to change that to something else. but you would know if you'd done it, most definitely.

To install OpenOffice, you should use a PPA.  The other options aren't nearly as good.  Using a PPA will integrate OpenOffice patching into your normal patch methods.  If you don't use a PPA, then you'll need to manually patch/upgrade the .deb files.  RPM files are not for use by Ubuntu systems and some .deb files won't work - it just depends on the different dependencies.   Sometimes installing .deb files directly will lead to "APT hell" in 3-6 months where the entire system cannot be patched anymore.

I searched for a PPA and didn't find one from a source I recognize as reputable.  You might also look for a flatpak or Ubuntu snap of openoffice. Either of those would be preferable to installing a .deb file, IMHO.  

Don't forget the JAVA requirements likely have to manually handled regardless.  IDK. 

I don't know if that is an easy answer or not.  With the power and great flexibility that Ubuntu provides, sometimes the answers aren't easy.

---

### Post by dragonfly41 on 2018-07-25
> [COLOR=#000000]I am writing a book. I've had trouble with LibreOffice Writer and so I want to try Open Office.[/COLOR]
Returning to original requirements you might try Scribus which is in Ubuntu Software Centre.
I am using scribus-trunk which is daily build.
Documents can be imported into Scribus.

Another useful tool which allows you to write documents in markdown format is Pandoc.
[https://pandoc.org/](https://pandoc.org/)
to be converted into end format.

---

### Post by skyesharica on 2018-07-26
> **Irihapeti said:**
> You might find it useful to get further information from the OpenOffice forums [https://forum.openoffice.org/en/forum/](https://forum.openoffice.org/en/forum/) They do also allow questions about LibreOffice.

Thanks, I had a look at the forum.  It's just as confusing as these forums - lots of code and high end user technical terms etc.  I think I'll persevere with LibreOffice Writer.  If I change I'll have to set up spell checker all over again, and go through all the same problems with line spacing etc.

---

### Post by dragonfly41 on 2018-07-26
@skyesharica .. If you would be more comfortable asking questions to other authors you could try Scrivener.
The unofficial free version for Linux is found here.   The mainline version is for Windows and Mac.
[http://www.literatureandlatte.com/forum/viewforum.php?f=33](http://www.literatureandlatte.com/forum/viewforum.php?f=33)

I have Scrivener 1.9.0.1 (beta) running well on Ubuntu 16.04.

---

### Post by skyesharica on 2018-07-26
Thanks for that but I feel safer if there's a forum that I can ask questions to if I get stuck.

---

### Post by monkeybrain20122 on 2018-07-27
Instead of installing Open Office maybe just make sure your LO is up to date. Not sure which Ubuntu you are using, if still 14.04 as your sig says and you are using the same LO that came with OS, it is centuries out of date. If that is the case try updating with the ppa [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa), most likely it will fix your problem.

---

### Post by skyesharica on 2018-07-27
> **monkeybrain20122 said:**
> Instead of installing Open Office maybe just make sure your LO is up to date. Not sure which Ubuntu you are using, if still 14.04 as your sig says and you are using the same LO that came with OS, it is centuries out of date. If that is the case try updating with the ppa [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa), most likely it will fix your problem.

Thanks, I'm on Ubuntu 18.04 LTS.  I've looked at that page and it is completely alienating.  I have absolutely no idea what it is about.  So I can't risk stuffing up my system by doing advanced things that I don't understand.  I am repeatedly saying the same thing in Linux forums.  I wish people could understand that not everyone on the forum is a programmer etc.  :o

---

### Post by PaulW2U on 2018-07-27
> **skyesharica said:**
> Thanks, I'm on Ubuntu 18.04 LTS.  I've looked at that page and it is completely alienating.
What that web page is prompting you to so is to run in a terminal:
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
```
and update to the latest version of LibreOffice. If you're using 18.04 then you're reasonably up-to-date anyway.
> **skyesharica said:**
> I wish people could understand that not everyone on the forum is a programmer etc.  :o
I share your pain. I've been using Ubuntu for eight years now. There are aspects of Ubuntu and Linux that I will never understand and don't ever want to. :mad:

It might be a good idea to update your profile using so that anyone helping you can quickly see which version of Ubuntu you are **now** using.

---

### Post by dragonfly41 on 2018-07-27
[COLOR=#000000]> I wish people could understand that not everyone on the forum is a programmer etc.

I did suggest earlier that you at least try joining an author's forum such as Scrivener.[/COLOR]

---

### Post by monkeybrain20122 on 2018-07-27
> **PaulW2U said:**
> 
and update to the latest version of LibreOffice. If you're using 18.04 then you're reasonably up-to-date anyway.


But I would still recommend OP to update anyway. The ppa version is currently 2 minor versions ahead of Bionic's package and may just fix his problem. Even if not the ppa will keep updating and in a few months will be very much ahead of the stock version.

---

### Post by monkeybrain20122 on 2018-07-27
> **skyesharica said:**
> Thanks, I'm on Ubuntu 18.04 LTS.  I've looked at that page and it is completely alienating.  I have absolutely no idea what it is about.  So I can't risk stuffing up my system by doing advanced things that I don't understand.  I am repeatedly saying the same thing in Linux forums.  I wish people could understand that not everyone on the forum is a programmer etc.  :o

Actually the page does have instructions. PPAs are unofficial repositories not maintained by Canonical. The maintainers may be the upstream developers or individual Ubuntu users. It is a convenient way to circumvent the version freeze in the official repo and get the latest software (or in some case with additional features not in the official packages) But the quality of ppas kind of varies so one has to be a bit discerning. This one is maintained by the same people who package the official LO packages so it is very safe.

---

### Post by The Cog on 2018-07-27
@skyesharica
I am not aware of any problems with line spacing in LibreOffice. Are you able to post a description of the problem and a small document that exhibits it?

---

### Post by skyesharica on 2018-07-28
> **PaulW2U said:**
> What that web page is prompting you to so is to run in a terminal:
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
```
and update to the latest version of LibreOffice. If you're using 18.04 then you're reasonably up-to-date anyway.

I share your pain. I've been using Ubuntu for eight years now. There are aspects of Ubuntu and Linux that I will never understand and don't ever want to. :mad:

It might be a good idea to update your profile using so that anyone helping you can quickly see which version of Ubuntu you are **now** using.

Thanks for that lovely reply.  I got this in terminal.:

```
mofa511@mofa511-All-Series:~$ sudo add-apt-repository ppa:libreoffice/ppa sudo apt-get update
[sudo] password for mofa511: 
Error: need a single repository as argument
```

---

### Post by PaulW2U on 2018-07-28
Those two lines need to be input into the terminal separately. After the first command you will be prompted to confirm that you wish to add the PPA.

---

### Post by skyesharica on 2018-07-28
> **PaulW2U said:**
> What that web page is prompting you to so is to run in a terminal:
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
```
and update to the latest version of LibreOffice. If you're using 18.04 then you're reasonably up-to-date anyway.
I tried this and got such a confusing response that I cancelled adding it.
```
sudo add-apt-repository ppa:libreoffice/ppa
[sudo] password for mofa511: 
 LibreOffice test builds and backports

This PPA will have what the Document Foundation calls "LibreOffice fresh", the latest release of the newest series (but no alpha/beta releases).

There is a PPA dedicated to specific LibreOffice major series which support a range of older Ubuntu releases too:
https://launchpad.net/~libreoffice/+archive/libreoffice-6-0 ("Fresh")
https://launchpad.net/~libreoffice/+archive/libreoffice-5-4 ("Still")
https://launchpad.net/~libreoffice/+archive/libreoffice-5-3 (EOL)
https://launchpad.net/~libreoffice/+archive/libreoffice-5-1 (EOL)
 (testbed for 16.04 LTS SRUs, EOL upstream)
https://launchpad.net/~libreoffice/+archive/libreoffice-4-2 (EOL)
 (testbed for 14.04 LTS SRUs, EOL upstream)

Alpha and beta releases of a new major releases and the first release candidate of minor updates can be found at:
https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases

So much for other ppas.

Please file bugs for these packages on launchpad as described in:
https://lists.launchpad.net/libreoffice/msg00072.html

This PPA might contain the release candidate that is assumed to become the final release even before it is declared so by the Document Foundation (e.g. usually release candidate 2 for minor updates).

Most of the packages in this PPA have only experienced minor testing -- in fact it is the place to enable a wider audience to test packages before they are published into the distro proper. In general, this PPA is _not_ for the average user to install without a closer look (if it would be, its packages would be in the main repositories). OTOH, it is _way_ _better_ to use packages from this PPA than using the *.deb files that The Document Foundation provides upstream, which are intentionally build against a very old baseline for maximum compatibility. So, _if_ you want to be on the bleeding edge, do it here, not with upstream *.debs.

In general, users are advised to take a look at the changelog for the details about a package. If there is a specific bug that is intended to be addressed by an update released into the PPA, you are encouraged to test, if the update solves that problem. Packages published after the distro release are mostly such specific fixes. Critical fixes will be SRUed into the main repositories after testing anyway (later, with more testing).

To return to the LibreOffice version from the main archive, use ppa-purge. see: http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html for details
 More info: https://launchpad.net/~libreoffice/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel adding it.
^C
```

> **PaulW2U said:**
> Those two lines need to be input into the terminal separately. After the first command you will be prompted to confirm that you wish to add the PPA.

Thanks Paul.  I've entered the commands separately.  This is what happened.  I don't understand a single word of it.  I hope I don't mess up my writer.:

```
mofa511@mofa511-All-Series:~$ sudo add-apt-repository ppa:libreoffice/ppa
[sudo] password for mofa511: 
 LibreOffice test builds and backports

This PPA will have what the Document Foundation calls "LibreOffice fresh", the latest release of the newest series (but no alpha/beta releases).

There is a PPA dedicated to specific LibreOffice major series which support a range of older Ubuntu releases too:
https://launchpad.net/~libreoffice/+archive/libreoffice-6-0 ("Fresh")
https://launchpad.net/~libreoffice/+archive/libreoffice-5-4 ("Still")
https://launchpad.net/~libreoffice/+archive/libreoffice-5-3 (EOL)
https://launchpad.net/~libreoffice/+archive/libreoffice-5-1 (EOL)
 (testbed for 16.04 LTS SRUs, EOL upstream)
https://launchpad.net/~libreoffice/+archive/libreoffice-4-2 (EOL)
 (testbed for 14.04 LTS SRUs, EOL upstream)

Alpha and beta releases of a new major releases and the first release candidate of minor updates can be found at:
https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases

So much for other ppas.

Please file bugs for these packages on launchpad as described in:
https://lists.launchpad.net/libreoffice/msg00072.html

This PPA might contain the release candidate that is assumed to become the final release even before it is declared so by the Document Foundation (e.g. usually release candidate 2 for minor updates).

Most of the packages in this PPA have only experienced minor testing -- in fact it is the place to enable a wider audience to test packages before they are published into the distro proper. In general, this PPA is _not_ for the average user to install without a closer look (if it would be, its packages would be in the main repositories). OTOH, it is _way_ _better_ to use packages from this PPA than using the *.deb files that The Document Foundation provides upstream, which are intentionally build against a very old baseline for maximum compatibility. So, _if_ you want to be on the bleeding edge, do it here, not with upstream *.debs.

In general, users are advised to take a look at the changelog for the details about a package. If there is a specific bug that is intended to be addressed by an update released into the PPA, you are encouraged to test, if the update solves that problem. Packages published after the distro release are mostly such specific fixes. Critical fixes will be SRUed into the main repositories after testing anyway (later, with more testing).

To return to the LibreOffice version from the main archive, use ppa-purge. see: http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html for details
 More info: https://launchpad.net/~libreoffice/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 http://au.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Get:3 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic InRelease [20.7 kB]
Get:4 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic/main i386 Packages [27.9 kB]
Get:5 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic/main amd64 Packages [27.9 kB]
Get:6 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic/main Translation-en [11.4 kB]
Fetched 171 kB in 4s (39.1 kB/s)         
Reading package lists... Done
mofa511@mofa511-All-Series:~$ sudo apt-get update
Hit:1 http://au.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic InRelease         
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Fetched 83.2 kB in 2s (45.6 kB/s)                             
Reading package lists... Done
```

---

### Post by monkeybrain20122 on 2018-07-28
Those are just preambles and disclaimers you find on the website. Don't worry.

sudo add-apt repository ...

adds the ppa to your sources list so that its repository becomes available to you

sudo update refreshes your database so your system now knows where to fetch LO.

But it looks like you forgot the final command to actually upgrade your LO, so now (don't need to repeat the first two which you already ran)
```

sudo apt upgrade
```

and just wait for it to complete.

---

### Post by skyesharica on 2018-07-28
> **monkeybrain20122 said:**
> But it looks like you forgot the final command to actually upgrade your LO, so now (don't need to repeat the first two which you already ran)
```

sudo apt upgrade
```
and just wait for it to complete.

I did that and got nothing.  So I did all three commands again and got the same.  Below is the terminal info.  After I did the first two commands I got a software update box and it downloaded a great deal of libreoffice stuff.  So maybe I'm up to date.  Anyway, this is what the terminal said.  ):P:
```
LibreOffice test builds and backports

This PPA will have what the Document Foundation calls "LibreOffice fresh", the latest release of the newest series (but no alpha/beta releases).

There is a PPA dedicated to specific LibreOffice major series which support a range of older Ubuntu releases too:
https://launchpad.net/~libreoffice/+archive/libreoffice-6-0 ("Fresh")
https://launchpad.net/~libreoffice/+archive/libreoffice-5-4 ("Still")
https://launchpad.net/~libreoffice/+archive/libreoffice-5-3 (EOL)
https://launchpad.net/~libreoffice/+archive/libreoffice-5-1 (EOL)
 (testbed for 16.04 LTS SRUs, EOL upstream)
https://launchpad.net/~libreoffice/+archive/libreoffice-4-2 (EOL)
 (testbed for 14.04 LTS SRUs, EOL upstream)

Alpha and beta releases of a new major releases and the first release candidate of minor updates can be found at:
https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases

So much for other ppas.

Please file bugs for these packages on launchpad as described in:
https://lists.launchpad.net/libreoffice/msg00072.html

This PPA might contain the release candidate that is assumed to become the final release even before it is declared so by the Document Foundation (e.g. usually release candidate 2 for minor updates).

Most of the packages in this PPA have only experienced minor testing -- in fact it is the place to enable a wider audience to test packages before they are published into the distro proper. In general, this PPA is _not_ for the average user to install without a closer look (if it would be, its packages would be in the main repositories). OTOH, it is _way_ _better_ to use packages from this PPA than using the *.deb files that The Document Foundation provides upstream, which are intentionally build against a very old baseline for maximum compatibility. So, _if_ you want to be on the bleeding edge, do it here, not with upstream *.debs.

In general, users are advised to take a look at the changelog for the details about a package. If there is a specific bug that is intended to be addressed by an update released into the PPA, you are encouraged to test, if the update solves that problem. Packages published after the distro release are mostly such specific fixes. Critical fixes will be SRUed into the main repositories after testing anyway (later, with more testing).

To return to the LibreOffice version from the main archive, use ppa-purge. see: http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html for details
 More info: https://launchpad.net/~libreoffice/+archive/ubuntu/ppa
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 http://au.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Hit:3 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic InRelease
Fetched 83.2 kB in 2s (44.8 kB/s)                              
Reading package lists... Done
mofa511@mofa511-All-Series:~$ sudo apt-get update
Hit:1 http://au.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]    
Hit:3 http://ppa.launchpad.net/libreoffice/ppa/ubuntu bionic InRelease         
Fetched 83.2 kB in 2s (45.8 kB/s)                              
Reading package lists... Done
mofa511@mofa511-All-Series:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by monkeybrain20122 on 2018-07-29
So you are already having the latest. Apparently you had an software upgrade at some point after you ran the first two commands and Libreoffice was upgraded along with the other upgrades. You can check LO's version. The ppa's version is 6.0.5.2, while the stock 18.04 version is 6.0.3

---

### Post by skyesharica on 2018-07-29
> **monkeybrain20122 said:**
> The ppa's version is 6.0.5.2, while the stock 18.04 version is 6.0.3
I've got 6.0.5.2.

---

### Post by monkeybrain20122 on 2018-07-29
> **skyesharica said:**
> I've got 6.0.5.2.
So you are already getting the newest from the ppa. Maybe you should start a different thread with an appropriate title concerning your spacing problem so that others can help.

---

### Post by dragonfly41 on 2018-07-30
Or .. browse the LibreOffice forum ..

[https://ask.libreoffice.org/en/question/42992/how-do-i-reduce-space-between-lines-writer/](https://ask.libreoffice.org/en/question/42992/how-do-i-reduce-space-between-lines-writer/)

---

### Post by skyesharica on 2018-07-30
> **dragonfly41 said:**
> Or .. browse the LibreOffice forum ..

[https://ask.libreoffice.org/en/question/42992/how-do-i-reduce-space-between-lines-writer/](https://ask.libreoffice.org/en/question/42992/how-do-i-reduce-space-between-lines-writer/)

Thanks. I've bookmarked that for future use.  ):P

---

