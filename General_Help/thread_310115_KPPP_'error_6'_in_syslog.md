---
title: "KPPP 'error 6' in syslog"
date: 2006-11-30
forum: General Help
---

### Post by Cariboo1938 on 2006-11-30
Hi all,
I posted this issue already [HERE]("http://www.ubuntuforums.org/editpost.php?do=editpost&postid=180")
but didn't get any answer, so I try it again.
I installed KDE in Ubuntu 6.10-64 bit and when I chose "Session KDE" I want to use Kppp to connect to the Internet. 
In Gnome I use GNOME ppp which works very well. 
Here is how I tried to configure kppp and to connect to the Internet.

> 
--> Kstart
---> Internet
----> KPPP Internet Dial-Up Tool
KPPP window opens. 	Click Tab: [COLOR="Magenta"]Configure[/COLOR]
                   	click Tab: Accounts and select: [COLOR="Magenta"]New[/COLOR]
'Create new Account' window opens.	Select: [COLOR="Magenta"]Manual Setup[/COLOR]
                                 	Enter Connection Name: [COLOR="Magenta"]Provider[/COLOR]. In my case [COLOR="Magenta"]"MyProvider"[/COLOR]
                                 	Under Phone Number click: [COLOR="Magenta"]Add [/COLOR]and enter the phone # to connect to Provider.  								   In my case "[COLOR="Magenta"]Provider's PhoneNumber[/COLOR]". 
                     
To finish configure click: [COLOR="Magenta"]ok[/COLOR]
                                 	Select tab: Modems and click: [COLOR="Magenta"]New[/COLOR]
                                 	Under Device enter Modem Name. 
In my case "[COLOR="Magenta"]TOPIC SEMICONDUCTOR Corp TP560[/COLOR]"
                           			"      "   Modem Device. 
In my case "[COLOR="Magenta"]/dev/ttyS2[/COLOR]"
						"      "   Connection Speed. In my case "[COLOR="Magenta"]575600[/COLOR]"
                                                   
To finish configure click: [COLOR="Magenta"]ok[/COLOR]
Back to KPPP window. Enter Login ID. In my case "[COLOR="Magenta"]MyUserName[/COLOR]"
                     Enter Password. In my case "[COLOR="Magenta"]MyPassword[/COLOR]"
		     Check mark "[COLOR="Magenta"]Show log window[/COLOR]"
		     click: [COLOR="Magenta"]Connect[/COLOR]
Window 'Connecting to: MyProvider' opens and says: '[COLOR="SeaGreen"]Modem Ready[/COLOR]' and '[COLOR="SeaGreen"]Initializing Modem[/COLOR]', and 
'Login Script Debug Window' opens but stays empty.


After a few seconds both windows --"Connecting to:..." and "Login Script Debug Window" --- close and nothing happens.
I tried this several times and got an [COLOR="Red"]'error 6'[/COLOR] registered in syslog> root@BitByter:/var/log#  tail -f /var/log/syslog
Nov 26 13:27:45 BitByter kernel: [10429.290784] [COLOR="Red"]kppp[8554][/COLOR]: segfault at 00007fff31a01df8 rip 00002b7e7a61cab6 rsp 00007fff31a01de0 [COLOR="Red"]error 6[/COLOR]
Nov 26 13:29:43 BitByter dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Nov 26 13:29:49 BitByter dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Nov 26 13:29:59 BitByter dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
Nov 26 13:30:18 BitByter dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
Nov 26 13:30:36 BitByter dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Nov 26 13:30:44 BitByter dhclient: No DHCPOFFERS received.
Nov 26 13:30:44 BitByter dhclient: No working leases in persistent database - sleeping.
Nov 26 13:31:36 BitByter kernel: [10561.066054] [COLOR="Red"]kppp[8570][/COLOR]: segfault at 00007fff54599fd8 rip 00002b5f57a65a71 rsp 00007fff54599fc0 [COLOR="Red"]error 6[/COLOR]
Nov 26 13:33:04 BitByter kernel: [10613.007390] [COLOR="Red"]kppp[8580][/COLOR]: segfault at 00007fff977b9f18 rip 00002b6114864ab6 rsp 00007fff977b9f00 [COLOR="Red"]error 6[/COLOR]
Nov 26 13:34:05 BitByter dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Nov 26 13:34:10 BitByter dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Nov 26 13:34:24 BitByter dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Nov 26 13:34:34 BitByter dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Nov 26 13:34:53 BitByter kernel: [10677.375495] [COLOR="Red"]kppp[8585][/COLOR]: segfault at 00007fff24e0dfa8 rip 00002b3e8644f9e8 rsp 00007fff24e0df90 [COLOR="Red"]error 6[/COLOR]
Nov 26 13:34:55 BitByter dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Nov 26 13:35:06 BitByter dhclient: No DHCPOFFERS received.
Nov 26 13:35:06 BitByter dhclient: No working leases in persistent database - sleeping.
Nov 26 13:35:27 BitByter kernel: [10699.220910] [COLOR="Red"]kppp[8589][/COLOR]: segfault at 00007fffe49c8dd8 rip 00002b10c7655ab6 rsp 00007fffe49c8dc0 [COLOR="Red"]error 6[/COLOR]
Nov 26 13:35:56 BitByter kernel: [10719.390353] [COLOR="Red"]kppp[8596][/COLOR]: segfault at 00007fffc7edffb8 rip 00002ac6e337d9e8 rsp 00007fffc7edffa0 [COLOR="Red"]error 6[/COLOR]
 
What do I do wrong?
Thanks in advance for any comment, reply or help!

---

### Post by Cariboo1938 on 2007-03-10
--> Kstart
---> Internet
still doesn't work!
You have to configure kppp as Super User in a terminal. 
-->Open terminal -->sudo kppp --><yourPassword> and then follow the instructions of the menu. 
Each time you connect, you have to be in a terminal as SU and type 'kppp'. 
I can live with this! 
Case closed.:)

BTW.: I have a dial-up connection.

---

