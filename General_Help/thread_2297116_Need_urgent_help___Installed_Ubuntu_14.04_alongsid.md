---
title: "Need urgent help:   Installed Ubuntu 14.04 alongside Windows 8.1, can't find Ubuntu"
date: 2015-10-01
forum: General Help
---

### Post by Roger_Coverley on 2015-10-01
Hello, I'm fairly new to Linux and I'm having a major problem.

Ubuntu was running perfectly. I had all of my files already downloaded and everything was configured exactly as I wanted it.

I made the apparent mistake of booting from Windows again (Windows 8.1, which came pre-installed with my computer) to play a game there that I was having trouble running in Ubuntu, and now I can't boot back into Ubuntu. 

Are all of my files gone? How can I find and return to Ubuntu again? 

I have disabled secure boot and fast boot in accordance with the somewhat related advice I have read elsewhere, but the problem remains and I still do not know what to do.

I press "Shift" while clicking on the restart button to access the boot menu/settings, but clicking on the boot from Ubuntu option in the "choose a device" section does nothing. The computer just goes back to running Windows 8.1, and at one point I received this error message:  [SIZE=4]"No boot disk has been detected or disk has failed."

[SIZE=3][SIZE=2]Please tell me what I should do to regain access to Ubuntu. Once I'm in Ubuntu, I will never boot from Windows again and I will hopefully be safe.


[/SIZE][/SIZE]**Edit: **[SIZE=3][SIZE=2] Sorry for the edit, but being the impatient idiot that I am, I tried reinstalling Ubuntu completely (and erasing Windows) a couple of minutes after submitting this post in the hopes of fixing the problem entirely, and now the entire computer seems to be corrupted. Alas, neither Ubuntu nor Windows 8.1 (the latter having been wiped by the second attempted Ubuntu installation) boot naturally. :(

The good news is that I can still boot successfully from a Linux live USB, and, having stared into the dark abyss of having possibly ruined my computer permanently, the idea of using a live USB (running Ubuntu 14.04) doesn't seem all that bad anymore. I'm going to just use the live USB from now on. My files are backed up in Google Drive and all I really need to use my computer for is Internet browsing.

Well, I guess this settles my problem. If you have any tips for making my computer naturally functional again (without having to boot from the USB), let me know. Thank you in advance.
[/SIZE][/SIZE]
[/SIZE]

---

### Post by mastablasta on 2015-10-01
> **Roger_Coverley said:**
> 
Are all of my files gone? How can I find and return to Ubuntu again? 

they are gone only if you format the drive. which apparently you now did?!


> 
I have disabled secure boot and fast boot in accordance with the somewhat related advice I have read elsewhere, but the problem remains and I still do not know what to do.

wrong on secure boot. if you installed Ubuntu with secure boot enabled then it has to be left on.

fast boot hibernates the PC when you "turn it off" in windows. so if you have dual boot then it's best to disable it. perhaps if you just turned it off and then boot into windows and shut down them down you would have solved your initial problem. instead you created a new one. it's never good to panic to much.

> 
[SIZE=4][SIZE=3][SIZE=2]Well, I guess this settles my problem. If you have any tips for making my computer naturally functional again (without having to boot from the USB), let me know. Thank you in advance.
[/SIZE][/SIZE][/SIZE]

start by formatting the disk and installing the OS. if you easily installed it before you should be able to install it now, if you suspect disk is bad you can test it. for example with ultimateboot cd: [B][http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
or hirens boot cd: [http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)[/B]

---

