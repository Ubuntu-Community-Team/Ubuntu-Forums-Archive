---
title: "Please help with Ubuntu GRUB killed by Windows on dual boot (I hate Windows &#129324;)"
date: 2024-04-26
forum: General Help
---

### Post by khurtsiya on 2024-04-26
Hello!

[This is my post from Reddit, where I did not receive much help.]

This might get a bit emotional, but I really hate Windows! It's only installed on my computer for occasionally playing Civilization, Rust, or DayZ. However, even that doesn't stop it from wasting my time and nerves to the maximum.

So, the characters in this story: me, my computer, Ubuntu, Windows, ChatGPT 4, ChatGPT 3.5.

Background: Since I've encountered Windows not playing nice with other OSes on the same machine before, I knew that I needed to install Windows first, then Ubuntu, to have the option to choose the OS at boot. I have 2 M.2 SSDs. I installed Windows on the first one, then Ubuntu on the second one. Everything worked perfectly. But it turned out my knowledge of Windows' treachery was not complete. One fine day, after successfully finishing a game of Civilization with a victory, I decided to shut down the computer, and of course, Windows couldn't resist the opportunity to update itself. Everything went fine. But the next day, when I wanted to boot into Ubuntu to work, it turned out that Windows, even after updating, killed the bootloader. I was furious. I thought that by correctly installing the systems, I had freed myself from these worries. It was naive.

I lack the knowledge to quickly fix the bootloader. I turned to the internet, read several articles, and tried to copy-paste commands, but quickly concluded that the general scheme wouldn't work for me. I decided to turn to AI. On the first day, things seemed to be going well; I booted from the Ubuntu Live USB, copy-pasted chat commands, and provided the output for control. Everything seemed to finish without errors, but upon rebooting, nothing had changed. I saw "Reboot and Select proper Boot Device or insert boot media in selected boot device and press a key" again.

I decided to try again the next day. Today, with renewed vigor and hope, I embarked on the battle. Again, I carefully executed chat commands, everything was going fine until I hit the request limit for ChatGPT 4. I had to switch to 3.5, and it turned the process into a nightmare. It stopped checking errors properly and gave scattered ideas. It all ended with suggesting creating an additional partition for the bootloader, and objections like "it used to work fine without it" didn't bother it.

In the end, I realized that I can't handle it without community help. And for these two days, I simply don't have the nerves, considering that I wasted two days just because Windows doesn't play nice with other OSes. And this is coming from someone who has been behind a computer for 20 years. What about newcomers?

I ask for help with my problem. Here's how I described it to the chat:

I am in BIOS. I have these options. Boot mode select: LEGACY + UEFY. Boot option #1: Hard Disk: Samsung SSD 970 EVO Plus 1TB (this is my Ubuntu). Boot Options #2: Windows Boot Manager (Samsung SSD 970 EVO Plus 1TB) - this is a separate SSD with Windows. I installed them in this order: 1. Windows, 2. Ubuntu (which created a menu where I can select which OS to boot). But after Windows update, it broke my menu. After I did all above, I still have this error while loading from Ubuntu SSD: Reboot and Select proper Boot Device or insert boot media in selected boot device and press a key.

Thank you to everyone who managed to read to the end!

What has been done:

Used Boot Repair with no luck.

Step 1: Verify Disk Partitioning and Boot Configuration

Step 2: Determine Boot Mode

Step 3: Check GRUB Configuration and Bootloader Installation

Actually I forgot I can share chat URL, You can see prompts and terminal outputs there:

