---
title: "Limewire set-up"
date: 2006-11-17
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-17
Along time ago I had gotten Limewire for my windows machine and now I want it with Edgy. I have downloaded the file (zip), but I can **NEVER** get a zip file to install unless I have had copy & paste instructions. Can some one help me please? Sally ;)

---

### Post by taurus on 2006-11-17
Instead of using LimeWire, why not use Frostwire because they're both the same except Frostwire is open source.  You can use automatix2 to install it or you can download the Ubuntu/Debian version from [http://www.frostwire.com/](http://www.frostwire.com/).

p.s.  Make sure you have java running on your machine first before you use limewire or frostwire.

---

### Post by earobinson on 2006-11-17
searched froums for: limewire
found: [http://www.ubuntuforums.org/showthread.php?t=278134&highlight=limewire](http://www.ubuntuforums.org/showthread.php?t=278134&highlight=limewire)

---

### Post by IusedTObeSOMEONEelse on 2006-11-17
Thanks for replies to the Both of you. Hi taurus ;)  I do have Frostwire but it seems to put my CPU at 100% so I thought I would see if Limewire did the same. And way before I used Linux, I had **PAID** for a lifetime - 360SharePro - (limewire). I just don't want to burn up my machine. Lordy, Lordy, I have installed Edgy 6 times this week over other fiasco's (w/Feisty) so my patiants are at a minimum. Will Limewire cause the 100% CPU as well?

---

### Post by earobinson on 2006-11-17
I doubt anyone will be able to answer this question, it shouldn't but then nor should Frostwire

---

### Post by taurus on 2006-11-17
Frostwire doesn't cause my CPU to jump to 100% when I run it.  In fact, azureus takes up more system resources on my machine than frostwire.  And since I don't use limewire, I can't say for sure.  I guess you just have to install it and see it yourself then!  ;)

---

### Post by IusedTObeSOMEONEelse on 2006-11-17
I will, then!

---

### Post by earobinson on 2006-11-17
also check out this: [http://www.ubuntuforums.org/showthread.php?t=278134&highlight=limewire](http://www.ubuntuforums.org/showthread.php?t=278134&highlight=limewire)

---

### Post by strabes on 2006-11-17
Why are you using a .zip to install limewire? Why don't you just use the rpm they provide on their website and then convert it to a deb with alien? 

[http://www.limewire.com/LimeWireSoftLinux](http://www.limewire.com/LimeWireSoftLinux)

Oh yeah by the way limewire is open source [www.limewire.org](www.limewire.org)

---

### Post by earobinson on 2006-11-20
> **strabes said:**
> Why are you using a .zip to install limewire? Why don't you just use the rpm they provide on their website and then convert it to a deb with alien? 

[http://www.limewire.com/LimeWireSoftLinux](http://www.limewire.com/LimeWireSoftLinux)

Oh yeah by the way limewire is open source [www.limewire.org](www.limewire.org)
It could be done either way whichever the user prefers alian will not always work however, maybe this is one of those cases

---

### Post by thistlebrae on 2006-11-21
Hi All-

I have installed both Limwire and Frostwire on my Edgy box.  Both now appear in the Internet Application list.  When I select them..they never launch.  Any ideas as to what the problem is?

In case you suspect java...here is what I get when I run Java -version from a console:
[I]
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)[/I]


and here are the files that I installed for each app:

limewire-free_4.12.6-1_i386.deb
FrostWire-4.10.9-2.i586.deb

Any help would be MOST appreciated...I don't want to have to go back to Windows....Heaven FORBID!

---

### Post by taurus on 2006-11-21
Try to run them from a terminal to see exactly what the error messages are, Applications -> Accessories -> Terminal.

```
limewire
frostwire
```

---

### Post by thistlebrae on 2006-11-21
Thanks for your reply

Here is what I got:

[I]tmiller@tmiller-thinkpad:~$ limewire
bash: limewire: command not found
tmiller@tmiller-thinkpad:~$ frostwire
runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")
tmiller@tmiller-thinkpad:~$[/I] 

In the interim I did find Gtk_Gnutella and it seems to offer the same capability...but I am still curious about the first two.

Thanks..

---

### Post by taurus on 2006-11-21
For limewire, see if you can find it anywhere on your system.

```
sudo find / -name limewire -print
```
For frostwire, paste your /usr/bin/frostwire here then.  I think the problem is the "sh" in the last line of it...

```
cat /usr/bin/frostwire
```

---

### Post by thistlebrae on 2006-11-21
> **taurus said:**
> For limewire, see if you can find it anywhere on your system.

```
sudo find / -name limewire -print
```


here is the output from that:

/home/tmiller/LimeWire/usr/bin/limewire

For frostwire, paste your /usr/bin/frostwire here then.  I think the problem is the "sh" in the last line of it...

```
cat /usr/bin/frostwire
```

and here is the result of that:

#!/bin/bash
cd /usr/lib/frostwire
sh runFrost.sh


I appreciate your help....

---

### Post by taurus on 2006-11-21
> **thistlebrae said:**
> and here is the result of that:

#!/bin/bash
cd /usr/lib/frostwire
sh runFrost.sh

I appreciate your help....
Change the last line from

```
sh runFrost.sh
```
to 

```
bash runFrost.sh
```
p.s.

```
gksudo gedit /usr/bin/frostwire
```

---

