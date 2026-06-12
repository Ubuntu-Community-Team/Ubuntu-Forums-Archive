---
title: "Firefox problem"
date: 2007-01-19
forum: General Help
---

### Post by jand on 2007-01-19
[SIZE="4"]
Hi, 
I have just upgraded to Unbuntu 6.10 but I still have the following problem with Firefox: 
There are some websites that when I access using Firefox, the browser automatically closes and other browsers in the same workspace are also closed. For ex, when I log in to my gmail account. After entering username and pass, the page is start to load. When I am just able to glance at the emails, the browser closes. 
I have no problem accessing my emails in yahoo.

Thank you and hope to hear from you soon.[/SIZE]

---

### Post by bollix47 on 2007-01-19
What extensions do you have installed?

You could try [Safe Mode]("http://kb.mozillazine.org/Safe_mode") to see if problem goes away.

If it does then one or more of your extensions/themes may be causing your problem.

---

### Post by taurus on 2007-01-19
Did you happen to install flash 9 plugin for firefox?

[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)

p.s.  And please, go easy on the font size, okay!

---

### Post by jand on 2007-01-19
Hi, I think I only have inline search extension for Firefox. 

About the flash one, there is no instruction for Ubuntu 6.10, am I right ? 

I am a newbie, by the way.

---

### Post by taurus on 2007-01-19
It works for Edgy too so look in the section "**Flash for i386 manual install**".

Basically, you download the latest flash, flash 9, to your system.  Unpack it and run the installer to install the plugins.

---

### Post by jand on 2007-01-19
Hi, 

Thanks for your instructions. But how to run the installer ? :( 

After extracting it, when I click on the flashplayer-installer, I am asked to choose an application to run it. 

Can you tell me how to do it in the terminal ? I have some problems with nautilus and my desktop is empty !!!

---

### Post by taurus on 2007-01-19
Run it from a terminal.

Applications -> Accessories -> Terminal
```
cd ~/Desktop/install_flash_player_9_linux
sudo ./flashplayer-installer
```

And when it asks you where to install the plugins, point it to **/usr/lib/firefox** (if it's not already showed).

---