[https://chat.openai.com/share/47ffc0c1-59d5-43b3-8546-63f6a6eb2876](https://chat.openai.com/share/47ffc0c1-59d5-43b3-8546-63f6a6eb2876)

---

### Post by Rubi1200 on 2024-04-26
The quickest and easiest solution to try and figure out what is going on would be to use a liveUSB with a current version of Ubuntu and boot the computer. Select the option to Try Ubuntu.

Then, follow the instructions to run the boot info script in my signature.

Please note: do not try and repair. 

Choose the option to create a summary report and to create a pastebin link. 

You can then post that link back here for people to analyze the results and make suggestions on how to fix the situation.

---

### Post by khurtsiya on 2024-04-26
I will do it. Meanwhile, may be report from Boot Repair will have needed info?

[https://pastebin.com/yDpiB2Y8](https://pastebin.com/yDpiB2Y8)

---

### Post by dragonfly41 on 2024-04-26
Interesting story.
Recent suggestions above might sort out your issues. But.

Let me start with your efforts to get advice from ChatGPT. I do supplement my own development research by letting AI agents take on the drudgery of searching for relevant sources. But the lesson I have learned is to be crystal clear in the prompts you submit. This new art is dubbed &#8220;prompt engineering&#8221;.

And follow AI advice with care. ChatGPT advises to run bootrepair but if you search this forum you will find advice *not* to apply boot-repair - simply publish the URL to the report to allow experienced users to peruse (as above posts). Challenge ChatGPT advice.

That apart, the agent I am comfortable with is Phind.com. And do not be afraid to challenge it's advice.
However your prompt is poorly worded.
Your forum post is better worded.

Here is one prompt to try:

[PROMPT] This developer occassionally uses Windows and has installed Ubuntu in dual boot mode.
There are two M.2 SSD's. One contains Windows, the other contains Ubuntu.
Boot BIOS is set to Legacy.
Following a session with Windows, on shutting down Windows and observing Windows update, this developer could not boot into Ubuntu which previously worked without fault. Windows update had disrupted the grub.


[PROMPT]In a dual boot Windows and Ubuntu configuration, following a Windows update, analyse the error message: &#8220;Reboot and Select proper Boot Device or insert boot media in selected boot device and press a key&#8221;.
Will installing rEFInd simplify the selection of Windows and Ubuntu in dual boot mode ? Boot-repair has not worked.


But another suggestion is to return to the hated Windows and download a 15days trial version of [https://www.easyuei.com/index-us.html]("https://www.easyuefi.com/index-us.html")
This should sort your UEFI issues from within Windows. 

But also concurrently install [rEFInd]("https://www.rodsbooks.com/refind/") as a supplementary boot loader. It works for me and I have multiple SSD's in external caddies in StarTech dual docking bay..
Windows is like a cuckoo in the nest. Throwing out other fledglings.


[POSTSCRIPT]
This is the killer message in your boot-repair report:-


[LIST]
[*][COLOR=#000000]The firmware is EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).[/COLOR]

[*][COLOR=#000000] [/COLOR]
[/LIST]

---

### Post by khurtsiya on 2024-04-26
Thank you for replies! I will try this. But as it is non-free software - does it mean that I will be able to boot with it just for 15 days for free?

Also, I am not sure that Ubuntu installed in UEFI mode, because if I set in BIOS UEFI-only (instead of LEGACY+UEFI) - my SSD with Ubuntu disappears from boot priority list in BIOS.

I found in Wikipedia that

> rEFInd is a boot manager for UEFI and EFI-based machines.[2][3] It can be used to boot multiple operating systems that are installed on a [COLOR="#0000ff"]**_single_**[/COLOR] non-volatile device. It also provides a way to launch UEFI applications.

Can this be a problem if I have systems on separate SSDs?

---

### Post by khurtsiya on 2024-04-26
> **Rubi1200 said:**
> The quickest and easiest solution to try and figure out what is going on would be to use a liveUSB with a current version of Ubuntu and boot the computer. Select the option to Try Ubuntu.

Then, follow the instructions to run the boot info script in my signature.

Please note: do not try and repair. 

Choose the option to create a summary report and to create a pastebin link. 

You can then post that link back here for people to analyze the results and make suggestions on how to fix the situation.

It seems that we are talking about the same software, so my report is actually what you asked for, correct?

---

### Post by khurtsiya on 2024-04-26
rEFInd seems to be exactly what I need, but I want to install it on Ubuntu, not on Windows. The thing is I can not boot Ubuntu in the first place.

---

### Post by khurtsiya on 2024-04-26
> This is the killer message in your boot-repair report:-


The firmware is EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).
I am not native English speaker, so I do not get what this means, sorry...

---

### Post by khurtsiya on 2024-04-26
Ok, I just found that while trying to repair boot myself using ChatGPT I somehow changed Windows bootloader also if this makes sense. So whatever SSD I select I just see GNU GRUB version 2.06 grub> prompt...

What I can do from here? My last plan was to load Windows, install EasyUEI, load Ubuntu and install rEFInd. But now the only thing I see is this grub> prompt. I also can boot from Ubuntu LiveCD, but is installing rEFInd there makes sense?

---

### Post by dragonfly41 on 2024-04-26
[COLOR=#000000]> I also can boot from Ubuntu LiveCD, but is installing rEFInd there makes sense?

Yes, it makes sense and you can install rEFInd into either the Windows partition or the Ubuntu partition.

The EASYUEFI is a supplementary appoach to fix UEFI. Quite separate from rEFInd. Try rEFInd first.

Also when booting up hit F2 or it might be F10 to view your BIOS settings (which might have been changed) and ensure that UEFI is seleted,* not* Legacy.  And select rEFInd as your priority boot loader.

After all this you can update Grub so you have two routes to startup. rEFInd is cleaner .. for me.[/COLOR]

---

### Post by dragonfly41 on 2024-04-26
I have followed your lengthy AI sesson and you are being drawn into the spider's web. I do note that there is reference to LVM and encryption which is beyond my ken.
But ask your friendly ChatGPT session. And clarify what PC you are using.

> [PROMPT]It has been suggested by another party that I should try installing rEFInd as a measure to restore boot order and later update Grub. I have been advised to set UEFI instead of Legacy in Bios and select rEFInd in boot order. Do you concur?

---

### Post by khurtsiya on 2024-04-26
Meanwhile chatting with ChatGPT I found that:

1. Windows is instelled in UEFI mode
2. Ubuntu is installed in Legacy mode + LUKS encryption
3. I do not have Secure Boot option in Windows OS Configuration in BIOS

I tried to install refind from LiveCD with no luck. I have Legacy+UEFI mode in BIOS enabled.

---

### Post by khurtsiya on 2024-04-26
Ok, finally some good news here. Actually I somehow installet Refind and it did not load (and alos Windows did not load) because yesterday at some point in my "repair" proccess I changed order in my BBS..something menu at the bottom of Boot menu. Now I changed it to Windows and I am in Refind menu.

Now I have these options:
1. Windows (loads fine)
2. Boot EFI\ubuntu\grubx64.efi from EFI system partition (loads grub> prompt)
3. Boot Fallback boot loader from EFI system partition
4. Boot EFI\ubuntu\grubx64.efi from EFI system partition (loads grub> prompt) - second one
5. Boot Fallback boot loader from EFI system partition - second one

At the bottom I have two yellow keys and some other icons.

So Ubuntu still not loading. How do I fix this?

---

### Post by HermanAB on 2024-04-26
BTW, I learned decades ago to rather run Windows on a virtual machine such as Virtualbox on Linux.

---

### Post by dragonfly41 on 2024-04-26
If Windows now loads fine then I would now (corrected from not)  try (in Windows) the 15days trial of EasyUEFI.
Also try installing rEFInd now in your Ubuntu partition. (I install it in every drive I have - windows and different Ubuntu caddies). Then you will have an rEFInd boot route into Ubuntu. You will need to go into boot order again after this. And ensure that you have UEFI *not Legacy *chosen in BIOS.

When you get into Ubuntu remember this advice from your ChatGPT session.

sudo apt-get install efibootmgr

You should also be able to run that in LiveUSB to select boot sequence.

[COLOR=#FFFFFF][FONT=&amp]
[/FONT][/COLOR]

---

### Post by dragonfly41 on 2024-04-26
Re: Windows on virtual machine.
From post #1
[COLOR=#000000]>  I really hate Windows! It's only installed on my computer for occasionally playing Civilization, Rust, or DayZ.
Is not access to bare metal required for these? I don't know. Still don't know what PC this is. The clue in profile is Ubuntu 14.04. july 2008.[/COLOR]

---

### Post by oldfred on 2024-04-26
You ran Boot-Repair report when in BIOS boot mode. You need to run in UEFI boot mode.
Boot-Mode setting in UEFI/BIOS is default for installed system. You have to choose mode when booting live installer, if live installer has both modes. 

Not 100% sure as BIOS report does not show all the UEFI info, but it looks like both are installed in UEFI mode. No old BIOS boot loaders in MBR, both drives have an ESP and both drives are gpt. Windows requires gpt for UEFI boot, Ubuntu does not, but clean install uses gpt.

But both Windows & major grub updates reset UEFI to have that system as first in boot order.
You can go into UEFI settings (not one time boot menu) and change boot order. Or manually boot from UEFI one time boot menu (same as you use to boot live installer) and choose Ubuntu entry.
Windows updates reset boot order, but often also turn fast start up back on. That may prevent grub from booting Windows. So then you boot Windows from one time boot menu and turn fast startup off. 

Check boot order in UEFI settings and/or boot Ubuntu from  UEFI one time boot menu.

---

### Post by dragonfly41 on 2024-04-26
Context.
A reminder of the flak this OP has walked through. Reddit, us and .. ChatGPT.

[https://chat.openai.com/share/47ffc0c1-59d5-43b3-8546-63f6a6eb2876](https://chat.openai.com/share/47ffc0c1-59d5-43b3-8546-63f6a6eb2876)

That is why I keep [Danny Kaye's sketch]("https://www.youtube.com/watch?v=TJ9f2rnjB84") in mind.

---

### Post by khurtsiya on 2024-04-27
> **HermanAB said:**
> BTW, I learned decades ago to rather run Windows on a virtual machine such as Virtualbox on Linux.

Yeah, this is may be great if you have good PC. Playing games in Virtual Box at least at average PC is not the best experience I think...

---

