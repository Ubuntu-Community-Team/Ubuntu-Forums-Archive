---
title: "Ubuntu Crashes in Battery Mode"
date: 2019-02-27
forum: General Help
---

### Post by gomes9563 on 2019-02-27
[COLOR=#242729][FONT=Arial]I have a few serious issues with my Ubuntu installation, all of them only when working with the battery. 
I have dual boot between W10 and Ubuntu 18.04 lts, and both of them work perfectly when charging, but once using battery only UBUNTU is the only one who doesn't work! 

The problems:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]1) Random Blinking; 
2) Crashes/Frozen WHITE screen after unlocking my session or recovering from suspension mode; 
3) The scariest one: Random sounds of electrical shocks, equal to the sound of a hard reset shutdown! 4) More recently whenever I tried to reboot my PC it asks my password and it unlocks to the desktop but just for a few seconds before freezing![/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]To prove my idea I tried to reboot my PC and each time after my password Desktop ends up freezing. To restart I use de alt+sysqr+ reisub shortcut but I end up freezing again. BUT at the moment that I turn the power adapter on it goes smooth! In some crash/freezing situation, my PC goes to a command screen (picture below) before going to the password unlock screen again and crashing definitely.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
[IMG] [https://imgur.com/a/lFR6TcD](https://imgur.com/a/lFR6TcD)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I really don't want to re install UBUNTU before exploring all sugestions. I already tried with a live Cd I ran the try Ubuntu, and I was able to initiate and work (both battery mode and plug in), the problem was that every time that I tried to reboot, log out or shut down all my attempts resulted in a crash/freeze. I ran Gparted to check for partition problems and nothing was found.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I would appreciate more suggestions.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Hint: A few days ago I installed preload, tlp and cpufreq. But I had everything associated with them removed(I think)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Specs: 
SO: Ubuntu 18.04 lts[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]PC: MSI GE62 Apache Pro
 IntelCore I7 
NVidea GTX960m[/FONT][/COLOR]

---

### Post by Autodave on 2019-02-27
This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by gomes9563 on 2019-02-27
Not possible, built-in battery.

---

### Post by gomes9563 on 2019-03-04
[update]
With a live Cd I ran the try Ubuntu, and I was able to initiate and work (both battery mode and plug in), the problem was that every time that I tried to reboot, log out or shut down all my attempts resutted in a crash/freeze.
I ran Gparted to check for partition problems and nothing was found.
I would appreciate more suggestions.

---

### Post by gomes9563 on 2019-03-08
More suggestions guys, please.

---

### Post by Autodave on 2019-03-08
If it were mine, I would do a new download (to make sure that the original one wasn't bad) and do a clean install.  If everything works properly at that point, I would install ONE program at a time and see if it still works properly.

---

### Post by gomes9563 on 2019-03-09
I know that would solve it, but it's running from the problem.
After another try, it crashed and started to show pci troubleshooting:
[https://imgur.com/PgOqcDK](https://imgur.com/PgOqcDK)
[IMG]https://imgur.com/PgOqcDK[/IMG]

---

### Post by gomes9563 on 2019-03-15
I really the answer is related with the pci problems but I don't Know for where to start.

---

### Post by gomes9563 on 2019-04-18
[COLOR=#2C2C2C][FONT=&amp]Hello Guys, again, well I did a clean install of my dual boot between Windows 10 and Ubuntu 18.04, and I did just install the basic, and once again it&#347; working smoothly, but the problem appears when I disconnect my charger from my computer:[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&amp]i) If I'm working in Ubuntu, and I disconnect my charger it eventually crashes after a few seconds maybe a minute.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&amp]ii) If I try to turn on my computer without my power adapter, it gets stuck in a loop in the user authentication page, or it simply crashes.[/FONT][/COLOR]

[COLOR=#2C2C2C][FONT=&amp]I don't have this problem with the windows installation neither have this problem with live cd Ubuntu.[/FONT][/COLOR]

[COLOR=#2C2C2C][FONT=&amp]Please can someone give me a hint.[/FONT][/COLOR]
[COLOR=#2C2C2C][FONT=&amp]I tried already to disable all power savings options, suspension options,I used grub parameter pci=nomsi and pci=noaer,Tlt,...

After one of the many crashes I had this:
[/FONT][/COLOR][IMG]https://i.imgur.com/VWPLM3b.jpg[/IMG]

---

### Post by him610 on 2019-04-18
> Not possible, built-in battery.
Removal of battery is documented here, [https://www.ifixit.com/Guide/MSI+GE62+Apache+Pro+004+Battery+Replacement/106698]("https://www.ifixit.com/Guide/MSI+GE62+Apache+Pro+004+Battery+Replacement/106698")

---

### Post by gomes9563 on 2019-04-19
Thx I will look this through, but wouldn't my Windows instalation be affected by this issue to?

---

