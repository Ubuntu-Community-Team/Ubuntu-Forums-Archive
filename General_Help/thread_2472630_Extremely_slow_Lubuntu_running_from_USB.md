---
title: "Extremely slow Lubuntu running from USB"
date: 2022-03-06
forum: General Help
---

### Post by bigmonmulgrew on 2022-03-06
Not sure if this should go in installation but here goes.

So recently I decided to do a little experiment, I have a Toshiba laptop with windows 10 and decided to try running Lubuntu on it. I had a spare 16GB memory stick so I thought I'd try running it from that. Requirements say 2GB so I thought that would be enough to get me on the web and testing it out.

Well I have a few problems.

First of all while I can run from the USB memory stick I can only boot from a USB2 port, the laptop has USB3 but that one wont boot. Not sure if this is the laptops limitation or something to do with how Lubuntu boots. Is here any way to rig this to run from USB3

Secondly it is painfully slow. Like taking 5 min to open a settings dialogue slow. Its a joke how faster windows 10 boots. I was hoping that it would be faster running from usb since its an old style hard drive not an ssd but clearly thats not the case. I started booting when I opened this post and as I finish writing its still booting. Good 5 min

The memory stick is a Corsair survivor stealth which by all intents an purposes should be vastly faster than the built in hard drive.

Any thoughts on improving the situation

---

### Post by guiverc on 2022-03-06
I can't provide much sorry.

- you've not said what release of Lubuntu you're talking about

- are you talking about a *live* system (*with or without persistence*) as they are much slower than any installed system, or taking about an *installed* system on USB drive?  Your description implies *live*, where an ISO written to USB media creates a *live* system that can be installed to other media; but is itself not an installed system.

- Lubuntu will boot from USB3 media/ports; so that issue appears to be your specific hardware; or how it was written to the thumb-drive, but you've provided no specifics.

- Requirements 2GB???    I have no idea where you got the 2GB from, and you didn't say ([https://lubuntu.me/?s=2gb&submit=Search](https://lubuntu.me/?s=2gb&submit=Search)), but I'm beginning to wonder if you've actually used a non-Lubuntu/Ubuntu site for your detail as I'm aware the Lubuntu ISO is offered from unofficial sites too; so I'd suggest you check where you got your details from, and if unsure don't trust search engines (*unless you can tell fake, fan from legitimate sites*) going instead to [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) for Ubuntu related sites.

---

### Post by dragonfly41 on 2022-03-06
I now run Ubuntu 20.04 very successfully on an SSD (in fact dual SSD's in a StarTech dual docking bay) attached via USB 3.0.
In my inner hard drive in a Dell PC I have Windows 10 and an earlier (unused) Ubuntu installation.
I had to reduce the size of the Windows partition to free room for Ubuntu internal.

As I see it your options include:

reducing size of internal partition using Windows resizing tool
OR
finding why your USB 3.0 does not perform (speed test)
OR
installing Ubuntu virtual machine in Windows 10

I would concentrate on solving your USB 3.0 port since the other options are not ideal.
I would hunt around for an old drive (HDD or SSD) to place in a container to try through your USB 3.0 port.
I would only use a flash drive for a liveUSB.

I have worked with Ubuntu on an old recycled HDD plugged in via USB (2.0 and 3.0). In fact I have two plugged in right now but switched off.

---

### Post by bigmonmulgrew on 2022-03-06
That would be 21.10. This isnt a live USB, this is installed to usb, although I have a live USB too, the live USB is actually way faster.

" but you've provided no specifics."

GPT partition table, 512MB efi partition, rest for "/". I think thats correct, its been several hours since i ran through it.  I installed it with it plugged into a USB3 port from a USB live stick plugged into USB2

I got the 2GB from a wiki through google, just double checked and its an older version but the other links from "lubuntu 21.10 requirements" dont actually list the requirements, so now I'm pouring through pages. The iso was from the official site

---

### Post by guiverc on 2022-03-06
FYI:  You won't find *modern* Lubuntu minimum requirements as reported here

- [https://lubuntu.me/taking-a-new-direction/](https://lubuntu.me/taking-a-new-direction/)

I personally used 1GB devices in QA-testing *i386* releases of Lubuntu (*and Xubuntu* so up to *disco* or 19.04 cycle) though most testing was done on devices with more RAM, but I still use 2GB for *amd64*, but again do most of my QA work on devices with more RAM.

For 21.10; the *live* performance is pretty good as the media validation causes the entire media to be transferred to RAM so md5check can be performed; it it remains there (as *cache*) until the RAM is required; thus on devices with decent RAM *live* performance can be  pretty good (*on lower RAM devices, or once cache is wiped due to use, it can slow down*)

Sorry with specifics I was thinking ISO used (*older releases had choice; Lubuntu 21.10 doesn't*) & *wiki* page details...


For looking at why it's slow; I'd likely open a terminal (*or have a text terminal session logged in if GUI becomes unresponsive*) and watch there.  My own system is running on a 2009 dell desktop (*running Lubuntu jammy*) so it's core2 CPU & thus doesn't have loads of spare resources; using a *spinning rust* HDD.  Lubuntu includes `htop` by default so it's usually my starting point; though once I have a clue as to issue I usually pick a more precise tool.

On a default install only a small *swap**file* is created; where in my experience (*on resource challenged boxes like I use*) a larger *swapfile* is **beneficial** so it's my first point of call. Did you opt to use *swap* during install; as if you didn't - it's what I'd correct first. I'll provide

- [https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591](https://discourse.lubuntu.me/t/swap-and-lubuntu-21-04-hirsute-and-up/2591)
- [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

The next thing I note on my old box; is my browsers (*both chromium & firefox*) don't like the extensions I like using, but I'd rather use those extensions & live with the memory leaks the [extensions] have that slow the browser & then machine down.. Back when I was on *impish* [21.10] the `htop` terminal window was always on screen & where I *confirmed my suspicion* the memory-leak was getting bad which I fixed by closing [`kill`] the *impacted* browser (*or both*), wait a little for the Linux kernel to reclaim the lost RAM & reduce swap size; then re-open browser. On my current *jammy* it's now auto-handled by `systemd-oomd` which kills them the moment I recognize the *trigger* (so I've one less step to do what on *impish*).  This may not be your issue, but I'm using it as example; and this issue requires no more than `htop` at least for me.

---

