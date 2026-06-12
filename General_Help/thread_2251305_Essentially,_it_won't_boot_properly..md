---
title: "Essentially, it won't boot properly."
date: 2014-11-03
forum: General Help
---

### Post by whizzer2 on 2014-11-03
EDIT: The main problem here is that Ubuntu won't boot. I've included information about my issues with Windows in case that helps anyone, but if that's a separate issue then I can deal with it later. **My aim is to get Ubuntu to boot properly, every time if possible. ***(Thanks for the tip, Bucky Ball)*

Okay, I'll start at the beginning.
Earlier this year, I installed elementary os luna (based on Ubuntu 12.04) in dual boot with Windows 8.1 - an update to Windows 8, which was an upgrade to Windows 7, which was preinstalled. I have an HP Pavilion dv6, and this was my first proper installation of Linux (I had previously dabbled with dual boot with Wubi and Ubuntu 12.04 LTS, but I removed this at the time of installing Windows 8 as I feared it was disrupting the installation).
Everything was fine and dandy for several months. But then... completely out of the blue, it didn't boot normally. Instead, it got stuck at some kind of BusyBox terminal. This happened on both normal and recovery boots. Also, **Windows wouldn't boot**. It stayed stuck on the spinning-dots boot animation.
I searched for a fix, and I should make an important note that I found someone with the same problem **on the same laptop**. There was a fix, but **I didn't apply it**, which in hindsight was probably a very bad decision. Instead, I decided to write over the elementary installation with Ubuntu 14.04 LTS.
This went successfully with a couple of minor hiccups that were quickly solved. But the problems didn't stop with the new installation. Sure, it booted fine - sometimes. When it did boot fine, it ran fine. It wouldn't suspend, however. The condition got gradually worse until today, and despite applying some fixes, it still wouldn't hold together.
I also installed Ubuntu 14.10 when I could. This went fine - no issues installing, and no new issues since. Utopic hasn't caused or fixed anything.
Today, I cannot get it to make a successful boot. I will outline all the problems I can think of below:

[LIST]
[*]Almost every time I attempt to boot, I get "**error: environment block too small**". I found a fix for this and have applied it twice. I'm not entirely sure what this error actually does, as I seem to have the same issues (or lack of) whether the message appears or not.
[*]I have also been getting "**error: attempt to read or write outside of hd0**" (I think). This seems to cause boot issues when it appears, often a kernal panic.
[*]Currently, if I boot Ubuntu, it seems to boot normally, but after the purple vanishes, I get a black screen. But not a black screen as in black pixels - **the screen is blank as if turned off**. However, I do hear the boot sound and I have previously had success typing my password in, but now it doesn't respond.
[*]Some time after installing Ubuntu, I tried booting Windows for the first time since elementary wouldn't boot. **It went to system repair**, though didn't go beyond spinning dots. For over an hour, it displayed the message "**attempting to repair disk errors. this may take over an hour to complete.**" (I think). Eventually, I came back to it to find kernal panic. I guessed that it had rebooted, grub selected Ubuntu by default, and I get the second error I mentioned.
[*]Since then, whenever I try to boot Windows, I get "**The Boot Configuration Data for your PC is missing or has errors. // File: \Boot\BCD // Error: 0xc000014c**" (// represents newline) and it then requests that I use my installation media to repair it. **I do not know where it is or even if I have any**, and even if I did it would be for Windows 7 and not 8.
[*]I believe I tried the two Windows Safe Mode options on grub. **The first one wouldn't boot**, and the second one started showing the Windows 7 boot animation before I switched it off for fear of the havoc 7 might wreak.
[*]**Ubuntu recovery won't boot** either. It gets stuck on varying stages of the hardware scan.
[*]By using some extra boot parameters ([described here]("http://community.linuxmint.com/tutorial/view/842")), I can get it to **boot, but with issues**. The interface appears as usual, but my icon pack and theme doesn't appear (after a while the theme appears, but not the icons or window decorations) and my external wireless mouse does not work (it does on other computers, such as the one I'm using right now). The cursor tends to vanish for a while before reappearing around the time the theme partially appears. I don't know if there are other issues, but there may well be. I believe it's a bit slower than a standard boot, though not as slow as a recovery resume boot.
[*]There's also a **ongoing network issue**. Earlier this year it was discovered that I had a faulty built-in Broadcom wireless card that was hogging the network inexplicably. This was easily fixed by using an external wireless adapter dongle thing and teaching elementary and Windows not to connect with the other card. However, when I installed Ubuntu, it insisted on always attempting to connect to the network with both cards. Recently, the network has been very slow until I disconnect the external wireless dongle thing and use the built-in card. After this, it runs fine. I haven't been able to test if this is hogging the network again, but it may not be.
[/LIST]
I think that's just about everything I can possibly think of. The root of the problem may lie back at elementary's death or it may be something else. I do still have live CDs for elementary os luna and Ubuntu 14.04 LTS. If you need more detail, then do say and I can clarify.

---

### Post by Bucky Ball on 2014-11-03
Welcome. Default font and colour, thanks. Also, paragraphs make it a lot easier to read (people will walk on by when they see the 'black blob' posts). 

Please clearly and succinctly outline one issue per thread. You have a lot of things going on here. You want help with getting Ubuntu to boot? Forget about booting Windows for now, then, and concentrate on that. Not sure. Your thread title is no more specific. :-k

Thanks. Good luck. ;)

---

