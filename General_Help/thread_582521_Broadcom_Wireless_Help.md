---
title: "Broadcom Wireless Help"
date: 2007-10-19
forum: General Help
---

### Post by Seraph1 on 2007-10-19
To all who can help,

     I have read the following threads: 

     [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
     [http://ubuntuforums.org/showthread.php?t=145558&page=2](http://ubuntuforums.org/showthread.php?t=145558&page=2)

     And I am still having problems with trying to setup a running wireless connection. The latter thread seemed too confusing for a newbie like myself. I was confused as the point when we had to use the ndiswrapper or import Windows Broadcom drivers. I guess I need more specificity. However, when I first tried install using the BCM43xx, the connection did not work although the wireless light was indeed on. If anyone can help me, I would certainly appreciated it. Thank you so much.

     For your information, the Broadcom device is as follows:

03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

---

### Post by Dark_Stang on 2007-10-19
That card *should* be supported on the 2.6.20 or newer kernels. If it doesn't work you can try to follow my small wireless section in this guide.
[http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)
Mine is actually for the (rev 02) version, but I'd think this would still work for you.

---

### Post by Page on 2007-10-20
Do you have the firmware loaded?

If not, use the bcm43xx-fwcutter tool to extract the FW from bcmwl5.dll

---

### Post by Seraph1 on 2007-10-20
Thank you to both of you for your responses.

It's 11:17 PM here, and I am a little frazzled, so I will take your advice and help into account tomorrow morning after some rest. With regards to the firmware situation, I have indeed loaded it once or twice, with errors occurring. A blue screen with a prompt appears indicating that I need to install the firmware into the system, of which I reply yes. Then something strange occurs and there is a failure to install. I will keep the thread open and try the techniques listed by both of you and specifically take all prompts into account, so that if the error continues, I can be of more useful information. Sorry for being so limited in my account of what's occurred but I was giving up on using the wireless until the blue light came. Unfortunately, it was only running at 11 mpbs and I ridded myself of the bcm43xx driver. Anyway, thank you both very much. I will be checking in tomorrow.:)

---

### Post by HW_Hack on 2007-10-20
I understand Broadcom hell --- I feel your best outcome for BCM is to go with an Ndiswrapper approach -- you will find several guides / tips here which you should look at (I even tried a few) but ultimately its not a huge thing to walk thru yourself. And the Ndiswrapper site has a ton of info and walk-thrus as well 

Download the Ndiswrapper application here
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_frontpage/Itemid,1/)

Walk thru the install here (but skip the building of Ndis file as you downloaded a compiled version above.
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/)

Most critical is to use the List of known good cards (from the above link) to pick out the windows  xxx.sys and xx.inf files for your wireless chip set (using your PCI output string)

Here is the over all flow of the steps

- To keep things simple turn off your wireless password / encryption 

- Black list the native 43xx driver  and reboot

- Open the Network Manager and ensure your wireless card is not present

- download the newest stable (not beta) ndiswrapper adplication 

- follow the steps as listed  (may need t reboot at the end)

- attempt to connect to your unprotected SSID  

- you may need to push your wireless button to turn your wireless on 

- test by launching a browser also use the debug command line tips from the Ndiswapper site. 

Once you have a basic connection ---- you can start looking at enabling WPA supplicant  etc.

---

### Post by Page on 2007-10-20
To Seraph:

Don't use the bcm43xx-fwcutter GUI installer, it's been broken for quite awhile now, not sure why.

Instead, find the broadcom driver file, and execute bcm43xx-fw-cutter (referencing the driver file in the command)  in the same directory as the driver file in a terminal (gnome-terminal, or whatever you use).  I was able to get a friend's wifi working recently with that method. 

Your laptop sounds a lot like mine... I have a HP DV-2000, bought late last year. My wifi has a off/on switch and an orange/blue light.

---

### Post by Seraph1 on 2007-10-21
Start trying about an hour and a half ago to all....
 
Tried using the bcm43xx method; however, doesn't work. Still very confused. Now definitely trying for the Ndiswrapper. I tried using the "shortcut" easy way out with the packaged scripts from the other thread; however, no result whatsoever. Claims to have difficulty loading files into directories and is now crapping out for me.

A little worried because when I do load the ndiswrapper, and type "ndiswrapper -l" the alternate driver bcm43xx still appears no matter how many times I have blacklisted the item. The worst part is that I am again trying to load ndiswrapper the long way. I am very new to this so I feel completely lost, but I won't quit yet. :) Still have hope for me people.....trying very hard.

---

### Post by Seraph1 on 2007-10-21
Hello to all and good evening,

     I have installed ndiswrapper and my light for the wireless is definitely a blue! :) However, I still cannot connect to wireless signal I have here at my home. I have the following tidbits of information if anyone would be willing to help...

/* Prior to running network manager */

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

/* After running network manager */
 iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:15:05:EC:34:C6
                    ESSID:"BLAH BLAH BLAH"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

I have also tried the following command line procedures:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

And when I do all of the following, I get a NO DHCPOFFERS reply and the connection does not work. If anyone can help me with this, it would be so greatly appreciated. I have almost given up since I have installed ndiswrapper several times and still cannot remove bcm43xx from the "alternate" driver setting. I have checked the file in question and still have not seen an entry relating to that driver specifically. Anyway, cheers! :) And have a wonderful day, night or whatever. Thank you to all.

---

### Post by Seraph1 on 2007-10-21
By the way my friends, I didn't intent for all those smilies to come up, there were only supposed to be two. Cheers! :)

---

