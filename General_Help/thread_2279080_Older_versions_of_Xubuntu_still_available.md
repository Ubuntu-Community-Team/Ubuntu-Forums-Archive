---
title: "Older versions of Xubuntu still available?"
date: 2015-05-20
forum: General Help
---

### Post by Autodave on 2015-05-20
I ended up with and *old* Dell laptop with a whopping 128K memory.  It is also speedy at 333mhz. :-)  However, it runs fine on Win98 that came with it.  I would like to wipe that and put some version of Ubuntu on it. However, it has no USB ports and only a CD Rom drive.  Unless someone can tell me how to get a newer version on it, I would like to find an old version that will fit on a CD for installation.

Anyone know where I might find a version small enough to make a bootatble CD?

---

### Post by grahammechanical on 2015-05-20
The older versions are around somewhere but the repositories are closed and so to be able install any applications you will have to go through a complicated process. Now for the good news.

Xubuntu Core is only 600 MB in size. And it is new.

[http://xubuntu.org/news/introducing-xubuntu-core/](http://xubuntu.org/news/introducing-xubuntu-core/)

Regards.

---

### Post by kerry_s on 2015-05-20
lol, put it back in the closet.

---

### Post by Autodave on 2015-05-20
I just want to see it run and keep as an antique!  And besides, it will be great for solitaire. :-)

---

### Post by kerry_s on 2015-05-20
> **Autodave said:**
> I just want to see it run and keep as an antique!  And besides, it will be great for solitaire. :-)

lucky for you win 98 has solitaire, cause your going to have go old school linux to run on those specs. ;)

---

### Post by mattharris4 on 2015-05-20
If you don't plan on using the internet, picture editing or anything even slightly resource-intensive Puppy Linux claims to work on this spec computer.  I don't recall if it has solitare on it, though.  If you use the older version (I think it is version 4.3) and have an working older printer to go with it you could possibly use it as a simple word processor with the included low-RAM word processor included with Puppy.  If you can upgrade the RAM to 256MB and have it still run you might manage to browse simple websites with it (the very low power processor would be an issue here).  Puppy also fits on a CD with room to spare (it is only about 160MB in size).  However, if you run into a problem support is thin at best, my understanding is that most maintenance is done by its creator Barry Kauler even though he has attempted to retire from it (he also has an even smaller OS called Quirky that might be an option but support for that is even thinner).  Compare this to Canonical which has a support staff of over 100 and probably another 100 participants here providing support as well.  Puppy's site is here:  [http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by newb85 on 2015-05-20
[http://old-releases.ubuntu.com/releases/xubuntu/dapper/](http://old-releases.ubuntu.com/releases/xubuntu/dapper/)

^^^ That's where you can download the .iso for Xubuntu 6.06 LTS, the original release of Xubuntu.  Of course, to do anything with the repositories (which have been taken down), you'll have to edit your sources.list file as mentioned here.  vvv

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


Keep in mind, running an outdated release connected to the net is a big security risk.

That said, you're pretty much stuck with 128 MB RAM, as far as current releases of Ubuntu and its variants are concerned.  Lubuntu needs a minimum of 512, and even Peppermint says 256 is an absolute minimum.

---

### Post by newb85 on 2015-05-21
Just for the fun of it, I dialed a VM I had set up with Peppermint down to 128 MB to see if I could boot up and play solitaire.  It booted up, and I was able to navigate through the menu to solitaire.  It probably took ten minutes to boot up and log in, and I had to wait a couple more after I clicked "menu" before the menu popped up, but once it did, navigation was within the parameters of what I would call "normal" speed.

Then, as I watched the blank desktop waiting for a window to appear, the thought crept into my mind that solitaire might be a cloud app on Peppermint.  Wikipedia confirmed my suspicions.  Peppermint will boot up and run on 128 MB, but that's about all it will do.

---

### Post by sudodus on 2015-05-21
> **Autodave said:**
> I just want to see it run and keep as an antique!  And besides, it will be great for solitaire. :-)

1. You can try some extremely light-weight linux distros - ***DSL*** and ***Tiny Core***. I am almost sure they will work in your computer.


2. Puppy Linux has been mentioned already - Maybe ***Wary Puppy*** is also a good alternative, but you cannot expect to do much more than run it. It will probably be extremely slow to run application programs.


3. A new ultra-light, not yet released distro is ***ToriOS***. It is based on Ubuntu 12.04 LTS and uses the window manager JWM and should run in your computer with 128 MB RAM, but you cannot expect to do much more than run it. It will probably need swapping and be extremely slow to run application programs. The iso-file released May 20 is bad, but that released May 16 works (still beta, so not ready for regular usage, which means that you would be a beta tester).

