---
title: "Gutsy Dropped Network Connection Problem"
date: 2007-10-19
forum: General Help
---

### Post by shane_on_u on 2007-10-19
I've done a fresh install of Gutsy on two of my machines. Everything is running great except for the fact that my network connection drops every so often when I'm browsing or downloading. Furthermore, my internet connection seems to be a lot slower than normal. I didn't experience any of these problems under Feisty. Does anyone know if this is a known issue? Is there any fix or temporary workaround?

I have a hardwired setup with all computers connected directly to the router. I did some searching on these forums but couldn't find any useful information regarding this issue. Can anyone help?

Thanks in advance.

Shane

---

### Post by shane_on_u on 2007-10-20
anyone?

---

### Post by azad on 2007-10-20
You're lucky you have internet. I cant get even get it up and running.

I configured Gutsy like I did Fiesty but when I ping my server it says "destination host unreachable".

I installed Gutsy on 4 machines (3 upgrades from Fiesty and 1 fresh install) and all of them have the same problem.

---

### Post by gb5uqx on 2007-10-21
Exactly the same problem here. For no apparent reason the connection drops downloading or surfing or doing anything synaptic.

Re-starting the network from a command script I have had to set up on the bar in a launcher instantly cures the problem till next time:

sudo /etc/init.d/networking restart

Apart from that everything amazingly worked out of the box but it's starting to become very irritating.

I'm trying Ubuntu Gutsy on an old P4 clunker with a D-Link RT2561/RT61 802.11g wireless PCI and a BT homeHub. It is plumbed into the wireless network with my main XP machine which does not share the problem happily.

Any ideas appreciated :)

---

### Post by cyberlion on 2007-10-21
I have the same problem with de wireless card rt61

---

### Post by hotani on 2007-10-21
my wired network is completely dead on a gutsy laptop. I'm posting this from a feisty box. It worked for a while but now I can't get anything. nm-applet shows it is connected, but when I display connection info there is nothing in there but 0's.

This is on a Dell latitude D600.

---

### Post by kashms on 2007-10-21
I also have a card based on RT2561/RT61. The Gutsy driver rt61pci worked but would drop connection once in a while. Now I'm using ndiswrapper and it is very stable.

---

### Post by shane_on_u on 2007-10-21
Looks like a lot of people with the same problem but no solution... I hope there is some work being done on this because it really is getting quite annoying. My connection is dropping almost once every minute now.

I even tried that ipv6 "fix" but nothing. So no one has any remedy for this? Are we just stuck waiting? I spent a lot of time doing a fresh install to gutsy and i really don't want to do it all over again just to return to feisty.

---

### Post by hotani on 2007-10-21
intermittent would be an improvement over what I have which is nothing. Funny since last night it was working fine. There is a feisty box connected to the same router and working normally. I tried connecting the laptop straight into the cable modem and still nothing which rules out the router.

In an attempt to isolate it further I'm going to boot with Gutsy final CD and see if it finds a connection. Then maybe do a reinstall. This is not as big a deal as it sounds; all I use that laptop for is pidgin and firefox.

---

### Post by JayBee808 on 2007-10-21
I am suffering from an unstable network connection as well.  I installed Gutsy RC last monday, and configured my ralink wifi with wicd and the included serialmonkey driver.  It worked fine for a few days, with a very stable connection.  Using WPA2 TPIK, and a static IP...no problems.

I downloaded all updates offered by synaptic, and installed the Flash player, and adblock+updater for firefox.  Soon after installing these the network connection started dropping out after a few minutes.  Now it won't stay connected at all.  I can look at all wireless connections through the router's control panel (running dd-wrt) and the ralink card connects, and then drops out about every 10-15 seconds.  I can also see the "pulses" of this connect/disconnecting in the system monitor's networking graph.  Other PC's on the network are running as they should.

The system is also very slow now.  It takes about five minutes to go from the login to the desktop, and it takes a long time for any applications to start up.  This was not a problem when the network was working properly.

