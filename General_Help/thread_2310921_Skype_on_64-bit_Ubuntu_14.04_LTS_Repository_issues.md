---
title: "Skype on 64-bit Ubuntu 14.04 LTS Repository issues?"
date: 2016-01-23
forum: General Help
---

### Post by Sameer_Gupta on 2016-01-23
Just installed Lubuntu 14.04 LTS 64-bit on my laptop Lenovo Thinkpad E450... Tried many different ways, but unable to install Skype.

Also tried reloading at several [COLOR=#ff0000]mirrors[/COLOR] (Main Server, as well as mirrors in various countries).. No luck.

Let [COLOR=#0000cd]SPM = Synaptic Package Manager[/COLOR].

Unselecting (unchecking the box) and then again selecting "Canonical Partners" and "Independent" (extras) in SPM? Did this many times, both for the binaries and the source code. (Of course, I did reloads both after unselecting and after selecting)

Implemented the steps at  [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)  several times -- adding i386 architecture, [COLOR=#0000cd]apt-get update[/COLOR] (command line) as well as clicking on [COLOR=#0000cd]reload[/COLOR] (in SPM), then [COLOR=#0000cd]*apt-get install skype*[/COLOR] -- did these many times -- no luck.

If I try [COLOR=#0000cd]*aptitude*[/COLOR] (instead of [COLOR=#0000cd]*apt-get*[/COLOR]), it wants to remove lots of packages, almost reducing the system to nothing!  No, thanks, I don't want to do this.. So had to forget *aptitude*.

If I do [COLOR=#000080]*sudo apt-get install skype*[/COLOR], it complains about lack of [COLOR=#0000ff]skype-bin[/COLOR].

If I do [COLOR=#800000]*sudo apt-get install skype-bin*[/COLOR], it complains that "[COLOR=#800000]libqtwebkit4:i386 and[/COLOR][COLOR=#800000] libgl1-mesa-glx:i386 cannot be installed[/COLOR]".

If I try [COLOR=#ff0000]apt-get install[/COLOR] for these 2 packages, then it complains that other packages cannot be installed.

**When I use the Package Manager (SPM)** -- "skype 4.3....." appears in the list of packages, but when I click on it and "Mark for Installation", it fails (unable to resolve dependencies) -- and this happens after reloading at several mirror sites.

Tried downloading the [COLOR=#800000]*.deb*[/COLOR] file directly from the Skype website (both the [COLOR=#0000ff]dynamic[/COLOR] and [COLOR=#0000ff]multi-arch[/COLOR] versions), then used both [COLOR=#ff0000]*gdebi*[/COLOR] as well as [COLOR=#ff0000]*dpkg -i*[/COLOR] -- nothing worked.. (same complaints, about lack of [COLOR=#800000]libqtwebkit4:i386 [/COLOR]etc)

**Repository problem?**
The thing is, when I add the i386 architecture, I can see heaps of [COLOR=#b22222]libxxxxx:i386[/COLOR] packages in SPM (some installed and some NOT) -- but I CANNOT find  [COLOR=#800000]libqtwebkit4:i386..  [/COLOR]I cannot find [COLOR=#800000]skype-bin[/COLOR], cannot find [COLOR=#800000]skype-bin:i386, [/COLOR]cannot find[COLOR=#800000] [COLOR=#800000]libgl1-mesa-glx:i386[/COLOR] [/COLOR]... Seems this is a problem with the repositories (mirrors)... How is it possible that adding the i386 architecture can result in loading so many xxxxx:i386 packages from the mirrors, BUT NOT these 3-4 packages?

I installed Lubuntu 64-bit 14.04 LTS on my Lenovo desktop 2 months ago (Nov 2015) -- also installed Skype -- everything went smoothly...  the 3 packages mentioned above ([COLOR=#800000]the i386 versions[/COLOR]) ARE available in that machine, and were installed automatically when I installed Skype!  So did something go wrong at the repositories within the space of 2 months?

Any suggestions?  Thanks.

If someone can delete Skype from their 64-bit Ubuntu, may be do a complete removal (remove those lib* files as well), then reload from the repositories and see what happens, even better :grin:

---

### Post by vasa1 on 2016-01-23
Could you post the entire output of **sudo apt-get update** and **sudo apt-get dist-upgrade**?

---

### Post by Sameer_Gupta on 2016-01-23
**dist-upgrade**?  Do I need to do this?

Anyway, will do it tonight after I get home and post the output.

---

### Post by vasa1 on 2016-01-23
> **Sameer_Gupta said:**
> **dist-upgrade**?  Do I need to do this?
...
Yes, because it will give us a fuller picture. You can always press "n" to abort because you'll be asked if you actually want to install the various upgrades (or kernels).

---

### Post by Sameer_Gupta on 2016-01-23
Attached 3 files:

apt-get-update-1.txt  (Attempt 1 of apt-get update)
 apt-get-update-2.txt  (Attempt 2 of apt-get update)
dist-upgrade-1.txt  (Dist upgrade)

When I do [COLOR=#ff0000]apt-get install skype-bin[/COLOR], the error message is:

```
The following packages have unmet dependencies:
 skype-bin:i386 : Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386
E: Unable to correct problems, you have held broken packages.
```

I have 241 packages whose names end with **:i386** (some installed, some not) -- I just do NOT have the ones that I need for skype :o

---

### Post by vasa1 on 2016-01-23
See if [http://askubuntu.com/a/223267/248158](http://askubuntu.com/a/223267/248158) is of help.

---

### Post by Sameer_Gupta on 2016-01-23
No, sorry, at least the aptitude option didn't work.

```
/root> aptitude -f install skype
The following NEW packages will be installed:
  libcgmanager0:i386{ab} libgl1-mesa-glx-lts-vivid:i386{a} libgstreamer-plugins-base1.0-0:i386{a} libgstreamer1.0-0:i386{a} 
  liborc-0.4-0:i386{a} libqt4-opengl:i386{a} libqtwebkit4:i386{a} libudev1:i386{a} skype skype-bin:i386{a} 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.8 MB of archives. After unpacking 87.0 MB will be used.
The following packages have unmet dependencies:
 libcgmanager0 : Breaks: libcgmanager0:i386 (!= 0.39-2ubuntu2~ubuntu14.04.1) but 0.24-0ubuntu7.5 is to be installed.
 libcgmanager0:i386 : Breaks: libcgmanager0 (!= 0.24-0ubuntu7.5) but 0.39-2ubuntu2~ubuntu14.04.1 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libcgmanager0:i386 [Not Installed]                 
2)     libgl1-mesa-glx-lts-vivid:i386 [Not Installed]     
3)     libqt4-opengl:i386 [Not Installed]                 
4)     libqtwebkit4:i386 [Not Installed]                  
5)     libudev1:i386 [Not Installed]                      
6)     skype [Not Installed]                              
7)     skype-bin:i386 [Not Installed]                     


Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```

The second option provided by aptitude was to remove 187 packages! Definitely don't want that..

Checked for "held" packages -- there are none.

---

### Post by vasa1 on 2016-01-23
I just noticed your prompt has "**root**" in it. I'm not saying that that has anything to do with your problems, but my understanding is that it's safer to just be a normal user and to use sudo when the situation warrants.

---

### Post by Sameer_Gupta on 2016-01-23
OK, thanks for the tip and your previous help.. May be I just have to use Skype on my other devices until the new LTS is released in April.

Also tried  [COLOR=#ff0000]sudo apt-get install ia32-libs[/COLOR] -- didn't work.

Looks to me that this is a repository issue...  can the 3-4 packages (mentioned in my first post) please be placed back in the repos?

Hope the dependency mismatches can be fixed soon (may be by the developers at skype).

---

### Post by vasa1 on 2016-01-24
One more link: [http://askubuntu.com/questions/504689/cant-install-skype-4-3-on-ubuntu-14-04-64-bit](http://askubuntu.com/questions/504689/cant-install-skype-4-3-on-ubuntu-14-04-64-bit)

---

### Post by Sameer_Gupta on 2016-01-24
Thanks.. Will try tonight.. I could try the suggestion from Mitch or Suri.. Don't think I want to follow the OP (z_inx)'s advice to re-format laptop and re-install Lubuntu (this might be a short term fix, but NOT the correct, long-term approach to deal with the problem).

EDIT-- Tried the Mitch-Suri approach.... Sorry, didn't work... Complaints the same as before.

Here's an interesting answer from Atul Jain,  July-16-2014 at 12:39 at:
 [http://askubuntu.com/questions/215298/unable-to-install-skype-on-64bit-ubuntu](http://askubuntu.com/questions/215298/unable-to-install-skype-on-64bit-ubuntu)

What do you think about that?

---

### Post by Vladlenin5000 on 2016-01-24
Perhaps all you need is to add 32-bit libraries, which is what you were trying to do by installing ia32-libs. This has been deprecated a long time ago. Try:

```
sudo dpkg --add-architecture i386
sudo apt-get update
```

Then try to install Skype normally:
```
sudo apt-get install skype
```

It should be as simple as this but most likely you already made a mess with your system so...

---

### Post by Sameer_Gupta on 2016-01-24
[COLOR=#800000]> **Vladlenin5000 said:**
> Perhaps all you need is to add 32-bit libraries, which is what you were trying to do by installing ia32-libs. This has been deprecated a long time ago. Try:
```
sudo dpkg --add-architecture i386
sudo apt-get update
```[/COLOR]
As I said in my first post, I had already done what you advise several times.

[COLOR=#800000]> Then try to install Skype normally:
```
sudo apt-get install skype
```
It should be as simple as this but most likely you already made a mess with your system so...[/COLOR]
Yes, it "[COLOR=#0000cd]*should*[/COLOR]" be as simple as that, I guess.... but *[COLOR=#0000cd]not[/COLOR]*, unfortunately.

Everything else is working fine -- so the system is **[COLOR=#0000cd]not[/COLOR]** in a mess :-)

Have done clean, autoclean, remove, autoremove, install -f --- done all these several times -- and all other software working perfectly -- so the system is in good condition (except for skype).

---

### Post by vasa1 on 2016-01-24
Sameer, while it may be true that your system appears perfect except for the Skype issue, no one knows whether some subtle, non-obvious, change has occurred that prevents the installation of Skype.

You asked about Anil's suggestion, I've never tried that and so can't help.

Re. the other suggestion that you reformat and then reinstall, I feel there's no need to reformat. Just a re-install should do.

Also, if you don't depend on Google Chrome, you could install a 32-bit version of Lubuntu instead of 64-bit. That should allow you to install Skype without the hassles, I hope. I doubt there'll be a performance hit for most casual work.

---

### Post by Sameer_Gupta on 2016-01-25
Thanks -- I'll try some more before going for the 32 bit version.

I notice that in my other machine (see my first post), [COLOR=#ff0000]libqtwebkit4:i386[/COLOR] and [COLOR=#ff0000]libqtwebkit4[/COLOR] have both been installed and co-exist harmoniously.

Same true for [COLOR=#b22222]libgl1-mesa-glx-lts-vivid[/COLOR] and [COLOR=#b22222]libgl1-mesa-glx-lts-vivid:i386[/COLOR].

---

### Post by vasa1 on 2016-01-25
> **Sameer_Gupta said:**
> Thanks -- I'll try some more before going for the 32 bit version.

I notice that in my other machine (see my first post), [COLOR=#ff0000]libqtwebkit4:i386[/COLOR] and [COLOR=#ff0000]libqtwebkit4[/COLOR] have both been installed and co-exist harmoniously.

Same true for [COLOR=#b22222]libgl1-mesa-glx-lts-vivid[/COLOR] and [COLOR=#b22222]libgl1-mesa-glx-lts-vivid:i386[/COLOR].

Okay, still just guessing here but I noticed **vivid** in both the above.

If you install Lubuntu using 14.0**1** and don't do something special, you'll remain on an older kernel. If you install Lubuntu using 14.0**3** onwards, I think, you'll automatically get newer kernels plus something called the Hardware Enablement Stack. Since you have vivid on one machine, that machine seems to have the HWE stack enabled.

Could you please post the kernel versions of both machines? The output of **uname -r** should do it. For example, I don't have any vivid software on my laptop and my kernel version is **3.13.0-76-generic**.

While you're at it, you could provide the output from **lsb_release -a** as well.

Edit: in case you decide you need the HWE stack, and you don't know how to go forward, please post a separate question. I haven't a clue.

Two related links:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
[http://ubuntuforums.org/showthread.php?t=2267071](http://ubuntuforums.org/showthread.php?t=2267071)

---

### Post by vasa1 on 2016-01-25
And a bit off-topic but here's a Skype-related success story with a valuable lesson at the end: [https://answers.launchpad.net/ubuntu/+source/skype/+question/256839](https://answers.launchpad.net/ubuntu/+source/skype/+question/256839).

---

### Post by Bucky Ball on 2016-01-25
Perhaps run these commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

That will get you to 14.04.3 if that's what you're after. Post any and all errors it throws, if any.

---

### Post by Sameer_Gupta on 2016-01-25
Okay, last night, did a re-install... after re-install, the first thing I did was to install skype using [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) -- worked well... Tested skype, echo test etc -- all good... Then installed all other software that I normally use, such as LaTeX, LaTeX beamer, evince, etc... Everything looks good (so far, touch wood).

Thanks everyone -- especially vasa1.

Here's my **uname -a**:

```
Linux sameer-ThinkPad-E450 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

And **lsb_release -a**:

```
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:        14.04
Codename:       trusty
```

God knows why installing skype first does the trick... but anyway, it worked.

To Bucky Ball:  Did what you said -- no change and no errors either... (the above indicates that I already have 14.04.3).

I have marked this thread as SOLVED, even though we didn't get to the root cause of the problem -- something just worked :wink:

---

### Post by vasa1 on 2016-01-26
> **Sameer_Gupta said:**
> Okay, last night, did a re-install... after re-install, the first thing I did was to install skype using [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) -- worked well... Tested skype, echo test etc -- all good... Then installed all other software that I normally use, such as LaTeX, LaTeX beamer, evince, etc... Everything looks good (so far, touch wood)

...

God knows why installing skype first does the trick... but anyway, it worked.

...

I have marked this thread as SOLVED, even though we didn't get to the root cause of the problem -- something just worked :wink:

Great to know you got things going. I know that re-installing the OS feels like a cop-out, but sometimes endeavoring to find the root cause of an issue would need a lot of patience and trouble-shooting skill with no guarantee. But if you're ever in the mood to dig deep, here's an interesting link: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

