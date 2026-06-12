---
title: "Ubuntuv18.04.03 Installation is stopped while selecting grub option"
date: 2019-08-14
forum: General Help
---

### Post by musfiqurcse23 on 2019-08-14
Hi Community,

I bought a new laptop Asus Vivobook S14 S430FN with following configuration
[LIST]
[*]Intel Core i7 Processor
[*]Nvdia Geforce MX150 2 GB
[*]SSD 512 GB
[*]RAM 8GB
[*]Genuine Windows 10 Home Edition
[/LIST]

Now, I want to use Ubuntu 18.04.03 in dual boot. But while installing Ubuntu, I am facing problems. I followed following steps.

[LIST=1]
[*]From BIOS I make sure it that **Fast Boot** is **disabled**
[*]There is no **UEFI** or **Enable CSM** option in the boot menu
[*]When start my computer I clicked ***esc*** and then choose the USB bootable stick
[*]After that I found the GRUB option [ 1. Try Ubuntu without Installing, 2. Install Ubuntu, 3. OEM Install, 4. Check disk for defects]
[*]When I choose any option from the Grub menu, it contains black screen. I tried all the possible solution which I find in the community
[LIST=1]
[*][https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it) , tried clicking button `e` while choosing option and adding the **nomodeset **in the  command. But still not working :mad:
[*]I tried the usb to install it in the other laptop [MSI FX600, Nvdia GT 325M, 8GB RAM, 512 HDD]. It was smoothly installed in to that laptop. :confused:
[/LIST]
[/LIST]

Please let me know if there is anything missing from my side. 

Thank you.

---

### Post by domingo-em on 2019-09-04
Hello, I had the same problem. Did you manage to solve it?

---

### Post by domingo-em on 2019-09-05
In case it happens to someone else, I have solved it by following the steps commented here-> [https://askubuntu.com/questions/1146431/no-possible-way-to-install-ubuntu-on-asus-zenbook-ux433fn](https://askubuntu.com/questions/1146431/no-possible-way-to-install-ubuntu-on-asus-zenbook-ux433fn)
Paste in case delete the solution:

[COLOR=#242729][FONT=Arial]It turns out update/upgrade will update the Intel related stuff and then crush the system[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This is what I did:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]In grub, choose Ubuntu, DON'T PRESS ENTER, press 'e', add dis_ucode_ldr after the line start with Linux, then boot (press F10), should be bootable now.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Once booted, in terminal:[/FONT][/COLOR]
sudo apt install intel-microcode=3.20180312.0~ubuntu18.04.1
[COLOR=#242729][FONT=Arial]Then hold the package:[/FONT][/COLOR]
sudo apt-mark hold intel-microcode=3.20180312.0~ubuntu18.04.1

---

