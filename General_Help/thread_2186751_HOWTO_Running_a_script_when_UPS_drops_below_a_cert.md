---
title: "HOWTO: Running a script when UPS drops below a certain point"
date: 2013-11-08
forum: General Help
---

### Post by terminator14 on 2013-11-08
**[SIZE="4"]About the Project[/SIZE]**

If you have a UPS that is connected to your linux box, you may have tried to set up APCUPSD like I did. If it has worked for you, awesome! Unfortunately, as far as I can tell, APCUPSD has not been updated since 2011, and doesn't always work as intended, especially with newer UPS's. In my case, I could not get it to show how much battery the UPS had left (in percent). 

Luckily, APCUPSD is not the only thing that works with UPS's. If you have a UPS that is connected to your linux box, and have either had a power outage, or have tried unplugging it from the wall, you may have noticed that your OS automatically tells you that the UPS is on battery power. This is what my script uses - existing tools that come preinstalled with most debian based systems.

**[SIZE="4"]What does it do?[/SIZE]**

It gets triggered by cron, and checks if the UPS is on battery, and is below a preset charge level (in percent). If so, it runs any scripts or commands you want it to run, and either hibernates, powers off, or suspends your machine. I use this to tell every other linux or FreeBSD based machine that is connected to the same UPS to power off before the UPS dies.

**[SIZE="4"]What it will run on[/SIZE]**

This was tested on Debian 7, and Mint 15, and should in theory work with any Debian based system. The only requirement is that if you run:

```
upower -d
```

the "on-battery" field and the "percentage" field actually reflect what your UPS is doing. If you unplug your UPS and give it a minute or two, the "on-battery" field should say "yes", and the percentage field should start dropping. If this works for you, than you should have no problem with my script.

**[SIZE="4"]Manual[/SIZE]**

Using this script is very simple. The instructions are clearly outlined in the INSTALL.rst file, found in the same folder as the script. I suggest you open the INSTALL.rst file with vim if you want to see the colored version of it, though it will open with any text editor just as easily. See below for download instructions.

**[SIZE="4"]Development[/SIZE]**

This project actually ended up being a bit bigger than I thought it would be. I started out looking for a simple way to run a script when my UPS was below, say 20%, and after failing at getting APCUPSD to work (it might have worked if I tried harder), and failing to find simple solutions online to this problem, the fact that the OS was already detecting when my UPS was running on battery power, and what percent the battery was at made me think - "I could easily whip up a simple script that would get its information from the same place the popups that I kept seeing are getting it from, and use cron to trigger it".

If you guys know of a simpler way to accomplish this, let me know. Otherwise, I hope someone finds this useful.

While I've run plenty of tests, if you try this and find bugs, let me know.

**[SIZE="4"]Download[/SIZE]**

In order to get the latest version of the script, first install git:

```
sudo apt-get install git
```

Once that's done, run:

```
git clone git://github.com/terminator14/UPS_watcher.git
```

This will create a UPS_watcher folder in your current working directory with the script in it, as well as the instructions for using it in the INSTALL.rst file.

---

