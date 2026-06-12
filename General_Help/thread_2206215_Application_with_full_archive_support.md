---
title: "Application with full archive support"
date: 2014-02-17
forum: General Help
---

### Post by dave2001 on 2014-02-17
I normally have a great bit of sympathy with open source developers. i understand it takes time to reverse engineer code, or write your own to run on new hardware with little help from manufacturers.. . but sometimes there's no good reason for lack of functionality, and the level of unnecessary obfuscation seems to increase for no particular reason.

I'm looking for something very simple... a gui applicaiton that will integrate with kde and archive files into some of the more common types: zip, 7zip, tar, etc. I would like the full functionality of each type of archive (for expample: I want the ability to password protect a 7zip archive)

the default kde archive tool, ark.. doesn't do this.

Peazip is a wonderful program, they even package it up in a nice little deb for ubuntu. Worked great on all counts, until 13.10 when the ia32-libs are no longer in the repos for 64 bit systems to run 32 bit applicaitons... so i get sent down an hour-long rabbit-hole of forum posts and info pages about multi-arch support and other crap I could really care less about. I mean really... 

I'd LOVE some simple how-to kind of explanation on getting peazip or other 32 bit apps to function on my 64 bit kde-unbuntu install. OR I'd be perfectly happy with another archive program which meets all the requirements I outlined above.

Any help much appreciated.

---

### Post by mc4man on 2014-02-18
This may or may not work out for you, tested on Ubuntu 14.04, seems ok.
If inclined - for either the **qt**  .deb or  portable version - 
[http://peazip.sourceforge.net/peazip-linux.html](http://peazip.sourceforge.net/peazip-linux.html)
```
sudo apt-get install libc6:i386 p11-kit:i386 libp11-kit-gnome-keyring:i386 libqt4pas5:i386 
```

If going with the .deb then additionally - (note these gtk2 are somehow used by the **qt** .deb, the portable may benefit from the murrine package
```
sudo apt-get install libgtk2.0-0:i386  gtk2-engines-murrine:i386
```

Then for the .deb just install, dpkg -i is fine, ex. 
> sudo dpkg -i  /home/doug/Downloads/peazip_5.2.1.LINUX.Qt-2_i386.deb
screen

---

