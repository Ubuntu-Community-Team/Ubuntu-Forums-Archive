---
title: "wireress not working after update"
date: 2013-01-29
forum: General Help
---

### Post by jadtech on 2013-01-29
OK here is the deal running Hp pavillion g6 BOught it new last spring Installed Ubuntu on it has been working great,

over the last few days there have been it seems a load of updates I dont always reboot after updates always how ever this morning there was updates and suddendly the broadcom sta wont log on our internet service ..

I opted to remove the broad com driver and got  the linux driver to  work not the best driver .. 

my question  was there a problem I was not alerted to with  some update or patch or something I missed to repair  my issues  because I can not see how the updates I had today could mess up a either card driver :) 

help love Ubuntu but I have not been able to get any info on and issue or repair for this so far but time is money I dont want to install microsoft windows but if it is the only working solution it is what I will do . 

if it helps I bleave a few days ago there was a broadcom driver update but no Idea why it would decided not to work now .. 

thanks

---

### Post by jadtech on 2013-01-29
??? anyone have  an answer as to how to get the driver working again  >>>

---

### Post by GordThompson on 2013-01-29
I just looked in Synaptic Package Manager on my Ubuntu 12.04 LTS box and it shows two versions of 'bcmwl-kernel-source':

5.100.82.38+bdcom-0ubuntu6.1 (precise-updates)
5.100.82.38+bdcom-0ubuntu6 (precise)

Maybe you could try to force-install the older version and see if that fixes your problem...?

---

### Post by noletolucas on 2013-01-29
same issue. i updated today (21/01/2013) and after rebooting wireless stopped working. :(

---

### Post by GordThompson on 2013-01-29
> **noletolucas said:**
> same issue. i updated today (21/01/2013) and after rebooting wireless stopped working. :(
Same recommendation: Try reverting to the earlier version of the driver and see if that solves the problem.

---

### Post by noletolucas on 2013-01-29
> **GordThompson said:**
> Same recommendation: Try reverting to the earlier version of the driver and see if that solves the problem.

ehehe if I only knew how to do that...

---

### Post by jadtech on 2013-01-30
if any one has some walk through on this ???

I know it isnt Rocket sceince im a bit rusty nor having  helped other here for a bit  as far as I know it is possble to have more then one version of a dtriver installed, if that is right than the question is  how to get the older version and how to install it :)

---

### Post by jadtech on 2013-01-30
hopefully someone  who can  help lead through the answer will find this post.

I know I am not the only one who  has this issue , the temporary solution is to remove the Broadcom STA proprietary driver the orginal lixus driver will take over its not Ideal but works  with out hard wiring in ..

---

### Post by GordThompson on 2013-01-30
Well, to help out a neighbor (eh?), see if the following works for you:

Start by opening a Terminal window. First, get everything up-to-date

```
sudo apt-get update && sudo apt-get upgrade
```Next, downgrade the driver

```
sudo apt-get install bcmwl-kernel-source=5.100.82.38+bdcom-0ubuntu6
```Then, pin that package so `apt` won't upgrade you back to the (presumably) broken one. Use the command...

```
sudo nano /etc/apt/preferences
```...and add the following block to that file:

```
Package: bcmwl-kernel-source
Pin: version 5.100.82.38*
Pin-priority: 1001
```Give that a try and let us know how it went.

---

### Post by jadtech on 2013-01-30
ok I wont say  the info you gave didn't work it dio just what you intended How ever it still didnt correct the problem at all the broad com sta driver is not working at all . 

I am on wireless with the driver that comes on the 12.04 install dvd I have that installs with ubuntu this works  but not well very weak signal if you move 10 foot from the router nothing .. 

 i cant say it was the driver up date  that caused the issue  over the last days there have been alot of updates that broad com sta driver was one of many  updated including kernal up dates and more  .

---

### Post by GordThompson on 2013-01-30
Did you try restarting your machine after making the changes? Sometimes a machine needs a reboot for driver changes to take effect.

---

### Post by jadtech on 2013-01-30
yeah I did the reboot
ok sory keep getting interrupted here with things ,

I followed everything you post  but I didnt do the pin I did the reboot and it was running the same driver I was using before I booted I went in system setting choose to install the broad com STA driver at which point after the install was going it disconnected my internet connection and even after reboot wouldnt reconnect .
I removed Deactivated it and it couldnt find any drivers so I did a cold shut down restarted and when it booted it all connected again as if I never did anything  .. 

as soon as I try to install the broad com sta driver that had worked before  I updated the other day everything  goes wrong ..

---

### Post by GordThompson on 2013-01-30
Okay, then let's see where we stand. Please post the results from...

```
nm-tool
```...and...

```
aptitude versions bcmwl-kernel-source
```(If you don't already have aptitude installed then install it via `sudo apt-get install aptitude`.)

---

### Post by jadtech on 2013-01-30
ok here  goes 

 Device: wlan0  [Imagination Movers Cafe] -------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:23:80:F1

  Capabilities:
    Speed:           48 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Imagination Movers Cafe: Infra, 68:7F:74:81:EF:0F, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WPA WPA2
    dlink:           Infra, 00:24:01:29:C5:C5, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.226.1.93
    DNS:             24.226.10.193
    DNS:             24.226.10.194


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6B:CF:B9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



--------------------------------------

The program 'aptitude' is currently not installed.  You can install it by typing:
sudo apt-get install aptitude


that is what I get

ok sorry Interupted again  here is result from aptitude after it was intstalled 

Package bcmwl-kernel-source:                        
p   5.100.82.38+bdcom-0ubuntu6                    precise                   500 
p   6.20.155.1+bdcom-0ubuntu0.0.1                 precise-updates           500 

Package bcmwl-kernel-source:i386:
p   5.100.82.38+bdcom-0ubuntu6                    precise                   500 
p   6.20.155.1+bdcom-0ubuntu0.0.1                 precise-updates           500

---

### Post by GordThompson on 2013-01-30
Okay, like the message says, do...

```
sudo apt-get install aptitude
```...and then show us the results from...

```
aptitude versions bcmwl-kernel-source
```Also, the output from the following command would be helpful:

```
lspci -vvnn | grep 14e4
```

---

### Post by jadtech on 2013-01-30
ok sorry Interupted again here is result from aptitude after it was intstalled 

Package bcmwl-kernel-source: 
p 5.100.82.38+bdcom-0ubuntu6 precise 500 
p 6.20.155.1+bdcom-0ubuntu0.0.1 precise-updates 500 

Package bcmwl-kernel-source:i386:
p 5.100.82.38+bdcom-0ubuntu6 precise 500 
p 6.20.155.1+bdcom-0ubuntu0.0.1 precise-updates 500
-----------------------------
grep results 

07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)




I guess we crossed paths :)

