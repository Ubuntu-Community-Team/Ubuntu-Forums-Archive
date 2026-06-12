---
title: "MySQL setup"
date: 2014-08-05
forum: General Help
---

### Post by andreadixon825 on 2014-08-05
Hi, I need to get MySQL to work, I'm using ubuntu 14.04 64bit and When I open MySQL Workbench and made a new connection, then I presset the Test Connection button I get this error and everytime I try new port or hostname I get the same error all the time please help me with this I really need this to work. Thanks So Much):P

Error
Failed to Connect to MySQL at 127.0.0.1:3306 with user root

---

### Post by The Cog on 2014-08-05
First, let's see if mysql is running and listening for connections. Please can you post the output of these two commands:
```
netstat m-lntp
ps -ef | grep mysql
```
It may help if you include the command you type in (in case there are any typing errors)

---

### Post by andreadixon825 on 2014-08-05
Ok here is the one of netstat m-lntp

```
andreadixon@andreadixon-MS-7641:~$ netstat m-lntp
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        1      0 andreadixon-MS-76:43682 194.71.107.50:http      CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:37951 91.237.88.230:http      CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:59934 62.244.40.222:http      CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:59482 lax02s02-in-f7.1e:https ESTABLISHED
tcp        1      0 andreadixon-MS-76:37722 irc.su:http             CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:41710 5.237.105.36:55753      TIME_WAIT  
tcp        0      0 andreadixon-MS-76:45452 188.190.120.74:http     CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:44778 94.242.192.231:http     CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:57314 91.236.116.33:http      CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:52247 publicbt.com:http       CLOSE_WAIT 
tcp        0 1343380 andreadixon-MS-76:37855 109.100.180.132:29448   ESTABLISHED
tcp        1      0 andreadixon-MS-76:34848 mail.netrogenic.co:http CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:46980 dsl-189-165-118-2:26997 TIME_WAIT  
tcp        0      0 andreadixon-MS-76:39662 93-173-165-166.bb:25887 ESTABLISHED
tcp        1      0 andreadixon-MS-76:33964 122.228.251.69:http     CLOSE_WAIT 
tcp        0      1 andreadixon-MS-76:38145 36.69.189.120:1500      SYN_SENT   
tcp        0      0 andreadixon-MS-76:57916 202.172.20.71:webmin    ESTABLISHED
tcp        1      1 andreadixon-MS-76:59826 62.244.40.222:http      LAST_ACK   
tcp        1      0 andreadixon-MS-76:45399 barbadine.canonica:http CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:53192 pc-in-f95.1e100.ne:http ESTABLISHED
tcp        1      0 andreadixon-MS-76:53792 121.14.200.21:http      CLOSE_WAIT 
tcp        0      1 andreadixon-MS-76:45724 31.214.59.78:56303      FIN_WAIT1  
tcp        0      0 andreadixon-MS-76:35456 89-168-78-24.dyna:61195 ESTABLISHED
tcp        1      0 andreadixon-MS-76:60065 web01.prq.se:http       CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:36454 mail.puggsy.net:http    CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:38669 teksavvy.is.recomm:http CLOSE_WAIT 
tcp        0      1 andreadixon-MS-76:42273 64.4.17.176:ftp         SYN_SENT   
tcp        1      0 andreadixon-MS-76:35562 193.0.202.27:http       CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:55276 46.39.251.15:http       CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:43031 edge-star-shv-05-:https ESTABLISHED
tcp        1      0 andreadixon-MS-76:51847 site-redirect.dynd:http CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:37644 210-244-71-11.adsl:6969 CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:54775 LXXXIX.CCXLVIII.CC:http CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:43215 194.71.107.27:http      CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:53784 121.14.200.21:http      CLOSE_WAIT 
tcp        0  26860 andreadixon-MS-76:48838 60-240-176-152.tp:19132 ESTABLISHED
tcp        0      0 andreadixon-MS-76:32796 retracker2.hq.erte:http CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:40209 107.14.47.50:https      ESTABLISHED
tcp        1      0 andreadixon-MS-76:52287 m2.flirtcity.com:http   CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:39938 backoo.canonical.c:http CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:36828 50-36-39-169.drr01:6881 ESTABLISHED
tcp        1      0 andreadixon-MS-76:48161 180.153.120.93:http     CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:56927 89.188.127.134:http     CLOSE_WAIT 
tcp       54      0 andreadixon-MS-76:32822 94.242.192.231:https    CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:56024 ip-46-238-28-56.h:18785 TIME_WAIT  
tcp        1      0 andreadixon-MS-76:55371 bg.yts.re:http          CLOSE_WAIT 
tcp        0      0 andreadixon-MS-76:40208 107.14.47.50:https      ESTABLISHED
tcp        1      0 andreadixon-MS-76:37625 www.dyn.com:http        CLOSE_WAIT 

tcp        1      0 andreadixon-MS-76:58644 193.107.16.142:http     CLOSE_WAIT 
tcp        1      0 andreadixon-MS-76:37610 backoo.canonical.c:http CLOSE_WAIT 
tcp        0     27 andreadixon-MS-76:45720 78.90.161.111:25252     ESTABLISHED
udp        0      0 andreadixon-MS-76:49389 192.168.0.1:5351        ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  18     [ ]         DGRAM                    10591    /dev/log
unix  2      [ ]         STREAM     CONNECTED     120995   @/dbus-vfs-daemon/socket-7DcHqSAo
unix  3      [ ]         STREAM     CONNECTED     12042    
unix  3      [ ]         STREAM     CONNECTED     113758   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10035    
unix  3      [ ]         STREAM     CONNECTED     19572    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     1493     
unix  3      [ ]         STREAM     CONNECTED     12177    /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     12164    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14840    
unix  3      [ ]         STREAM     CONNECTED     116230   
unix  3      [ ]         STREAM     CONNECTED     15235    
unix  3      [ ]         STREAM     CONNECTED     12112    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     117943   @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     14687    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12050    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12106    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     14540    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     1643     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     113760   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18528    
unix  3      [ ]         STREAM     CONNECTED     12671    @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         DGRAM                    1477     
unix  3      [ ]         STREAM     CONNECTED     12859    @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         STREAM     CONNECTED     12754    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     111132   
unix  3      [ ]         STREAM     CONNECTED     12165    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     8817     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8402     
unix  3      [ ]         STREAM     CONNECTED     12604    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     258011   
unix  2      [ ]         STREAM     CONNECTED     254312   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     12144    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14562    
unix  3      [ ]         STREAM     CONNECTED     105136   
unix  3      [ ]         STREAM     CONNECTED     9083     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9044     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     115737   
unix  2      [ ]         DGRAM                    9903     
unix  3      [ ]         STREAM     CONNECTED     15460    
unix  3      [ ]         STREAM     CONNECTED     12066    
unix  3      [ ]         STREAM     CONNECTED     15635    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     9061     @/tmp/.X11-unix/X0
unix  2      [ ]         DGRAM                    9652     
unix  3      [ ]         STREAM     CONNECTED     23681    
unix  3      [ ]         STREAM     CONNECTED     12090    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15422    
unix  3      [ ]         STREAM     CONNECTED     9178     
unix  3      [ ]         STREAM     CONNECTED     14739    
unix  3      [ ]         STREAM     CONNECTED     12578    @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         DGRAM                    10038    
unix  3      [ ]         STREAM     CONNECTED     25691    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     9174     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12166    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     15488    
unix  3      [ ]         STREAM     CONNECTED     11228    
unix  3      [ ]         STREAM     CONNECTED     9060     
unix  3      [ ]         STREAM     CONNECTED     9190     /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     9136     /var/run/dbus/system_bus_socket
unix  2      [ ]         STREAM     CONNECTED     21968    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     9005     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12591    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15462    
unix  3      [ ]         STREAM     CONNECTED     9047     @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     111136   
unix  3      [ ]         STREAM     CONNECTED     14855    @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         STREAM     CONNECTED     105181   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     9035     @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     111142   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     115733   
unix  3      [ ]         STREAM     CONNECTED     14697    
unix  3      [ ]         STREAM     CONNECTED     15461    
unix  3      [ ]         STREAM     CONNECTED     15543    
unix  3      [ ]         STREAM     CONNECTED     12072    
unix  3      [ ]         STREAM     CONNECTED     257859   
unix  3      [ ]         STREAM     CONNECTED     9176     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15390    
unix  3      [ ]         STREAM     CONNECTED     120887   
unix  3      [ ]         STREAM     CONNECTED     10218    
unix  3      [ ]         STREAM     CONNECTED     10186    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     1482     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12728    
unix  3      [ ]         STREAM     CONNECTED     15547    
unix  3      [ ]         STREAM     CONNECTED     14788    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     8444     @/com/ubuntu/upstart
unix  3      [ ]         SEQPACKET  CONNECTED     118610   
unix  3      [ ]         STREAM     CONNECTED     15048    
unix  3      [ ]         STREAM     CONNECTED     14967    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     108499   
unix  3      [ ]         STREAM     CONNECTED     9148     @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         DGRAM                    8829     
unix  3      [ ]         STREAM     CONNECTED     12107    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12067    
unix  3      [ ]         STREAM     CONNECTED     116231   
unix  3      [ ]         STREAM     CONNECTED     10170    
unix  3      [ ]         STREAM     CONNECTED     15464    
unix  3      [ ]         STREAM     CONNECTED     115158   
unix  3      [ ]         STREAM     CONNECTED     12727    
unix  3      [ ]         STREAM     CONNECTED     8977     
unix  3      [ ]         STREAM     CONNECTED     9675     
unix  3      [ ]         STREAM     CONNECTED     12672    
unix  3      [ ]         STREAM     CONNECTED     1597     
unix  3      [ ]         STREAM     CONNECTED     15463    
unix  3      [ ]         STREAM     CONNECTED     9922     
unix  3      [ ]         STREAM     CONNECTED     9689     /var/run/dbus/system_bus_socket
unix  2      [ ]         STREAM     CONNECTED     249000   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     114026   @/tmp/.ICE-unix/2019
unix  3      [ ]         STREAM     CONNECTED     15471    
unix  3      [ ]         STREAM     CONNECTED     117944   @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     23684    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     12634    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12598    
unix  3      [ ]         STREAM     CONNECTED     12087    
unix  3      [ ]         STREAM     CONNECTED     12061    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     9002     
unix  3      [ ]         STREAM     CONNECTED     210915   
unix  2      [ ]         DGRAM                    14390    
unix  3      [ ]         STREAM     CONNECTED     105137   
unix  3      [ ]         STREAM     CONNECTED     19558    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     266525   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20545    @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         STREAM     CONNECTED     23774    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     14679    
unix  3      [ ]         STREAM     CONNECTED     16510    /run/user/1000/keyring-EcrT3Y/pkcs11
unix  3      [ ]         STREAM     CONNECTED     9682     
unix  3      [ ]         STREAM     CONNECTED     114028   @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     16419    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14760    
unix  3      [ ]         STREAM     CONNECTED     8842     
unix  3      [ ]         STREAM     CONNECTED     9049     @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         STREAM     CONNECTED     117474   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     16565    
unix  3      [ ]         STREAM     CONNECTED     9006     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     115734   
unix  3      [ ]         STREAM     CONNECTED     8943     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9360     
unix  3      [ ]         STREAM     CONNECTED     9063     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15212    
unix  3      [ ]         STREAM     CONNECTED     12062    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     108491   
unix  3      [ ]         STREAM     CONNECTED     19575    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     18519    
unix  3      [ ]         STREAM     CONNECTED     115740   
unix  3      [ ]         STREAM     CONNECTED     10220    @/tmp/.ICE-unix/2019
unix  3      [ ]         STREAM     CONNECTED     12633    
unix  3      [ ]         STREAM     CONNECTED     14761    
unix  3      [ ]         STREAM     CONNECTED     11834    
unix  3      [ ]         STREAM     CONNECTED     111138   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9963     
unix  3      [ ]         STREAM     CONNECTED     17377    
unix  3      [ ]         STREAM     CONNECTED     12119    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     20548    @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         STREAM     CONNECTED     108470   @/tmp/dbus-3G8Imo7M
unix  2      [ ]         STREAM     CONNECTED     45176    @/dbus-vfs-daemon/socket-AkVcU2CE
unix  3      [ ]         STREAM     CONNECTED     14970    
unix  3      [ ]         STREAM     CONNECTED     9184     @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     15634    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12621    
unix  3      [ ]         STREAM     CONNECTED     10221    @/tmp/.ICE-unix/2019
unix  3      [ ]         STREAM     CONNECTED     12120    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     49164    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12521    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     111135   
unix  3      [ ]         STREAM     CONNECTED     12825    /run/user/1000/keyring-EcrT3Y/pkcs11
unix  3      [ ]         STREAM     CONNECTED     15569    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12167    /var/run/dbus/system_bus_socket
unix  2      [ ]         DGRAM                    9471     
unix  3      [ ]         STREAM     CONNECTED     16566    /var/run/sdp
unix  3      [ ]         STREAM     CONNECTED     117492   
unix  3      [ ]         STREAM     CONNECTED     20606    @/tmp/dbus-vOslSp0RUR
unix  2      [ ]         STREAM     CONNECTED     51441    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     12130    
unix  3      [ ]         STREAM     CONNECTED     15445    
unix  2      [ ]         STREAM     CONNECTED     124104   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     19579    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     10224    @/tmp/.ICE-unix/2019
unix  3      [ ]         STREAM     CONNECTED     15472    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     13345    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14875    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     14538    
unix  3      [ ]         STREAM     CONNECTED     18527    
unix  3      [ ]         STREAM     CONNECTED     1719     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     270348   
unix  3      [ ]         STREAM     CONNECTED     257858   
unix  3      [ ]         STREAM     CONNECTED     12854    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     1783     
unix  3      [ ]         STREAM     CONNECTED     12590    
unix  3      [ ]         STREAM     CONNECTED     15444    
unix  3      [ ]         STREAM     CONNECTED     17401    
unix  3      [ ]         STREAM     CONNECTED     15421    
unix  3      [ ]         STREAM     CONNECTED     12466    
unix  3      [ ]         STREAM     CONNECTED     39601    
unix  3      [ ]         STREAM     CONNECTED     14411    
unix  3      [ ]         STREAM     CONNECTED     9084     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     116229   
unix  3      [ ]         STREAM     CONNECTED     12074    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     8986     @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     9942     
unix  3      [ ]         STREAM     CONNECTED     21098    
unix  3      [ ]         STREAM     CONNECTED     13356    
unix  2      [ ]         STREAM     CONNECTED     9681     
unix  3      [ ]         STREAM     CONNECTED     9001     
unix  3      [ ]         STREAM     CONNECTED     9704     
unix  3      [ ]         STREAM     CONNECTED     267646   @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     108490   
unix  2      [ ]         STREAM     CONNECTED     48078    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     12597    
unix  3      [ ]         STREAM     CONNECTED     9082     /var/run/dbus/system_bus_socket
unix  2      [ ]         STREAM     CONNECTED     257324   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     14783    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     117945   
unix  2      [ ]         STREAM     CONNECTED     111141   
unix  3      [ ]         STREAM     CONNECTED     9473     
unix  2      [ ]         DGRAM                    1492     
unix  3      [ ]         STREAM     CONNECTED     1551     
unix  3      [ ]         STREAM     CONNECTED     16404    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     14675    
unix  3      [ ]         STREAM     CONNECTED     266427   @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12673    
unix  3      [ ]         STREAM     CONNECTED     14776    /run/user/1000/pulse/native
unix  3      [ ]         STREAM     CONNECTED     15446    
unix  3      [ ]         STREAM     CONNECTED     114027   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15549    
unix  2      [ ]         DGRAM                    9725     
unix  3      [ ]         STREAM     CONNECTED     14782    
unix  3      [ ]         STREAM     CONNECTED     12860    @/dbus-vfs-daemon/socket-jwjnfSqR
unix  2      [ ]         DGRAM                    12602    
unix  3      [ ]         STREAM     CONNECTED     8750     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15465    
unix  3      [ ]         STREAM     CONNECTED     9029     @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     23682    
unix  3      [ ]         STREAM     CONNECTED     18534    
unix  3      [ ]         STREAM     CONNECTED     111137   
unix  3      [ ]         STREAM     CONNECTED     12674    @/tmp/.X11-unix/X0
unix  2      [ ]         STREAM     CONNECTED     70609    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     14810    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     105127   
unix  3      [ ]         STREAM     CONNECTED     15466    
unix  3      [ ]         STREAM     CONNECTED     15395    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12176    
unix  3      [ ]         STREAM     CONNECTED     15548    
unix  3      [ ]         STREAM     CONNECTED     14758    
unix  3      [ ]         STREAM     CONNECTED     9523     
unix  3      [ ]         STREAM     CONNECTED     12580    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     1478     
unix  3      [ ]         STREAM     CONNECTED     14680    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12053    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12122    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12715    
unix  3      [ ]         STREAM     CONNECTED     14828    
unix  3      [ ]         STREAM     CONNECTED     15473    
unix  3      [ ]         STREAM     CONNECTED     14601    
unix  3      [ ]         STREAM     CONNECTED     15410    
unix  3      [ ]         STREAM     CONNECTED     8985     
unix  3      [ ]         STREAM     CONNECTED     11629    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     258004   
unix  3      [ ]         STREAM     CONNECTED     108500   
unix  3      [ ]         STREAM     CONNECTED     111131   
unix  3      [ ]         STREAM     CONNECTED     12665    
unix  3      [ ]         STREAM     CONNECTED     12041    
unix  2      [ ]         STREAM     CONNECTED     120993   @/dbus-vfs-daemon/socket-O8phAkxY
unix  3      [ ]         STREAM     CONNECTED     113750   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     113762   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     115738   
unix  3      [ ]         STREAM     CONNECTED     9982     
unix  3      [ ]         STREAM     CONNECTED     14545    @/com/ubuntu/upstart-session/1000/1854
unix  3      [ ]         STREAM     CONNECTED     12714    
unix  3      [ ]         STREAM     CONNECTED     12059    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     8796     /var/run/dbus/system_bus_socket
unix  2      [ ]         STREAM     CONNECTED     257597   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     12142    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12626    
unix  3      [ ]         STREAM     CONNECTED     11189    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9182     
unix  3      [ ]         STREAM     CONNECTED     9135     @/tmp/.ICE-unix/2019
unix  2      [ ]         DGRAM                    1594     
unix  3      [ ]         SEQPACKET  CONNECTED     118611   
unix  3      [ ]         STREAM     CONNECTED     14684    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12206    
unix  3      [ ]         STREAM     CONNECTED     15004    
unix  3      [ ]         STREAM     CONNECTED     1526     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12619    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     117596   
unix  3      [ ]         STREAM     CONNECTED     10202    
unix  3      [ ]         STREAM     CONNECTED     10223    @/tmp/.ICE-unix/2019
unix  3      [ ]         STREAM     CONNECTED     12199    
unix  3      [ ]         STREAM     CONNECTED     1479     
unix  3      [ ]         STREAM     CONNECTED     270347   @/tmp/.ICE-unix/2019
unix  3      [ ]         STREAM     CONNECTED     54895    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     9048     @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12071    
unix  3      [ ]         STREAM     CONNECTED     258010   
unix  3      [ ]         STREAM     CONNECTED     116123   @/tmp/.X11-unix/X0
unix  2      [ ]         STREAM     CONNECTED     48137    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     10039    
unix  3      [ ]         STREAM     CONNECTED     14841    
unix  3      [ ]         STREAM     CONNECTED     229760   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12131    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12399    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     258003   
unix  3      [ ]         STREAM     CONNECTED     14965    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12593    
unix  3      [ ]         STREAM     CONNECTED     14544    @/com/ubuntu/upstart-session/1000/1854
unix  3      [ ]         STREAM     CONNECTED     108501   /run/user/1000/keyring-EcrT3Y/pkcs11
unix  3      [ ]         STREAM     CONNECTED     10219    @/tmp/.ICE-unix/2019
unix  3      [ ]         STREAM     CONNECTED     14757    
unix  3      [ ]         STREAM     CONNECTED     11601    
unix  2      [ ]         STREAM     CONNECTED     130179   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     14787    
unix  2      [ ]         DGRAM                    9567     
unix  3      [ ]         STREAM     CONNECTED     16452    
unix  3      [ ]         STREAM     CONNECTED     12627    
unix  3      [ ]         STREAM     CONNECTED     1661     
unix  3      [ ]         STREAM     CONNECTED     11425    @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     115751   
unix  3      [ ]         STREAM     CONNECTED     12073    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     9188     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     1646     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15213    
unix  3      [ ]         STREAM     CONNECTED     12227    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12676    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12160    
unix  3      [ ]         STREAM     CONNECTED     2023     /var/run/dbus/system_bus_socket
unix  2      [ ]         STREAM     CONNECTED     115175   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     9068     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15470    
unix  3      [ ]         STREAM     CONNECTED     12157    
unix  3      [ ]         STREAM     CONNECTED     12057    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12044    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     14539    
unix  3      [ ]         STREAM     CONNECTED     14690    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19566    /var/run/dbus/system_bus_socket
unix  3      [ ]         DGRAM                    10557    
unix  3      [ ]         STREAM     CONNECTED     12603    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     9003     @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     12616    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19466    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     115741   
unix  3      [ ]         STREAM     CONNECTED     15542    
unix  3      [ ]         STREAM     CONNECTED     14391    
unix  3      [ ]         STREAM     CONNECTED     105128   
unix  3      [ ]         STREAM     CONNECTED     15467    
unix  2      [ ]         DGRAM                    15222    
unix  3      [ ]         STREAM     CONNECTED     17379    
unix  3      [ ]         STREAM     CONNECTED     15419    
unix  3      [ ]         STREAM     CONNECTED     14876    
unix  3      [ ]         STREAM     CONNECTED     15490    
unix  3      [ ]         STREAM     CONNECTED     12849    
unix  3      [ ]         STREAM     CONNECTED     9194     @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     14602    
unix  2      [ ]         STREAM     CONNECTED     120996   @/dbus-vfs-daemon/socket-li4iucC8
unix  3      [ ]         STREAM     CONNECTED     51901    
unix  3      [ ]         STREAM     CONNECTED     15636    
unix  3      [ ]         STREAM     CONNECTED     15469    
unix  3      [ ]         STREAM     CONNECTED     14542    @/com/ubuntu/upstart-session/1000/1854
unix  3      [ ]         STREAM     CONNECTED     12594    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     115744   
unix  3      [ ]         STREAM     CONNECTED     15491    
unix  3      [ ]         STREAM     CONNECTED     9197     
unix  3      [ ]         STREAM     CONNECTED     119007   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     21963    
unix  3      [ ]         STREAM     CONNECTED     15391    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17378    
unix  3      [ ]         STREAM     CONNECTED     15420    
unix  3      [ ]         STREAM     CONNECTED     114186   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9004     @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     9743     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     10102    
unix  3      [ ]         STREAM     CONNECTED     9055     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10222    @/tmp/.ICE-unix/2019
unix  3      [ ]         STREAM     CONNECTED     12561    
unix  3      [ ]         STREAM     CONNECTED     1614     
unix  2      [ ]         STREAM     CONNECTED     268577   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     9112     
unix  3      [ ]         STREAM     CONNECTED     15492    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     14700    
unix  3      [ ]         STREAM     CONNECTED     8849     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     116228   
unix  3      [ ]         STREAM     CONNECTED     12589    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     268751   @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     258002   
unix  3      [ ]         STREAM     CONNECTED     15230    
unix  3      [ ]         STREAM     CONNECTED     12163    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     117493   
unix  3      [ ]         STREAM     CONNECTED     12058    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     14775    
unix  3      [ ]         STREAM     CONNECTED     12091    
unix  3      [ ]         STREAM     CONNECTED     12068    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14546    @/com/ubuntu/upstart-session/1000/1854
unix  3      [ ]         STREAM     CONNECTED     12518    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     20601    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     12453    
unix  3      [ ]         STREAM     CONNECTED     105135   
unix  3      [ ]         STREAM     CONNECTED     15561    
unix  3      [ ]         STREAM     CONNECTED     9501     
unix  3      [ ]         STREAM     CONNECTED     263072   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     15229    
unix  3      [ ]         STREAM     CONNECTED     2047     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     117486   
unix  3      [ ]         STREAM     CONNECTED     14683    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     111133   
unix  2      [ ]         STREAM     CONNECTED     120994   @/dbus-vfs-daemon/socket-ldVS1qCc
unix  3      [ ]         STREAM     CONNECTED     20609    @/dbus-vfs-daemon/socket-5UGk1SyG
unix  3      [ ]         STREAM     CONNECTED     15232    
unix  3      [ ]         STREAM     CONNECTED     9000     
unix  2      [ ]         DGRAM                    1790     
unix  3      [ ]         DGRAM                    10558    
unix  3      [ ]         STREAM     CONNECTED     15555    
unix  3      [ ]         STREAM     CONNECTED     14773    
unix  2      [ ]         DGRAM                    14329    
unix  2      [ ]         STREAM     CONNECTED     21105    @/tmp/dbus-3G8Imo7M
unix  3      [ ]         STREAM     CONNECTED     9474     
unix  3      [ ]         STREAM     CONNECTED     111134   
unix  3      [ ]         STREAM     CONNECTED     12143    
unix  3      [ ]         STREAM     CONNECTED     12623    
unix  3      [ ]         STREAM     CONNECTED     9025     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9758     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12622    @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     12558    
unix  3      [ ]         STREAM     CONNECTED     115745   
unix  3      [ ]         STREAM     CONNECTED     19055    @/dbus-vfs-daemon/socket-Sbc7tIO0
unix  3      [ ]         STREAM     CONNECTED     9032     @/tmp/dbus-vOslSp0RUR
unix  3      [ ]         STREAM     CONNECTED     8689     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     115156   
unix  3      [ ]         STREAM     CONNECTED     21962    @/dbus-vfs-daemon/socket-uHd8USff
unix  3      [ ]         STREAM     CONNECTED     17407    
unix  2      [ ]         DGRAM                    1532     
andreadixon@andreadixon-MS-7641:~$ 
andreadixon@andreadixon-MS-7641:~$ 

```

here is the other ps -ef | grep mysql

```
andreadixon@andreadixon-MS-7641:~$ ps -ef | grep mysql
andread+  1288  1242  0 12:31 pts/4    00:00:00 grep --color=auto mysql
andreadixon@andreadixon-MS-7641:~$ 

```

I hop I did this right. Thanks

---

### Post by andreadixon825 on 2014-08-06
Can Anyone help me with this plese.

---

### Post by cj13579 on 2014-08-06
The result of your *ps -ef* command shows that mysql-server isn't running. Before you start it, take a look at the file */etc/my.cnf* to find out which port it will be running on:

```
grep "port" /etc/my.cnf
```

I suggest that unless you have changed it that you will be using port 3306. Also, it looks like perhaps mysql isn't scheduled to start on boot. You can use the following to configure that:

```
sudo update-rc.d mysql defaults
```

---

### Post by The Cog on 2014-08-07
I made a typo, sorry. I don't know where the m came from. The command I meant was
```
netsgtat -lntp
```
Not that it matters. That command would have told us the address mysql was listening on, but it seems it's not running. Have you actually installed the server package? This command does it:
```
sudo apt-get install mysql-server
```
and it should start as soon as it's installed.

---

