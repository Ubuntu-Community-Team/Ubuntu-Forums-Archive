---
title: "Bios update with Lenovo Ideacentre 510/510A Series but not using Win?"
date: 2020-09-10
forum: General Help
---

### Post by trpted on 2020-09-10
As of right now on my Lenovo Ideacentre 510/510A Series I am using Windows 10 64 bit. but I have to ask.

I looked at the directions for HP as how to update the BIOS and found at [https://support.hp.com/us-en/document/c00007682](https://support.hp.com/us-en/document/c00007682) this line

[b]
Update the BIOS manually from a USB Flash drive (outside of Windows)
[/b]

:)

However with my Lenovo it seems to only possible to update the BIOS while using Windows.

[https://pcsupport.lenovo.com/us/en/products/desktops-and-all-in-ones/500-series/510a-15icb/downloads/driver-list/component?name=BIOS%2FUEFI](https://pcsupport.lenovo.com/us/en/products/desktops-and-all-in-ones/500-series/510a-15icb/downloads/driver-list/component?name=BIOS%2FUEFI)

While I know if I switch my HP computer to Linux I can still update the BIOS without using Windows 10 64 bit.

I have wonder about my Lenovo if for sure only possible to update the BIOS within Windows. Different wording but same meaning. I want to know if anyone verified that or not and what the truth is (yes only from Windows. Nope can with the help of Wine) for my Lenovo.

This will help me if I decide to switch to Linux on my computers. Not saying that I can't add a second HD to my Lenovo so that one drive has to be Windows and the other is my primary OS and turn dual boot (for ex running Windows only when updating BIOS)

Please and thank you

---

### Post by trpted on 2020-09-11
No one knows ?

---

### Post by tea for one on 2020-09-12
> **trpted said:**
> No one knows ?

No one knows because they probably do not have your PC and, even if they had your PC, they haven't yet considered your dilemma.

Anyway, you've already answered your own question by thinking about adding a second drive for Ubuntu.

One drive for Windows and one for Ubuntu - Boot from UEFI boot screen and no worries about grub.

Out of curiosity, have you contacted Lenovo and asked them how to update UEFI firmware without Windows?

Also, have a look here [https://fwupd.org/lvfs/search?value=lenovo](https://fwupd.org/lvfs/search?value=lenovo)

---

### Post by trpted on 2020-09-12
While only asking about it, will consider asking them too.

Thank you

---

### Post by tea for one on 2020-09-12
> **trpted said:**
> While only asking about it, will consider asking them too.

Thank you

I hope that Lenovo provide you with sound and pertinent advice.

As a matter of interest, Lenovo are no strangers to Ubuntu as they are going to sell some of their PCs with Ubuntu pre-intalled.

Therefore, I imagine they must have considered how to update UEFI without Windows?

[https://www.omgubuntu.co.uk/2020/06/ubuntu-on-lenovo-laptops](https://www.omgubuntu.co.uk/2020/06/ubuntu-on-lenovo-laptops)

[https://news.lenovo.com/pressroom/press-releases/lenovo-brings-linux-certification-to-thinkpad-and-thinkstation-workstation-portfolio-easing-deployment-for-developers-data-scientists/](https://news.lenovo.com/pressroom/press-releases/lenovo-brings-linux-certification-to-thinkpad-and-thinkstation-workstation-portfolio-easing-deployment-for-developers-data-scientists/)

---

### Post by trpted on 2020-09-12
I asked via their fourms. REF [https://forums.lenovo.com/t5/English-Community/ct-p/Community-EN](https://forums.lenovo.com/t5/English-Community/ct-p/Community-EN)

Does asking them on their forums count or should I ask them some other way? If some other way, how?

I prefer online as one of the reasons I am not a good talker.

Please and thank you

---

### Post by tea for one on 2020-09-13
Using Lenovo forums may yield some useful info.

You could also contact the vendor. However, if they are simply a **box shifter**, it could be a frustrating.

Is there not a Lenovo website contact where you are situated?

Direct contact with the manufacturer would provide the best results if you can get to the right department/person.

---

### Post by trpted on 2020-09-13
After pressing contact us, it ask what kind of product it is: PC, Mobile, Data Center and Smart. 

If I press PC, I am given these options: 

#1 Search by product name, serial number or machine type

#2 Signup or Log-in

#3 Browse by product or Auto Detect Serial Number.

So I selected auto detect serial number for example, after it detect it my options for contacting them are only these: Check repair Status, Consult our forums, Incorrect Warranty Stats and Find a Service Provider (Find the nearest authorized service provider to service your system). :(

If Selected browse by product, I browse for it - I am also given

Speak with Technical Support (Connect with one of our technical experts). :)

So if I copied that URL down [https://pcsupport.lenovo.com/us/en/ContactUs/Callback_US](https://pcsupport.lenovo.com/us/en/ContactUs/Callback_US)

If I go there with the other web browser Window or tab that went through auto detect serial number, that Callback URL tells me for the exact same product (ID = 510A-15ICB Desktop (ideacentre)): 

> The current product is not supported


Expect that if I paste in my serial number at the page that gave to me  Check repair Status, Consult our forums, Incorrect Warranty Stats and Find a Service Provider, it stops giving the option of  Technical Support. :( 

And if I try to go that Callback URL, again it tells me 


> The current product is not supported


What the bleep? 

Based upon what I am trying to do, it should not matter that my Warranty has expired. Warranty as far I know is for repairs only. Boy oh boy am I am mad! And I will tell them on their forum too as well if I get a call back after making sure not to tell paste in the serial number.

---

### Post by tea for one on 2020-09-13
The episode you describe is frustrating yet not unusual for multinational companies.

Here's an idea, based on UEFI upgrades being important.

Remove the internal Windows hard drive.

Purchase a new hard drive, pop it into the PC, install Ubuntu and leave the frustration behind.

If, in the future, you feel you need to upgrade UEFI, put your Windows drive in the PC, update UEFI via Windows.

For the small cost of a bit of hardware, it may be worth consideration.

---

### Post by CatKiller on 2020-09-13
> **trpted said:**
> However with my Lenovo it seems to only possible to update the BIOS while using Windows.

Have you actually tried?

UEFI updates itself. The helper application they provide just sets things up so that the UEFI knows where the file is and reboots into the mode where it automatically installs the update, in case the setup screen is too intimidating.

You can generally achieve the same thing by going into the UEFI setup yourself, telling it to update, and pointing it at the update file. You'll need to have put the file somewhere that the UEFI can read from, like the ESP or a FAT-formatted USB stick.

Note that updating the UEFI will reset all the settings to defaults so, if there's a setting that you need set a particular way, make a note of it and remember to change it back after the update's done.

---

### Post by trpted on 2020-09-13
No I have not tried it yet.

For that computer in BIOS/UEFI, this/these are my only options.

Took a screen shot.

As you can see all I have is: Main, Devices, Advanced, Power, Security, Startup and Exit.

If you think you know where the option to update the BIOS without the use of Windows is in there, please tell me where.

As your request I will then show what is in that area (Not the best example as I am sure it is not in Exit) and always getting creative so that I do not show any info that I should not show publicly (like serial number of the computer or for that matter for the OS).

---

### Post by trpted on 2020-09-24
Bump/update.

Contacted them through twitter and they said users can't update the BIOS without the use of Windows.

---