---

### Post by GordThompson on 2013-01-30
I believe what happened last time was this:

You installed the older STA driver ('bcmwl-kernel-source', a.k.a. 'wl') but you didn't pin it. After rebooting you were still on the 'brcmsmac' driver because it had precedence and wasn't blacklisted. When you installed the STA driver *again *you upgraded it to the newer (presumably broken) version because you hadn't pinned the older version. That messed you up so you had to deactivate the STA driver and you were back using the 'brcmsmac' driver.

My recommendation: Reinstall the older version of 'bcmwl-kernel-source' and then **PIN IT**. (See above for steps.) Reboot. After restarting your machine if you are still on the 'brcmsmac' driver then blacklist it (and its friend) by running the command...

```
sudo nano -w /etc/modprobe.d/blacklist.conf
```...and adding the following lines to the end of that file:

```
blacklist bcma
blacklist brmcsmac
```Reboot again. See if you are now using the 'wl' driver.

---

### Post by jadtech on 2013-01-30
ok I will get on this in just a few here :) 

I have a 3 year old here and I Run a hopfully up and coming E zine  with  lap top issues I have fallen behind a bit the lap top being my only  connection to the net at this time :)  on that and my son is not great help today hehe . 

let you know how it turns out hope fully this wor s hehe I do have win 7 still installled  but  I cant get that going because then down arrow on the key board  isnt working and there is no touch pad or pointer on boot screen blahhh

---

### Post by jadtech on 2013-01-30
ok Im back Here is where I am at 

I went through  all the process again update down grade then I pinned this time as directed I rebooted .. 
ok this is where i am at lap top rebooted still on the old driver so far as I can tell  and signal strength appears not good cant say if it is or isnt .. 
 it booted and loged me in already online i lopened the broswer came here made no other changes .. 

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Imagination Movers Cafe] -------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:23:80:F1

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Imagination Movers Cafe: Infra, 68:7F:74:81:EF:0F, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    dlink:           Infra, 00:24:01:29:C5:C5, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.226.1.93
    DNS:             24.226.10.193
    DNS:             24.226.10.194


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6B:CF:B9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

