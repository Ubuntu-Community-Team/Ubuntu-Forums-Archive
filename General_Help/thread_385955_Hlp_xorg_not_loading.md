---
title: "Hlp xorg not loading"
date: 2007-03-16
forum: General Help
---

### Post by f1renz on 2007-03-16
Hi:

I have a dual boot xp/ubuntu on my PC (2.3GHz, 3 hard drives--ubuntu on first one, Nvidia graphics card). I've been using Ubuntu now for 3 months without any major problem. However now my system doesn't boot.

I can chose partitions from the grub loader. When I choose the Ubuntu partition I get a message that says "Cannot load xorg server(graphical interface)" Tried going in with recovery mode to see if the nvidia drivers were the problem or the /etc/x11/xorg.conf file needed fixing but the system won't log me on as root!!! it keeps saying incorrect password??

On loading the windows partition ------ it boots and takes me to the desktop but after a while
the system crashes and comes up with an error message on a blue screen.

"A problem has been detected and windows has been shut down to protect damage to your computer.  If this is the 1st time you've seen this stop error screen, restart your computer. If this screen appears again, follow these steps:.................."
...............and goes on to list advice 

I've restarted twice witout any luck. What i'm trying to find out is if this is a problem with ubuntu or is it a hardware problem?

---

### Post by chewearn on 2007-03-16
I used to have an old PC, which got clogged up with dust easily.  Windows will lock-up or suddenly reboot at least one a year.  I have to vacuum all the dust, unplug the graphics card and clean up the AGP metal contacts.  Then, it will work again for another year.

 :lolflag:

---

### Post by dannyboy79 on 2007-03-16
if your computer went thru an upgrade and it updated its kernel than you will have to reinstall the nvidia driver no matter. envy is an awesome script to do this. to log into the recovery mode, you don't need to be root, you can log in as yourself and again use sudo as normal.

try this out once you have logged in:

```
sudo aptitude install wget
```

```
sudo wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb
``` 

```
sudo dpkg -i envy_0.9.1-0ubuntu3_all.deb
```

```
envy
```

 you need to make sure you run the dpkg -i command from whatever folder the envy deb file was downloaded to, it should be your home directory, but if it's not, you can do

```
sudo find / -name envy_0.9.1-0ubuntu3_all.deb
```

to find it, once you find it, you just "cd" into that directory and run the dpkg command. that's it. then you shouuld be able to log into your x-server again with nvidia support

as far as winbloz, sounds like a hardware issue. if ubuntu doesn't work either after the above steps, than I would check your ram, one stick at a time. also, are your power supply rails ok?

---

### Post by f1renz on 2007-03-16
Thanks for the quick advice.

It seems that nvidia scripts are downloaded but i can't dpkg -i command it.
It keeps telling me that there is an error processing the data.

Is there another way around loading nvidia drivers ------------reconfiguring the xorg config file maybe??

---

### Post by dannyboy79 on 2007-03-16
do you have debconf installed?

sudo aptitude install debconf

sudo aptitude install dpkg

dpkg --clean-avail

what about just double-cliking on it thru nautlius? Ubuntu should open it with Gdebi, it's a graphical installer for deb files

---

### Post by f1renz on 2007-03-17
sorry ...............can't get up any garphical interface at all. i'm working from a command terminal in recovery mode.

Maybe the grub boot loader is broken as well???

---

### Post by f1renz on 2007-03-21
Ok finally managed to fix this problem........................I hope!!

Removed, cleaned and refitted all memory and drive parts in the tower.
This got Windows running again.

Over the course of 4 days tried all sorts of things to get the linux partition up again.
What finally did it was getting the nvidia drivers installed correctly from the albertomilone site.
Not quite sure why it didn't work the first time. What made it even more frustrating was that I had to work from a rescue mode terminal, couldn't get a graphical interface up, couldn't log in from the recovery mode and kept getting error messages whenever I tried to install anything. 

Thanks to those who provided advice!!

---

