---
title: "Saving programs on wine?"
date: 2012-11-22
forum: General Help
---

### Post by Ragi1992 on 2012-11-22
How do I open windows .exe files on my lubuntu 12.04?

I am trying to get splashtop streamer

---

### Post by Ragi1992 on 2012-11-22
Nevermind figured it out.

---

### Post by vasa1 on 2012-11-22
Two points:
Is this a WUBI install?
If you figure out something, it would be nice if you post the solution.

---

### Post by Ragi1992 on 2012-11-22
> **vasa1 said:**
> Two points:
Is this a WUBI install?
If you figure out something, it would be nice if you post the solution.

I am using Mozilla Firefox. I saved the file using Mono Runtime (default), I right clicked and clicked open containing folder. Then I went to file manager and put in /tmp. I found said .EXE file and right clicked and then clicked Wine Windows Program Loader. And yes this is a WUBI install. Lubuntu 12.04. Could you possibly help me with this other thread I started? [http://ubuntuforums.org/showthread.php?t=2086816](http://ubuntuforums.org/showthread.php?t=2086816)

Thanks for your time.

---

### Post by vasa1 on 2012-11-22
> **Ragi1992 said:**
> ... Could you possibly help me with this other thread I started? [http://ubuntuforums.org/showthread.php?t=2086816](http://ubuntuforums.org/showthread.php?t=2086816)
...
Sorry, what you're trying to do over there is way beyond me :(

---

### Post by Ragi1992 on 2012-11-22
Does anyone on this site know how to? I'm seriously getting irriatated to the point I just want to quit using Ubuntu. I really need a remote desktop application that can work on my phone. If I can't get that for my phone then Ubuntu is completely and utterly useless to me.

---

### Post by zombifier25 on 2012-11-22
Looked up Splashtop Streamer on WIneHQ, and the rating is Bronze, wich means "Don't count on it".

Ubuntu has a remote desktop client installed by default, and any program  on Android/iOS that supports VNC should work with it. Here's an example tutorial: [http://maketecheasier.com/remote-control-ubuntu-from-android-tablet/2011/12/20](http://maketecheasier.com/remote-control-ubuntu-from-android-tablet/2011/12/20)

---

### Post by Ragi1992 on 2012-11-22
> **zombifier25 said:**
> Looked up Splashtop Streamer on WIneHQ, and the rating is Bronze, wich means "Don't count on it".

Ubuntu has a remote desktop client installed by default, and any program  on Android/iOS that supports VNC should work with it. Here's an example tutorial: [http://maketecheasier.com/remote-control-ubuntu-from-android-tablet/2011/12/20](http://maketecheasier.com/remote-control-ubuntu-from-android-tablet/2011/12/20)

Its still not working. I dont know what I am doing wrong, but I type in the IP address and it says it can not connect. When I tried to install it through windows it said it was interrupted and keeps doing that.

---

### Post by zombifier25 on 2012-11-22
Check that you typed the correct IP address. Is your phone and the computer in the same network?

---

### Post by Ragi1992 on 2012-11-22
Yes, my phone and computer are both on WIFI ATT9353. 

here is the results of sudo ifconfig command I did:

```
eth0      Link encap:Ethernet  HWaddr 00:07:e9:27:56:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:10:18:07:88:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1922094 (1.9 MB)  TX bytes:1922094 (1.9 MB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:a9:a7:a3  
          inet addr:192.168.1.112  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:304:6f87:d599:e91e:86fd:1571:abea/64 Scope:Global
          inet6 addr: 2602:304:6f87:d599:211:50ff:fea9:a7a3/64 Scope:Global
          inet6 addr: fe80::211:50ff:fea9:a7a3/64 Scope:Link
          inet6 addr: 2602:304:6f87:d599:e8cb:b9af:84ac:a902/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:173311 errors:0 dropped:0 overruns:0 frame:0
          TX packets:115950 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:184634441 (184.6 MB)  TX bytes:15961774 (15.9 MB)

and netstat:

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp      213      0 ubuntu:44690            ec2-50-18-128-253.:http CLOSE_WAIT 
tcp6       0      0 2602:304:6f87:d59:53291 lax02s02-in-x04.1e:http ESTABLISHED
tcp6       0      0 2602:304:6f87:d59:59375 lax02s01-in-x0e.1e:http ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ]         DGRAM                    8989     /var/run/wpa_supplicant/wlan0
unix  14     [ ]         DGRAM                    8374     /dev/log
unix  2      [ ]         DGRAM                    961023   
unix  2      [ ]         DGRAM                    961020   
unix  2      [ ]         DGRAM                    928289   
unix  3      [ ]         STREAM     CONNECTED     855745   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     855744   
unix  2      [ ]         STREAM     CONNECTED     855187   
unix  3      [ ]         STREAM     CONNECTED     855045   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     855044   
unix  3      [ ]         STREAM     CONNECTED     832914   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     832913   
unix  3      [ ]         STREAM     CONNECTED     832912   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     832911   
unix  3      [ ]         STREAM     CONNECTED     832901   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     832900   
unix  3      [ ]         STREAM     CONNECTED     831869   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     831868   
unix  3      [ ]         STREAM     CONNECTED     831867   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     831866   
unix  3      [ ]         STREAM     CONNECTED     831853   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     831852   
unix  3      [ ]         STREAM     CONNECTED     831850   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     831849   
unix  3      [ ]         STREAM     CONNECTED     792975   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     792974   
unix  3      [ ]         STREAM     CONNECTED     542196   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     542195   
unix  2      [ ]         STREAM     CONNECTED     542146   
unix  3      [ ]         STREAM     CONNECTED     542083   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     542082   
unix  3      [ ]         STREAM     CONNECTED     542073   
unix  3      [ ]         STREAM     CONNECTED     542072   
unix  3      [ ]         STREAM     CONNECTED     541983   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     541982   
unix  2      [ ]         STREAM     CONNECTED     541942   
unix  3      [ ]         STREAM     CONNECTED     541898   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     541897   
unix  3      [ ]         STREAM     CONNECTED     541889   
unix  3      [ ]         STREAM     CONNECTED     541888   
unix  3      [ ]         STREAM     CONNECTED     541480   
unix  3      [ ]         STREAM     CONNECTED     541479   
unix  3      [ ]         STREAM     CONNECTED     541470   
unix  3      [ ]         STREAM     CONNECTED     541469   
unix  3      [ ]         STREAM     CONNECTED     541461   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     541460   
unix  2      [ ]         STREAM     CONNECTED     541458   
unix  3      [ ]         STREAM     CONNECTED     541434   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     541433   
unix  3      [ ]         STREAM     CONNECTED     541423   
unix  3      [ ]         STREAM     CONNECTED     541422   
unix  3      [ ]         STREAM     CONNECTED     540172   
unix  3      [ ]         STREAM     CONNECTED     540171   
unix  3      [ ]         STREAM     CONNECTED     540164   
unix  3      [ ]         STREAM     CONNECTED     540163   
unix  3      [ ]         STREAM     CONNECTED     540157   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     540156   
unix  3      [ ]         STREAM     CONNECTED     540148   
unix  3      [ ]         STREAM     CONNECTED     540147   
unix  3      [ ]         STREAM     CONNECTED     535714   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     535713   
unix  3      [ ]         STREAM     CONNECTED     535711   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     535710   
unix  3      [ ]         STREAM     CONNECTED     535673   
unix  3      [ ]         STREAM     CONNECTED     535672   
unix  3      [ ]         STREAM     CONNECTED     535601   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     535600   
unix  3      [ ]         STREAM     CONNECTED     535513   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     535512   
unix  3      [ ]         STREAM     CONNECTED     535505   
unix  3      [ ]         STREAM     CONNECTED     535504   
unix  3      [ ]         STREAM     CONNECTED     535497   
unix  3      [ ]         STREAM     CONNECTED     535496   
unix  3      [ ]         STREAM     CONNECTED     535485   
unix  3      [ ]         STREAM     CONNECTED     535484   
unix  3      [ ]         STREAM     CONNECTED     535474   
unix  3      [ ]         STREAM     CONNECTED     535473   
unix  3      [ ]         STREAM     CONNECTED     535463   
unix  3      [ ]         STREAM     CONNECTED     535462   
unix  3      [ ]         STREAM     CONNECTED     535432   
unix  3      [ ]         STREAM     CONNECTED     535431   
unix  3      [ ]         STREAM     CONNECTED     535411   
unix  3      [ ]         STREAM     CONNECTED     535410   
unix  3      [ ]         STREAM     CONNECTED     534181   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     534180   
unix  3      [ ]         STREAM     CONNECTED     401681   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     401680   
unix  3      [ ]         STREAM     CONNECTED     360319   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     360318   
unix  3      [ ]         STREAM     CONNECTED     327167   @/dbus-vfs-daemon/socket-dQOMIhkf
unix  3      [ ]         STREAM     CONNECTED     327166   
unix  3      [ ]         STREAM     CONNECTED     327165   @/dbus-vfs-daemon/socket-1LllklX8
unix  3      [ ]         STREAM     CONNECTED     327164   
unix  3      [ ]         STREAM     CONNECTED     327159   @/dbus-vfs-daemon/socket-BMwMe5k0
unix  3      [ ]         STREAM     CONNECTED     327158   
unix  3      [ ]         STREAM     CONNECTED     327160   @/dbus-vfs-daemon/socket-qAEObmCt
unix  3      [ ]         STREAM     CONNECTED     327157   
unix  3      [ ]         STREAM     CONNECTED     327154   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     327153   
unix  3      [ ]         STREAM     CONNECTED     100951   @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     100950   
unix  3      [ ]         STREAM     CONNECTED     86761    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     86760    
unix  3      [ ]         STREAM     CONNECTED     35786    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     35785    
unix  3      [ ]         STREAM     CONNECTED     35770    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     35769    
unix  3      [ ]         STREAM     CONNECTED     35768    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     35767    
unix  3      [ ]         STREAM     CONNECTED     35759    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     35758    
unix  3      [ ]         STREAM     CONNECTED     35749    
unix  3      [ ]         STREAM     CONNECTED     35748    
unix  3      [ ]         STREAM     CONNECTED     35735    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     35734    
unix  3      [ ]         STREAM     CONNECTED     35728    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     35727    
unix  3      [ ]         STREAM     CONNECTED     16892    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     16891    
unix  2      [ ]         DGRAM                    16890    
unix  3      [ ]         STREAM     CONNECTED     16885    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     16884    
unix  3      [ ]         STREAM     CONNECTED     16877    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     16876    
unix  3      [ ]         STREAM     CONNECTED     16409    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     16408    
unix  3      [ ]         STREAM     CONNECTED     14933    @/dbus-vfs-daemon/socket-OhDPahBH
unix  3      [ ]         STREAM     CONNECTED     14932    
unix  3      [ ]         STREAM     CONNECTED     14931    @/dbus-vfs-daemon/socket-EKnb3cdH
unix  3      [ ]         STREAM     CONNECTED     14930    
unix  3      [ ]         STREAM     CONNECTED     14898    @/dbus-vfs-daemon/socket-59JfkX05
unix  3      [ ]         STREAM     CONNECTED     14897    
unix  3      [ ]         STREAM     CONNECTED     14896    @/dbus-vfs-daemon/socket-9CbQvSbt
unix  3      [ ]         STREAM     CONNECTED     14895    
unix  3      [ ]         STREAM     CONNECTED     14892    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     14891    
unix  3      [ ]         STREAM     CONNECTED     14848    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     14847    
unix  3      [ ]         STREAM     CONNECTED     14846    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     14845    
unix  3      [ ]         STREAM     CONNECTED     14844    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     14843    
unix  3      [ ]         STREAM     CONNECTED     14842    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14841    
unix  3      [ ]         STREAM     CONNECTED     14839    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14838    
unix  3      [ ]         STREAM     CONNECTED     14640    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     14639    
unix  3      [ ]         STREAM     CONNECTED     13336    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     13335    
unix  3      [ ]         STREAM     CONNECTED     13331    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     13330    
unix  3      [ ]         STREAM     CONNECTED     13027    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     13026    
unix  3      [ ]         STREAM     CONNECTED     13024    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     13023    
unix  3      [ ]         STREAM     CONNECTED     12933    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12932    
unix  3      [ ]         STREAM     CONNECTED     12814    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12813    
unix  3      [ ]         STREAM     CONNECTED     12812    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12811    
unix  3      [ ]         STREAM     CONNECTED     12804    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12803    
unix  3      [ ]         STREAM     CONNECTED     12765    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12764    
unix  3      [ ]         STREAM     CONNECTED     12736    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12735    
unix  3      [ ]         STREAM     CONNECTED     12728    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12727    
unix  3      [ ]         STREAM     CONNECTED     12726    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12725    
unix  3      [ ]         STREAM     CONNECTED     12719    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12718    
unix  3      [ ]         STREAM     CONNECTED     12717    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12716    
unix  3      [ ]         STREAM     CONNECTED     12712    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12711    
unix  3      [ ]         STREAM     CONNECTED     12708    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12707    
unix  3      [ ]         STREAM     CONNECTED     12700    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12699    
unix  3      [ ]         STREAM     CONNECTED     12698    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12697    
unix  3      [ ]         STREAM     CONNECTED     12683    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12682    
unix  3      [ ]         STREAM     CONNECTED     12673    
unix  3      [ ]         STREAM     CONNECTED     12672    
unix  3      [ ]         STREAM     CONNECTED     12671    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12670    
unix  3      [ ]         STREAM     CONNECTED     12666    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12665    
unix  3      [ ]         STREAM     CONNECTED     12656    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12655    
unix  3      [ ]         STREAM     CONNECTED     12650    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12649    
unix  3      [ ]         STREAM     CONNECTED     12648    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12647    
unix  3      [ ]         STREAM     CONNECTED     12641    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12640    
unix  3      [ ]         STREAM     CONNECTED     12638    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12637    
unix  3      [ ]         STREAM     CONNECTED     12630    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12629    
unix  3      [ ]         STREAM     CONNECTED     12611    /tmp/.menu-cached-:0-stetson
unix  3      [ ]         STREAM     CONNECTED     12610    
unix  3      [ ]         STREAM     CONNECTED     12594    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12593    
unix  3      [ ]         STREAM     CONNECTED     12590    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12589    
unix  3      [ ]         STREAM     CONNECTED     12587    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12586    
unix  3      [ ]         STREAM     CONNECTED     12568    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12567    
unix  3      [ ]         STREAM     CONNECTED     12566    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12565    
unix  3      [ ]         STREAM     CONNECTED     12561    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12560    
unix  3      [ ]         STREAM     CONNECTED     12515    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12514    
unix  3      [ ]         STREAM     CONNECTED     12509    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12508    
unix  3      [ ]         STREAM     CONNECTED     12482    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12481    
unix  3      [ ]         STREAM     CONNECTED     12433    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12432    
unix  2      [ ]         DGRAM                    12431    
unix  3      [ ]         STREAM     CONNECTED     12414    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12413    
unix  3      [ ]         STREAM     CONNECTED     12411    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12410    
unix  3      [ ]         STREAM     CONNECTED     12401    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12400    
unix  3      [ ]         STREAM     CONNECTED     12366    @/tmp/dbus-C8PphWGWM7
unix  3      [ ]         STREAM     CONNECTED     12365    
unix  3      [ ]         STREAM     CONNECTED     12363    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12362    
unix  3      [ ]         STREAM     CONNECTED     12330    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12329    
unix  3      [ ]         STREAM     CONNECTED     12325    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12324    
unix  3      [ ]         STREAM     CONNECTED     12322    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12321    
unix  3      [ ]         STREAM     CONNECTED     12317    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12316    
unix  3      [ ]         STREAM     CONNECTED     12229    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12228    
unix  3      [ ]         STREAM     CONNECTED     12227    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12226    
unix  3      [ ]         STREAM     CONNECTED     12217    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12216    
unix  3      [ ]         STREAM     CONNECTED     12215    
unix  3      [ ]         STREAM     CONNECTED     12214    
unix  3      [ ]         STREAM     CONNECTED     12201    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12200    
unix  3      [ ]         STREAM     CONNECTED     11888    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11887    
unix  2      [ ]         DGRAM                    10842    
unix  2      [ ]         DGRAM                    9891     
unix  3      [ ]         STREAM     CONNECTED     9612     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9611     
unix  3      [ ]         STREAM     CONNECTED     9608     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9607     
unix  2      [ ]         DGRAM                    9524     
unix  3      [ ]         STREAM     CONNECTED     9373     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9372     
unix  3      [ ]         STREAM     CONNECTED     9350     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9349     
unix  3      [ ]         STREAM     CONNECTED     9241     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9240     
unix  3      [ ]         STREAM     CONNECTED     9237     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9236     
unix  3      [ ]         STREAM     CONNECTED     9194     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9193     
unix  3      [ ]         STREAM     CONNECTED     9028     
unix  3      [ ]         STREAM     CONNECTED     9027     
unix  3      [ ]         STREAM     CONNECTED     8968     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8967     
unix  2      [ ]         DGRAM                    8962     
unix  3      [ ]         STREAM     CONNECTED     8878     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8877     
unix  2      [ ]         DGRAM                    8867     
unix  3      [ ]         STREAM     CONNECTED     8866     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8865     
unix  3      [ ]         STREAM     CONNECTED     8811     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8810     
unix  3      [ ]         STREAM     CONNECTED     8778     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8777     
unix  2      [ ]         DGRAM                    8773     
unix  3      [ ]         STREAM     CONNECTED     8504     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8503     
unix  2      [ ]         DGRAM                    8502     
unix  3      [ ]         STREAM     CONNECTED     8466     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8465     
unix  2      [ ]         DGRAM                    8463     
unix  3      [ ]         STREAM     CONNECTED     8434     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8433     
unix  3      [ ]         STREAM     CONNECTED     8412     
unix  3      [ ]         STREAM     CONNECTED     8411     
unix  3      [ ]         STREAM     CONNECTED     8197     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     8196     
unix  3      [ ]         DGRAM                    6990     
unix  3      [ ]         DGRAM                    6989     
unix  3      [ ]         STREAM     CONNECTED     6920     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     6917     
```

I typed my IP address as well as the routers ip address AND MAC address. Nothing. All it says is that it can not connect.

---

### Post by Ragi1992 on 2012-11-22
It also did this on Mocha VNC Lite. Just would not connect. Its either the host ID I put in is wrong or the server port is wrong. Bad thing is I don't know how to do server ports at all. Not on Windows or Linux..

---

### Post by zombifier25 on 2012-11-22
OK, this topic has kinda spiralled into off-topic land. You should create a new thread about your problem.

---

### Post by Ragi1992 on 2012-11-22
> **zombifier25 said:**
> OK, this topic has kinda spiralled into off-topic land. You should create a new thread about your problem.

[http://ubuntuforums.org/showthread.php?t=2086816](http://ubuntuforums.org/showthread.php?t=2086816)

---

