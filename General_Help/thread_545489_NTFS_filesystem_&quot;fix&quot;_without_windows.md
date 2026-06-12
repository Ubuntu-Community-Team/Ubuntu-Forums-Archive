---
title: "NTFS filesystem &quot;fix&quot; without windows"
date: 2007-09-07
forum: General Help
---

### Post by Leon945 on 2007-09-07
Hello people,
I have a problem...

I have an external HD with NTFS filesystem...
I have installed ntfs-3g so i can read/write

My problem is, apprently at some point there was a "bad" shutdown of the drive... and now it tells me i need to use ntfsfix to be able to mount it.

so.. ok..
i do:

```
ntfsfix /dev/sda4
```

And NOW it tells me i need to reboot to windows TWICE to get it to work...

I DONT have windows installed on my PC, but i DO need the external HD to be in NTFS because i sometimes use it at work.

Is there a way to fix this WITHOUT windows?

I tried using the "force" method, which worked... but i don't know what problems could be caused by using a "dirty" partition, plus i cant get it to mount automatically on boot.

What do you guys recommend?

---

### Post by merlinus on 2007-09-07
Best bet is to put it in a machine with windows, and let that os do its thing.

You can try ringing a neighbor's doorbell.   :)

Mounting a "dirty" volume may easily cause problems with your data, as will force mounting it.

 ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk. It only repairs  some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

-merlin

---

### Post by Leon945 on 2007-09-07
dang..
i didnt wanna have to do that..

but oh well..
thank you for your help! :D

---

### Post by merlinus on 2007-09-07
You are most welcome.  BTW, be sure to unmount the external properly from windows before unplugging it, or you will be back on the merry-go-round again.

:)

-merlin

---

### Post by szaka on 2007-09-07
You're using a very old release of ntfs-3g. Just upgrade to the latest version (currently 1.826) and these problems should be gone.

---

### Post by Leon945 on 2007-09-07
hmmmm...
actually
first it got screwed up before installing ntfs-3g

i installed ntfs-3g from the official ubuntu repos..
i'll check the version later...

thank you for the info..

---

### Post by merlinus on 2007-09-07
1.328 is the one in the ubuntu repos.

-merlin

---

### Post by merlinus on 2007-09-07
> **szaka said:**
> You're using a very old release of ntfs-3g. Just upgrade to the latest version (currently 1.826) and these problems should be gone.

I downloaded the .tgz.  To where should it be extracted, since there is one in /usr/bin with a different name (ntfs-3g)?  This one is ntfs-3g-1.826.

Many thanks!

-merlin

---

### Post by merlinus on 2007-09-07
I extracted the folder to /home, navigated there, and opened a terminal.

./configure was successful, but make returned this:

 make
make: *** No targets specified and no makefile found.  Stop.

-merlin

---

### Post by szaka on 2007-09-08
This means that './configure' was not successful. You probably don't have the development tools and libraries installed.

---

### Post by s-lime on 2007-09-10
I have the same problem, 

force attribute does not work,
nor does the newest ntfs-3g. I installed the newest ntfs-3g folowing the istructions here: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Is that OK?

---

### Post by szaka on 2007-09-10
I doubt you have the latest ntfs-3g release which is 1.826 currently: [http://ntfs-3g.org/releases.html](http://ntfs-3g.org/releases.html)

You can see what version you have by typing **ntfs-3g** on the command line.

---

### Post by s-lime on 2007-09-10
I have 1.328. I know that it is late, but I followed instructions ([http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)) and still the same...

Please help...

---

### Post by s-lime on 2007-09-10
How can I install the newest version of ntfs-3g... OMG I would be glad if it worked.

Please :)

---

### Post by s-lime on 2007-09-10
Please... I'm almost crying... Everyting is going wrong...  First windows disk failure, and i now i can't read slave NTFS????

Please just tell me how to install the newest version. I tried everything, and it is just damn 1.3!

Please...

---

### Post by s-lime on 2007-09-10
sudo apt-get install ntfs-3g

that will install only 1.3? Am I right?

---

### Post by merlinus on 2007-09-10
version 1.328.  I tried installing via the .tgz file from their website, but could not get it to work (something about missing libraries and such).

Too bad they do not simply have a .deb that will install easily on ubuntu.

But I am not experiencing any problems with the version currently in the repos.

---

### Post by s-lime on 2007-09-11
I managed it.

But to tell you, 1.3 is not good enough for me, because it didn't clean windows log files.

---

### Post by And1945 on 2007-09-20
> **s-lime said:**
> I managed it.

But to tell you, 1.3 is not good enough for me, because it didn't clean windows log files.

It didnt on my dads laptop either.

I plugged it into my own windows machine, but it takes a damn war this thing. NTFS fix gave me some errors.

---

### Post by And1945 on 2007-09-20
Sorry for double post, but this is not so relevant to my prior post.

I tried to make a safe removal of the usb unit in windows and that was all ubuntu wanted... scandisk and whatever wasnt what it was looking for.

---

