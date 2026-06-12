---
title: "Ubuntu has messed with BIOS"
date: 2008-04-24
forum: General Help
---

### Post by ericf88 on 2008-04-24
I recently installed 7.10 from windows due to my internet issues with the campus service, and I've had some network issues that wouldn't allow me to connect to the University of Florida network. DHNet, the service provider we have uses a wpa_supplicant with a IEEEX. I took the tower to one of their linux specialists and he was able to get the internet up and running fine at their office. However, I bring it back to my place and find that a lot of the applets/programs he used there were, for some reason, nonexistant at my place and the script he told me to use manually, due to terminal not automatically running it, was not working. I call him up and he suggests I reinstall Ubuntu since the most likely cause was a faulty installation since my linux was fresh yet I couldn't run pf in terminal. 

Here's the script for the wired ehternet connection eth0:

sudo sbin/wpa_supplicant -i eth0 -DWired -B -c
/etc/wpa_supplicant/wpa_supplicant.wired.conf
exit 0

  Now that 8.04 has come out, I was hoping to upgrade to fix all this, but can't, due to the fact that the boot CD I created will not be read, and I could not access my BIOS setup page normally. I was able to for the initial linux installation of 7.10 but it seems that after this I've been unable to mess with the boot priority to get my computer to boot off this CD and upgrade to 8.04. I made every attempt at a function key, del, esc, and whatnot to get that BIOS page but to no avail. I even pulled the BIOS battery cell out, cut the power, and reset the BIOS to see if I can restore any hidden corruption. I also discovered about the Smart Boot Manager directory in the Ubuntu 8.0 boot CD but I have no idea how to set up a dummy floppy drive and boot from an image off of it because I don't even know if I have the SBM requisites nasm, make, and gcc or how to check if I have them. Although 7.10 should come standard with these, my linux is another story. So, I'm pretty much in a rut and I'm looking to install 8.04 with a faulty linux, a possibly faulty BIOS, no internet connection, and I can't run the simple exe's in the CD either, because I can't even get Wine to install. =(

Specs:

Pentium 4
Onboard Network Card
Radeon 9800 Pro
Asus P4C-800-E Deluxe Ai Series

-Eric, Linux Noobert.

---

### Post by TransitMan on 2008-04-24
A Linus OS or any other for that matter cannot touch the BIOS. That is enabled by pushing F2, DEL or some other combination to get into it on boot.
As far as not being able to read the install CD, it is possible you got a corrupt download, bad burn to the disc, or the disc itself has a fault to it.
Having pulled the BIOS battery, did you leave it out for at least 60 minutes? 
As to your specs, the ASUS motherboard has a default of either F2 or DEL to access the BIOS. 
Could your BIOS be corrupt? Yes, but it would take a lot of user interaction to do it, or a dose of static electricity.

My suggestion, calm down, relax, find a friend who can help you download and burn another copy of 8.04LTS and try again.
Sometimes walking away and coming back to it later helps.

---

### Post by ericf88 on 2008-04-25
Thank you for the reply. I had not tried keeping the battery out for an entire hour until today but it doesn't seem to change anything. After making another 8.04 boot CD, I've come to the conclusion that it's not a damaged copy of the boot CD and it might be that my BIOS is too old to automatically run it. That still doesn't explain the fact that I could no longer access my BIOS page immediately after installing 7.10, though. Any additional advice aside from "wait and see" will be greatly appreciated.

---

### Post by TransitMan on 2008-04-25
If you're running a P4 processor, then your motherboard is not old - per se.
I am running a P4 system with an Intel 925X motherboard, about 3 years old. I've got a couple of Athlon 2000+ and 2100+ systems on older hardware running Ubuntu or a flavor thereof.

When you first boot the computer, any computer, it goes through the BIOS check. At that point you should be able to get into the BIOS from the commands listed further back in this thread.

Since you are having trouble, 2 things come to mind.
1 is you stated that you cleared the BIOS settings, presuming that you used the jumpers on the motherboard?
the 2nd is that a series of unfortunate circumstances has led to the BIOS becoming corrupt.

While it would be easy to blame the OS, this is not possible or practical. The OS has no way of access the BIOS.

So in retrospect, I would look at the jumper on the motherboard,  and if that is reset correctly, then try one more time. If you still cabnnot get inot the BIOS, then most probably the BIOS is toast and you will have ot make a decision as to what to do next.

---

### Post by ericf88 on 2008-04-25
Ok, so regardless of 7.10's relevancy to my BIOS, the jumpers look fine and the hardware in general is spic and span. Assuming my BIOS is irrevocably damaged but still operable, what would be my next course of action to install 8.04 without replacing the BIOS?

---

### Post by TransitMan on 2008-04-25
Can you reinstall 7.10?
If so, instead of using a fresh install of 8.04 from CD, try using the command line upgrade method. I've used twice and it works well.

Follow the directions from this page - [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Hopefully you'll get 8.04 up and running.
As for the BIOS issue, without having it in front of me, I am now clueless. Sorry.

---

### Post by lunarcloud on 2008-04-25
The problem could be the keyboard, if something resets the bios and usb legacy support is not default, then the keyboard wont work until the OS. Try a ps/2 keyboard if that seems legit.

---

### Post by dcstar on 2008-04-26
> **zarquad said:**
> The problem could be the keyboard, if something resets the bios and usb legacy support is not default, then the keyboard wont work until the OS. Try a ps/2 keyboard if that seems legit.

I once had to work on a machine with a Microsoft multi-media keyboard on it, and guess what mode the combo Function/Multi-Media keys were in on reboot?

Yep, Multi-media mode, so no matter how many times you hit the particular F key to go into the BIOS, you couldn't **until** you put those keys back into non-Multi-media mode immediately after reboot.

It's not good to have to swear out loud once you figure out that some design mug has wasted your time because of a "feature" like this, but it can be therapeutic...... :tongue:

---

### Post by Cue2 on 2008-04-26
> **TransitMan said:**
> A Linus OS or any other for that matter cannot touch the BIOS. That is enabled by pushing F2, DEL or some other combination to get into it on boot.

Thats a very interesting point can an OS touch the BIOS because on an ASUS board you get realtime overclocking (in the OS) and you can upgrade the BIOS from the OS or change the boot logo. So I don't see how that works if it has absolutly no access.

Can you find out what Asus board you have. Del is usually the Bios setup, F8 is the Boot selection screen and Alt+F2 may take you to a bios upgrade EZ-Flash or something like that (for me anyway).

---

### Post by ericf88 on 2008-04-26
Ok, I checked out that link you gave me and I used the alternate CD option and ran that command line in the alt+f2 window but all it does is ask for my password and doesn't follow up with anything. The update manager will also find 0 corrections/upgrades and consider my linux perfectly fine. 

As for the keyboard problem, I've been using a ps/2 from the get go. I made sure to modify the keyboard preferences to 101 Keys Del Keyboard, also.

And finally, I attempted to reinstall 7.10 with a good CD but it seems to face the same problems as 8.04. That first installation was a one-hit wonder.

I also don't know how to find out the specifics of my motherboard using linux because any hardware related option makes no mention of it and I got this computer like 4-5 years ago.

---

### Post by nicedude on 2008-04-26
Of course from an OS you can touch the bios. I have updated tons of Bios from Windows all it takes is a Bios flash program so it is possible but at the same time I doubt Ubuntu did it. If you PM me with what happens exactly when you startup and what exact motherboard or PC model you have I would be glad to run down the problem and try to help.

---

### Post by TransitMan on 2008-04-26
The OP was refering to the install disc for 8.04 touching his BIOS. Doesn't happen.
As far as any OS touching the BIOS once the system is up and running, only by user intervention. And unless the user has a virus or trojan (highly unlikely in Linux) running on the system to cause an effect on the BIOS, again it is very unlikely the OS will do anything to the BIOS without user intervention.

I am aware of the programs available under Windows where one can manipulate the BIOS and do upgrades to the BIOS, but again, user intervention. The OS is not capable of this by itself.

From what the OP has stated, he cannot get into the BIOS regardless of the keys hit on cold boot. Hence, my thinking is the BIOS has become corrupt somehow, giving him the problems he is seeing.

---

### Post by ericf88 on 2008-04-26
Also, indicative of a BIOS issue: "The computer clock appears to be wrong. The session might encounter issues if the computer clock is not properly configured. If the computer clock is not properly configured, please consider adjusting it."

If I click "Change it," it says I don't have access to it, even though I'm admin. And even if I change it inside Ubuntu, it resets upon every startup. This problem started with resetting the BIOS. I guess I didn't reset it properly, as it seems to always be messed up.

---

### Post by TransitMan on 2008-04-26
It could be indicative of a failing battery issue.
Those button batteries do not last a lifetime and do fail.

Replace it with a fresh one and see what happens.

---

### Post by ericf88 on 2008-04-26
FYI, the motherboard is an Asus P4C-800-E Deluxe. Pent 4 etc.

---

### Post by seth elohim on 2010-03-16
I have to agree with the cmos battery being bad. i cannot see how that would prevent total access to the bios altogether, but it is one of the only two logical conclusions I can think of, the other being static discharge from working on the 'puter without grounding yourself to the case.
I would find an old mobo laying around and try swapping out batteries.
good luck :)

---

