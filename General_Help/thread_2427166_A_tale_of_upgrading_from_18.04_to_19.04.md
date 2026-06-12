---
title: "A tale of upgrading from 18.04 to 19.04"
date: 2019-09-18
forum: General Help
---

### Post by Edward_Diener on 2019-09-18
I can now run both Ubuntu 18.04 and 19.04 separately on a multi-boot computer with the same hardware. I thought I would write this in case anybody else had the same type of problems I had trying to go from Ubuntu 18.04 to 19.04. I understand that many people would question why I would want to upgrade from a LTS like 18.04 in the first place, but still I want to tell the tale of my problems doing so. This is not an effort of putting down Ubuntu but of helping others out who may run into the same problems I did.

My first effort to upgrade from 18.04 to 19.04 occurred by first trying to update from 18.04 to 18.10 in order to eventually upgrade from 18.10 to 19.04, when 18.10 was available as the next supported release. I both tried the graphical update path and the console window update path, both essentially doing the same eventual upgrade in both cases which downloads and installs the upgraded files, and then has the user reboot the system to complete the upgrade. In both cases the first part went without a hitch, but when I rebooted my system and chose from the grub menu the latest Ubuntu choice, the boot sequence would start but eventually just hang before the final screen showing the boot login dialog. What I would see were messages such as:

Starting GNOME Display Manager...
Started OpenVPN Service.
Starting Hostname Service...
Started Hostname Service.
Starting Network Manager Script Dispatcher Service...
Started Network Manager Script Dispatcher Service.
Started Accounts Service.
Started Modem Manager.
Started Gnome Display Manager.
fsckd-cancel-msg press Ctrl+C to cancel all filesystem checks in progress

and then everything would halt. I tried manually checking all my partitions but everything was OK. I made the upgrade effort a number of times, restoring Ubuntu 18.04 backups each time before I would try again and attempting various changes to my Ubuntu 18.04 setup like changing my video adapter drivers from proprietary to the Noveau drivers, but nothing worked and eventually I got tired and stuck to 18.04.

Finally I noticed that the 18.10 supported time had run out and that 19.04 was offered directly as an upgrade from my 18.04 installation. Maybe the upgrade problem was in 18.10 and upgrading to 19.04 would solve my problem. So I tried the graphical update from 18.04 to 19.04. Once again the actual graphical update worked flawlessly but when I tried again the reboot process to get to 19.04 the exact same hangup would occur just before the final Login screen should have appeared.

Someone had suggested I just install 19.04 from scratch but not to overwrite my /home partition but just let 19.04 install on top of it. So to be safe I copied my 18.04 system to new partitions with a gparted boot DVD, gave the new partitions their own unique UUIDs, and booted up the 19.04 DVD successfully on my computer. Then I installed 19.04, choosing the partitions I had copied as the ones I wanted to use for Ubuntu 19.04, making sure not to reformat my /home partiton, but to reformat my / and /boot partitions, installing Minimal Software, and choosing to install the proprietary drivers/codecs etc. as part of the install. Everything went fine for installing 19.04, and now I rebooted my computer agaian and chose the Ubuntu 19.04 system I had just installed.

!!! The exact same problem which had occurred when I had tried to upgrade to 19.04 occurred as when I had installed 19.04 from scratch ! I hung up at the exact same point in the bootup sequence as before, and this was on a fresh install of 19.04. Definitely something wrong with Ubuntu I thought, and was about to give up using the OS entirely although I like the system and I know Ubuntu has an excellent reputation. Something in my hardware Ubuntu beyond 18.04 does not like.

I then decide to give the fresh installation one more shot, not thinking that anything I might do would get Ubuntu 19.04 to work on my computer. I booted the 19.04 DVD again, installed Ubuntu 19.04 to the partitions I had setup, did a minimal install, formatted all my partitions, not that I think not wiping out all my previous /home partition's data should have caused any problem but just playing it safe, and not choosing the installation of proprietary drivers and codecs. As before the install from the Ubuntu 19.04 DVD went smoothly, and now I rebooted my computer and chose the Ubuntu 19.04 bootup. Well you can guess the rest. This time there was no hang-up at the end of the boot sequence and the Login screen came up as it should and I was able to login to Ubuntu 19.04 successfully.

