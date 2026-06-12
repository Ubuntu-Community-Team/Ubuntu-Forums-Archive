---
title: "Laptop take a long time to boot"
date: 2024-09-27
forum: General Help
---

### Post by lenn219 on 2024-09-27
hello i just installed Ubuntu on my laptop after trying a lot of other Linux distro's and other stuff so i have some experience

but this is the first time that this has happens.

What happens is when the computer starts i select the drive to boot and then it just hangs for 3 min and then boots in seconds and during the hanging its just a black screen and nothings seems to happen.

Startup finished in 14.635s (firmware) + 2min 54.534s (loader) + 2.336s (kernel) + 6.536s (userspace) = 3min 18.043s 
graphical.target reached after 6.502s in userspace.

the laptop uses a ssd and is pretty fast.

my guess is that is has to do with grub but i can't figure it out.

so if you have advise or know a way to help i would thank you very much.

---

### Post by oldfred on 2024-09-27
What brand/model system?
What video card/chip?
Do you have latest firmware for UEFI & SSD?
Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status

Is install UEFI & system set to default boot in UEFI mode?

Do you get grub menu? And have tried recovery mode?

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lenn219 on 2024-09-27
hi thank you for replying

i noticed because my system is in dutch that some stuff is also in dutch in those paste bins is that oke?