[http://phillw.net/isos/torios/oldISO/ToriOS-2015-05-16-beta.iso](http://phillw.net/isos/torios/oldISO/ToriOS-2015-05-16-beta.iso)

Check it with the following md5sum file

[http://phillw.net/isos/torios/oldISO/md5sum-2015-05-16](http://phillw.net/isos/torios/oldISO/md5sum-2015-05-16)

I was curious and tested in my Dell Dimension 4600 with a Pentium 4 processor. I limited the available RAM with the boot option **mem=128m**, and it worked for me. 116 MB of those 128 MB (actually Mibibytes) were available for the operating system, and it was running idle with (only xterm and htop and screenie) using only 72 MB. See the attached screenshot. I was able to install it into the HDD with only 128 (116 available) MB available using the ultra light-weight ***One Button Installer***.


4. As has already been mentioned in earlier posts, all current Ubuntu flavours need more RAM than 128 MB. ***Lubuntu*** wants 512 MB, but you might succeed with less RAM. See this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

**Absolute minimun RAM** for the standard installers 

[LIST]
[*]Lubuntu 14.04 LTS 'Trusty' desktop 32-bit: 224 MB
[*]Lubuntu 14.04 LTS 'Trusty' alternate 32-bit: 176 MB
[/LIST]

-o-

See also the following link, [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by mastablasta on 2015-05-22
you could try something like antiX or simply add a widnows manager to ubuntu minimal iso. however as others pointed out not much can be done with such low specs. at least in term of current websites etc. 

though some htings will work. but depends what oyu plan to use it for. I would rather use it to run old DOS/WIN95, WIN98 games.

it will also be fine as a server. maybe osme older games from 2000-2005 server or something like that.

---

### Post by lisati on 2015-05-22
128K might be a bit small, is that a typo? I have an older machine with 64Mb RAM and running @ 133Mhz (?, could be 100, it's been a while) that came with Win98SE and 1 Gb hard drive (replaced with a 2Gb model). I managed to get a CLI version of 6.06 up and running on it a couple of years ago, but it couldn't cope too well with a GUI.

---

### Post by newb85 on 2015-05-22
Guess I read it as 128 MB.  It sounds more realistic.  I doubt '98 would run on 128 kB.

---

### Post by sudodus on 2015-05-22
> **newb85 said:**
> Guess I read it as 128 MB.  It sounds more realistic.  I doubt '98 would run on 128 kB.

+1 :-)

---

### Post by Bucky Ball on 2015-05-22
*Thread moved to **General Help**.*

***New to Ubuntu*** is for those new to Ubuntu ...

---

### Post by Autodave on 2015-05-30
Thanks for all the replies.  We put it out of our misery last Saturday: it went quietly.

---

### Post by mattharris4 on 2015-05-30
Sorry you could not use the old computer anymore.  If money is tight and you need another computer you can purchase a refurbished model that should work well for about $150 from either Newegg or Tiger Direct.  Make sure the computer has 4GB of RAM, a DVD-RW drive, a 250GB hard disk drive and at minimum a Core 2 Duo CPU (check the CPU's Passmark score by doing a Google search, it should score over 1000 if you want it to work smoothly, 1250 plus would be even better).

If you are purchasing a new computer the minimum I would recommend is 4GB RAM, a DVD-RW drive, 500GB HDD and at least an i3 processor (or the AMD equivalent -- the lowest i3 Passmark score I could find in a quick search was about 2500). What you would save by going with a computer with a lesser processor such as a Celeron or Pentium (or worse yet an Atom or Bay Trail) is minimal nowadays -- you would save less than $150 usually.  Dell sells computers with my recommended minimum specs and Windows 8.1 for less than $500 in both desktop and laptop forms and people report that a Linux install is relatively painless on them (that is expected as they sell several laptop models with Ubuntu on them pre-installed).  Our Dell desktop works fine after four years of heavy use (except for the borked Windows 7 install thanks to my careless nephew or niece -- don't download screen backgrounds from just anywhere, unfortunately the schools use Windows here so that is what they know how to use).  I would recommend a Dell to just about anyone and their website actually has excellent prices on their computers.

 Avoid any computer with an Intel Atom or Bay Trail and AMD E1 or E2  CPUs at all costs, they are made for power conservation and are very  slow and balky in heavy use (I have a laptop with an AMD E1, it doesn't handle heavy CPU loads well at all (but granted the laptop's battery life is great for a 15.6" computer).  I am actually running Lubuntu on it even though it is only a year old because it doesn't handle the full Ubuntu OS very well.

Avoid HP computers with Windows 8 or 8.1 if you wish to install Linux on them, that company makes its UEFI so it is very difficult to boot anything but Windows on their new computers.  There has also been Linux boot issues with some Toshiba and Acer computers (according to people posting here at Ubuntu Forums) with Win 8 or 8.1 on them but at least with my Toshiba laptop I successfully dual-booted Win 8.1 and Lubuntu without much difficulty on mine, it is only one year old.  

If you buy a laptop you may need the Synaptics touchpad fix here: [http://ubuntuforums.org/showthread.php?t=2233632&page=2](http://ubuntuforums.org/showthread.php?t=2233632&page=2) .  You would need to reboot after that code modification for your touchpad to work properly.  It was posted by gary51 but he said he got it from someone else and did not give credit to that person.

---

