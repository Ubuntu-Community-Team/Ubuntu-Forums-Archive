---
title: "using Ubuntu Live CD 12.04 to purge virus on Windows Vista"
date: 2013-12-03
forum: General Help
---

### Post by dragonfly41 on 2013-12-03
A friend who is not too computer savvy has telephoned me for some technical help.

She has a virus contaminated Windows PC and is now being blackmailed by a caller to remove a planted virus.
I've told her to not use her PC until I have a look.

From what I gather I believe the attacker has been given remote access to her PC since she 
followed some telephoned instructions from this rogue caller.
She is seeing a white screen.
I've warned against crook callers who masquerade as Microsoft Support and plant viruses.
Another possibility is her younger family using the shared PC for games.

Tomorrow I'm going to pay a visit with my Ubuntu 12.04 Live CD to try to sort this out on the Windows box.

What procedure is recommended to run Ubuntu live CD to clear out host PC windows virus(es)?

I've looked at Clamtk but the latest Clamtk runs on 13.04 (not my 12.04).

Could I run AVG (windows only) in wine on Ubuntu 12.04 to clear out viruses on the (contaminated) Windows partition?

From Ubuntu Live CD I should be able navigate to windows file system and access widows registry and system folders.

Any particular registry / dll files to search for and remove manually if AVG virus scanner does not work in wine?

---

### Post by rclocher3 on 2013-12-04
Yikes!  I'm not so sure that what you're planning is even possible.  I think you should try downloading a free antivirus rescue disk .iso file, burn the .iso file to a CD, and then boot the infected computer to the CD.  You can find an antivirus rescue CD image to download by Googling "antivirus rescue CD".  Many are free.

The problem with viruses is that the computer is usually damaged even if you can completely remove the virus.  Often the virus can't be removed.

In such a situation I usually try to remove the virus with the rescue CD, and then copy the important files off the computer.  You can use the Ubuntu live CD to copy the files.  Then I erase the hard drive and reinstall Windows.

Good luck.
- Rob

---

### Post by dragonfly41 on 2013-12-04
I read up on latest "white screen trojans" ...

[http://readwrite.com/2013/11/08/cryptolocker-prevent-remove-eradicate#awesm=~ooZEILVBAscRfd](http://readwrite.com/2013/11/08/cryptolocker-prevent-remove-eradicate#awesm=~ooZEILVBAscRfd)

[How to Remove Viruses from a Windows PC Using a Linux Live CD - Support.com]("http://www.support.com/blog/post/how-remove-viruses-windows-pc-using-linux-live-cd")

I tried launching windows XP in safe mode ... but that didn't work.
Windows XP login password had been zapped.

I tried Kaspersky Rescue CD but this didn't find any trojan. But I could inspect innards of Windows XP and run browser.

Finally persuaded my friend to draw a line under this and convert from Windows to Ubuntu.

Long installation of Ubuntu 12.04 + ubuntu-desktop followed on old PC.

Hopefully this new setup should stop future attacks.

[color=maroon]
[Later edit]

More found here on "CryptoLocker" experiences ... 

[http://ubuntuforums.org/showthread.php?t=2189320](http://ubuntuforums.org/showthread.php?t=2189320)

but as I understand so far only attacking Windows users.

[/color]

---

### Post by slooksterpsv on 2013-12-04
It's called ransomware. It's a backdoor virus, usually a trojan, that instructs users to call a number or purchase an card that you load with cash and send them the numbers. My friend got one 3 times and he spent $500 paying them to "remove" the virus only to get it again. You could have also tried other antivirus boot CDs such as Avira, AVG, BitDefender, etc. If they were running XP, I'd just switch them to Linux. Not sure what kind of sites they were on, but not good.

---

### Post by dragonfly41 on 2013-12-04
> ... paying them to "remove" the virus only to get it again.

that was my suspicion and I thought a good reason for ditching windows xp.

I had pre-prepared Kaspersky Rescue CD and AVG Rescue CD.

...

And I now learn of this risk in sharing Ubuntu files with Windows users via Ubuntu One, Dropbox, Samba etc..

[http://ubuntuforums.org/showthread.php?t=2185011](http://ubuntuforums.org/showthread.php?t=2185011)

---