----------------------------------------

aptitude versions bcmwl-kernel-source
Package bcmwl-kernel-source:                        
i   5.100.82.38+bdcom-0ubuntu6                    precise                   500 
p   6.20.155.1+bdcom-0ubuntu0.0.1                 precise-updates           500 

Package bcmwl-kernel-source:i386:
p   5.100.82.38+bdcom-0ubuntu6                    precise                   500 
p   6.20.155.1+bdcom-0ubuntu0.0.1                 precise-updates           500
------------------------------------------------------

 lspci -vvnn | grep 14e4
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)


this is where it is at I did not black list the brmcsmac as it  seems to be the only driver working at the time all be it not the best ..

---

### Post by GordThompson on 2013-01-30
> **jadtech said:**
> I did not black list the brmcsmac as it  seems to be the only driver working at the time all be it not the best ..
I understand your reluctance but if the 'brcmsmac' driver trumps the 'wl' driver then you'll never know if 'wl' is working unless you blacklist 'brcmsmac' (and its sidekick). Try it, and if after a reboot you can't connect *at all *then remove the blacklist entries and you can try some other solution.

---

### Post by jadtech on 2013-01-30
well not sure how to unblack list this is somethings I never had  to get involved in when I would help out with Getting bad OS upgrades  going and such :)
I do have  the option to install the broad come driver still  I didnt  do that this time on reboot .. 
 I did do the pin before the reboot that seems not to matter how to un black list is a concern if it dont work ..

---

### Post by GordThompson on 2013-01-30
> **jadtech said:**
> well not sure how to unblack list
Think about it. You've been told that blacklisting drivers involves adding corresponding lines to the...

/etc/modprobe.d/blacklist.conf

..file. If you wanted to REMOVE driver(s) from the blacklist, can you hazard a guess as to how you might do that?

---

### Post by apochry on 2013-01-30
Hi,
I had the exact same problem with my Broadcom 'BCM4313 802.11b/g/n Wireless LAN Controller' and this [s]fixed it like a charm.[/s]  [COLOR=Red]didn't fix it.[/COLOR]

```

sudo modprobe -r wl
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe b43
sudo rm /etc/modprobe.d/broadcom-sta-common.conf

```Here is the original post from [bob ba]("http://askubuntu.com/users/126502/bob-ba") on [askubuntu.com]("http://askubuntu.com/questions/247993/cant-connect-to-any-wireless-connection-after-updating").

I didn't go trough all the three pages of previous post, just read your first description, but I guess this will do the job. If you have already loaded another driver in place of 'wl' you might need to substitute 'wl' in the first line.

---

### Post by jadtech on 2013-01-30
apochry

THat decribes the issue to nearly  exact and according to the time fame of 4 days ago on theat link  the same time frame all the updates started happening on my end here as well . .

GordThompson I am going to take a wild guess if I  use the same code I used to black list it will open the file and choose to remove the drivers from the list  delete them out ? 

Im not Really a computer nerd I just play one I really only have a monocle hehe !!!

---

### Post by noletolucas on 2013-01-30
I figured you can revert a package version using "Synaptics" -- not sure if you need to be online in order to do that.

I guess it does exactly what GordThompson mentioned.

So, if you find it easier:
[LIST=1]
[*] go to "Synaptics"
[*] select the "bcmwl-kernel-source" package
[*] click on the menu "Package", "Force version". Choose the version "5.100..."
[*] click the "apply" button
[*] click on the menu "Package", "Lock version"
[/LIST]

[IMG]http://s17.postimage.org/ijopz68mn/change_package_version.png[/IMG]

---

### Post by GordThompson on 2013-01-31
> **apochry said:**
> Hi,
I had the exact same problem with my Broadcom 'BCM4313 802.11b/g/n Wireless LAN Controller' and this fixed it like a charm.

```

sudo modprobe -r wl
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe b43
sudo rm /etc/modprobe.d/broadcom-sta-common.conf

```Here is the original post from [bob ba]("http://askubuntu.com/users/126502/bob-ba") on [askubuntu.com]("http://askubuntu.com/questions/247993/cant-connect-to-any-wireless-connection-after-updating").