[https://paste.ubuntu.com/p/nktdSHB7pR/](https://paste.ubuntu.com/p/nktdSHB7pR/)

And yes this is a EUFI System and i do get the grub menu but i just hangs over selecting the "ubuntu" option for 3 minutes or so than something fails but it goes to fast to see what fails.

And i tried recovery mode but it didn't seem to do anything. it just had the same behavoir.

and what do you mean with this "Please copy & paste the pastebin link to the BootInfo summary report  ( do not post report), do not run the auto fix till reviewed. Use often  updated ppa version with your USB installer or any working install over  somewhat older ISO."?

should or shoudn't i post those links?

thank you

---

### Post by oldfred on 2024-09-27
Please post pastebin link, but not the report. Its easier to read in another tab than have to scroll up & down in  a thread.

Have you updated Firmware to latest available?
Note sure if F.06 is current for your model.

Some other settings to review.
[https://ubuntuforums.org/showthread.php?t=2462045](https://ubuntuforums.org/showthread.php?t=2462045)

Are you dual booting with Windows.
HP likes to default boot a Windows entry and you have to go into UEFI settings to set Ubuntu as first boot option.
Not sure if then, it still looks for Windows, if you do not have it & then has to time out?

---

### Post by lenn219 on 2024-09-28
hi thank you 

[https://support.hp.com/nl-nl/drivers/hp-17-laptop-pc-17-cp3000/model/2101549775?sku=83R83EA](https://support.hp.com/nl-nl/drivers/hp-17-laptop-pc-17-cp3000/model/2101549775?sku=83R83EA)

it seems to be the exact model number and the firmware is the latest.

i also just used the ssd on my pc and it also seems to just hang and shows nothing

i do have windows on both pc's but on the desktop i booted as number 1 in the list.

and the linux and windows parts are on different drives.

and here is both of the pastebin's

[https://paste.ubuntu.com/p/XvVtvJW2HQ/](https://paste.ubuntu.com/p/XvVtvJW2HQ/)

[https://paste.ubuntu.com/p/3mqGXF7Mzk/](https://paste.ubuntu.com/p/3mqGXF7Mzk/)

they look the same but they are by the programs you said.

but i think something is timing out but i don't know what is

when it start to boot the message i get is:

"EFI stub: Loaded initrd from LINUX_EFI_INITRD_MEDIA_GUID device path"
"EFI stub: Measured initrd data into PCR 9"

and then it just blasts stuff into the screen but it looks fine and i don't spot any error's

thank you

---

### Post by tea for one on 2024-09-28
[COLOR="#0000FF"]Line 72 [/COLOR]- OS#1 (linux):   Het nu gebruikte besturingssysteem - Ubuntu 24.04.1 LTS on sda2
[COLOR="#0000FF"]Line 162[/COLOR] - sda:1024GB:scsi:512:512:gpt:Kingston DataTraveler Max:;

Ubuntu 24.04 is located on an external USB
Perhaps your firmware is not set up to boot external devices quickly?

Try this:-
Isolate, de-activate or physically remove your internal nvme disk
Boot to the USB
Any improvement?
> **lenn219 said:**
> and then it just blasts stuff into the screen but it looks fine and i don't spot any error's
To avoid seeing this scrolling text, you need to edit grub as below
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Are you familiar with editing /etc/default/grub?

---

### Post by oldfred on 2024-09-28
I do not see this file in your sda1. > /efi/Boot/bootx64.efi 

In Windows it is normally a copy of Windows boot file bootmgfw.efi.
But in Ubuntu it is a copy of shimx64.efi.
Bootx64.efi is a deault or fallback drive type boot entry, similar to how you boot USB flash drive.
If you unplug an external drive UEFI may change UEFI entry and it will not work, but then you boot the drive entry.

Try copying /efi/ubuntu/shimx64.efi to /efi/Boot/bootx64.efi. If it really is there then should be ok, leave existing files in /efi/Boot.

---

### Post by lenn219 on 2024-09-29
<br><br>yes i am familiar with editing the grub file i have changed it before because i thought maybe something was timing out and trying to see if something was.<br><br>thank you i wil try the stuff you said and will report back

---

### Post by lenn219 on 2024-09-29
that file is in the efi file system and i tried what you advised but it didn't change anything

and thank you for any idea's

---

### Post by lenn219 on 2024-09-29
oke so tried what you advised but it doesn't seem to help

i do want to say that i have tried different linux distro' s on the same drive and those did seem to work

should i just try a reinstall?

i am willing to use unstable versions of ubuntu if that is needed.

---

### Post by tea for one on 2024-09-29
> **lenn219 said:**
> 
i do want to say that i have tried different linux distro' s on the same drive and those did seem to work
That's good news
It's always a good idea to use tools/applications/systems which present no problems
> **lenn219 said:**
> should i just try a reinstall?
Of course, if you wish - worth a shot
Nothing ventured, nothing gained

---

### Post by lenn219 on 2024-09-29
i did reinstall but this time i used kubuntu but it also has the same problem so i don't know i think something is borked somewhere

---

### Post by tea for one on 2024-09-29
Do you have other security/trust options in your UEFI settings?

---

### Post by oldfred on 2024-09-29
Something wrong somewhere.
My 2017 build with a newer NVMe drive.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 4.168s (kernel) + 4.081s (userspace) = 8.249s  
graphical.target reached after 4.066s in userspace.
[/FONT]
```

I do also change a variety of settings:
I remove all snaps & install .debs from ppa for both Firefox & Thunderbird

Lot of similar info in multiple threads:
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456](https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

---

### Post by lenn219 on 2024-09-29
There is a secure boot option but that is off so no I don't think there are anymore options in the uefi

---

### Post by lenn219 on 2024-09-29
Oke I might think this is some sort of regression so I am going to try like 18.04 to see If that works

---

### Post by oldfred on 2024-09-29
You cannot get support for 18.04. Unless you have Ubuntu Pro.
Ubuntu 18.04LTS (Bionic Beaver) became unsupported in April, 2023, Ubuntu 18.04 has passed its End-Of-Life date, and is no longer supported on AskUbuntu. Upgrade to a supported release.
[https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/](https://fridge.ubuntu.com/2023/05/13/extended-security-maintenance-for-ubuntu-18-04-bionic-beaver-begins-31-may-2023/)

---

### Post by lenn219 on 2024-09-30
hi i got it working i changed out grub with systemd-boot and that boot way faster 

[FONT=monospace][COLOR=#000000]systemd-analyze  [/COLOR]
Startup finished in 16.152s (firmware) + 12.946s (loader) + 3.147s (kernel) + 8.255s (userspace) = 40.502s  
graphical.target reached after 8.225s in userspace.

[/FONT]https://gist.github.com/gdamjan/ccdcda2c91119406a0f8d22f8b8f2c4a

i used this but WATCH OUT DON'T REMOVE GRUB BECAUSE APT TRIES TO REMOVE THE WHOLE DE(desktop enviroment) IF YOU DO THAT
[FONT=monospace]
[/FONT]

---

### Post by lenn219 on 2024-10-01
what i did for the person having the same problem is that is switched to systemd-boot
PLEASE WATCH OUT THIS IS KINDA SKETCH

PLEASE REVIEW THE APT COMMAND BEFORE RUNNING IF YOU HAVE 200+ ITEMS it removes something is wrong.

PLEASE READ BEFORE DOING.

sudo apt install systemd-boot

# you can use to check if everthing is wright
sudo bootctl 

# to have it put the files in your /boot/* folder to make it boot linux
sudo bootctl install


# then this command without "libfreetype6" [https://gist.github.com/gdamjan/ccdcda2c91119406a0f8d22f8b8f2c4a](https://gist.github.com/gdamjan/ccdcda2c91119406a0f8d22f8b8f2c4a) use this as a guide and make sure you inform apt that you don't want grub reinstalled
sudo apt purge --allow-remove-essential grub2-common grub-pc-bin grub-pc grub-gfxpayload-lists grub-efi-amd64-bin grub-efi-amd64-signed grub-common os-prober shim-signed

#this makes sure that we don't reinstall grub
sudo apt-mark hold "grub*"

before you restart make sure with

sudo bootctl

that everthing looks good and there are files in this folder 

[FONT=monospace][COLOR=#5454ff]**/boot/efi/EFI**[/COLOR]
[/FONT]
and also remove the grub files but that is said in the guide i linked above

---

