---
title: "Kernel panic not syncing fatal exception in interrupt with Ubuntu 16.04.2 LTS amd64"
date: 2017-03-11
forum: General Help
---

### Post by iomatt on 2017-03-11
After installing Ubuntu 16.04.2 LTS amd64 alongside with Windows 8. Everything was running fine but two days later the computer freezes on Ubuntu login screen after typing the password. 

I tried to access to terminal via CTRL + ALT + F4 and after typing the password I have the following message alongside with some codes, the terminal also freezes : Kernel panic not syncing fatal exception in interrupt with Ubuntu 16.04.2 LTS amd64

Screenshot of the problem is attached below

Any help would be much appreciated, as I'm starting with linux, thanks in advance.

---

### Post by iomatt on 2017-03-12
Should I reinstall Ubuntu to get this fixed ?

---

### Post by iomatt on 2017-03-12
I finally solved this problem myself, after investigating these error messages. 

I found the word "wifi" somewhere so I restarted the computer and unplugged my belkin wifi usb adapter.
Ubuntu was starting without problems with no freeze.

So I installed grub customizer via wired connection.
> 
[COLOR=#111111][FONT=Consolas]sudo add-apt-repository ppa:danielrichter2007/grub-customizer[/FONT][/COLOR]sudo apt-get update [COLOR=#111111][FONT=Consolas]sudo apt-get install grub-customizer[/FONT][/COLOR]

Then I changed back to the first kernel. (from 41 to 36)
Restarted ubuntu and selected ubuntu kernel on GRUB and after I plugged in my wifi adapter everything was running fine.

---