I didn't go trough all the three pages of previous post, just read your first description, but I guess this will do the job. If you have already loaded another driver in place of 'wl' you might need to substitute 'wl' in the first line.
If the 'b43' driver worked for you that's great. It could be that the b43 developers got BCM4313 support to work; if so then they haven't updated the page [here]("http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices") which says

> Chips that are not supported include:
[...]
    BCM4313 - chipset uses unsupported LCN PHY, we work on itPerhaps the OP can try the 'b43' driver if downgrading the 'wl' driver doesn't work out.

---

### Post by GordThompson on 2013-01-31
> **jadtech said:**
> I am going to take a wild guess if I  use the same code I used to black list it will open the file and choose to remove the drivers from the list  delete them out ?
Yes, if you want to "un-blacklist" a driver you just delete (or comment out) the corresponding line you added in

/etc/modprobe.d/blacklist.conf

---

### Post by GordThompson on 2013-01-31
> **noletolucas said:**
> I figured you can revert a package version using "Synaptics" -- not sure if you need to be online in order to do that.

I guess it does exactly what GordThompson mentioned.

So, if you find it easier:
[LIST=1]
[*] go to "Synaptics"
[*] select the "bcmwl-kernel-source" package
[*] click on the menu "Package", "Force version". Choose the version "5.100..."
[*] click the "apply" button
[*] click on the menu "Package", "Lock version"
[/LIST]
Yes, Synaptic Package Manager can downgrade the driver package, but unfortunately the "Lock version" feature in Synaptic applies ***only ***to Synaptic. Both `apt-get upgrade` and the Software Updates application ("Muon Update Manager" in kubuntu) will try to upgrade the driver if it is not "pinned" in apt, even if it *is *"locked" in Synaptic.

---

### Post by apochry on 2013-01-31
> **apochry said:**
> Hi,
I had the exact same problem with my Broadcom 'BCM4313 802.11b/g/n Wireless LAN Controller' and this fixed it like a charm.

```

sudo modprobe -r wl
sudo apt-get install linux-firmware-nonfree
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe b43
sudo rm /etc/modprobe.d/broadcom-sta-common.conf

```Here is the original post from [bob ba]("http://askubuntu.com/users/126502/bob-ba") on [askubuntu.com]("http://askubuntu.com/questions/247993/cant-connect-to-any-wireless-connection-after-updating").

I didn't go trough all the three pages of previous post, just read your first description, but I guess this will do the job. If you have already loaded another driver in place of 'wl' you might need to substitute 'wl' in the first line.

Well, It turns out this haven't solved my issue to the desired extent. Yesterday I wasn't at all able to connect to my home wifi so I changed to the 'b43' driver, which seemed to have solved the problem. Today at the university, where we have WPA2 Enterprise security, I get disconnected every 5 minutes. Now I switched to the driver provided by jockey (Broadcom 802.11 Linux STA wireless driver source, package is bcmwl-kernel-source, version 6.20.155.1+bdcom-0ubuntu0.0.1) and it seems stable for the last 10-15 minutes.
[COLOR=Red]
EDIT: It was stable until I've put my laptop to sleep and moved to another building of the university. Than it wasn't able to connect at all. I'm home now and I can not connect to my home network either. I think I went back the initial situation by reverting to the 'wl' driver.[/COLOR]

---

### Post by jadtech on 2013-01-31
ok so to this point I have done nothing there was 2 glib updates this morning  I installed other then that I have meade no changes.

this morning how ever there is the yellow lock on the top tool bar asking me to install drivers ..

not sure if these are new drivers or the same old ones I been removing  either way other then the updates thing still sit where i left off yesterday I had to sleep while while I could :)

---

### Post by GordThompson on 2013-01-31
I believe that the next step was for you to take the plunge and blacklist the 'bcma' and 'brmcsmac' drivers to see if that lets the 'wl' driver take over. Before doing that you might want to peruse the thread [here]("http://ubuntuforums.org/showthread.php?t=1889170") (at least the first couple of posts) to get some more background on the types of changes you are making and why you are making them (particularly w.r.t. conflicting drivers).

---

