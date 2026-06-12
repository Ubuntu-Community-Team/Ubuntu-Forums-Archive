---
title: "wpa breaks xubuntu"
date: 2007-11-23
forum: General Help
---

### Post by qkmbr22 on 2007-11-23
Hello,

My parents have an old eMachines desktop with 667 Mhz Celeron and 320 MB RAM. The machine ran XP and was pretty slow but it did the job. My dad wanted to install anti-virus on it, but I told him it would make it even slower. Since the machine is only used for minimal internet, email, and word processing, I offered to install a light version of Linux on it, which I hoped would make it faster and would eliminate the need for anti-virus. Having used Ubuntu for a couple of years before getting a macbook, I decided to go with Xubuntu for this desktop.

The computer has a wifi card which works out of the box with (X)Ubuntu 7.10. My dad has a wpa encrypted network at home. After attempting to connect to this wpa network, the whole system seems to break. I thought initially that it was a problem with the hard drive, but I replaced the hard drive and the same problem occurs every time. After attempting to connect, I cannot start any application or work with any opened application. Restarting X is the only thing that works, although it ends up in a blank brown screen. After a hard shut down, the system refuses to boot up with a graphical boot screen, instead writing a bunch of text on the screen. The system stops booting at all when CUPS begins to start up. 

This happens every single time. I've reinstalled the system about 15 times already. I wish I could just use an ethernet cable, but there is no way that's possible in my parent's house.

Does anybody have any suggestions? Any help would be appreciated. I don't want to leave my parents with such a negative impression about Linux and a non-working computer.



[EDIT]

