---
title: "Default paper size in Evolution"
date: 2007-04-26
forum: General Help
---

### Post by bnebb on 2007-04-26
Just got started again with ubuntu feisty.  Everything seems to work except for evolution printing.
I've already searched the forum for my problem and can't seem to find it.  I may have overlooked something though.
I've got an HP Laserjet 4 Plus.  It is networked and using the hpijs driver.  Printer and driver is set up to use letter size paper.  I print fine from everything, it seems, except evolution.  When I try to print a message, it makes the printer default to A4 size paper.  I've already changed /etc/papersize to letter so this shouldn't be the problem.  I can't find any way in evolution to change the default printer paper size.  All the other applications do it right; print to letter size paper.

Any help would be most appreciated.

Bnebb

---

### Post by Macchi on 2007-05-01
I have the same problem, except that here in Sweden we use A4 instead of LETTER. 

a) One of the problems that Evolution may not follow the system-wide printer settings.
 
b) Another face of the same problem is that (at least) HP LaserJet 4 or HP LaserJet 2700 gets stuck at "manual feed letter page" or similar message. 

We could not yet identify exaclty where is the problem. There must be some conflicting or forgotten settings along the way in Gnome, CUPS, Hplip, Evolution, etc with combinations that remained untested for A4 and/or Letter paper sizes.

---

### Post by fanatik on 2007-05-01
have a look at:

$ cat /etc/papersize

and see if thats set incorrectly.

---

### Post by a50sn95 on 2007-05-06
Same here.
Fixed /etc/papersize to A4. 
Removed an re-installed printer. (Dell 3110 Color Laser)
Firefox, OO, everything else prints properly.
Evolution still want A4. 
Came from Fedora/Centos, since Dell is likely to start offering Ubuntu, I wanted to try Ubuntu. 
I LIKE Ubuntu, but this is kind of an irritant.
Based on my searches here in the forums, it's been an issue for a while.
ANYONE have a solution. (Besides installing Thunderbird?)
Dennis

---

### Post by a50sn95 on 2007-05-06
Oh, and the one time I stuck A4 in the MPF , it printed out 10 copies. I didn't specify more, so what gives....

---

### Post by notiones on 2007-09-06
Has no one been able to find a solution to this? It is driving me crazy. I just switched from Fedora 7 to Ubuntu 7.04 and this wasn't a problem in Fedora. I'll keep looking and post a solution when I find it.

---

### Post by oldtimer_3478 on 2007-12-18
I've been have problems too.   The only thing I could find in the forums was to set the paper size before starting up evolution and it would work.  So I put a spare drive in my computer and did a fresh install of 7.10.  I configured the printer, started up Evolution, and guess what?  It worked.  In my case, it printed US Letter as I wanted.

So I started with the fresh install and installed all the software I need and got everything configured.
Now today I click on print and Evolution is trying to print A4 again.  I haven't printed in a while, but I have not changed any print settings.  What is up with that?

Why is printing from evolution so broken?  Can anyone find a fix?

---

### Post by oldtimer_3478 on 2007-12-21
OK, this was driving me crazy so I started poking around in the source.

Evolution completely ignores all paper size settings.   It does not care what you have set your printers to.   All it cares about is your locale.  If your locale is en_CA, en_US, es_PR, or es_US you get Letter paper.  Any other locale and you get A4 paper.

Use the command 'locale' to check your locale.  The LC_PAPER is the one that matters. 

To change your paper size in evolution, but leave the rest of your locale alone, edit /etc/environment and add something like:

```
LC_PAPER="en_US"
```

to get Letter paper, or

```
LC_PAPER="POSIX"
```

to get A4.

Hope that helps!

Dan D Niles

---