### Post by GordThompson on 2013-01-31
> **apochry said:**
> Now I switched to the driver provided by jockey (Broadcom 802.11 Linux STA wireless driver source, package is bcmwl-kernel-source, version 6.20.155.1+bdcom-0ubuntu0.0.1) and it seems stable for the last 10-15 minutes.
[COLOR=Red]
EDIT: It was stable until I've put my laptop to sleep and moved to another building of the university. Than it wasn't able to connect at all. I'm home now and I can not connect to my home network either. I think I went back the initial situation by reverting to the 'wl' driver.[/COLOR]
Have you tried downgrading the 'wl' driver back to the earlier 5.x version?

---

### Post by jadtech on 2013-01-31
wow IM back been very busy all day  

I understand the reasoning and purpose of black listing  the driver from working for sure .. 
heh my reluctance as I pointed out is that it is at this point the only working driver and this is the only computer or computer acess I have  at the moment if I black list that and things dont work im out of luck I dont even have or use a mobile phone :) 

I mean my wife does have a laptop how ever I run business online and using it many hours a day would be an issue .. 

I am copying all the detail here down so I have them hehe  I know its nuts to run an online business  and not have extra equipment but we are just getting start here money is tight :) 

at this point she is here watching me load of doubt in her eyes anything needs fixing at all after all I am logged on here and I have been warned if things get broken there is no way to replace anything at this time im just out of luck there is $0 sinced  she is just getting back to work after a year unemployed  ..
 
so my reluctance is a mix of things all in one hehe 

thoughI know things arent quite right even thoughI am using wireless at this time the wirless light on the key baod is a no connection orange :)

---

### Post by jadtech on 2013-01-31
ok so I have all the info coped in notes just incase I chacked the driver I pinned yesterday shows its still pinned . 

should I go through The  whole  down grade and install before I black list ??

---

### Post by GordThompson on 2013-02-01
> **jadtech said:**
> my reluctance as I pointed out is that it is at this point the only working driver and this is the only computer or computer acess I have  at the moment if I black list that and things dont work im out of luck
Do you have an Ethernet cable? If not, you really should have one as a fallback in case some future update trashes your wireless connectivity completely. (Excuse the pessimism, but as you can see from searching this forum, AskUbuntu, etc., BCM43xx wireless support is a bit of a mess right now.)

---

### Post by GordThompson on 2013-02-01
> **jadtech said:**
> should I go through The  whole  down grade and install before I black list ??
It shouldn't be necessary if you were successful the last time, but it wouldn't hurt to check the output from...

```
aptitude versions bcmwl-kernel-source
```
...just to make sure that the installed version (flagged as 'i') is still 5.100.82.3....

---

### Post by jadtech on 2013-02-01
Package bcmwl-kernel-source:                        
i   5.100.82.38+bdcom-0ubuntu6                    precise                   500 
p   6.20.155.1+bdcom-0ubuntu0.0.1                 precise-updates           500 

Package bcmwl-kernel-source:i386:
p   5.100.82.38+bdcom-0ubuntu6                    precise                   500 
p   6.20.155.1+bdcom-0ubuntu0.0.1                 precise-updates     

thats what I get looks  good to me not sure what the update is  .

I dont have a cable to hard wire in  here right now  our situation here is  complicated let just say we are liturally starting  over from nothing :)

---

### Post by GordThompson on 2013-02-01
> **jadtech said:**
> I dont have a cable to hard wire in  here right now
The choice is yours (with significant input from your wife, of course) but if you are really counting on that machine to run your business then $10 for an inexpensive Ethernet cable sounds like cheap insurance to me....

---

### Post by jadtech on 2013-02-01
ok here is where it stands the drivers are on the black list confermed this  how ever it still booted using the bmac driver.. 

the odd thing I did note is that on shut down before the reboot  message up said it couldnt find a reliable driver  for something then rebooted ..  not sure I can black list the only working driver SHrug !?!?!?! 
whenI logged in it was logged on line I did a check found this 

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Imagination Movers Cafe] -------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:23:80:F1

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Imagination Movers Cafe: Infra, 68:7F:74:81:EF:0F, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2
    dlink:           Infra, 00:24:01:29:C5:C5, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.226.1.93
    DNS:             24.226.10.193
    DNS:             24.226.10.194


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6B:CF:B9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

----------------------------------------

for the record this is how the black list looks 
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist bcma
blacklist brmcsmac

this is the avaliable proptary driver avable on the list not  actived 

his package contains Broadcom 802.11 Linux STA wireless driver for use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-, BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-based hardware.

---

### Post by GordThompson on 2013-02-01
Sorry, I forgot a step:

After changing "blacklist" entries you need to update the initramfs for the kernel, *then *reboot.

