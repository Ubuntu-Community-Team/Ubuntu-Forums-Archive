---
title: "Create batch script to ensure ath0 is always ifup!!"
date: 2006-12-23
forum: General Help
---

### Post by dannyboy79 on 2006-12-23
I have a atheros wifi card, the netgear wg511t i think. it's lspci -v is: 0000:05:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: Netgear: Unknown device 4b00
        Flags: bus master, medium devsel, latency 168, IRQ 9
        Memory at 16000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
anyway, i don't know why but every once in awhile my wireless connectivity will stop. all it takes for me to get it to work is to do sudo ifdown ath0 and then sudo ifup ath0. now I don't know if I have to ifdown it but I just do it anyway. and when I sometimes I ssh into my ubuntu server I want to someone ssh into my wireless laptop and i can't because the wireless connectivity goes down once in awhile. there is really no consistency of when the wireless card doesn't work. i do have to say it seems to always be when I am away from the computer and then when I return i find that it doesn't work or like I said when I try to ssh into it and it doesn;t work. so I saw this batch script that this other guy created and he added it to init or whatever but I thought I could just create the same file and put a cron job in  roots cron file by doing sudo -i and then crontab -e. here is the line I used and tehn here is the bash script. it's not working. any help would be appreciated.

*/10 * * * * /bin/sh /home/daniel/.wifi


#! /bin/sh

conectado=`ifconfig | grep ath0`

if [ "$conectado" == "" ]; then
        ifup ath0
fi

i was wondering if there would be someway i could have the script try to ping another compouter in my network first, then if the ping is successful the script can stop or if the ping fails, then the script should continue and do ifup ath0. i do use a static ip. if it matters. i'll give ya some info if it'll help.

**iwconfig**
lo        no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11g  ESSID: "not for your eyes, hehe"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:09:5B:ED:2C:A2 
          Bit Rate:36 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:4C91-0239-290B-E406-7013-134E-53   Security mode:restricted
          Power Management:off
          Link Quality=39/94  Signal level=-56 dBm  Noise level=-95 dBm
          Rx invalid nwid:1205  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:21  Invalid misc:21   Missed beacon:292

**ifconfig**
ath0      Link encap:Ethernet  HWaddr 00:09:5B:C5:DA:A3
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fec5:daa3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33418 errors:19717 dropped:0 overruns:0 frame:19717
          TX packets:36774 errors:21 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:16210191 (15.4 MiB)  TX bytes:5144449 (4.9 MiB)
          Interrupt:9 Memory:c89a0000-c89b0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1593220 (1.5 MiB)  TX bytes:1593220 (1.5 MiB)

**/etc/interfaces**
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface ath0 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid DRAWN
        wireless-key1 not for your eyes!
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 24.94.163.33
        wireless-key na-ahh!

**iwlist ath0 scan**
ath0      Scan completed :
          Cell 01 - Address: 00:09:5B:ED:2C:A2
                    ESSID: not for you!
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/94  Signal level=-56 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

hopefully someone can help. thanks if so!

---

### Post by dannyboy79 on 2006-12-26
anyone, please. I am sure there are people who know how to create a bash script.

---

### Post by speedman on 2006-12-26
sudo gedit /usr/local/bin/ath0alive

Insert this:

===== copy below here

#!/bin/bash
# /usr/local/bin/ath0alive

PC=$(ping -c3 192.168.0.1|wc -l)

if [ $PC -ne 8 ]; then
        ifdown ath0 && ifup ath0
else    echo "";
fi

exit

===== copy above here

Save the file and make it executable:

sudo chmod +x /usr/local/bin/ath0alive

sudo gedit /etc/crontab

Insert this:

*/5 *   * * *   root    /usr/local/bin/ath0alive &> /dev/null

Save the file and cron will run the script every 5 minutes.

HTH


SM

---

### Post by dannyboy79 on 2006-12-26
i am trying to learn here. i tried to do this but I couldn't figure out how to get ping to stop after awhile? is that what the -c3 does. If you wouldn't mind, could you explain exactly each part of the program etc etc. I am trying to learn bash scripting in it's very easiest form. thank you so much for the script and if you could provide me with the explaination I would really really appreciate that! Also, wouldn't I need to first su, and then do crontab -e? One last thing, is this going to be logged anywhere. Crontab log possibly? If so, wouldn't I want to change the part where you have, else echo "";
and I owuld make it say else echo "It's already working, YEAH";
then wouldn't that be logged? I could just be speaking out of my butt I am trying to learn as I said.

---

