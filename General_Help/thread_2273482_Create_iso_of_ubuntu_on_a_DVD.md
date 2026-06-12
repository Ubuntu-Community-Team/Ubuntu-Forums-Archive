---
title: "Create iso of ubuntu on a DVD"
date: 2015-04-13
forum: General Help
---

### Post by Camilia on 2015-04-13
I need to reinstall ubuntu. Could someone give me steps how to create an ISO of ubuntu onto a DVD? 

I have downloaded ubuntu 14.04 onto a flash drive.

---

### Post by papibe on 2015-04-13
Hi Camilia.

Here's a detail tutorial on how to do that: [Burning ISOs]("https://help.ubuntu.com/community/BurningIsoHowto").

Let us know if you need more help with that.
Regards.

---

### Post by Camilia on 2015-04-13
> **papibe said:**
> Hi Camilia.

Here's a detail tutorial on how to do that: [Burning ISOs]("https://help.ubuntu.com/community/BurningIsoHowto").

Well at the [link]("https://help.ubuntu.com/community/HowToMD5SUM") told to Check the iso file with commands in the terminal. The result was command not found. I paid for the ISO so I guess it is okay. Since 1 part of the instruction is out of date I wonder about the rest of the instructions. Is important to check the ISO? Also that link directs me to go to another link and then another link. There I find I am suppose to have a usb-imagewriter packag. I don't know if I have it. Getting more and more confused. All I understand from this [link]("https://help.ubuntu.com/community/Installation/FromImgFiles#Ubuntu") is to burn it onto a DVD. Then it say to put it in the computer. I know from the past I have to make an ISO, what ever that is. I PendriveLinux for USB last time. Don't have an extra USB this time.

Stumped!! Those instructions are not helpful for they are to be used with a windows OS. I am using ubuntu 14.04 on computer trying to make an ISO

I went to that link, that is where i got the download. i don't get any usefull instructions there. 

Are you going help or just keep telling me to go to links that refer me to other links.

---

### Post by Bashing-om on 2015-04-13
Camilia; Huh ?

Very confused:
> 
I paid for the ISO so I guess it is okay.

The .iso if free (all of the 'buntu flavors !), and readily available via download on the internet . Here are we talking about the .iso file that is used to make up the image ? OR the actual burned to disk image ??

In respect to verifying what you have:
> 
 Is important to check the ISO? 

Short answer is YES, That does insure a firm foundation and precludes software faults as a source of possible problems. How ?
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Is Windows your operating system platform ?

IF you are too burn that .iso to disk, see:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

[INDENT]1st time confusing
[INDENT][INDENT][INDENT]then it is as easy as falling out of bed, wide awake
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-04-13
You paid for a free download? Or did you just donate to Ubuntu?

Some have issues with download which is not related to where it is from, but how it is saved. 
Often best to check md5sum.

What are you running Ubuntu or Windows?
The download site also has links on how to create DVD or flash drive from Ubuntu or Windows.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I burned many "coasters" or defective DVDs over the years, so I changed to use flash drives as they can be reused.

---

### Post by Camilia on 2015-04-13
Donated. I am running ubuntu 14.04 Everything you have given me refers to windows. I don't have an extra flashdrive. The one I used before didn't work so I have cleared a few partions. Thus it is probably useless now.

not having a happy ubuntu. getting of getting referred to a link that refers me to another link. not helpful.

Tried copying to A CD. It didn't seem to be working for taking to long, thus cancelled it. Took disk out and then put it back in. Now nothing happens.

> **oldfred said:**
> 
I burned many "coasters" or defective DVDs over the years, so I changed to use flash drives as they can be reused.
I only have 1 extra flash drive. I read that you are suppose to have a blank flash drive. Thus tried to clear it. Got 2 partions off it. I don't think it is safe to use now.Nothing has been working as I have been told would. So now I have extra large fonts under icons on desktop and can't undo the process because the sheet on tweek is to large to be made smaller. Extra flash drive and CD unusable.

---

### Post by papibe on 2015-04-13
> **Camilia said:**
> Stumped!! Those instructions are not helpful for they are to be used with a windows OS. I am using ubuntu 14.04 on computer trying to make an ISO
The instructions include hints for all mayor OSes (and Ubuntu versions):
> 1. Burning from Windows
2. Burning from Mac OS X
3. Burning from Ubuntu
4. Burning from Kubuntu
To get to what you want, please scroll down to the page, or click on the left size box that says contents.

Regards.

---

### Post by Camilia on 2015-04-13
Again things are not working as in instructions. I now have the option burn it as a file or contents. That is **not** in the instructions. Burn it as file or contents? got it working a page behind like in instructions.

---

### Post by Bashing-om on 2015-04-13
Camilia; Hey;

OK, I keep trying to assist.
Working from an ubuntu install to make uo a liveDVD.
1) Verify the .iso file:
say that the .iso is downloaded to your Downloads directory (default) and the name of the .iso is "  ubuntu-14.10-desktop-amd64.iso "
In this instance verify the file with terminal command:
```

md5sum ~/Downloads/ubuntu-14.10-desktop-amd64.iso

```
and you get a response:
> 
sysop@1404mini:~$ md5sum ~/Downloads/ubuntu-14.10-desktop-amd64.iso
08494b448aa5b1de963731c21344f803  /home/sysop/Downloads/ubuntu-14.10-desktop-amd64.is

