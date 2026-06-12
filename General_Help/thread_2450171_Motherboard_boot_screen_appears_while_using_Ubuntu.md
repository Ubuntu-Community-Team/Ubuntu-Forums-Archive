---
title: "Motherboard boot screen appears while using Ubuntu"
date: 2020-09-08
forum: General Help
---

### Post by daved31415 on 2020-09-08
Hello,

I just installed Ubuntu and within thirty minutes the motherboard boot screen (not sure what else to call it - MSI Krait MB, there's an image of a snake and a message to press Del or F11 to enter setup or boot menu) appeared and I was unable to log back into the system. I rebooted several times, tried following a threads with advice on accessing GRUB (I was not able to open it using the shift key), changing boot mode to secure and several others items that I ran through quickly and didn't note down because I was getting impatient.

I ended up re-installing the entire system and was up and running for over an hour, wishfully hoping that there was just some strange fluke. I created a new users account, selected "switch user" and was taken right back to the MSI boot screen in less than a second. I tried CTRL+ALT+function keys, nothing seemed to have an effect. I looked at video output from other graphics cards, nothing displayed (using one of the GeForce GTX cards, if that matters, I can get more information on it).

Is this a common issue (and if so, what terms should I use to refer to it?)

Does anyone have suggestions on what I should look into/try to prevent the problem from continuing to occur?

Thanks,

Dave

---

### Post by oldfred on 2020-09-08
It looks like Krait is model used for everything, both Intel & AMD and from Z97 to recent versions.
So what version?
What video cards?
UEFI or BIOS installs?
Is UEFI updated to most current version?
If SSD, does it have newest firmware?

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by daved31415 on 2020-09-09
> **oldfred said:**
> It looks like Krait is model used for everything, both Intel & AMD and from Z97 to recent versions.
So what version?
What video cards?
UEFI or BIOS installs?
Is UEFI updated to most current version?
If SSD, does it have newest firmware?

Lets see details, use ppa version with your live installer (2nd option) or any working install, not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Is this type of problem at all common and is there a better way to refer to it other than "dropping to motherboard boot screen"?

Motherboard is a MSI Z97S SLI Krait
UEFI install as far as I know - MB is set to legacy or UEFI and I'm not sure how to determine the difference. I don't recall any sort of prompting on this when I installed from USB DVD drive.
UEFI updated - if this would be part of MB firmware update, yes.
Checked SSD firmware with smartctl, verified latest for Samsung SSD 860 QVO 1 TB, version RVQ02B6Q, same as Samsung's website.

I'm not sure what ppa version or live installer is - does this mean I need to use the install DVD? I tried sudo apt-get install ppa but no luck. Is this just to list installed packages? I chose quite a few this time but the first time around I hadn't installed anything other than whatever the installer included.

The O/S does boot, so I'm hoping I can run things from within it. It's just not very stable.

Thanks for taking a look and replying.

---

### Post by CelticWarrior on 2020-09-09
> [COLOR=#000000]UEFI install as far as I know - MB is set to legacy or UEFI and I'm not sure how to determine the difference. I don't recall any sort of prompting on this when I installed from USB DVD drive.[/COLOR]


Should be UEFI only. (And who still uses DVDs in 2020?)
How it boots is how it installs. AFAIK, even with a DVD, it should be able to install either way but @oldfred may correct me on this one. If it's the same as with USB then you'd have seen two entries for the DVD, one with UEFI. That's why we disable Legacy/CSM. UEFI only assures it boots and install in UEFI mode. We can check later with the Boot Repair report.


> [COLOR=#000000]UEFI updated - if this would be part of MB firmware update, yes.[/COLOR]

UEFI IS the motherboard's firmware. Since a decade or so it's used instead of the old BIOS. Good to know it's updated.

> [COLOR=#000000]I'm not sure what ppa version or live installer is - does this mean I need to use the install DVD? I tried sudo apt-get install ppa but no luck. Is this just to list installed packages? I chose quite a few this time but the first time around I hadn't installed anything other than whatever the installer included.[/COLOR]

If you cared to read the link provided you'd know. The point is to use the 2nd Option mentioned there and not the first because the ISO to make a bootable Boot Repair media hasn't been updated in ages. So, instead of that, we boot a live session - hopefully the DVD will do - and follow the instruction there to add the PPA and install and run the tool.

---

### Post by oldfred on 2020-09-09
I have an Asus Z97 and in UEFI or BIOS/CSM/Legacy mode, it only booted in BIOS mode. I had to use UEFI only.
The setting of UEFI or BIOS in UEFI settings is only for the installed system. How you boot USB flash drive as live installer has two choices if Secure Boot is off. You should see UEFI:flash or flash where flash is the name or label of your flash drive and the one with just the name/label is a BIOS boot. Only UEFI is clearly labeled. But all that varies by vendor.

It may just be with either as boot option, it first tries one & fails and then tries another. But that may then not always work.

If your system is updated, the only install packages are just a couple related to Boot-Repair. If not updated then you are also getting all the other updates.

System should be fully updated before running Boot-Repair.
apt-get update
apt-get upgrade

Then add ppa & run Boot-Repair.

---

### Post by coffeecat on 2020-09-09
Since forum members have gone to the trouble of providing advice, which could be of use to others, I have restored the original text of the OP's two posts. The OP had replaced them with a "never mind" message. In the circumstances I have also closed the thread.

Our [Forum Data Attribution, Retention and Privacy Policy](https://ubuntuforums.org/showthread.php?t=2231107) includes this:

> Removal of significant content from a number of posts is considered to be forum vandalism and will probably be dealt with by the account being banned and restoration of original post content.

Thanks to all who contributed.

---

