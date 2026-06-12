---
title: "mrtg client/server setup"
date: 2022-01-16
forum: General Help
---

### Post by atux on 2022-01-16
i am writing this post, sonce i am bit confused on how to configure a monitoring system for my LAN and add devices.
at the moment i have 3 ubuntu servers(A, B, C), physical machines, running different services in the LAN. I would like to be able from server_A to monitor the other 2 servers and afew other switches. I am confused about the setup.
Up to now i have done in server_A: i followed the guide in [https://www.howtoforge.com/tutorial/how-to-install-and-configure-mrtg-on-ubuntu-1804/](https://www.howtoforge.com/tutorial/how-to-install-and-configure-mrtg-on-ubuntu-1804/). How do i add different the other 2 machines (CPU/RAM/Traffic)? All are in the same LAN 192.168.1.x/24

---

### Post by atux on 2022-01-17
up to now i have the server_A to be able to login at [http://IP_address/mrtg](http://IP_address/mrtg) and i can see the localhosts traffic. How do i add the other 2 machines?

---

### Post by SeijiSensei on 2022-01-18
I recommend taking a look at [https://www.ntop.org/](https://www.ntop.org/) before going too far down the mrtg road.

---

### Post by ActionParsnip on 2022-01-18
May help
[https://aacable.wordpress.com/2011/09/21/howto-monitor-isa-server-linux-server-or-any-windows-pc-using-mrtg/](https://aacable.wordpress.com/2011/09/21/howto-monitor-isa-server-linux-server-or-any-windows-pc-using-mrtg/)

---

### Post by mIk3_08 on 2022-01-18
You can try this  [Click Here]("https://help.ubuntu.com/community/MRTG") for the installation guide of Multi Router Traffic Grapher. And this link also [Click Here]("https://askubuntu.com/questions/696947/mrtg-installation-on-ubuntu-and-monitoring-rpi") will redirect you to some solution to your concern. Good Luck and Cheers

---

### Post by atux on 2022-01-20
thanks a lot for the replies. I managed to create in the server the mrtg to show the ethernet traffic for local and remote server. So far so good.
I would like to add information for CPU and ram for localhost and remote server. How can i do that please?
Currently i have the following /etc/mrtg.conf file:
```
# Created by # /usr/bin/cfgmaker public@localhost




### Global Config Options


#  for UNIX
# WorkDir: /home/http/mrtg


#  for Debian
WorkDir: /var/www/html/mrtg




#Include: /cfg/mibs/cpu.txt
#Include: /cfg/mibs/mem.txt
#Include: /cfg/mibs/mempercent.txt
#Include: /cfg/mibs/memfree.txt






#  or for NT
# WorkDir: c:\mrtgdata


### Global Defaults


#  to get bits instead of bytes and graphs growing to the right
# Options[_]: growright, bits


EnableIPv6: no


######################################################################
# System: mainmrtg
# Description: Linux mainmrtg 5.10.0-8-amd64 #1 SMP Debian 5.10.46-4 (2021-08-03) x86_64
# Contact: atux <me@example.org>
# Location: office
######################################################################




### Interface 1 >> Descr: 'lo' | Name: 'lo' | Ip: '127.0.0.1' | Eth: 'No Ethernet Id' ###
### The following interface is commented out because:
### * it is a Software Loopback interface
# 
# Target[localhost_1]: 1:public@localhost:
# SetEnv[localhost_1]: MRTG_INT_IP="127.0.0.1" MRTG_INT_DESCR="lo"
# MaxBytes[localhost_1]: 1250000
# Title[localhost_1]: Traffic Analysis for 1 -- mainmrtg
# PageTop[localhost_1]: <h1>Traffic Analysis for 1 -- mainmrtg</h1>
# 		<div id="sysdetails">
# 			<table>
# 				<tr>
# 					<td>System:</td>
# 					<td>mainmrtg in office</td>
# 				</tr>
# 				<tr>
# 					<td>Maintainer:</td>
# 					<td>atux &lt;me@example.org&gt;</td>
# 				</tr>
# 				<tr>
# 					<td>Description:</td>
# 					<td>lo  </td>
# 				</tr>
# 				<tr>
# 					<td>ifType:</td>
# 					<td>softwareLoopback (24)</td>
# 				</tr>
# 				<tr>
# 					<td>ifName:</td>
# 					<td>lo</td>
# 				</tr>
# 				<tr>
# 					<td>Max Speed:</td>
# 					<td>1250.0 kBytes/s</td>
# 				</tr>
# 				<tr>
# 					<td>Ip:</td>
# 					<td>127.0.0.1 (localhost)</td>
# 				</tr>
# 			</table>
# 		</div>




### Interface 2 >> Descr: 'VMware-VMXNET3-Ethernet-Controller' | Name: 'ens192' | Ip: '192.168.1.14' | Eth: '00-0c-29-a1-58-dd' ###


Target[localhost_2]: 2:public@localhost:
SetEnv[localhost_2]: MRTG_INT_IP="192.168.1.14" MRTG_INT_DESCR="VMware-VMXNET3-Ethernet-Controller"
MaxBytes[localhost_2]: 536870911
Title[localhost_2]: Traffic Analysis for 2 -- MRTG server .14
PageTop[localhost_2]: <h1>Traffic Analysis for 2 -- MRTG server .14</h1>
		<div id="sysdetails">
			<table>
				<tr>
					<td>System:</td>
					<td>mainmrtg in office</td>
				</tr>
				<tr>
					<td>Maintainer:</td>
					<td>atux &lt;me@example.org&gt;</td>
				</tr>
				<tr>
					<td>Description:</td>
					<td>VMware-VMXNET3-Ethernet-Controller  </td>
				</tr>
				<tr>
					<td>ifType:</td>
					<td>ethernetCsmacd (6)</td>
				</tr>
				<tr>
					<td>ifName:</td>
					<td>ens192</td>
				</tr>
				<tr>
					<td>Max Speed:</td>
					<td>536.9 MBytes/s</td>
				</tr>
				<tr>
					<td>Ip:</td>
					<td>192.168.1.14 (192.168.1.14)</td>
				</tr>
			</table>
		</div>




# Created by 
# /usr/bin/cfgmaker public@192.168.1.15




### Global Config Options


#  for UNIX
# WorkDir: /home/http/mrtg


#  for Debian
WorkDir: /var/www/html/mrtg


#  or for NT
# WorkDir: c:\mrtgdata


### Global Defaults


#  to get bits instead of bytes and graphs growing to the right
# Options[_]: growright, bits


EnableIPv6: no


######################################################################
# System: client15
# Description: Linux client15 5.10.0-8-amd64 #1 SMP Debian 5.10.46-4 (2021-08-03) x86_64
# Contact: atux <me@example.org>
# Location: System .15 client
######################################################################




### Interface 1 >> Descr: 'lo' | Name: 'lo' | Ip: '127.0.0.1' | Eth: 'No Ethernet Id' ###
### The following interface is commented out because:
### * it is a Software Loopback interface
# 
# Target[192.168.1.15_1]: 1:public@192.168.1.15:
# SetEnv[192.168.1.15_1]: MRTG_INT_IP="127.0.0.1" MRTG_INT_DESCR="lo"
# MaxBytes[192.168.1.15_1]: 1250000
# Title[192.168.1.15_1]: Traffic Analysis for 1 -- client15
# PageTop[192.168.1.15_1]: <h1>Traffic Analysis for 1 -- client15</h1>
# 		<div id="sysdetails">
# 			<table>
# 				<tr>
# 					<td>System:</td>
# 					<td>client15 in System .15 client</td>
# 				</tr>
# 				<tr>
# 					<td>Maintainer:</td>
# 					<td>atux &lt;me@example.org&gt;</td>
# 				</tr>
# 				<tr>
# 					<td>Description:</td>
# 					<td>lo  </td>
# 				</tr>
# 				<tr>
# 					<td>ifType:</td>
# 					<td>softwareLoopback (24)</td>
# 				</tr>
# 				<tr>
# 					<td>ifName:</td>
# 					<td>lo</td>
# 				</tr>
# 				<tr>
# 					<td>Max Speed:</td>
# 					<td>1250.0 kBytes/s</td>
# 				</tr>
# 				<tr>
# 					<td>Ip:</td>
# 					<td>127.0.0.1 (localhost)</td>
# 				</tr>
# 			</table>
# 		</div>




################################################################
#CPU for MRTG server .14
################################################################
Target[CPU]: .1.3.6.1.4.1.2021.10.1.5.1&.1.3.6.1.4.1.2021.10.1.5.2:public@127.0.0.1:::::2
MaxBytes[CPU]: 100
Unscaled[CPU]: dwmy
Options[CPU]: gauge, growright, nopercent
YLegend[CPU]: Load Average
ShortLegend[CPU]: (%)
LegendI[CPU]: Load Average 1 min
LegendO[CPU]: Load Average 5 min
Legend1[CPU]: Load Average 1 min
Legend2[CPU]: Load Average 5 min
Title[CPU]: CPU Load Average
PageTop[CPU]: <h1>CPU Load Average MRTG server .14</h1>
################################################################




################################################################
#RAM
################################################################
Target[mem]: .1.3.6.1.4.1.2021.4.6.0&.1.3.6.1.4.1.2021.4.4.0:public@127.0.0.1:::::2
# total memory
MaxBytes1[Mem]: 4047620
# total swap
MaxBytes2[Mem]: 3145724
Unscaled[Mem]: dwmy
Options[Mem]: gauge, growright
YLegend[Mem]: Mem Free(Bytes)
ShortLegend[Mem]: Bytes
kilo[Mem]: 1024
kMG[Mem]: k,M,G,T,P
LegendI[Mem]: Real
LegendO[Mem]: Swap
Legend1[Mem]: Memory Free [MBytes]
Legend2[Mem]: Swap Free [MBytes]
Title[Mem]: Memory Free
PageTop[Mem]: <H1>Memory Free MRTG server .14</H1>
################################################################


#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
########################################          15          #########################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################
#######################################################################################################################################








































### Interface 2 >> Descr: 'VMware-VMXNET3-Ethernet-Controller' | Name: 'ens192' | Ip: '192.168.1.15' | Eth: '00-0c-29-2d-e1-6c' ###


Target[192.168.1.15_2]: 2:public@192.168.1.15:
SetEnv[192.168.1.15_2]: MRTG_INT_IP="192.168.1.15" MRTG_INT_DESCR="VMware-VMXNET3-Ethernet-Controller"
MaxBytes[192.168.1.15_2]: 536870911
Title[192.168.1.15_2]: Traffic Analysis for 2 -- client15
PageTop[192.168.1.15_2]: <h1>Traffic Analysis for 2 -- client15</h1>
                <div id="sysdetails">
                        <table>
                                <tr>
                                        <td>System:</td>
                                        <td>client15 in System .15 client</td>
                                </tr>
                                <tr>
                                        <td>Maintainer:</td>
                                        <td>atux &lt;me@example.org&gt;</td>
                                </tr>
                                <tr>
                                        <td>Description:</td>
                                        <td>VMware-VMXNET3-Ethernet-Controller  </td>
                                </tr>
                                <tr>
                                        <td>ifType:</td>
                                        <td>ethernetCsmacd (6)</td>
                                </tr>
                                <tr>
                                        <td>ifName:</td>
                                        <td>ens192</td>
                                </tr>
                                <tr>
                                        <td>Max Speed:</td>
                                        <td>536.9 MBytes/s</td>
                                </tr>
                                <tr>
                                        <td>Ip:</td>
                                        <td>192.168.1.15 (192.168.1.15)</td>
                                </tr>
                        </table>
                </div>














##############################################################################################
################################################################
#CPU for MRTG server .15
################################################################
#Target[CPU]: .1.3.6.1.4.1.2021.10.1.5.1&.1.3.6.1.4.1.2021.10.1.5.2:public@192.168.1.15:::::2
#MaxBytes[CPU]: 100
#Unscaled[CPU]: dwmy
#Options[CPU]: gauge, growright, nopercent
#YLegend[CPU]: Load Average
#ShortLegend[CPU]: (%)
#LegendI[CPU]: Load Average 1 min
#LegendO[CPU]: Load Average 5 min
#Legend1[CPU]: Load Average 1 min
#Legend2[CPU]: Load Average 5 min
#Title[CPU]: CPU Load Average
#PageTop[CPU]: <h1>CPU Load Average .15</h1>
################################################################




################################################################
#RAM
################################################################
#Target[mem]: .1.3.6.1.4.1.2021.4.6.0&.1.3.6.1.4.1.2021.4.4.0:public@192.168.1.15:::::2
# total memory
#MaxBytes1[Mem]: 4047620
# total swap
#MaxBytes2[Mem]: 3145724
#Unscaled[Mem]: dwmy
#Options[Mem]: gauge, growright
#YLegend[Mem]: Mem Free(Bytes)
#ShortLegend[Mem]: Bytes
#kilo[Mem]: 1024
#kMG[Mem]: k,M,G,T,P
#LegendI[Mem]: Real
#LegendO[Mem]: Swap
#Legend1[Mem]: Memory Free [MBytes]
#Legend2[Mem]: Swap Free [MBytes]
#Title[Mem]: Memory Free
#PageTop[Mem]: <H1>Memory Free MRTG client .15</H1>
################################################################



```

With this config i got from the localhost(.14) ethernet, CPU, Memfree and i added the remote pc (.15) ethernet. 
in the last part of the file i have commented out a few lines for CPU and memory of the remote host. even though they work fine for the localhost, once i got these lines in the code i get the following error:
```
root@mainmrtg: ~ $ indexmaker --columns=3 /etc/mrtg.cfg > /var/www/html/mrtg/index.htmlERROR: Line 342 (Target[CPU]: .1.3.6.1.4.1.2021.10.1.5.1&.1.3.6.1.4.1.2021.10.1.5.2:public@192.168.1.15:::::2) in CFG file (/etc/mrtg.cfg)
contains a duplicate definition for target[cpu].
First definition is on line 199
root@mainmrtg: ~ $



```

Any ideas please on how to overcome this issue and monitor remote cpu/memory, please?

---

