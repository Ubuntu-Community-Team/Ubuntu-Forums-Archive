---
title: "errors when trying to install Wine"
date: 2017-10-15
forum: General Help
---

### Post by jacko777 on 2017-10-15
rod@rod:~$ sudo apt install --reinstall ubuntu-software
[sudo] password for rod: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rod@rod:~$ 

This pops up often, I have tried various "fixes" but nothing seems to work.  I have had a lot of errors before and figured I broke it.. So I reinstalled Ubuntu 16.04.2  and still have problems trying to do things.
Another example:  When I followed the Wine installation guide, at the end of the download process, instead of getting another screen to do things,  it came up with a "Microsoft list of conditions and had an <ok> at the bottom.
Nothing I could do would accept the agreement so it could get on and install the end part of Wine.
I tried just closing the Terminal, but got a warning that a current file was running and it would not finish installing the program.
I waited overnight, next morning, the same thing.
I gave it away as a bad deal.

Has anyone struck this problem.? If so, I would love to hear of a solution.

Regards,

---

### Post by Dennis N on 2017-10-15
> Nothing I could do would accept the agreement so it could get on and install the end part of Wine.
You probably need to use the keyboard to get to the OK at the bottom. The TAB key should move you to it. Then press ENTER to accept. Mouse won't work.
The pop up about the lock means that another package manager is open and using your software sources. Only one manager at a time is allowed to do this.

---

### Post by jacko777 on 2017-10-16
Hello Dennis N  thank you for your input, I'll try the tab key and let you know back here how it goes.
The other thing seems to be always doing something else, right from boot.  I have no idea what it is, but it is certainly a nuisance.

Regards,
Rod

---

### Post by jacko777 on 2017-10-16
Hello again Dennis N well your solution worked well.  I now have Wine installed , all I need now is to fiddle with it so that it runs my "Good Solitaire" program, which is a windows 7 and probably higher program.
I have played this game for a few years now and have almost fretted when I was unable to use it.

Now 1555Hours here, and hopefully by tonight I might have it going again.

Thank you Dennis,
Rod

---

### Post by mörgæs on 2017-10-16
I hope you also need Wine for other applications, else it was a long journey. Buntu has several Solitaire games available.

---

### Post by jacko777 on 2017-10-16
Hello morgaes, No other use for it.
This worked so well before my hard drive died, reloaded everything but I still cannot figure out why "Pretty Good Solitaire" will not run.
I suppose I will have to reload Wine again.   Seems everything I do gives an error message of some kind.  Or simply does not work....:(

---

### Post by oldos2er on 2017-10-16
Thread moved to *General Help*

---

