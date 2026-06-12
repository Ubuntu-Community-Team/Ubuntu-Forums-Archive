---
title: "Moving home: Device busy"
date: 2013-06-19
forum: General Help
---

### Post by makamba on 2013-06-19
Hi,

Because I had bad sectors in my home drive I decided to move everything to another partition, as explained in [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving). At the end I had to perform a
```
cd / && sudo mv /home /old_home && sudo mkdir /home
```
This resulted in something like 'device busy'. 

I logged out, got to a terminal and tried to perform what was described in [http://askubuntu.com/questions/245925/mv-cannot-move-home-to-old-home-device-or-resource-busy](http://askubuntu.com/questions/245925/mv-cannot-move-home-to-old-home-device-or-resource-busy). But I got the same result. 

What do I need to do to be able to move my old home to old_home?

TIA,
Makamba

---

### Post by HermanAB on 2013-06-19
You cannot change a partition that is in use. Boot with a live CD.

---

### Post by makamba on 2013-06-19
Thanks for the reply. I'm already running Live CD. I'm unclear how to progress further.

When I open the nautilus browser for the home folder, and go to the partition containing the root I cannot rename home. I do not know how to get to the root partition using a terminal.

Edit:
I might have found it using [http://askubuntu.com/questions/78691/recovering-user-files-with-a-live-cd](http://askubuntu.com/questions/78691/recovering-user-files-with-a-live-cd)
> If you are told that you lack permissions to access any of the files,  then you can get around this by using a Nautilus (i.e., file browser)  window running as root. To do that, press Alt+F2, type in gksu nautilus, and press enter.

Let's see if that helped.

---