I removed the networking-manager when I installed wicd.  I messed with settings in the Sysyem>Admin>Network panel to no avail, and now I am afraid this might have conflicted with wcid's settings.

I am revisiting linux after a 5 year break so my skills aren't that sharp yet.  I loved Ubuntu when it was running smoothly, I am very frustrated because I think I did something that broke it.  I am considering a reinstall, but it would be nice if I could salvage this installation.

Is there a way I could reset all the network settings back to how they were upon installation?  I'll try whatever possible to get this running again.  I just don't know what changed, the connection was great for several days.

System is a intel p35 with Core2 Quad, geforce 8800gts, ralink 2561, it is a brand new machine...running 64-bit Gutsy with all updates.

---

### Post by guidoman on 2007-10-21
Does [disabling IPV6]("http://ralph.n3rds.net/index.php?/archives/177-How-to-Disable-IPV6-in-Ubuntu.html") work for you?

---

### Post by nabla on 2007-10-21
I'm experiencing the same problems on a fresh Gutsy install that I didn't have on Feisty, I'm on an Inspiron 6000 ,  Anyone know the Launchpad bug report?

---

### Post by kashms on 2007-10-22
The rrt61 drivers from Serialmonkey changed from legacy to the new beta driver they are working on. Try first using the windows drivers with ndiswrapper to rule out other networking problems.

---

### Post by shane_on_u on 2007-10-22
> **guidoman said:**
> Does [disabling IPV6]("http://ralph.n3rds.net/index.php?/archives/177-How-to-Disable-IPV6-in-Ubuntu.html") work for you?


No this didn't work. No change after disabling ipv6.

---

### Post by unisol on 2007-10-22
i just did a fresh install of gutsy and the rt61 cards works,but after a while the connection drops. i heard something about enabling ifupdown in youe /etc/network/interfaces. anyone know how to go about this?

---

### Post by ekravche on 2007-10-23
Have a similar issue... Also the signal strength is showing up as 0, even though I'm connected see my other problem here [http://ubuntuforums.org/showthread.php?t=584104](http://ubuntuforums.org/showthread.php?t=584104)

---

### Post by JayBee808 on 2007-10-23
I did a reformat/reinstall with the official Gutsy release.  This time I tried the ndiswrapper + rt61.inf and it exhibits the same behavior as before;  connects perfectly for a while, and then just randomly drops out.  The router says it is still connected, but the Internet is not available.  I cannot get to the router's web config either.  Network manager kept asking for the passkey, so I removed it and tried Wicd again.  Still an unstable connection.  Sometimes it disconnects after a minute, sometimes it is 3 hours, or anywhere in between.  This PC works as expected in XP, and all other WiFi connected hardware is working properly when Gutsy drops the Internet.

I am away from this machine now, but will try disabling IP6 stuff when I get back.  I also want to try a different pair of DNS servers, is OpenDNS a good choice?  

I have also ordered a Linksys WET200 ethernet to WiFi bridge.  I'm hoping this will eliminate all of this WiFi configuration hassle.  Whatever it takes...I don't want to go back to MS...

---

### Post by damageDOne on 2007-10-23
I think I have the same problem. 

Here's my situation. Saturday night I installed gutsy fresh over feisty on my laptop. I have another laptop with wifi running edgy and another laptop connected via cable running feisty.

They are connected to a wifi router either by wifi or cable with no problem. Wifi just worked.

10-15mins after the installation all three machines lost their net connection in terms of web pages. I could still use instant messaging, receive emails, and download via synaptic and ktorrent. But no webpages. I thought it was a DNS problem and tried switching to another DNS. This got some partially loaded pages and then nothing. I rebooted into XP on my gutsy machine and all three machines got a full connection back. I rebooted into gutsy and all 3 still had the full connection for about 10-15mins... then it went back to no webpages again.

I have also tried turning off the other machines which gives me a full connection again for about... 10-15min! Then I lose it again.

