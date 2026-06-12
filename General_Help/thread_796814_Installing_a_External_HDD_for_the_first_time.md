---
title: "Installing a External HDD for the first time"
date: 2008-05-16
forum: General Help
---

### Post by carl99fan on 2008-05-16
Good evening Ubuntu pros, I am installing a:
Seagate FreeAgent Pro 320gb usb2.0/eSATA External Hard drive.
When I plug it in, I get this message:
[IMG]http://i198.photobucket.com/albums/aa208/carl99fanipo/Screenshot.png[/IMG]

I don't understand what to do. This hard drive will be used on Ubuntu only.
Any help would be appreciated...

---

### Post by carl99fan on 2008-05-16
OK I have looked all around, still no clue what I'm doing here.
:confused:

---

### Post by Redrazor39 on 2008-05-16
Could you move that window more right of the desktop and post that? That would help a lot.

Also, I've heard of someone else having this problem too. I wonder if there's a help/error archive for ubuntu?

---

### Post by carl99fan on 2008-05-16
If I let you see her face will you help me set up the hard drive? lol:)

---

### Post by carl99fan on 2008-05-16
OK People I REALLY want to get this thing hooked up tonight.
I hope this helps you help me!

[IMG]http://i198.photobucket.com/albums/aa208/carl99fanipo/Screenshot-1.png[/IMG]
:lolflag:

---

### Post by stoneage on 2008-05-16
It is a well-known issue with the freeagent series. Search the forum, there are many people with the same trouble. After a set time the drive spins down and linux then fails to recognise it(I don't know the tech stuff, but the spindown is the problem). Workarounds include downloading the windows software and turning off the spindown function, or running a shell script to keep 'nudging' the drive to keep it awake. I believe there is a workaround  to allow restarting the drive after it spins down, if you care to search for it(it is on the forum somewhere). Here are some fixes, please do research:-

[http://ubuntuforums.org/showthread.php?t=607518&highlight=seagate+freeagent](http://ubuntuforums.org/showthread.php?t=607518&highlight=seagate+freeagent)

[http://alienghic.livejournal.com/382903.html](http://alienghic.livejournal.com/382903.html)

[http://news.softpedia.com/news/Workaround-Released-for-Seagate-Free-Agent-73528.shtml](http://news.softpedia.com/news/Workaround-Released-for-Seagate-Free-Agent-73528.shtml)

[http://ubuntuforums.org/showthread.php?t=494673&highlight=seagate+freeagent](http://ubuntuforums.org/showthread.php?t=494673&highlight=seagate+freeagent)

---

### Post by stoneage on 2008-05-16
There is another thread somewhere dealing with the 'force' commands in Choice 2 of the error message, but I don't remember exactly where, and am unable to find it at the moment. Try searching something like 'seagate freeagent' and 'force'. Hope you get it working soon. 

Good luck!

---

### Post by carl99fan on 2008-05-16
> **stoneage said:**
> There is another thread somewhere dealing with the 'force' commands in Choice 2 of the error message, but I don't remember exactly where, and am unable to find it at the moment. Try searching something like 'seagate freeagent' and 'force'. Hope you get it working soon. 

Good luck!

Thanks again, It figures I would find this thing on sale for 59.99 and I jumped on it before researching it at all. Very uncharacteristic of me. 
You have given me a LOT to work with and read. Just a small challenge. I will be keeping my "Seagate FreeAgentPro", but I will not be purchasing any more products from These guys... no way. 

I have gone Ubuntu, and I will NEVER go back.

---

### Post by carl99fan on 2008-05-17
Well it seems there is some kind of program on there from Windows right out of the box.
I am not interested in this drive EVER working on windows.
Can't I just reformat it or something.
There has to be a way to make this work without finding a friend with Windows to fix it for me! lol

---

### Post by stoneage on 2008-05-17
Don't be too down on Seagate, as far as I know this only affects the Freeagent, it doesn't lower the quality of their other hardware. Though I know how you must feel. I believe others have had success by reformatting to ext3. Here is some more info, I hope things work out.

[http://ubuntuforums.org/showthread.php?t=679228&highlight=reformat+freeagent](http://ubuntuforums.org/showthread.php?t=679228&highlight=reformat+freeagent)

[http://ubuntuforums.org/showthread.php?t=461042&highlight=reformat+freeagent](http://ubuntuforums.org/showthread.php?t=461042&highlight=reformat+freeagent)

[http://ubuntuforums.org/showthread.php?t=738433&highlight=reformat+freeagent](http://ubuntuforums.org/showthread.php?t=738433&highlight=reformat+freeagent)

[http://ubuntuforums.org/showthread.php?t=718664&highlight=reformat+freeagent](http://ubuntuforums.org/showthread.php?t=718664&highlight=reformat+freeagent)

[http://ubuntuforums.org/showthread.php?t=701113&highlight=pettertorp](http://ubuntuforums.org/showthread.php?t=701113&highlight=pettertorp)

---

### Post by carl99fan on 2008-05-24
OK I have gparted on my computer now....
I tried to reformat it but it only sees 299gb.

Is there a way, I can wipe it clean and reformat it just for use on my Ubuntu computer?

There is NOTHING on my drive that I want.
I just want to reformat the thing. 
I have read and read. Nothing seems to be working very well.

---

### Post by carl99fan on 2008-05-24
It mounts now, I think when I plug it in, [disk-file browser] opens, it says lost and found!?

And it says I have 280gb of space left. I can not put anything on the drive still.

seems I am getting closer!
[IMG]http://i198.photobucket.com/albums/aa208/carl99fanipo/ubuntuhelp.png[/IMG]

---

### Post by ssharps711 on 2008-06-05
Bump. same thing.

---

### Post by stoneage on 2008-06-25
I don't know much about system admin, but possibly you need to change permissions. Usually something like 'sudo chmod 700 /pathtofile/filename'.

Not sure how to apply it to a whole drive though.

---