I stiil do not know why I could not upgrade or why my initial attempt to install 19.04 fresh failed also. My guess is that installing the proprietary driver/codecs caused the problem at bootup, for I doubt that keeping my old files in my /home partition could have affected just booting into a new release. i am writing this so that if anybody else has similar problems they might be able to follow my path to a solution. My hardware is only a few years old, and I am able to boot successfully other OSs including Windows 10 and a number of other Linux distros. This does not mean that Ubuntu is bad in any way but simply that for my hardware it has proved more problematical than other OSs to which I can multi-boot.

---

### Post by mastablasta on 2019-09-19
18.04 to 19.10 directly will not work. 
the issue is that 18.04 to 18.10 didn't work as it should.

these upgrades... i mean they really should do something about them.

in any case: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

it seems most advise having separate home partition and doing fresh install. kind of ridiculous since this isn't the 90's anymore. windows upgrades every 6 months. and aside from their issue with testing bugs and seeing the reported bugs, the upgrade works. at least it did until now . especially on enterprise edition (which is what LTS is supposed to be). i mean if it didn't businesses would be quick to find an alternative.

---

### Post by Edward_Diener on 2019-09-19
> **mastablasta said:**
> 18.04 to 19.10 directly will not work. 
the issue is that 18.04 to 18.10 didn't work as it should.

these upgrades... i mean they really should do something about them.

in any case: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

it seems most advise having separate home partition and doing fresh install. kind of ridiculous since this isn't the 90's anymore. windows upgrades every 6 months. and aside from their issue with testing bugs and seeing the reported bugs, the upgrade works. at least it did until now . especially on enterprise edition (which is what LTS is supposed to be). i mean if it didn't businesses would be quick to find an alternative.

It was otiginally 18.04 to 18.10 and then when 18.10 was no longer officially supported it was 18.04 to 19.04. Both were allowed at different times by the graphical upgrader in 18.04. Thanks for the link for reporting bugs.

---

### Post by deadflowr on 2019-09-19
Because of the shorter support period for non-lts release, users who want to upgrade (for whatever insane reason.)
Would get stuck on an unsupported release after support for that next release came to an end.
To fix that Ubuntu now opens the channel for upgrades to the next supported release.
When 19.04 ends it's life, support will open for 18.04 to 19.10.
And 19.10 support should end right around the time 20.04.1 comes out and upgrade support channel opens for that.

---

### Post by mastablasta on 2019-09-20
> **Edward_Diener said:**
> It was otiginally 18.04 to 18.10 and then when 18.10 was no longer officially supported it was 18.04 to 19.04. Both were allowed at different times by the graphical upgrader in 18.04. Thanks for the link for reporting bugs.


sometimes upgrade is done half way through. in that case system will believe it is at for example 18.10 while in fact it hasnt' upgraded yet. that is why it could offer upgrade to 19.04. 

there is also option to do EOL upgrades: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

but i understand why it all felt frustrating. i went through this myself when trying to upgrade Kubuntu from 14.04 to 16.04, only to get stuck in middle of process. i later found out that this was actually not possible (it still isn't) even though the updater was telling me to do it. the only solution was to turn off the updater. so lame...

---

### Post by Edward_Diener on 2019-09-20
> **mastablasta said:**
> sometimes upgrade is done half way through. in that case system will believe it is at for example 18.10 while in fact it hasnt' upgraded yet. that is why it could offer upgrade to 19.04. 

there is also option to do EOL upgrades: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

but i understand why it all felt frustrating. i went through this myself when trying to upgrade Kubuntu from 14.04 to 16.04, only to get stuck in middle of process. i later found out that this was actually not possible (it still isn't) even though the updater was telling me to do it. the only solution was to turn off the updater. so lame...

Ubuntu does supply newer releases, even if those releases are not LTS. Even when I initially tried just installing 19.04 from the bootup DVD it should not really fail just because I choose to install proprietary drivers/codecs. Maybe the thing to learn is that unless a Ubuntu release is LTS there is no point in upgrading or installing it unless you are willing to deal with basic failures. I guess I never expected a basic failure of a Ubuntu release would be that I could not even boot it unless I chose not to install its proprietary drivers/codecs <g>. I know others have suggested to only upgrade/install a Ubuntu LTS release, so maybe that is the wise advice to follow.

---

