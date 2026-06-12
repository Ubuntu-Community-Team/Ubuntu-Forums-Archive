---
title: "What can I do to fix this?"
date: 2018-05-24
forum: General Help
---

### Post by Lou Reed on 2018-05-24
I have been usug Linux especially, Ubuntu, for a long time. Sometimes I leave it for months and come back and things have changed. This is one of those times. 

I installed Ubuntu on a Lenovo laptop using Oracle  Virtualbox and everything was fine. I stopped woring on it about a week ago and then came back. 

The operation was quite sluggish now. This persisted no matter how many times I rebboted.

It was very frustrating.  I was on the verge of reinstalling Ubuntu 16.04 (64 bit), because no matter what I tried the operation of
Ubuntu was very slow.

Then one moment a message popped up stating that it appears that an Ubuntu script has stalled. Below this statement were some options to let the script continue to run or terminate the script.Nothing happend if I clicked on them.  

So by rebooting, I finally was able to shake something loose and the Ubuntu OS starting operatig at the normal speed again.


Now my question is this:

When you get such as message how can you see what programs are running Ubuntu and which could be causing them to slowdown. 

I know how to do this in Windows 10, (Ctrl-Alt-Del) and find the thread or threads causing the clogging. 
In Ubuntu what do I do? This happens all too often and it makes using Ubuntu 16.04, 64 bit occasionally very frustating.

Any help much appreciated.

Respectfully,

ErnestTBass

---

### Post by HermanAB on 2018-05-24
Howdy, with Linux, there is no reason to poke around in the dark like a back bear stumbling in a coal mine at night.  You can see the running processes with 'top' and then you can kill processor sapping tasks with 'kill -9 PID'.  Similarly, you can view speed sapping networked processes with 'ntop'.

As an aside, I would not run the Gnome desktop in a virtual machine, since it is very graphics intensive.  The XFCE desktop is better suited for that.  You can install XFCE with 'apt install xfce4' and then select either xfce or gnome when you log in.

---

### Post by Lou Reed on 2018-05-24
Thanks for your help I will try what you said. How do I run XFCE? I am hopping it will solve some problems with running Ubuntu in Oracle Virtual Box?

Respectfully,

ErnestTBass

---

### Post by PaulW2U on 2018-05-25
> **James_M._Yunker said:**
> Thanks for your help I will try what you said. How do I run XFCE? 
In a terminal run the command that HermanAB suggested:
```
sudo apt install xfce4
```
Then reboot and select Xfce at login rather than GNOME.

Alternatively you can install [Xubuntu]("https://xubuntu.org/") which uses the [Xfce]("https://xfce.org/") desktop by default. That would be my personal preference as I don't like mixing desktop environments. Obviously by using Virtualbox you have plenty of scope to experiment in order to find out what works best for you especially with regards to the various Ubuntu [flavours]("https://wiki.ubuntu.com/UbuntuFlavors").

---