So after a couple of days of fighting this issue, I've finally managed to get it to work. Basically the default driver (ACX111) for the WG311v2 wireless card (which is what i use) doesn't support WPA, so ndiswrapper needs to be used. The solution is in this post [http://ubuntuforums.org/showthread.php?p=3832123#post3832123](http://ubuntuforums.org/showthread.php?p=3832123#post3832123) . Thanks to everybody who helped!

---

### Post by qkmbr22 on 2007-11-23
I tried installing just plain old Ubuntu instead and I get the same issue. As soon as I disable roaming mode in order to enable WPA the system breaks. I was able to restart the computer the normal way, but the graphical boot screen broke into text near the end and the booting process stopped at "starting common unix printing system: cupsd". 

PLEASE help! Please, please, please...

---

### Post by Craigus on 2007-11-23
May I suggest PCFluxboxOS? Tinyflux 1.0 would do what you want. I'm using it with my wpa encrypted network on laptops with no problems:

[http://pcfluxboxos.wikidot.com/]("http://pcfluxboxos.wikidot.com/")

antix also works nicely on another laptop:

[http://antix.mepis.org/index.php/Main_Page]("http://antix.mepis.org/index.php/Main_Page")

Finally, I am also using Dapper xubuntu on another laptop, and that also works fine.

---

### Post by qkmbr22 on 2007-11-23
thanks for the suggestions! I would like to be able to fix Ubuntu because it seems like the more user-friendly choice (if it works of course) and other than this bug, I've had a pretty good experience with it. However, if I can't fix this, then I'll give these a try. So thanks for the links!

However, can anybody help me at least recover my installation so that I could even see the desktop? I've selected the recovery mode in GRUB and it boots into text-mode and logs me in as root. I have not a clue where to start.

---

### Post by ugm6hr on 2007-11-23
> **qkmbr22 said:**
> I tried installing just plain old Ubuntu instead and I get the same issue. As soon as I disable roaming mode in order to enable WPA the system breaks. I was able to restart the computer the normal way, but the graphical boot screen broke into text near the end and the booting process stopped at "starting common unix printing system: cupsd". 

PLEASE help! Please, please, please...

With Ubuntu, why do you disable roaming?  Network Manager should just work, and offer options to connect to all wifi, including encrypted.  Just left-click on the applet in the taskbar (it will look like 2 grey spots).

For Xubuntu, I would recommend you use wicd [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) (served me well with Xubuntu7.04).

EDIT:
Sorry - that's not very clear.  My point is that connecting to WPA should be no harder than point, click, type password in Ubuntu.  In Xubuntu, install wicd, then do the same!

---

### Post by mahousaru on 2007-11-23
If you install it without enabling the WPA have you tried to connect to an non secured network?  Just want to check if it is networking or specifically WPA breaking it.

Before you enable the WPA support check the contents of

/etc/network/interfaces

Then personally if I was you trying to troubleshoot the issue I would open a terminal and do

sudo tail -f /var/log/messages

the -f will display all new messages as they appear.

Have this open in the background so you can see it and then make your changes to the network and see if any error messages appear.

Once it breaks and you have a black screen try

ctrl alt f2

try different function keys and hopefully you can get a command line login.

Login and then check the /etc/network/interfaces file to see what has changed.  Setting that back to how it was hopefully will get it working again.  But the changes might give you a clue about what is causing your system to hang.

Also check System, Administration, System Log, Xorg.0.log

From command line it will be
/var/log/Xorg.0.log

Try to see if there are any error messages there.

What is the make and model of your wireless card?  Maybe check below to see if it is supported.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Goodluck!

---

### Post by qkmbr22 on 2007-11-23
Thanks a lot for all the feedback.

booted in text-mode as root, i first removed the network-manager and rebooted, but that didn't help - the startup froze again while starting cupsd. then i logged into recovery mode again and removed wpasupplicant, because when rebooting that was the thing that was freezing the normal shutdown. Then I was able to boot and see my desktop again. So now I have a functioning install minus network-manager and wpasupplicant. The problem now is that I cannot connect to the network at all and can't install network-manager. Any way to install it from the cd? tried sudo apt-get install network-manager-gnome while the cd is in but no luck. the CD is checked as a source for installing software.

@mahousaru: I'm fairly sure the computer can connect to non protected networks (I tried it a while ago... this is actually a project i started in october). Since I don't have network-manager installed right now, probably not much point in looking at error logs. I think the card is a Netgear WG311 and according to the documentation is supported out of the box.

@ugm6hr: By default if i click on a wpa protected network it asks for a 128-bit WEP password, but WPA is not an option until I disable roaming mode. 

Is it possible that downgrading to 6.06 would help? It seems like the simplest solution right now.

---

### Post by ugm6hr on 2007-11-23
> **qkmbr22 said:**
> @mahousaru: I'm fairly sure the computer can connect to non protected networks (I tried it a while ago... this is actually a project i started in october). Since I don't have network-manager installed right now, probably not much point in looking at error logs. I think the card is a Netgear WG311 and according to the documentation is supported out of the box.
The Netgear WG311T is well supported - it has an Atheros chipset.  You can check that fact with:
```
lspci
```
Look out for Ethernet or Network controller, and you can double-check here [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)

> @ugm6hr: By default if i click on a wpa protected network it asks for a 128-bit WEP password, but WPA is not an option until I disable roaming mode. 
Are you talking about Xubuntu here?  If so, that is because Xubuntu has Network Monitor (not *Manager*).  You still **do not** have to configure WPA manually - wicd does an excellent job.  The .deb is available here: [https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573) so you don't need internet on the Ubuntu machine to install (download, transfer across, double-click).

In Ubuntu, Network Manager in the taskbar should offer you WPA (it did on my WPA network).  If it didn't, I'm not sure why.

> Is it possible that downgrading to 6.06 would help? It seems like the simplest solution right now
I'm not sure how this would help.  I would suggest you re-install Xubuntu from scratch (so no potential "fixes" to interfere), and install Wicd.
The other option - do you have a Ubuntu LiveCD?  If so - you should be able to connect from the LiveCD itself (which will tell you if Ubuntu will work flawlessly).

I can't stress this enough, but wifi management in Ubuntu does not require any editing of files etc **if your network card is recognised automatically**, and the chipset is supported by NM / wicd (Atheros generally are).

---

### Post by mahousaru on 2007-11-23
It is a bit bleh atm as all the documentation is for 7.04

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29)

Seems to think that you need ndiswrapper to get it working properly.  You should take this with a pinch of salt because with my laptop, it needed ndiswrapper for the rt2500 and WPA in 7.04, but it is natively supported in 7.10.

---

### Post by qkmbr22 on 2007-11-23
@mahousaru: the ndiswrapper instructions looked promising but when i checked the wireless adapter with lspci it didn't give the same response. It said it was using a Texas Instruments driver, so i think it is WG311 v2, not v3 or the WG311T. 

@ugm6hr: i'm using Ubuntu (not Xubuntu) right now. When roaming is enabled, I see wpa networks in the drop down list from the network manager applet, but when I click on them I only get 4 options for encryption: WEP 128-bit passphrase, WEP HEX, WEP ascii, or LEAP. I'm also not sure why this happens, I understand WPA should be an option ideally.

I switched the network temporarily to WEP and was able to connect through System > Network and reinstall wpasupplicant and network manager. wicd conflicted with network manager so it wouldn't install. So i did a full system update and the internet was working for a while until i started messing with roaming mode again. Now I can't connect to even WEP. When I try, nm-applet quits and doesn't start up again.

---

### Post by qkmbr22 on 2007-11-23
okay so i'm getting somewhere in determining what the problem is. My card is the WG311v2 which uses the ACX111 driver, which doesn't support WPA (at least for this specific card), so I guess thats why my system crashes when i try using it. The windows driver with ndiswrapper should work with WPA, so now i gotta figure out how to install that.

---

### Post by ugm6hr on 2007-11-23
> **qkmbr22 said:**
> okay so i'm getting somewhere in determining what the problem is. My card is the WG311v2 which uses the ACX111 driver, which doesn't support WPA (at least for this specific card), so I guess thats why my system crashes when i try using it. The windows driver with ndiswrapper should work with WPA, so now i gotta figure out how to install that.

```
lspci
```
This will confirm your chipset (presumably Texas Instruments ACX111) - worth checking before wasting any more time.

I have an ACX111, but have never used it with Ubuntu.  And, as you have realised, the native ACX driver doesn't do WEP.  I did get it to connect to WPA with ndiswrapper (on Puppy Linux) - the only problem with ndiswrapper is finding the *correct* Windows .inf file to get it to work...

As for ndiswrapper - the package *ndisgtk* might make it easier to use, although it was very buggy in the Feisty release (maybe better now).

This might help (see No 31-34) for where to get the Windows drivers:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

Good luck.

---

### Post by qkmbr22 on 2007-11-23
i'm pretty close to giving up and installing xp again. 

i checked lspci and it is listing asx111. I did install the winxp driver for the wg311v2 in ndiswrapper. I used the [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29) tutorial except i replaced the windows driver with the correct one from the netgear website. I switched the network back to WPA and when I tried to configure ubuntu to use WPA I got the same crap again. WPA wasn't an option in network manager and it broke my system again, so i can't boot.

aldkjfalkdjflakjlkja ugh

---

### Post by Craigus on 2007-11-24
My acx111 equipped laptop works out of the box with WPA in antix-M7. ndiswrapper is already set up with the necessary driver. All you have to do is run the Mepis network configuration utility and type in your ssid and wpa key. Give it a try.

[http://antix.mepis.org/index.php/Main_Page]("http://antix.mepis.org/index.php/Main_Page")

---

### Post by ugm6hr on 2007-11-24
> **qkmbr22 said:**
> i'm pretty close to giving up and installing xp again. 

i checked lspci and it is listing asx111. I did install the winxp driver for the wg311v2 in ndiswrapper. I used the [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3?highlight=%28WifiDocs%2FDevice%29) tutorial except i replaced the windows driver with the correct one from the netgear website. 

That tutorial doesn't mention *blacklisting* the native ACX driver, which is a bit rubbish.  Perhaps someone should edit it.

Anyway - your likely problem is that Ubuntu is trying to load both ndiswrapper (with Windows driver) and ACX Linux driver, and they are conflicting with each other.

In order to blacklist it, you need to find the proper driver name (I think it might be *acx1xx*) and add it to the bottom of the file (& resave):
```
gksudo mousepad /etc/modprobe.d/blacklist
```
Perhaps best to save a copy of the file before tinkering though.... (and remember the name you give it).

EDIT:
I think the conflicting drivers are (case sensitive):
acx100_pci
acx_pci
Just add 2 new lines to the file and restart before going through the ndiswrapper instructions again (and Gutsy ndiswrapper is 1.44)

---

### Post by qkmbr22 on 2007-11-24
thanks i'll certainly try this.

how do i tell what the driver is called exactly. are acx100_pci and acx_pri the real values i need to blacklist?

---

### Post by ugm6hr on 2007-11-24
> **qkmbr22 said:**
> thanks i'll certainly try this.

how do i tell what the driver is called exactly. are acx100_pci and acx_pri the real values i need to blacklist?

I think they are right (or at least 1 of them is - it shouldn't matter if you have extras blacklisted) - but the only way I know to find out is to check from Terminal *when the acx driver is installed (i.e. before installing ndiswrapper*

```
lshw -C network
```

---

### Post by qkmbr22 on 2007-11-24
ok so I blacklisted the acx_pci and the acx100_pci. i installed the winxp driver in ndiswrapper. i rebooted.

I don't see any difference. WPA is still not an option in Network manager. I opened Device Manager and I looked up the info on my wireless card. Under the "Advanced tab" the value for "info.linux.driver" is still acx_pci. Does that mean it's still using the acx_pci driver? How do I get it to just use ndiswrapper?

---

### Post by ugm6hr on 2007-11-24
> **qkmbr22 said:**
> ok so I blacklisted the acx_pci and the acx100_pci. i installed the winxp driver in ndiswrapper. i rebooted.

I don't see any difference. WPA is still not an option in Network manager. I opened Device Manager and I looked up the info on my wireless card. Under the "Advanced tab" the value for "info.linux.driver" is still acx_pci. Does that mean it's still using the acx_pci driver? How do I get it to just use ndiswrapper?

What does this return?
```
lshw -C network
```

Obviously we're only interested in the bit about your wifi.  You should have a line that starts something like:
configuration: broadcast=yes driver=ath_pci
except it should list ndiswrapper as driver.

just need to check... did you finish the rest of the instructions to install ndiswrapper...
```
sudo modprobe ndiswrapper 
sudo ndiswrapper -m 
```

---

### Post by qkmbr22 on 2007-11-24
lshw -C network said acx was the driver not ndiswrapper.

and yes, I did do the part at the end.

I'm looking at this howto right now and trying some things from it [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

---

### Post by qkmbr22 on 2007-11-24
ok well after additionally blacklisting simply acx and following some other tips from the above mentioned howto, lshw -C network lists ndiswrapper+wg311v2 as the driver, which is progress i guess. but wpa still seems to be unavailable.

---

### Post by ugm6hr on 2007-11-24
Try this for more info.... look at step 3.7 & 3.7.1, which you may have neglected.

Also - I have realised you are using Xubuntu, which doesn't have Network Manager installed as default - have you installed it?  If not, Network *Monitor* (in Xubuntu) doesn't do WPA anyway.

Your options are either Network Manager (as per Ubuntu) or wicd (which I used to use in Xubuntu7.04):
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

I would recommend wicd if you are trying to maintain the speed of xubuntu, especially if you don't need to roam on wifi too frequently.

---

### Post by Craigus on 2007-11-24
Try configuring it manually. Create /etc/wpa_supplicant.conf with contents like:

> network={
     ssid="MySSID"
     scan_ssid=1
     key_mgmt=WPA-PSK
     psk="secret"
}

To associate the Wifi card :

> sudo /sbin/wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf -D wext

To obtain IP, DNS:

> sudo dhclient3 wlan0

Doing iwconfig should show that the network is up.

I ended up using wifi-radar to automate this on my Dapper Xubuntu laptop that has an acx111 adapter.

---

### Post by qkmbr22 on 2007-11-24
Thanks for all the help guys!

Actually it didn't give WPA as an option because it still thought that my network was WEP. I rebooted my computer and it refreshed all the networks and now it works. I clicked on my network and it told me to type my WPA password and now i'm connected.

I actually am using Ubuntu now, because I realized its not that much slower compared to Xubuntu. Plus I can give it a pretty simple theme and disable all the effects to make GNOME faster.

So if anybody else ever has this problem, here's what I ended up doing to make the WG311v2 work with WPA in Gutsy:

1.blacklist the acx driver
```

sudo modprobe -r acx
sudo nano /etc/modprobe.d/blacklist

```
add "blacklist acx" (without quotes) [just in case i also blacklisted acx_pci and acx100_pci]
ctrl+x to quit, y to save changes, ENTER to return to terminal

2. Install ndiswrapper-common and ndiswrapper-utils with
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils
```
or if you don't have working internet, download the latest .deb files from [http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/) on a different computer, put them on a flash drive, transfer them, and install (first common, then utils)

3. Get the windows drivers for the WG311v2 from [http://kbserver.netgear.com/products/WG311v2.asp](http://kbserver.netgear.com/products/WG311v2.asp) and unzip

4. install the windows driver in ndiswrapper
```

cd <path to unzipped folder>/Drivers/Windows\ XP/
sudo ndiswrapper -i wg311v2.inf

```

to make sure its installed
```
ndiswrapper -l
```

5. insert kernel module
```
sudo modprobe ndiswrapper
```

6. set up to work at boot
```
sudo nano /etc/modules
```
add "ndiswrapper" (without quotes) on a separate line at the end

ctrl+x to exit, y to save changes, ENTER to return to terminal

7. reboot and hopefully it will work.


again, thanks for all the help guys!

---

### Post by ugm6hr on 2007-11-25
Glad you got it to work :guitar:

I think one of the things Ubuntu does not do well enough is ndiswrapper - there are lots better Linux ndiswrapper wizards that will automate everything for you.  Well done anyway.

---

### Post by xMachina on 2008-03-13
Thanks qkmbr22,

your HOWTO works for me, excellent!

Hmm, I know it is a never-ending race for Linux driver devs to keep up with Windows-oriented hardware, but it would be nice if Ubuntu was a bit smarter about this and as soon as i tried to connect to a WPA, popped up a box recommending ndiswrapper rather than expecting me to blunder through all these kernel panics myself ;)

---

