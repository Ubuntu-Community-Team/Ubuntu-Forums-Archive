---
title: "Ubuntu 14.04 64-bit keeps locking up"
date: 2014-10-22
forum: General Help
---

### Post by cobradabest on 2014-10-22
I've recently installed Ubuntu (14.04) on a PackerdBell Easynote ENME69BMP, and I'm having an issue with it. It works fine at first, in fact it's pretty fast and responsive, but after a while, maybe 5 or 10 minutes, it starts locking up, and everything that is open stops responding, I can move the mouse, but that's about it. I usually have to press the power button for it to respond again, but when I do that, it starts to shut down, as expected.

I looked up nthis problem, and it seems like a common problem, usually with PCs with Nvidia cards, but I don't even know what graphics card, if any, my laptop uses, and looking up the laptop online doesn't help.

So what do I do?

---

### Post by davit2 on 2014-10-22
Hi,
Try 12.04 32bit

---

### Post by cobradabest on 2014-10-22
> **davit2 said:**
> Hi,
Try 12.04 32bit

Well, alright, I'll do it when I have to to download it, but it says it uses a 64-bit OS, and I'm assuming by that, that it's a 64-bit PC, so what effect would using a 32-bit OS it do?

---

### Post by ibjsb4 on 2014-10-22
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:
```
top
```
Right click on the title bar and check 'Always on top'.

Now go about using your laptop and see if anything is using up your resources (cpu and memory).

---

### Post by fantab on 2014-10-22
Have you checked your PC's Power Settings?
There will be a screen lock/blank option... set it to 'never'... If the auto setting is to 'suspend' after locking/blanking then change it to do 'nothing' or something on those lines...
If you have screensaver then also set it to 'never'.
(I am not on Uubntu right now, so excuse me if I am not particular).

---

### Post by cobradabest on 2014-10-25
> **ibjsb4 said:**
> [Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:/
```
top
```
Right click on the title bar and check 'Always on top'.

Now go about using your laptop and see if anything is using up your resources (cpu and memory).
Okay, I've been doing this, and to be honest, I don't see anything unusual.

> **fantab said:**
> Have you checked your PC's Power Settings?
There will be a screen lock/blank option... set it to 'never'... If the auto setting is to 'suspend' after locking/blanking then change it to do 'nothing' or something on those lines...
If you have screensaver then also set it to 'never'.
(I am not on Uubntu right now, so excuse me if I am not particular).

Okay, I went through the settings, and I turned off the option to lock the screen after a while, and it seems to be a little better, but the problenm still persisted.

---

### Post by cobradabest on 2014-10-27
Okay, it see,s Ubuntu doesn't lock up at all, but rather the mouse stops working, because if I have a terminal up, I can still type when I'm "locked up". Also, my touch screen seems broken now, even when the mouse works perfectly, the touch screen doesn't, it worked perfectly when I installed ubuntu and it still works fine in Windowws 8. What is going on?

---

### Post by westie457 on 2014-10-27
Try turning the touch-pad off either using the key combination (Fn+F whatever the manual says) or System Settings > Mouse and Touchpad.
Let us know if it makes any difference.

---

### Post by cobradabest on 2014-10-27
It didn't make any difference. Besides, it worked perfectly with the touchpad enabled when I first installed Ubuntu, but somehow it just stopped working one day, and hasn't fixed itself.

EDIT: Nevermind, I disabled the touchpad in the settings, and the touch screen worked agaibn, and it did still when I renabled it!

There's still the issue of it locking up, but if I call the terinal using Ctrl+Alt+T, it unfreezes it, which is good for a temporary solution, but I don't want to have to be doing that every 10 or so minutes, there surely has to be a perminent fix somewhere?

---

