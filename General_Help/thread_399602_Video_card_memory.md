---
title: "Video card memory"
date: 2007-04-02
forum: General Help
---

### Post by ggaaron on 2007-04-02
Hi,
I have an integrated intel video card in my laptop - intel 945 - that shares memory with system memory, by default it uses 8 MB of it, but it dynamicaly can allocate up to 128 MB. At least it is what I've found about it. Is there any way to tell linux to have less avilable memory and make video card use 128MB of memory all the time. In theory the memory is dynamicaly allocated, but I have never seen it actualy happening. And with only 8MB the video card can't really run well. ="( I'm using ubuntu 6.10. Thank's in advance.

Aaron

---

### Post by RedSquirrel on 2007-04-02
> **ggaaron said:**
> Hi,
I have an integrated intel video card in my laptop - intel 945 - that shares memory with system memory, by default it uses 8 MB of it, but it dynamicaly can allocate up to 128 MB. At least it is what I've found about it. Is there any way to tell linux to have less avilable memory and make video card use 128MB of memory all the time. In theory the memory is dynamicaly allocated, but I have never seen it actualy happening. And with only 8MB the video card can't really run well. ="( I'm using ubuntu 6.10. Thank's in advance.

Aaron

It's one of the options when you reconfigure the Xserver. 

Log out.

At the login window, hit Ctrl-Alt-F2. 

Login.

Type

```
 sudo /etc/init.d/gdm stop
```and press Enter.

Type:

```
sudo dpkg-reconfigure xserver-xorg
```and press Enter. You can accept the default answers in most cases, except where you add the amount of memory to use.

Type

```
 sudo /etc/init.d/gdm start
```and press Enter. That should take you back to the login window.

---

### Post by ggaaron on 2007-04-03
Yes, I've reconfigured xorg before to get resolutions I want to work, and I've set the memory as it should be, but does it really work? When I run a system monitor the free memory and the used one sums up to more or less the amount of memory I have, maybe video card memory is somewhere there added already, but I think there should be some improval in performance, as I've set about 16 times more video card memory than there was on start, and there was none (yes, I know that glxgears is not a benchmark). Thanks for reply, really good guide, I wish I had it when I first reconfigured xorg... I only hope, that my question isn't so stupid...

---

### Post by RedSquirrel on 2007-04-04
No, your question isn't stupid at all. I'm not sure if you can have it set aside 128 MB of RAM for video *all the time*. I'm kind of thinking that you cannot do that.

I would have a look at the manual page of i810:

```
man i810
```It says there:

> It is advisable to check the Xorg log file to check if any features have been [COLOR=Red]disabled[/COLOR] because of insufficient video memory.
So if you haven't done so already, you might have a look in /var/log/Xorg.0.log and see if anything is failing or disabled.

I'm not sure if it would help, but there is a question in the configuration of xserver that asks about using the kernel framebuffer. I'm not certain, but I think you have to say yes to this.

There are some [bugs]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bugs") with the i810 driver. 

[Here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/61306") is one discussion where they mention glxgears.

Perhaps someone with more detailed knowledge of configuring the i810 can jump into this thread... or (of course) you can try Google. There's no shortage of discussion about the i810. :)

---

### Post by dbbolton on 2007-04-06
i have a related question, but i don't think it warrants starting a new thread.

my laptop has an ati radeon xpress 200m. in total, my computer has 512MB of memory, but from my understanding, about 128MB is dedicated to the video card. so, whenever i look at the system monitor (or task manager on windows) it says that i have 376MB of memory.

how can i tell if the memory that belongs to the video card is being used ?

---