I have also tried disabling networking (right-clicking on NetworkManager icon) and then re-enabling it and I get the full connection back... for about 10-15mins.

Please help. :confused:

---

### Post by Garfiel78 on 2007-10-24
Hi Folks!

I confirm the problem with my rt61 based wireless PCI adapter dropping the connection after some time in Gutsy. The time intervall ranges from a couple of minutes to hours.

Some quick facts:

[LIST]
[*]I did an upgrade from Feisty to Gutsy
[*]In Feisty WLAN worked fine with very rare connection problems after booting.
[*]The network is configured via DHCP.
[*]I am not using ndiswrapper.
[*]Encryption ist WEP. The passkey is entered into my /etc/network/interfaces file:
[/LIST]

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface wlan0 inet dhcp
address 192.168.1.35
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key ***here comes my WEP-key***
wireless-essid ***here comes my ESSID***

auto wlan0

auto eth0
```

Doing a
```
 sudo /etc/init.d/networking restart
```
sometimes but not allways helps.

I noticed something strange. I found a strange device WMASTER0  showing up in ifconfig and iwconfig:
iwconfig output
```
lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:6400 (6.2 KB)  TX bytes:6400 (6.2 KB)

wlan0     Protokoll:Ethernet  Hardware Adresse 00:80:5A:4E:D7:FE  
          inet Adresse:192.168.1.35  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6 Adresse: fe80::280:5aff:fe4e:d7fe/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12352 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:22806495 (21.7 MB)  TX bytes:1695707 (1.6 MB)

