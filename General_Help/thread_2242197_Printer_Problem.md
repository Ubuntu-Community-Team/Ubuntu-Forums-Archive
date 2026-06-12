---
title: "Printer Problem"
date: 2014-08-31
forum: General Help
---

### Post by daniell59 on 2014-08-31
Ubuntu 14.04 32

I have a dual boot. XP and Ubuntu
I rarely use XP
When I boot into Ubuntu the printer wont work (HP laserjet P1005)
I deleted and installed the printer driver numerous times.
Here is the interesting part. If I boot into windows, the printer will work.
Then, if I boot back into Ubuntu, the printer works again.
I would really appreciate any ideas. I am at loss to explain this.

---

### Post by kurt18947 on 2014-08-31
I am no expert when it comes to HP printers but HP has perhaps the best linux support of any manufacturer.  Common advice is to install the latest hplip and hplip-gui packages from HP.  The packages in Ubuntu may not be the most recent and may not support newer printers.  Perhaps someone better versed in HP printers can give you better advice.

---

### Post by fidelis2 on 2014-08-31
According to this:
[http://www.hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1005.html](http://www.hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1005.html)
... your printer should fully be supported by HPLIP.
Could you please check if your installed HPLIP version is the same or higher as the one recommended on that website?
Last I checked for some HP printers I'm interested in, Ubuntu 14's current HPLIP (i.e. installed from the software center) always matched the recommended version number or was even higher.

Now, you mention that WinXP can address the printer, and only when you re-boot to Ubuntu it then works, too. This sounds like some USB initialisation problem on the Linux side... USB can cause so much trouble.

---

### Post by daniell59 on 2014-08-31
Now, you mention that WinXP can address the printer, and only when you re-boot to Ubuntu it then works, too. This sounds like some USB initialisation problem on the Linux side... USB can cause so much trouble.[/QUOTE]

It makes sense what you say, but the scanner has no problem working.
Where do I go from here?

---

### Post by daniell59 on 2014-08-31
I would like to add more to the "mystery."
Booting into windows is not enough to activate the printer in Ubuntu. I must also print something while in Windows. When I re enter Ubuntu, the printer prints out what I tried to print before I booted into windows.
I hate unsolved problems. I would appreciate ideas.

---

### Post by Otto-C on 2014-09-01
While I had a similar problem and fixed it, I did not save my steps.
This thread has some info that should help you.
[http://ubuntuforums.org/showthread.php?t=2241809](http://ubuntuforums.org/showthread.php?t=2241809)

hth

---

### Post by daniell59 on 2014-09-02
I just reinstalled Ubuntu with the hope that the problem would be corrected. It has not. It makes no sense that I should first have to print in windows before I can print in Ubuntu.

---

### Post by fidelis2 on 2014-09-02
> **daniell59 said:**
> It makes no sense that I should first have to print in windows before I can print in Ubuntu.
Yes, indeed. Unfortunately I don't know a solution so far.

My Canon MP printer is even worse: it won't print at all in Ubuntu 14. It did in Ubuntu 12 (or 13?). The Linux OS sends data, but stops at half of the page. So until I got this problem solved, I'm using an interesting printer "driver": a minimal WinXP virtual machine in Virtualbox running in Ubuntu 14. Because in WinXP the printer driver works. I then network share the VM's printer via Virtualbox's bridged network mode to the Intranet, and so also all Ubuntu 14 installations can print...

This "solution" is a fat printer "driver" for sure, but a very adequate usage of Windows: to act as a printer driver, and nothing more.


P.S. Until you find a solution, maybe you could use that VM work-around, too? I give 256 MB to the WinXP VM in Virtualbox. You already have a dual booting WinXP partition? Then you could either copy it into a VBox virtual drive to be used under your Linux host ( [https://www.virtualbox.org/wiki/Migrate_Windows](https://www.virtualbox.org/wiki/Migrate_Windows) ) , or let the Linux VBox use the physical WinXP partition directly ( [https://www.virtualbox.org/manual/ch09.html#rawdisk](https://www.virtualbox.org/manual/ch09.html#rawdisk) ).

---

### Post by daniell59 on 2014-09-02
> **fidelis2 said:**
> Yes, indeed. Unfortunately I don't know a solution so far.

My Canon MP printer is even worse: it won't print at all in Ubuntu 14. It did in Ubuntu 12 (or 13?). The Linux OS sends data, but stops at half of the page. So until I got this problem solved, I'm using an interesting printer "driver": a minimal WinXP virtual machine in Virtualbox running in Ubuntu 14. Because in WinXP the printer driver works. I then network share the VM's printer via Virtualbox's bridged network mode to the Intranet, and so also all Ubuntu 14 installations can print...

This "solution" is a fat printer "driver" for sure, but a very adequate usage of Windows: to act as a printer driver, and nothing more.


P.S. Until you find a solution, maybe you could use that VM work-around, too? I give 256 MB to the WinXP VM in Virtualbox. You already have a dual booting WinXP partition? Then you could either copy it into a VBox virtual drive to be used under your Linux host ( [https://www.virtualbox.org/wiki/Migrate_Windows](https://www.virtualbox.org/wiki/Migrate_Windows) ) , or let the Linux VBox use the physical WinXP partition directly ( [https://www.virtualbox.org/manual/ch09.html#rawdisk](https://www.virtualbox.org/manual/ch09.html#rawdisk) ).

Thanks for your input. For the time being, it is easier for me to briefly go into windows, print something, then I can reboot to Ubuntu and print all day.
I do not like unsolved puzzles and will try to find a solution.

---

### Post by kurt18947 on 2014-09-03
I'm not at all familiar with HP's linux support.  I wonder if there's a way to make your problem known to HP and see if they have a suggestion.  It sounds to me like there's something with HPLIP that needs to be tweaked.  I have Brother printers and notice that the first print job of the day takes quite a bit longer - sometimes a minute or more - than subsequent print jobs.  I don't think it's solely due to coming out of sleep mode.  I wonder if there's something similar in your case but the first job of the day doesn't quite get started.

---

### Post by daniell59 on 2014-09-11
Someone on the HP Linux Imaging and Printing site helped me. The follwoing commands in the terminal did it.

=> Reconfigure print queue using below commands.
=> hp-setup -r (remove all print queues)

=> sudo hp-plugin (This will download right plugin)

=> hp-setup

I am still curious to know why first printing in XP made it possible for me to print in Ubuntu.

---

