---
title: "Stuck on Ubuntu 12.10"
date: 2015-05-19
forum: General Help
---

### Post by Wroif on 2015-05-19
Hi,

I recently feel upon one of my old laptops. It's a laptop that I was using about 2-3 years ago, and It still have ubuntu 12.10 installed. I learned that Ubuntu 12.10 have been discontinueted, and have been trying to updrade it bu nothing works. The upgrade center keep telling me to check my internet connection, even tought I am connected to internet, the sudo apt-get update, and " sudo apt-get upgrade" commands both doesnt work (I get error everywhere with them. I don'T really know what to do. How should I go about upgrading my computre to the latest version of ubuntu?

---

### Post by coffeecat on 2015-05-19
Do a fresh installation of a supported version of Ubuntu after backing up any personal files that you might need. The 12.10 repositories are closed which is why you are getting errors.

It is theoretically possible to upgrade 12.10 to the currently supported LTS 14.04, but it would involved upgrading to 13.04 and then to 13.10 by using the old releases repository. After that you would upgrade to 14.04. I would not recommend this as there are three upgrades to perform, all of which take time and bandwidth, and all of which might fail, especially if you have installed things from 3rd party repositories.

---

### Post by grahammechanical on 2015-05-19
The very latest version of Ubuntu is 15.04 but that only has 9 months support. Which is why we are recommending 14.04.2 as its repositories will keep open until April 2019.

Regards.

---

### Post by Wroif on 2015-05-19
And how do I do a fresh install of ubuntu?

---

### Post by Bashing-om on 2015-05-19
keven-abellard; Hello;

A very open ended question that has no one answer:
> 
And how do I do a fresh install of ubuntu?

As there are so many variables - hardware support, desk top preference, install medium(s) available , use case , multi-booting ect ect ect ...

Let's use this:
[https://help.ubuntu.com/14.04/installation-guide/](https://help.ubuntu.com/14.04/installation-guide/)
as a common reference, and as you have questions and concerns we can address these .

[INDENT][INDENT]millions do
[INDENT][INDENT][INDENT]you can too
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sammiev on 2015-05-19
> **keven-abellard said:**
> And how do I do a fresh install of ubuntu?

Hi,

You can get the latest releases [here]("http://www.ubuntu.com/download/desktop").

I would suggest a LTS version and you can use a DVD/USB to install the OS to your HD.

---

### Post by coffeecat on 2015-05-19
> **keven-abellard said:**
> And how do I do a fresh install of ubuntu?

The same way you (presumably) installed Ubuntu 12.10 on that laptop - from a live session booted from a DVD or USB flash drive.

So that members do not waste time describing things which are self-evident to you, or are too advanced for you, you need to tell us your level of expertise. Have you installed Ubuntu before? Many times or infrequently? Do you know how to burn a bootable DVD? Ditto - bootable flash drive?

Also - do you need links from where you can download the Ubuntu ISOs? Do you want to install the LTS (long-term support) 14.04 which will have updates for a few years yet, or the newer 15.04 which will have later versions of most apps, but which will only be supported until January next year?

---

### Post by Wroif on 2015-05-19
I installed Ubuntu myself, booted from a dvd where I burned the os. I burned another Dvd, with ubuntu 14.04, but when I insert the Dvd in ubuntu, nothing happens. Since my computer can dual boot with windows, I guessed that I should run the DVD on windows to install it, ubt If I do that, what will happen to the version of Ubuntu that was on my computer? 

I already backed up all important files from that computer, so data loss isn't really an issue.

Thank you all so much for your help

---

### Post by coffeecat on 2015-05-19
You don't run the DVD from Ubuntu. You need to set the BIOS of the laptop to boot from the DVD.

---

### Post by Wroif on 2015-05-19
And how do I do that?

---

### Post by Wroif on 2015-05-19
I rebooted the computer with the cd in the DVD tray. I don't know why, but the computer booted from the DVD, and it upgraded ubuntu. If somebody know why I would appreciate, if not, thank you all for your help

---

### Post by Bashing-om on 2015-05-19
keven-abellard; Good deal;

That you are now release upgraded.

As to booting:
short primer:
In bios set up there are the options to set the boot device priority.
Let's "assume" that this boot priority had been left as the CD as 1st boot priority, 2nd is the hard drive, and perhaps 3rd as a USB drive.
So what does bios do ? 
1st it looks for a CD and IF that CD has boot code; IF it does find a CD WITH bootcode, the CD(DVD) is booted, else it looks for the hard drive, elseif it looks for the USB.

These options can be re-arranged in the bios set up utility .

[INDENT][INDENT]clear as mud ?
[/INDENT][/INDENT]

---

### Post by Wroif on 2015-05-19
Crystal clear!

Thank you mate!

---

### Post by Bashing-om on 2015-05-19
keven-abellard; Hey !

Pleased that I am of some small assistance.

If this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

