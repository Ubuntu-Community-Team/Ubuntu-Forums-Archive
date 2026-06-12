---
title: "Ubuntu 14.04 maintenance guide"
date: 2014-08-31
forum: General Help
---

### Post by tegelstom on 2014-08-31
Hello everyone,
I do some regular maintenance in my Ubuntu 14.04 using the following commands/tools:
1) sudo [COLOR=#333333][FONT=UbuntuMono]apt-get update
[/FONT][/COLOR]2) sudo [COLOR=#333333][FONT=UbuntuMono]apt-get upgrade
[/FONT][/COLOR]3) sudo [COLOR=#333333][FONT=UbuntuMono]apt-get dist-upgrade
[/FONT][/COLOR]4) sudo [COLOR=#333333][FONT=UbuntuMono]apt-get check[/FONT][/COLOR]
5) sudo apt-get install -f, this gives a report for packages to remove or to upgrade, if they are != 0 then I go to synaptics and I do the removal and the upgrades
6) sudo update-apt-xapian-index, I'm not sure what exactly does but I guess it updates a package index, don't know for what reason :)))
7) BleachBit for apt autoclean, autoremove and clean and all the system options checked except Free Disk Space and Memory, cause they need too much time and they are buggy, also I don't check all the Deep Scan options for the same reasons, plus I keep the bash history.
8)Ubuntu Tweak -> Janitor, all options checked, some times I keep some old kernels.
9)GtkOrphan to remove orphaned packages.
Do I missing something or do I do something wrong that it is not necessary?

Thanks in Advance
Thomas

ps: updated from [COLOR=#DD4814][COLOR=#000000][grahammechanical]("http://ubuntuforums.org/member.php?u=1087323")'s link... [/COLOR][/COLOR][https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by rbmorse on 2014-08-31
Most (all?) of the things on your list deal with freeing up disk space, but unless you're really capacity restrained I'd not worry about them until there's an actual need to free up some real estate. 

 Beyond that, utilities like BleachBit, GTKorphan and UbuntuTweak are subjects that often invoke strong opinions by both proponents and opponents of their use...my personal approach is to avoid them because I don't completely understand the ramifications of of some of the things they propose to do. But, that's just me. Others will tell you they perform a valuable service and should be employed regularly. 

One thing I do not see on your list is backup....the /home partition at a very minimum.  That's probably a more pressing need than anything else I can think of.

---

### Post by grahammechanical on 2014-08-31
I think that you will find that in some instances those utilities are often just another way of running some apt-get commands. Check this out and look for apt-get check; apt-get autoclean; apt-get clean; apt-get autoremove.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Regards.

---

### Post by tegelstom on 2014-09-01
@[[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323")[COLOR=#000000]  really useful link, thanks a lot![/COLOR]
[URL="http://ubuntuforums.org/member.php?u=1087323"]
[/URL]

---

### Post by tegelstom on 2014-09-01
@[rbmorse]("http://ubuntuforums.org/member.php?u=82")[SIZE=4][COLOR=#000000], actually I use the most basic partitioning scheme, one primary partition for the root(/) dir and one primary partition for the swap. And other two primary partitions for the windows7. I do take backups the entire disk using Clonezilla.[/COLOR][/SIZE]

---

### Post by tegelstom on 2014-09-19
Ubuntu 14.04 Maintenance Guide
========================================================================================================================================================================
========================================================================================================================================
1) sudo apt-get update


2) sudo apt-get upgrade


3) sudo apt-get dist-upgrade


4) sudo apt-get check


5) sudo apt-get install -f, this gives a report for packages to remove or to upgrade, if they are != 0 then I go to synaptics and I do the removal and the upgrades


6) sudo update-apt-xapian-index, I'm not sure what exactly does but I guess it updates a package index, don't know for what reason ))


7) BleachBit for apt autoclean, autoremove and clean and all the system options checked except Free Disk Space and Memory, cause they need too much time and they are buggy, also I don't check all the Deep Scan options for the same reasons, plus I keep the bash history.


8)Ubuntu Tweak -> Janitor, all options checked, some times I keep some old kernels.


9)GtkOrphan to remove orphaned packages.


10) AGAIN: sudo update-apt-xapian-index, just in case...


****************************************************************************************************************************************


a) Ubuntu Utopic Unicorn
-------------------------
!!!do-release-upgrade -d!!!, t is also possible to use do-release-upgrade to upgrade to a development version of Ubuntu. To accomplish this use the -d switch, CAN CAUSE PROBLEMS.


b) edubuntu sch.gr(for greeks)
-----------------------------------
sudo add-apt-repository ppa:ts.sch.gr
sudo apt-get update
sudo apt-get install sch-scripts


****************************************************************************************************************************************
 
========================================================================================================================================
=======================================================================================================================================================================


See also:
[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by tegelstom on 2014-09-20
Any comments, updates, etc. are very welcome to above maintenance list!
Thank you!
Thomas

---

### Post by tegelstom on 2014-10-02
UPDATE
========
Control your CPU frequency: cpufreq-selector. Useful for new and old laptops, powerbooks... for energy savings and preventing overheating.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
sudo apt-get install -y indicator-cpufreq sysfsutils cpufrequtils

Reboot. Click the newly installed icon (right-top, next to Network, Sound). Choose between Powersave, Performance, Ondemand (default) or Conservative options, or select by processor frequency!

---