where the series " 08494b448aa5b1de963731c21344f803 " is the 'md5sum. Check this series against the published what should be the correct sum:
one source of these sums:
 [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
in the list see that the systems generated sum is a match for one of the published sums - here it is the 1st sum in the published listing.

2) So, known good .iso file, time now to burn it to disk. I use brasero as my reference;
double click on the .iso file -> choose "burn to disk" and in the brasero screen I suggest to burn at lowest speed -> select properties and choose '4x'  -> select burn and wait while it is completed. It will advise you when done, and to eject the DVD.

3) OK, now with a liveDVD in hand, reset in bios for the DVD drive as 1st boot priority -> boot the liveDVD;
As soon as the bios screen clears depress the right _shift_ key -> language screen; escape key to accept the default -> boot options screen -> "check disk for defects" . Wait for the check to complete and as prompted ; reboot.

4) Boot the liveDVD to "try ubuntu" and play with the system. Insure all the attached hardware and all pallications function as expected.

Now you have a liveDVD suitable to use as the install medium.

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by Richard-S on 2015-11-01
I am trying to burn a DVD of Ubuntu in Win 8.1. When I follow the instructions on the Ubuntu web site, it says right click on the iso image and select "burn disk image". When I right click on the iso file that I downloaded, I see no selection to "burn disk image" as shown in the instructions. All I see are "Choose default program", "Add to start menu", "7 Zip", "Mount as virtual drive", "View disk image" and on down the usual list of selections to "Properties" at the bottom. Am I missing something?

Richard

---

### Post by Vladlenin5000 on 2015-11-01
> **Richard-S said:**
> Am I missing something?

Yes, two things actually:

1. This isn't your thread and your question is unrelated considering the user who started it is trying to burn Ubuntu installation media using Linux native software on her already installed Ubuntu OS, from an ISO file. This file is the only thing in common. Techniques and software to accomplish such task are totally independent from the ISO files contents therefore you're having a difficulty with your particular Windows version/settings. You'd have the exact some problem with any other ISO image file (DVD-Video, CD-Audio, Data CD/DVD/BR, etc., ect.).

2. The instructions provided in the Ubuntu help pages are probably for an older Windows version and are, at best, a general guide. There are hundreds of tools to do the same job and the result is what matters, not the process in itself. Both free and commercial tools/software are available for Windows and ultimately is up to Windows users to find the one they like the best.

---

### Post by Camilia on 2015-11-01
Well I started the thread I am ok with him posting here. I gave up and bought a CD on Ebay for $6. I got 2 CDs. One for 32bit and 64 bit. I don't need the 32bit. Can you use it Richard? I would just need to be reimbursed for the shipping cost.

---

### Post by howefield on 2015-11-02
> **Richard-S said:**
> I am trying to burn a DVD of Ubuntu in Win 8.1. When I follow the instructions on the Ubuntu web site, it says right click on the iso image and select "burn disk image". When I right click on the iso file that I downloaded, I see no selection to "burn disk image" as shown in the instructions. All I see are "Choose default program", "Add to start menu", "7 Zip", "Mount as virtual drive", "View disk image" and on down the usual list of selections to "Properties" at the bottom. Am I missing something?

Using File Manager and highlighting the downloaded iso file, do you see the Disc Image tools menu,.. along with the image mount/burn buttons ?

---

