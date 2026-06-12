---
title: "Can my computer Handle Ubuntu?"
date: 2007-02-02
forum: General Help
---

### Post by stevendiamond on 2007-02-02
My computer crasehd last ight and says I need to reinstall windows, but someone told me about linux so Id rather use it instead.

However, my pc is old - pentium 200, and only 196k ram. Can it handle ubuntu?

If so, how do I go about installing it? I am fairly unfamiliar with command prompt. Also, the computer I am at has no DVD burner - can I burn ubuntu to cd or flash drive?

Cheers

---

### Post by igknighted on 2007-02-02
Yes, you could handle Ubuntu.  You will need to install from the alternate install CD however, so when you download it make sure thats what you get.  All ubuntu discs are CD only, so no DVD burning is necessary.  Also, there is no CLI involved in the install.  There may be some after the install to tweak your system, but it will be laid out step by step on the forums so all you would have to do is copy/paste code.

---

### Post by DMAthlon on 2007-02-02
i'd say that if you installed ubunutu on that system you would probably kill yourself before it got a chancce to boot the live CD.

good luck with it, i suppose it COULD be done but not sure - it needs at least around 3 GB HDD space too.

---

### Post by drumkitcat on 2007-02-02
Hi,

I'm new to Ubuntu and Linux myself and asked a similar question this morning.

There is a "lite" version of Ubuntu called Xubuntu, and it is more favorable for older systems... you may want to give that a try.

I'm giong to try it out myself this weekend.

Best of luck!
Paul

---

### Post by stevendiamond on 2007-02-02
Pretty impressed by the quikc responses there! Pretty funny too - 1st response I thought 'yeah, happy days', 2nd I thought 'damn - won't work after all...' , then a nice happy medium with the 3rd response.

So I will go for this xubuntu then. So just burn it to cd, then put the disc in and it should basically self-install?

---

### Post by russell.h on 2007-02-02
You will have to go into your BIOS and tell your computer to first try to boot from the CD drive. You typically press the 'Delete' key (not backspace, although it might work also?) when the computer first begins to boot. It should tell you what key to press, it might not be delete at all. Then navigate around the menus until you find something about boot order, and set your CD drive as the first boot device. Then press whatever button saves and exits (F10 on mine), you will probably have to type the letter Y at a prompt (to confirm that you want to save changes), then it will reboot again. If you have the CD in the drive it should now boot to the Xubuntu installer.

Good luck!

Edit: Of course your computer may already try the CD drive first, I think some OEM computers do that.

---

### Post by DarkN00b on 2007-02-02
You need the Xubuntu alternate CD. Do a command line install (its not as hard as you might think...just answer the questions). It should run fairly well on that machine, albeit slowly due to the low powered proc. Xubuntu uses the XFCE desktop which is a lightweight window manager so it should work pretty well.

---

### Post by Topsiho on 2007-02-02
"pentium 200, and only 196k ram"

It might work, but will be terribly slow, with (K)Ubuntu. The processor is way too slow, and the ram is only just enough: > 192 Kb. If you want to see what (K)Ubuntu is like and don't mind it is very slow, just try.

Putting in more ram will help greatly I think, but the processor is still much too slow.

And, as others already said, you could try Xubuntu which uses the xfce-desktop, which is much smaller than either Gnome (Ubuntu) or KDE (Kubuntu), and needs less ram to work.

How to configure your BIOS to make your computer boot from the CD-Rom you should find out from the manual as there are many different methods to do this, for the many different BIOSes.

So: put in more ram, and if that's an option: replace the processor for a faster one, if you want to try (K)Ubuntu :)

Topsiho

---

### Post by all4linux on 2007-02-02
I don't believe you can get any version of Windows to run on 196K of ram, except possible Windows 3.1. The minimum requirements for Win95 was 8 megs of memory. Also, I can't imagine a pentium II machine with such a small amount of ram.

---

### Post by russell.h on 2007-02-02
He means MB (I hope)

---

### Post by russo.mic on 2007-02-03
Oh Stop,

I've got Ubuntu, not Xubuntu running on an old 400 mhz machine with about 10 gig hd and 128 mb of ram.  It doesn't fly around, but it's more pleasing than using windows on the same machine.

You should be fine with Ubuntu.  give it a go.

---

### Post by K.Mandla on 2007-02-03
I'd start with Xubuntu and see if it is too sluggish. If it is, take a look at the [Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") page in the wiki. 

By the way, 192Mb of memory is more than enough. Adding more memory isn't going to make your computer faster.

---

### Post by igknighted on 2007-02-03
If you avoid using apps like OpenOffice and Firefox and instead use some alternatives that are easier on the system (abiword/gnumeric, epiphany) you should be fine.  There is always IceWM and Fluxbox if you get in a jam, but I dont forsee that.

---

### Post by Topsiho on 2007-02-03
@ russel.h:
"He means MB (I hope)"

Ha! I hope he does. Did not notice :)

@K.Mandla:
"By the way, 192Mb of memory is more than enough. Adding more memory isn't going to make your computer faster."

This is of course not true. With so little memory, even if it is considered enough, swapping is often necessary, which slows down the computer considerably. Adding memory is THE method of improving the speed of the computer.

:)

Topsiho

---

### Post by sloggerkhan on 2007-02-03
I think he'll be OK with xubuntu. It works ok on sytems with 256 megs, and seems to only use about 120 megs on them. I imagine the processor will limit more than the RAM.

---

### Post by K.Mandla on 2007-02-03
> **Topsiho said:**
> Adding memory is THE method of improving the speed of the computer.
I disagree; I feel this is a very common misconception. But I'm not willing to fight over it. If the OPer wants to add memory and feels there is an improvement afterward, that is his call to make.

---

### Post by jrickmar on 2007-02-03
You could try Damn Small Linux, although it's not exactly the most user friendly.

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

(and yes, I hate the name also.)

---

### Post by stevendiamond on 2007-02-04
Cheers for the help everyone, and just to clarify yes - i did mean MB and not K. I am not the most computer savvy, as you may have guessed.

---

### Post by russell.h on 2007-02-05
Did you get it working yet?

---

### Post by d.j.schroeder on 2007-02-17
When I first tried linux I tried Damn Small Linux and couldn't get it to work well.  I used Puppy Linux and got that working without too much trouble, it is also small and easy on system resources.  Just another option...

---

### Post by Resurrection on 2007-02-17
I had a thought, worst case scenario if you can't get it to work, I am sure you would be able to find a used computer somewhere like a swap meet or "flea market" or something like that that you might be able to buy for next to nothing.  Basically, you should be able to find a used computer that is newer than your with better specs, say maybe around 5-7 years old that shouldn't cost more than $100.  

I get the impression that you don't want to shell out for a brand new computer, and I don't blame you.  A lot of Linux users though get their start trying it out on an used machine purchased second hand.

Where are you from?  Maybe someone here lives close to you and knows where to get a good used machine.

---

### Post by RuarriS on 2007-02-17
alternatively you could look on craigslist for your town/city/state. Theres a linux forum (atleast for mine) there too, and i'm sure you would have some luck

---

