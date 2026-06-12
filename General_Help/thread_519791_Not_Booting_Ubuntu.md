---
title: "Not Booting Ubuntu"
date: 2007-08-07
forum: General Help
---

### Post by JustFlash on 2007-08-07
Hi,
I installed Wubi today.
I am assuming I did it successfully as I got to the point where it asks me to reboot the system.
I did, and it got to the screen that gives the option of booting ubuntu or windows.
I chose ubuntu and on it went. It started installing other things so I left to go watch some TV while waiting.
I checked on it every several minutes.
When I checked to see if it was done (maybe 45m later) I came back to my windows login screen (I was thinking wow ubuntu looks a lot like windows).
I thought ok I'll restart and see what happens ..
I restarted the computer and there is no option for me to boot ubuntu or windows .. it just boots windows like normal..

Help?

thanks in advanced.

---

### Post by logos34 on 2007-08-07
In a windows explorer bar, type this in the address bar:

C: \boot.ini

Copy and post it.

---

### Post by JustFlash on 2007-08-07
I'm a noob to this and don't know what a 'windows explorer bar' is >_<
but I did try to run "C:\boot.ini" and this is what popped up in a notepad

> [boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
c:\wubildr.mbr="Ubuntu"


---

### Post by logos34 on 2007-08-07
sorry, typo, meant browser not bar.

boot.ini looks fine...i was thinking maybe the timeout was 0 or there was no wubildr line

Do you see a wubildr.mbr file in C:\ ?

---

### Post by JustFlash on 2007-08-07
> **logos34 said:**
> 
Do you see a wubildr.mbr file in C:\ ?

Yes.

---

### Post by logos34 on 2007-08-07
You could try making Ubuntu the default OS in boot.ini.

(See '**How do I make Ubuntu the default boot option**?' in the [WubiGuide]("https://wiki.ubuntu.com/WubiGuide#head-7e1711f45843d41aff1ec27f06cdf8aca70cb88c").)

---

### Post by JustFlash on 2007-08-07
So I restarted my computer (again)
and this time it worked! .. the ubuntu/windows option showed and im on ubuntu right now.

Except I have another problem .. It doesn't use my whole moniter .. its about 3/4 of an inch to the left and half a centimeter down.

 If I can't find a topic on I'll create a new topic with this new problem..

THanks!


EDIT: I fixed that problem as well simply by changing the resolution and then changing it back.


everythings working great ..

---

### Post by logos34 on 2007-08-07
ok, so it looks like it was just a matter of rebooting again.  

Have fun

---

### Post by movienut50 on 2007-08-11
Can you list what is in your wubildr.mbr file for me. I am having a problem booting also and I think my is correct. thanks

---

### Post by movienut50 on 2007-08-11
Never mind I found my problem

---