```
sudo update-initramfs -u
```Note that if you want to "un-blacklist" those drivers you need to remove the "blacklist" lines from the blacklist.conf file, run the above command again, then reboot.

---

### Post by jadtech on 2013-02-01
hehe 
learning something news everyday I guess 

Then you think dont be worried about the shut down warning and the fact that its been nearly an hour since the reboot  the system settings is  still searching  for a valid relieable driver ??

---

### Post by GordThompson on 2013-02-01
Not sure about the "searching..." message. You have rebooted and your WiFi is working? What do you get from

```
nm-tool
```

---

### Post by jadtech on 2013-02-01
i posted it  once but here it is again :) 

the scanning could have been something freaking out from when I did the cpoy and paste from  the setting  I was in there I dont always pay attention  to the desk top since im stapled mostly to chrome hehe 

Might as well be running a chrome book  I think on some days 

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Imagination Movers Cafe] -------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:23:80:F1

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Imagination Movers Cafe: Infra, 68:7F:74:81:EF:0F, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    dlink:           Infra, 00:24:01:29:C5:C5, Freq 2417 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.226.1.93
    DNS:             24.226.10.193
    DNS:             24.226.10.194


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6B:CF:B9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by GordThompson on 2013-02-01
> **jadtech said:**
> i posted it  once but here it is again :) 
I wanted to see if anything had changed after you did the `sudo update-initramfs -u` and then rebooted again. Did you do that? If so, does the `nm-tool` output *still *show 'brcmsmac' as the active driver?

---

### Post by jadtech on 2013-02-01
Not yet my bad :P 

I thought you  wanted to see it before  going now to run the code and reboot

---

### Post by jadtech on 2013-02-01
ok still using it after the -initramfs -u everything still looks black listed  and pinned as it was . 

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Imagination Movers Cafe] -------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:23:80:F1

  Capabilities:
    Speed:           36 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    dlink:           Infra, 00:24:01:29:C5:C5, Freq 2417 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    *Imagination Movers Cafe: Infra, 68:7F:74:81:EF:0F, Freq 2462 MHz, Rate 54 Mb/s, Strength 43 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             24.226.1.93
    DNS:             24.226.10.193
    DNS:             24.226.10.194


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6B:CF:B9

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by GordThompson on 2013-02-01
[LEFT]Hmmm, some other module might be loading and bringing 'brcmsmac' along for the ride. What does the following command tell you?

```
lsmod | grep brcmsmac
```[/LEFT]

---

### Post by jadtech on 2013-02-01
lsmod | grep brcmsmac
brcmsmac              570930  0 
mac80211              506862  1 brcmsmac
brcmutil               15139  1 brcmsmac
cfg80211              205774  2 brcmsmac,mac80211
crc8                   12893  1 brcmsmac
cordic                 12574  1 brcmsmac

there you have it this driver was built in  12:04 when I installed from dvd , all I did after install back when was to active the proptary driver ..

---

### Post by Sharpie1 on 2013-02-01
My wireless stopped working about 4 days ago. I connected to the internet via Ethernet, went to the "additional drivers"  control panel, selected the Broadcom STA proprietary driver and removed it. 
Removed the ethernet and my wireless connected again...
just my 2c

Sharpie1

---

### Post by jadtech on 2013-02-01
yeah the wireless here is working too after removing the STA driver that the update killed  however the driver is not Ideal signal is weak and connection trends to drop if I move more then 10 feet from the router .

I have been trying to black list the Bmac driver and down grade to the oler sta driver  that worked before the upgrade

---

### Post by GordThompson on 2013-02-02
I borrowed a friend's HP notebook that has the same wireless adapter (BCM4313 [14e4:4727]) and tested it under 64-bit Kubuntu 12.04 LTS. Here's what I found:

Immediately after installing 12.04 along with the STA driver ('wl') the wireless adapter worked fine. Then when Update Manager told me that updates were available I took them all, including the updates to the STA driver and the latest kernel image. After the updates were finished the machine told me that it needed to restart to complete the installation.

I expected the wireless connection to be dead after the updates, but it wasn't. I was still using 'wl' (the updated 6.x version) and my wireless connection was working fine.

Still, while I had the machine I figured I'd try downgrading the 'wl' driver to the older 5.x version and see if that would work. It did, sort of: After downgrading (and pinning) the driver and restarting the machine my wireless connection was still working, but it was using the 'brcmsmac' driver. 