wmaster0  Protokoll:UNSPEC  Hardware Adresse 00-80-5A-4E-D7-FE-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
iwconfig output:```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"***MY ESSID***"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:49:9F:5B:19   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
While doing a network restart the wmaster0 device provokes two identical errors:
```
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:80:5a:4e:d7:fe
Sending on   LPF/wlan0/00:80:5a:4e:d7:fe
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.35 -- renewal in 129056 seconds.
```
Any help would be appreciated!

Greetings Garfield

---

### Post by damageDOne on 2007-10-25
Turning off ipv6 did nothing for me.

I can add that I have now also tried using wifi at a net cafe and it seems to do the same thing there. I connect and everyone gets booted after 10-15mins. 

However, I am currently at a different net cafe and am plugged in to the router via cable and I don't have the problem. Everyone here still has net after a full hour. 

It looks like I'll have to try plugging in at home until a fix can be found.

---

### Post by JayBee808 on 2007-10-26
A short summary and update here:

I tried a fresh installation of Gutsy three different times.  The first using Wicd and serialmonkey (drivers included with 7.10 release), the second using serialmonkey and editing the interfaces file directly.  The third install I tried ndiswrapper and both Wicd and Network Manager.  All four attempts resulted in the previously described behavior;  a great connection for a while, then all network connectivity stops functioning but the router still shows a link.  I was unable to ping anything on the network.  Each time this happened, I had to reboot the PC to get a working connection back.  "Networking restart" command did not work.

The WET200 ethernet/wifi bridge has solved my problems.  It works great, holding the connection as long as the computer is on.  It supports WPA2 (personal and enterprise), lots of adjustable settings and filtering, a 5 port switch, power over e-net, and has a nice stong signal.  Plus I can set my router back to a hidden SSID (I know, not that big a deal...but if you can, why not).  I don't want to sound like an advertisment for this, but it really solved my wireless connectivity problems, and expanded the possibilities for my network.  There are several other wifi to e-net bridges, but in my haste I didn't find another that supported WPA2, they could exist though.  WET200 is $100.

While the bridge solution works great for a stationary desktop, it is not a solution for laptops.  These wifi problems are very discouraging.  I have a laptop that I was going to install Ubuntu on, but I don't think I will until it will have reliable wifi.  This is pretty important in today's computer world.  As the poster above has shown, crashing a whole net-cafe is not a good promotional feature for this OS.

I am very new to this community, so I am still learning the procedures and stuff.  Is there already a bug report filed for this?  If not, what do we do to get that ball rolling?

---

### Post by damageDOne on 2007-10-26
I have found [this bug report]("https://bugs.edge.launchpad.net/ubuntu/+bug/156720") but I don't understand it at all. 

Is this what is causing my problem? When will the update come out? 

I don't want to buy any new hardware to get my OS working... I'm not using Vista!  :)

Some one please help resolve this issue.

---

### Post by blazercist on 2007-10-26
I confirm this problem with rt61 gutsy i386. It seems to hang during heavy network usage.  restarting the networking and reassociating with the AP seems to temporarily fix the problem.

---

### Post by snooo on 2007-10-26
Also having this problem. Initially thought it was Warcraft's server's which were booting me offline but then noticed it extended to browsing. Connection widget in my status box will show i'm still connected, but the connection will not **do** anything...

---

### Post by caolan on 2007-10-29
I also confirm this problem using both the included rt61 drivers and the latest CVS version from serialmonkey on a Dell Inspiron 1000 laptop.

---

### Post by mokshadaya on 2007-10-29
I am having a very similar issue.  With 6.06 my Atheros based Netgear card worked flawlessly.  With 7.04 my signal strength was significantly degraded.  With 7.10 I have no wireless at all and my onboard ethernet doesn't work either.  So, back to 7.04 I went.

DellC610

---

### Post by Grafster on 2007-10-29
Ditto. I thought I had it fixed (even posted a how-to about it) but no dice.

---

### Post by gb5uqx on 2007-10-30
Not sure how to explain this but I have not had a problem for two days and have been streaming media and surfing with no problem.

All I did was change my connection properties. In Network Tools - Devices my network device is shown as loopback device (lo), however in connection properties by clicking the panel networking icon it was shown as wlan0. I changed that to loopback device (lo) as well and it seems (fingers crossed) it most certainly has made a difference. Any ideas?.

---

### Post by Grafster on 2007-10-31
> **gb5uqx said:**
> 
All I did was change my connection properties. In Network Tools - Devices my network device is shown as loopback device (lo), however in connection properties by clicking the panel networking icon it was shown as wlan0.

It would be most awesome if you could explain this in more detail. I use Xubuntu and I'm having trouble finding out which switch this refers too.

---

### Post by newbunti on 2007-10-31
Problem 1. Installed 7.04 on clunker 2.13Ghz celeron, 512M ram, hooked up to network at work which has permanent internet connection. Worked perfectly, no problem accessing the internet. Two weeks later it dropped the network and I cannot access internet no matter what network setting I try. I did not change something unwittingly to cause loss. Decided fresh install might help so waited for 7.10. Installed but ubuntu did not pick up the network so still no network or internet. I have installed gutsy on seperate drive - if I reboot and select xp I access network and internet no problem. So this is definately ubuntu problem.
Problem 2. Fresh install of 7.10 on dell laptop 8200 inspiron at home. Works perfectly accesses internet through DSL cable no problem all automatically configured - very happy.......until..........network connection dropped last night and have not been able to access internet since.
Systems have different intenet, network, hardware etc. only common factor is ubuntu. As soon as I access same with XP there is NO PROBLEM so it must be the way ubuntu is configured or has instability. Both systems hardware id detected correctly so assume ubuntu has loaded correct drivers.
get NETDEV watchdog: eth0: transmit timed out error message
but other than that no clues.
please help!!!!

---

### Post by gb5uqx on 2007-10-31
> **Grafster said:**
> It would be most awesome if you could explain this in more detail. I use Xubuntu and I'm having trouble finding out which switch this refers too.

Quite unfamiliar with Xubuntu but it can't be that different. As simply put as I can...

Network is set to roaming disabled, automatic DHCP, ipv6 disabled etc, I have tried about everything.

In system admin network tools devices tab three active devices are shown here.

1) loopback device (lo) which is the default selected device
2) unknown device wmaster0
3) wlan0

Changing any of the above settings merely reverted back to default.

The original panel network icon showed no activity, I removed it and then replaced it again with the add to panel option network monitor icon. This now shows network activity ok.

By clicking the network icon on the panel I saw the connection properties were set to wlan0. I perhaps had somewhat simplistically suspected a conflict of some kind and set the option to loopback device (lo) to match the tools devices setting. Changing this to a matching configuration has effectively cured my wireless connection loss/time out problem.

---

### Post by gb5uqx on 2007-11-02
I can confirm this has fixed my problem after four days no disconnections or network restarts despite heavy downloads from Stage6 and various other downloads. Returning to the original config caused the connection to drop repeatedly after only four or five minutes surfing.

Hope someone else has this success.........

---

### Post by Grafster on 2007-11-02
Thanks. The Xubuntu interface is different. I'll keep plugging away at it.

---

### Post by Alucard-sama on 2007-11-02
[http://youtube.com/watch?v=Sd8nHsUevAY](http://youtube.com/watch?v=Sd8nHsUevAY)
This should fix the slowness and may fix the drop-outs.

---

### Post by shane_on_u on 2007-11-04
For anyone here that's still having problems with repeated dropped network connections while surfing... I've found that turning of desktop visual effects (System -> Preferences -> Appearance -> Visual Effects) seems to have done the trick for me. 

I'm only at 30 minutes of usage right now so I can't be 100% certain that this fixed it... but my network connection would drop every few seconds while surfing/downloading so 30 minutes is pretty good so far. I was actually just getting ready to revert back to feisty when I decided to try this one last thing! Hope this can help someone else.

---

### Post by jeffjohn on 2007-11-10
Not an answer, I know, but faced with similar problems, I re-installed 7.04 Fiesty from scratch and everything works swimmingly!  "If it aint broke..."  sorry.........jeffjohn

---

### Post by elmerfud on 2007-11-16
I am extremely frustrated with Gutsy as far as networking goes.  So frustrated, in fact, that I am thinking of moving back to Fedora.

My machine is now dropping the network.  I've been fighting with it all day.  I think it is ludicrous that this got shipped the way it is.  First it was ipv6, now this.  Ubuntu is TERRIBLE as far as networking is concerned.

How do I troubleshoot this problem ?

---

### Post by Mr. Tos on 2007-11-17
I had a problem with my network randomly dropping as well a few weeks back - only rebooting would restore it. In my case it was caused by a kernel bug that was fixed in .23 (not ubuntu-specific).

I posted something about it on the forums as well:

[http://ubuntuforums.org/showthread.php?t=590853](http://ubuntuforums.org/showthread.php?t=590853)


Maybe that can help some people with problems here, if you have the "NETDEV WATCHDOG: eth0: transmit timed out" and "Tx timed out, lost interrupt?" errors in your logs.

---

### Post by mithion on 2007-11-17
I will also confirm the bug with my rt61 based card.  I also haven't had success with turning IPV6 off.  This is a big regression since everything was working perfectly in Feisty. :(

---

### Post by oracle1 on 2007-11-25
Anyone find a fix for this yet? I'm having the same problem using an rt61 based wireless card. Connection drops during high bandwidth usage, it's happened when transferring files via nfs, irc, samba, and bittorrent. It seems to work fine if im just browsing the web.

---

### Post by Grafster on 2007-11-26
I was only able to fix my rt61 problems by going back to Feisty. 

If you figure out a magic bullet do let folks know though.

---

### Post by Peace on 2007-11-28
Same problem here...

One of my fellow techs built an Ubuntu router to be used temporarily on our network. It has 4 individual NICs installed. It was working perfectly until our Tech Director attempted to apply some security updates. Harmless right? The router died.

Our Ubuntu "administrator" came back in and installed 7.10, an upgrade from our previous version. All the networking settings are assumed to be the same as they were. The only difference is, we get NetDev Watchdog EthX transmit timeout errors, randomly on any one of the 4 NICs.

Me and my Boss have been stuck in the server room taking turns watching the router, rebooting it when one of our interfaces drops.

I feel like we've tried everything. Now, we were also getting Neighbor Table Overflow error logs as well, almost every minute except when we were A) Rebooting or B) when an interface dropped.

I was able to stop those errors by shutting down a network monitoring tool (The Dude) we had running on another machine on our network. I thought that was kind of crazy..

In any case, that seemed to help alot, but it doesn't seem to have solved our problem completely.

Any input? Is it feasible that an overflowing ARP table could have shut us down? Should we be going back a version of Ubuntu? 

Thanks a lot guys!

Peace

---

### Post by JayBee808 on 2008-01-07
Has there been any advancement here?  I have not enabled the rt61 since November.  Have any of the updates solved these problems?

---

### Post by Gattsu on 2008-01-24
I had the same problem with rt61 and wireless disconnecting under heavy load.
I tried everything including ndiswrapper, rt61 driver from ralinktech and I tried wicd, ruitilt and finally I got it working using the serialmonkey CVS driver and using iwconfig with a WEP connection.

By the way my card is a Linksys WMP54G.

Hope someone finds this helpful.

---

### Post by buuu2 on 2008-01-25
I thought I would thank gb5uqx for his/her post:
[COLOR="SeaGreen"]Quite unfamiliar with Xubuntu but it can't be that different. As simply put as I can...

Network is set to roaming disabled, automatic DHCP, ipv6 disabled etc, I have tried about everything.

In system admin network tools devices tab three active devices are shown here.

1) loopback device (lo) which is the default selected device
2) unknown device wmaster0
3) wlan0

Changing any of the above settings merely reverted back to default.

The original panel network icon showed no activity, I removed it and then replaced it again with the add to panel option network monitor icon. This now shows network activity ok.

By clicking the network icon on the panel I saw the connection properties were set to wlan0. I perhaps had somewhat simplistically suspected a conflict of some kind and set the option to loopback device (lo) to match the tools devices setting. Changing this to a matching configuration has effectively cured my wireless connection loss/time out problem.
__________________[/COLOR]
NOW PERHAPS IT IS TOO SOON TO TELL BUT ALREADY MY SPEED HAS DOUBLED. I HAVE NOT HAD THE CHANGE LONG ENOUGH TO KNOW IF IT WILL SOLVE MY RANDOM NETWORK SETTINGS CHANGES. BUT I AM HOPEFUL.  JUST TO NOTE-- WHEN ADDING THE NETWORK MONITOR ICON, IT LOOKS VERY SIMILAR TO THE NET CONFIG ICON THAT IS ALREADY ON THE PANEL SO DONT BE FOOLED.
MY PROBLEM HAS BEEN THAT MY NET SETTING RANDOMLY CHANGE. I HAVE WIRELESS AND EVERY NOW AND THEN SETTINGS WILL CHANGE TO WIRED, DESPITE ME SAVING AND APPLYING LOCATIONS THE WAY I WANT THEM. SOMETIMES THEY CHANGE BACK IN A MATTER OF MINUTES AND MY CONNECTION WILL STOP WORKING. I WOULD HAVE TO CHANGE BACK TO MY SAVED LOCATION, UNCLIK THE WIRELESS, WAIT FOR THE CONFIG INTERFACE SETTINGS TO CHANGE AND THEN CLICK IT BACK ON AND WAIT AGAIN FOR THE SETTINGS TO CHANGE AGAIN. CLOSE THE BOX AND RETRY THE INTERNET AND IT WOULD WORK.
I AM MOST HOPEFUL WITH GB5UQX'S FIX AS IT HAS ALREADY SPEEDED ME UP!!!!

---

### Post by Cyanic420 on 2008-03-17
Bump. I have the same issue with the Ralink 2561/RT61. The workaround mentioned above did not work for me. I guess I will try Feisty, I don't feel like playing around with drivers and config files, don't have the time.

---

