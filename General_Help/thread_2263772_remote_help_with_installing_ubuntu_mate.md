---
title: "remote help with installing ubuntu mate?"
date: 2015-02-03
forum: General Help
---

### Post by lemured on 2015-02-03
Hi everyone,

ok, I'm at trying to install Ubuntu Mate 14.04 for about a week now, and I'm getting desperate.
Pre-installed OS on this my new comp is windows8, which is absolutely hateful.

I went through dozens of threads with very good advise and manuals - I'm not being cynical, they were excellent - but nothing worked.
I'm not an IT-wizard, in fact I'm a latecomer and I'm still learning, so I might give the impression of a moron at times, but even I sense that at the bottom it's microsoft's effort to make installing alternatives which is the main problem.

I'm seeking someone talented who could dig out some time to have a look via remote take-over;
I've installed TeamViewer.
I'm situated in Europe, and I'm flexible with scheduling within limits.

Some basics:
[FONT=comic sans ms]comp: Toshiba SATELLITE PRO NB10t-A-108 [/FONT]
[FONT=comic sans ms]Intel Celeron CPU N2810 [/FONT]
[FONT=comic sans ms]2GB/ 500GB[/FONT]
[FONT=comic sans ms]Win 8.1 [/FONT]
[FONT=comic sans ms]
[/FONT]
[FONT=comic sans ms]need to install via stick, no CD [/FONT]
[FONT=comic sans ms]won't boot, keys don't work either, none of them[/FONT]
[FONT=comic sans ms]tried both with and without SecureBoot[/FONT]
[FONT=comic sans ms]priority set to USB in UEFI

My email addr.:
  {email removed}
I'd greatly appreciate help of this sort.
Thank you,
                       Daniel[/FONT]

---

### Post by lemured on 2015-02-03
p.s. 

was in the meantime able to solve the problem by redownloading iso and installer and start from scratch.
problem is now an error message:


SQUASHFS error: unable to read page,blockd9def17,sizeb46c

the error message appears when trying Mate without installing, after Ubuntu Mate [+logo] appears;
if installing is chosen Ubuntu Mate [[+logo] appears, it's trying for a while [dots below 'in motion'], then stops trying, stays like this

---

### Post by yancek on 2015-02-03
The error you posted in your last post is usually the result of a bad download.  Do an md5 checksum on the iso file.  If all you have is windows to do it on, the site below at microsoft explains how to do it:

[https://support.microsoft.com/kb/889768/en-us](https://support.microsoft.com/kb/889768/en-us)

You can find the md5sum for each Mint iso at the site below, click on whichever you used, 32bit or 64bit, cinnamon, mate, etc and on the next page the md5 sum will show.  Compare the outputs.  If they are not identical, the download was bad and you will continue to have problems.

---

### Post by lemured on 2015-02-03
hi yancek,

thank you :)
i'll do that, already downloaded from another source as this was given as a possible root for the problem.
alternatively i might have to try another USB
1st your way, though...

   thanks

---

### Post by lemured on 2015-02-03
yancek, you were spot on right and correct ! :)

it's not solved yet, though. have to try again with another tomorrow.

thanks 1000 for your help :)

---

### Post by lemured on 2015-02-04
ok, i'm meanwhile able to access grub, but i keep getting the same squashfs error, and with every mirror i tried; they can't all be faulty, unless i'm very unlucky.
does anyone know an image download that is with certainty well?
it'd at least confirm that the problem lies elsewhere.

---

### Post by oldfred on 2015-02-04
Even though your email was not in the clear, I removed it just in case. Forums are regularly parsed and having email can lead to spam. We also are a forum so others can also find solutions, so we prefer you post details. And if you do have to, you can use forum to send a PM (private message).

Most are downloading from the main site. But then it can save bandwidth to use a local mirror.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


 Install ISO Mirrors:
[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors)


 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you want Mate, we do not know what differences they have made to Ubuntu. I can then move thread to the sub-forum for Ubuntu un-offical versions.

I think most of these were successful, but show some work arounds/fixes needed.

 Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)
[SOLVED] Trouble installing Xubuntu 14.04 on Toshiba Satellite P55-A (UEFI) - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T - rEFInd
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

---

### Post by raptir on 2015-02-04
Have you confirmed the md5sum on the image you've downloaded as was recommended in the second post?