I did `sudo rmmod brcmsmac` to disable that driver, and that killed my wireless connection (as expected). However, when I did `sudo modprobe wl` my wireless connection did not come back.

Still curious, I blacklisted 'brcmsmac', did the `update-initramfs` thing, and rebooted again. This time I had no wireless connection. I tried forcing 'wl' to load but that didn't work.

Finally, I thought I'd see if 'b43' would work so I tried to install it, but `sudo apt-get install firmware-b43-installer` complained with "Unsupported device(s) found: PCI id 14e4:4727 \ Aborting."

Summary: 

- I was unable to recreate your original issue. I don't doubt that the recent update to the 'wl' driver broke some people's BCM4313 wireless connections, but it didn't break "mine".

- Downgrading the 'wl' driver to the older 5.x version doesn't seem to help. It appears that the 5.x version won't work with the rest of the updates in place, and the machine uses 'brcmsmac' as a fallback. So, downgrading the 'wl' driver and disabling it both amount to the same thing: you wind up using 'brcmsmac'.

- Substituting the 'b43' driver does not appear to be a viable option.


So, at this point all I can suggest is that you limp along with 'brcmsmac', keep an eye on the versions of 'bcmwl-kernel-source' that are available until a newer one appears, and then try re-enabling the STA ('wl') driver to see if the problem is fixed. 

Good luck!

p.s. - Remember to remove the 'pin' entry from /etc/act/preferences, remove the 'blacklist' lines you added to blacklist.conf, and run the `sudo update-initramfs -u` command again.

p.p.s. - If you were wondering why your blacklisting wasn't working it's because there was a typo in the post where I gave the blacklist entries (post #17). It says to blacklist 'brmcsmac', not 'brcmsmac'. Sorry about that....

---

### Post by jadtech on 2013-02-02
Very interesting GO figure

the issue I do have with this driver is that it  is not the best its signal is always weak and it disconnects a few times a day and wont reconnect unless I reboot . 

I did have a few odd updates  over the last day nothing  connected to the driver  as far as I could tell hopfully the fix will come about sooner then later.. 

I will look into getting a cable  and a wireless keyboard since  the down key isnt working I cant  even change what OS boots even though I havent used windows now in serveral years if the connection gives up I would still have windows as a back up . 

I know im not the only one who has the issue more and more are surfacing ..

---

### Post by jadtech on 2013-02-02
ok so I unpinned everything ubanned everything and rebooted  I am back where I started .

The way I see it at this point if nothing else I have learned these things to go long with everything else I have learnedthe last 3 years hehe .

would you know it what pops up on reboot an update for STA

ok im back to working  with the bmac driver unpinning caused the driver to update and install which took me throughthe whole nightmare all over again bacause the Bmac driver was gone and I had no wireless had to install the boot disc to get it going again .. 

not sure what changes they made but they forsure don not work and break the wireless on this HP

---

### Post by apochry on 2013-02-03
> **GordThompson said:**
> Have you tried downgrading the 'wl' driver back to the earlier 5.x version?

I have. You know the result - you have tried it yourself on your friends laptop - it didn't work. 
The strange thing is that the proprietary 'wl' driver v.6.x seems to - kind of - work and connects to the university's wifi , which is WPA2 Enterprise secured (the issue to be unable to connect again after changing AP persist though) Home,  where I WPA2 Personal, it is useless.
I'm reading this thread from the begging but I've missed the part with `sudo update-initramfs -u` and can't find where you say what it does. Can you please clarify it for me shortly. Thank you!

---

### Post by apochry on 2013-02-03
I decided to stick with the 'brcmsmac' but it doesn't get loaded automatically after reboot. It's not blacklisted in '/etc/modprobe.d/blacklist.conf'.
Any idea what could cause this?

[COLOR=Red]_EDIT:_[/COLOR]
I did some googling and I figured it out.
What I did is to remove the residual 'etc/modprobe.d/broadcom-sta-dkms.conf' where 'brcmsmac' was blacklisted and add 'brcmsmac' to 'etc/modules'. I have also blacklisted ```
b43
b43legacy
bcma
ndiswrapper
``` in '/etc/modprobe.d/blacklist.conf'. I'm not sure if this is actually necessary.
'brcmsmac' is now being loaded at boot time.

Thanks for your help anyway!

---

