---
title: "Ubuntu version with build-essential?"
date: 2014-10-28
forum: General Help
---

### Post by godzillathecing92 on 2014-10-28
Hello everyone, wasn't really sure where to post this so apologies if this is the wrong thing.

So I installed Ubuntu a couple of days ago and it's giving me a lot of hard time with my network and long story short I can't get it working without build-essential.
Now the problem is, I can't get build-essential without an internet connection (can I? I mean I've looked everywhere and it doesn't seem like I can, but I don't know maybe 1 of you guys knows something I don't), but I also can't get an internet connection without build-essential. So I was wondering: is there an Ubuntu iso (or any variation of Ubuntu as long as it's Ubuntu at its core) that comes with build-essential?

Thanks in advance.

---

### Post by Doug S on 2014-10-28
On another computer, one that has internet, you could download the .deb files and perhaps others that build essential depends on, than take them over to your problematic computer and install them manually.
See here: [http://packages.ubuntu.com/trusty/amd64/build-essential/download](http://packages.ubuntu.com/trusty/amd64/build-essential/download) for example, which I got to from here: [URL="http://packages.ubuntu.com/trusty/build-essential"]http://packages.ubuntu.com/trusty/build-essential

To answer your actual question: I do not know if there is or not.
[/URL]

---

### Post by ian-weisser on 2014-10-28
> **godzillathecing92 said:**
> [I]s there an Ubuntu iso (or any variation of Ubuntu as long as it's Ubuntu at its core) that comes with build-essential?

Not any of the official flavors of Ubuntu.

To expand on Doug S's solution (which is the easiest way):
- Get the list of packages you need using the command: [FONT=courier new]sudo apt-get --simulate install build-essential[/FONT]
- After you download the packages, copy them to /var/cache/apt/archives. The packages in that directory should be owned by root.
- Install the new packages using the command: [FONT=courier new]sudo apt-get install build-essential[/FONT]

---

### Post by godzillathecing92 on 2014-10-29
> **ian-weisser said:**
> Not any of the official flavors of Ubuntu.

To expand on Doug S's solution (which is the easiest way):
- Get the list of packages you need using the command: [FONT=courier new]sudo apt-get --simulate install build-essential[/FONT]
- After you download the packages, copy them to /var/cache/apt/archives. The packages in that directory should be owned by root.
- Install the new packages using the command: [FONT=courier new]sudo apt-get install build-essential[/FONT]

Hm, would that even work on a computer without an internet connection? I mean, how would it know how to simulate the installation and fetch which packages it depends on? Would it even know what build-essential is? I hate to ask, but could you please write the dependencies? It'd probably save a lot of restarts to find all of them :P

Either way, thanks.

---

### Post by ian-weisser on 2014-10-29
> **godzillathecing92 said:**
> Hm, would that even work on a computer without an internet connection? I mean, how would it know how to simulate the installation and fetch which packages it depends on? 

Apt does not need to be online to check the dpkg database, which is installed with the package manager, which is installed with Ubuntu.
Apt does not need to be online to check the contents of /var/cache/apt/archives to determine which packages it already has available.
Try it and see. It worked for me last time I did an offline install.

If you wish to do it another way, you can find all of the direct dependencies for each package at [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by SeijiSensei on 2014-10-29
Are you connecting with an Ethernet cable, or trying to use wifi?  If you haven't used a cable, that would be my first choice.  It's pretty rare that Ubuntu won't connect via Ethernet out-of-the-box.

---