Also, the preferred method for downloading is torrent. It's much more reliable and has some built-in error checking.

[https://ubuntu-mate.org/trusty/](https://ubuntu-mate.org/trusty/)

The torrent links and md5sums are available there.

---

### Post by lemured on 2015-02-05
hi oldfred,

thanks, thank you very much indeed! :)
unfortunately i'm only online for a very brief time today, will study as much as i can tonight.
also thanks reg. the emal issue, wasn't  thinking straight, a bit desperate...

---

### Post by lemured on 2015-02-05
> **raptir said:**
> Have you confirmed the md5sum on the image you've downloaded as was recommended in the second post?

Also, the preferred method for downloading is torrent. It's much more reliable and has some built-in error checking.

[https://ubuntu-mate.org/trusty/](https://ubuntu-mate.org/trusty/)

The torrent links and md5sums are available there.


hi raptir,

thanks :)
it wasn't, but i got this problem with all the mirrors i tried so far. which is odd.
tried torrent, same result
the site you linked was the 1st i used

---

### Post by lemured on 2015-02-07
hi everyone,

and thanks for your help.

In the end writing the stick worked. 
But now I got a new problem:

ok, installing seemed to work wonderfully.
Restart.
Back to:

'Try Ubuntu without installing
Install Ubuntu, 
etc'

So it asked me to install, although I just installed.

Install again, same game, same result.

I noticed something towards the end of installing process:
loads of packages were rapidly removed -
'preparing to remove [...] package
completely removing [...] package
[...] package removed'

these were linux packages [they were not all called packages, ofc]

i don't get how during an installation so much should be [I]removed.


[/I]especially, and here's my 2nd problem, when it's a singular installation.
because during repeated attempts, and i don't know how this could have happened, i was very, very tired indeed,
can't remember it, but must have chosen singular installing at one point, one time, which of course wiped 
windows 8 off the surface of my computer's world [might have been a subconscious thing].

repeated installing now leads of course to the question 
'do you want to install ubuntu alongside ubuntu'

or not 'of course', because this would mean that it actually *is* already on the comp.
only it isn't.
without stick there's nothing.
with stick there's the friendly offer to install.

both is true: i'm stupid, and the ways of the digital deities are ineffable.

anyone? ideas? help? 

  thanks, sepiae

---

### Post by lemured on 2015-02-07
p.s. 
meanwhile, i might have erased windows 8 by means of another mistake, see
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

it's of no use to dwell on it now, windows is gone, so the question left i'm asking is
how to get ubuntu mate to actually installing from here.

---

### Post by oldfred on 2015-02-07
Ubuntu live installer has many packages, and uninstalls many that then are not used in your install. I see it uninstall gparted which I really want and immediately reinstall. But many others like LVM drivers are not required unless you do a LVM install.

On a reinstall you should not use any of the auto install options, but choose Something Else and select the same / as the root partition and the same /home as the same /home partition. If you have any data at all in /home that you want to keep DO NOT tick the format box.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by lemured on 2015-02-08
hi oldfred,

thank you, this is of real good help :)
especially the 2nd & 4th link, 2nd which is precisely about what we're at right now

---

### Post by lemured on 2015-04-09
hi everyone,

due to longer absence from net i couldn't mark this thread as either solved or unsolved.

my problem's over, ubuntu mate running fine, i'm happy with it.

however, i would not be able to say how exactly this came to be. i required a wizard having a good sit down with 
the comp, and although he solved it over a weekend, some of what he said was conflicting.
Initially he stated that it's made difficult by microsoft on purpose, somethin i've heard numerous times, to install another OS.
he added that we needed to reinstall windows 8 again first, otherwise there'd be no way of getting anything to boot.

whatever configurations he applied in bios at that point, when i came for installing Ubuntu he siad, and showed, that w8 was not on the comp. there was no way to configure bios before. 

so i cannot mark this thread as 'solved', unless someone knows what went on and can declare this solved.

thanks for all the help :)

---

### Post by oldfred on 2015-04-09
Windows often has not been shown with Ubuntu installer in any of the auto install options.
Part Windows and making sure fast startup/always on hibernation is off and part a bug in the auto install options, probably only fixed with 15.04.

And new systems with UEFI then become more complicated just because UEFI has more features (or settings you must change).

---

