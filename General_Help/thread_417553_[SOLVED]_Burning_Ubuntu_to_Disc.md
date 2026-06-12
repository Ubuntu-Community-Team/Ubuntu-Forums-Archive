---
title: "[SOLVED] Burning Ubuntu to Disc"
date: 2007-04-21
forum: General Help
---

### Post by noerrorsfound on 2007-04-21
I have seen the Burning ISO howto: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

It seems to be incomplete (or outdated):
> In Ubuntu
   1. Insert a blank CD into your burner. A "CD/DVD Creator" file browser will pop up. Close this browser as we will not be using it. (Edgy will say "Choose Disk Type", click 'Ignore")
   2. Find the downloaded ISO image in the file browser (available at Places &#8594; Home menu on top of the screen.) Right click on the ISO image file and choose Write to Disc and wait for burning to complete.
It says that after clicking Write to Disc that you just wait for the burning to complete, but for me a window pops up for more options. There is a screenshot of the "Write to Disc" window attached to this post.

I'm wondering what to choose to make this a working Ubuntu 7.04 disc. What option should I click on *Write disc to* and *Write speed*?

My two options for *Write disc to* are **BENQ DVD DD DW1650** as seen in the screenshot and **File image**.

If I select to burn as **File image** then the *write speed* box is grayed out so I'm guessing that I shouldn't choose that one.

I have the following options for *Write speed*:
[LIST]
[*]Maximum possible
[*]56.4x
[*]47.0x
[*]37.6x
[*]28.2x
[*]18.8x
[*]14.1x
[/LIST]
Which of these speeds should I choose?

---

### Post by Compyx on 2007-04-21
The lowest speed, I can tell you from experience that writing a bootable CD at high speeds usually makes the CD unbootable. I usually burn bootable CD's at 2x - 8x, perhaps GnomeBaker will give you more options for low speeds.

---

### Post by noerrorsfound on 2007-04-21
> **Compyx said:**
> The lowest speed, I can tell you from experience that writing a bootable CD at high speeds usually makes the CD unbootable. I usually burn bootable CD's at 2x - 8x, perhaps GnomeBaker will give you more options for low speeds.
Which one of those speeds in the list is 2x, though? Do you determine that by the number at the end? :confused: The lowest there is is 14.1x, but there's also a 28.2x which is the only "2x" in the list.

---

### Post by Compyx on 2007-04-21
None of those is 2x or 4x, the lowest speed in your case is 14.1x. Try burning at that speed.

---

### Post by Sef on 2007-04-21
GnomeBaker should be installed under Sound&Video, so try that.   In GnomeBaker, Toos > burn iso

---

### Post by orb9220 on 2007-04-21
> **Compyx said:**
> The lowest speed, I can tell you from experience that writing a bootable CD at high speeds usually makes the CD unbootable. I usually burn bootable CD's at 2x - 8x, perhaps GnomeBaker will give you more options for low speeds.

Why is this the case for linux?
I have never seen this as the case in windows xp.

I have seen multiple threads on burning at slower speed.

Is Linux capable of burning disc's at rated speed?

I say this as I have never  had a bad burn from burning disc's at max speed in winXP or ubuntu except k3b says it is burning at 16x for dvd's that are 16x but actual shows burning at 4x and takes 16 mins to burn.

This is not a bash just wondering.

---

### Post by DoktorSeven on 2007-04-21
Burning at high speed should work fine most of the time; burning at a lower speed would just ensure that the image is written correctly without errors, which would mess things up during install. 

It's just a precaution.  Most people find that the resulting burn is more reliably correct when done at low speed, but I burned my Feisty CD at full speed and had no problems during install.

---

### Post by Slim Odds on 2007-04-21
> **Compyx said:**
> The lowest speed, I can tell you from experience that writing a bootable CD at high speeds usually makes the CD unbootable. I usually burn bootable CD's at 2x - 8x, perhaps GnomeBaker will give you more options for low speeds.

This is ABSOLUTE non-sense. If your CD burner is bad, go get a new one. I always burn at MAXIMUM speed and NEVER get a bad or unbootable disc.

This is such a widespread myth that I think it's about time to start calling it the crap that it is.

If you can't get successful burns at high speed, get better discs or get a new drive.

---

