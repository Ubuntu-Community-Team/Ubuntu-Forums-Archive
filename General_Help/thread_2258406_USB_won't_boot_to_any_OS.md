---
title: "USB won't boot to any OS"
date: 2014-12-27
forum: General Help
---

### Post by -Marco on 2014-12-27
Good evening, today I formatted in **FAT32** 20 times my SanDisk Cruzer Blade USB for installing on Ubuntu MATE. Invane my tests, I tried both **dd through terminal, UNetbootin, usb-creator et**c. but every time I went to boot in me came out errors like _**"Machine check error" or you just restarted the PC.**_ 

Now I changed to exasperation distro, Linux Mint now, but this boot in but the moment I start the installation (via GRUB, entering Start Linux Mint 17.1 x64) PC restarts. 
I also tried using **UEFI, EFI and CSM**. Nothing to do. 

What is the matter? :( :confused:

---

### Post by yancek on 2014-12-27
What is the exact command you used with dd?
Did you do an md5checksum of the iso file after downloading to verify the download?
Did you get a success message when using unetbootin?

---

### Post by grahammechanical on 2014-12-27
Are you over-clocking this machine? Is it a self-build? Did the message say Machine check error or Machine check exception? The difference may be irrelevant. It most likely indicates a hardware fault.

> [COLOR=#252525][FONT=sans-serif]Normal causes for MCE errors include overheating and/or incorrect hardware installation. Specific manually-induced causes include:[/FONT][/COLOR]

[LIST]
[*][overclocking]("http://en.wikipedia.org/wiki/Overclocking") (which normally increases heat-output)
[*]poorly-fitted [heatsink]("http://en.wikipedia.org/wiki/Heatsink")/[computer fans]("http://en.wikipedia.org/wiki/Computer_fan") (the same problem can happen with excessive dust in the CPU fan)
[*]an overloaded internal or external power-supply (fixable by upgrading)
[/LIST]


[http://en.wikipedia.org/wiki/Machine-check_exception](http://en.wikipedia.org/wiki/Machine-check_exception)

Regards.

---

