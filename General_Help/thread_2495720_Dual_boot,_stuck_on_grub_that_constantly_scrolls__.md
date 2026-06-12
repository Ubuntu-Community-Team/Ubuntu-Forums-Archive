---
title: "Dual boot, stuck on grub that constantly scrolls   grub&gt;    down the screen"
date: 2024-02-28
forum: General Help
---

### Post by quest-uk on 2024-02-28
HI,

I have Ubuntu & Windows 10.
Yesterday my CPU went to 100% so I rebooted and now I get black screen, with grub>   scrolling down the screen.
If I go into UEFI motherboard screen and directly select Ubuntu, i see the normal grub screen and I can boot into Ubuntu successfully.
I have added zip file with boot-repair full info.

What is the solution please, I did try [FONT=arial][SIZE=1][COLOR=#000000]boot-repair-disk [/COLOR][/SIZE][/FONT]but that did not solve the problem.

Screen shot ...
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293439&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293440&stc=1[/IMG]

Thanks

---

### Post by yancek on 2024-02-28
When you run boot repair with the Create BootInfo Summary option, it gives you a link to post here or elsewhere so other can view the information.  Many people will not download a file from an unknown site.

---

### Post by quest-uk on 2024-02-28
Hi,

I hoped that the zip file would be ok, anyway I have added it the text only here ... [https://privatebin.net/?2a9741f43fc8bb30#9i2oHG3UvpjonPqDb5E3PE1r9UBE61jRHv9XFdogbosr](https://privatebin.net/?2a9741f43fc8bb30#9i2oHG3UvpjonPqDb5E3PE1r9UBE61jRHv9XFdogbosr)

---

### Post by tea for one on 2024-02-28
Boot-repair reports that you have three operating systems:-

OS#1:   Ubuntu 21.04 on sda5
OS#2:   Ubuntu 23.04 on sda7
OS#3:   Windows 8 or 10 on sda4

Ubuntu 21.04 and 23.04 have reached end of life.
Hopefully, you have Windows 10 rather than Windows 8.
> **quest-uk said:**
> 
If I go into UEFI motherboard screen and directly select Ubuntu, i see the normal grub screen and I can boot into Ubuntu successfully.
Which Ubuntu version boots?

---

### Post by oldfred on 2024-02-28
I see grub proxy scripts. That is from Grub Customizer.
Often with multiple installs better not to use Customizer and just make your own modifications.
The only way to get rid of customizer is both uninstall it and totally reinstall grub-efi-amd64 for UEFI boot.  That will reset everything to defaults, so you then have to manually change your settings.

I always turn off os-prober and add my own boot stanzas to my main working install and most other installs I have. I do not want grub scanning all my partitions which can take a while and it finds old obsolete installs that I do not want in grub menu. And I want to add my own reboot & shutdown entries into 40_custom.

You can easily start the custom process by backing up grub.cfg and copy any boot stanza you want into 40_custom and turn off os-prober in /etc/default/grub.

40_custom
examples from cavfan
[https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046](https://ubuntuforums.org/showthread.php?t=2392441&p=13816046#post13816046)
Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[https://askubuntu.com/questions/1425637/how-can-i-add-windows-11-to-grub-menu](https://askubuntu.com/questions/1425637/how-can-i-add-windows-11-to-grub-menu)

---

### Post by quest-uk on 2024-02-28
Hi,


I have solved the problem, i have 2 keyboards attached to my PC,  I use a white one most of the time and the other black keyboard if I have dirty hands.


Guess what ... the other black keyboard was resting &#8230; very &#8230; very slightly against a cable .
There was a key being pressed on that one, not sure which key, but one on the extreme left of the keyboard.


Strange thing is that the key didn&#8217;t affect any typing I did on screen, so it was a key that had nothing to do with text on the screen !


At least Linux hadn&#8217;t let me down as I thought it was corrupted by my PC CPU going to 100% and I shutdown via terminal, then the problem occurred. 


ALL coincidence !


8-[

**Thanks** for your help as you gave me the confidence to think nothing was wrong with my system, because of the tests we did.

---

### Post by dragonfly41 on 2024-02-28
Recently I had an erratic mouse pasting content into documents. After much research and digging I found in a discussion Input Remapper which allows selective disabling. In my case the middle scroll button.

---

