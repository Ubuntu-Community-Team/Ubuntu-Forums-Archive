---
title: "HOW TO  finding port numbers"
date: 2007-06-29
forum: General Help
---

### Post by adityakavoor on 2007-06-29
HI 
is it possible to find which ports are being used by different applications in ubuntu ??
If yes ,.. how ??
Is it possible even on Win XP ?

Thanks in advance

---

### Post by orasis on 2007-06-29
> **adityakavoor said:**
> HI 
is it possible to find which ports are being used by different applications in ubuntu ??
If yes ,.. how ??
Is it possible even on Win XP ?

Thanks in advance

The same way you do in Windows... almost, In windows you start 'CMD' and type 'netstat -a' 

In Linux you start console and 'netstat' and 'man netstat' if you wish to see all the commands, this will show what ports are connected to what.

And if you want more local data, 'ifconfig' in console.

---

### Post by adityakavoor on 2007-06-29
this is the o/p of netstat

```
aditya@ubuntu:~$ netstat -v
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 ubuntu.local:45938      cs30.msg.dcn.yahoo:mmcc ESTABLISHED
tcp        1      0 ubuntu.local:53136      80.67.87.38:www         CLOSE_WAIT 
tcp        1      0 ubuntu.local:53137      80.67.87.38:www         CLOSE_WAIT 
tcp        0      0 ubuntu.local:40726      wf-in-f83.google.co:www ESTABLISHED
tcp        0      0 ubuntu.local:40724      wf-in-f83.google.co:www ESTABLISHED
tcp        0      0 ubuntu.local:40721      wf-in-f83.google.co:www ESTABLISHED
tcp       38      0 ubuntu.local:39003      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39002      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39001      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39006      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39005      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39004      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39008      colo-static.174.8:https CLOSE_WAIT 
tcp        0      0 ubuntu.local:53967      po-in-f125.:xmpp-client ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    8267     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    8444     @/org/kernel/udev/udevd
unix  10     [ ]         DGRAM                    14973    /dev/log
unix  2      [ ]         DGRAM                    15090    @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     36737    /tmp/ksocket-aditya/klauncherQDkPHb.slave-socket
unix  3      [ ]         STREAM     CONNECTED     36736    
unix  3      [ ]         STREAM     CONNECTED     36617    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     36616    
unix  3      [ ]         STREAM     CONNECTED     36613    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     36612    
unix  3      [ ]         STREAM     CONNECTED     36609    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     36608    
unix  3      [ ]         STREAM     CONNECTED     36555    
unix  3      [ ]         STREAM     CONNECTED     36554    
unix  3      [ ]         STREAM     CONNECTED     36552    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     36551    
unix  3      [ ]         STREAM     CONNECTED     36547    /tmp/orbit-aditya/linc-4302-0-5df776cf5321
unix  3      [ ]         STREAM     CONNECTED     36546    
unix  3      [ ]         STREAM     CONNECTED     36545    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     36544    
unix  3      [ ]         STREAM     CONNECTED     36543    /tmp/orbit-aditya/linc-4302-0-5df776cf5321
unix  3      [ ]         STREAM     CONNECTED     36542    
unix  3      [ ]         STREAM     CONNECTED     36539    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     36538    
unix  3      [ ]         STREAM     CONNECTED     36536    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     36535    
unix  3      [ ]         STREAM     CONNECTED     36531    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     36530    
unix  3      [ ]         STREAM     CONNECTED     36135    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     36134    
unix  3      [ ]         STREAM     CONNECTED     36131    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     36130    
unix  3      [ ]         STREAM     CONNECTED     36123    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     36122    
unix  3      [ ]         STREAM     CONNECTED     36120    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     36119    
unix  3      [ ]         STREAM     CONNECTED     35948    /tmp/orbit-aditya/linc-421e-0-5c68a1491779a
unix  3      [ ]         STREAM     CONNECTED     35947    
unix  3      [ ]         STREAM     CONNECTED     35944    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     35943    
unix  3      [ ]         STREAM     CONNECTED     35932    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     35931    
unix  3      [ ]         STREAM     CONNECTED     35660    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     35659    
unix  3      [ ]         STREAM     CONNECTED     35640    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     35639    
unix  3      [ ]         STREAM     CONNECTED     35501    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     35479    
unix  3      [ ]         STREAM     CONNECTED     35258    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     35257    
unix  3      [ ]         STREAM     CONNECTED     34613    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     34612    
unix  3      [ ]         STREAM     CONNECTED     33988    /tmp/ksocket-aditya/ubuntu-3e88-4684acfb
unix  3      [ ]         STREAM     CONNECTED     33987    
unix  2      [ ]         STREAM     CONNECTED     33962    /tmp/ksocket-aditya/kdeinit__0
unix  3      [ ]         STREAM     CONNECTED     33932    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     33931    
unix  3      [ ]         STREAM     CONNECTED     33930    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     33929    
unix  3      [ ]         STREAM     CONNECTED     33922    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     33921    
unix  3      [ ]         STREAM     CONNECTED     29463    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     29462    
unix  3      [ ]         STREAM     CONNECTED     28662    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     28661    
unix  3      [ ]         STREAM     CONNECTED     28660    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     28659    
unix  3      [ ]         STREAM     CONNECTED     28658    /tmp/orbit-aditya/linc-283d-0-68773cf687e8b
unix  3      [ ]         STREAM     CONNECTED     28657    
unix  3      [ ]         STREAM     CONNECTED     28654    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     28653    
unix  2      [ ]         STREAM     CONNECTED     27884    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     26851    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     26850    
unix  3      [ ]         STREAM     CONNECTED     26791    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     26790    
unix  3      [ ]         STREAM     CONNECTED     26787    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26786    
unix  3      [ ]         STREAM     CONNECTED     26781    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     26780    
unix  7      [ ]         STREAM     CONNECTED     26775    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26774    
unix  3      [ ]         STREAM     CONNECTED     26734    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26733    
unix  3      [ ]         STREAM     CONNECTED     26726    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     26725    
unix  3      [ ]         STREAM     CONNECTED     26718    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26717    
unix  3      [ ]         STREAM     CONNECTED     26708    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     26707    
unix  3      [ ]         STREAM     CONNECTED     26705    
unix  3      [ ]         STREAM     CONNECTED     26704    
unix  2      [ ]         STREAM     CONNECTED     25477    /var/run/acpid.socket
unix  2      [ ]         STREAM     CONNECTED     22760    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     22556    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     22555    
unix  3      [ ]         STREAM     CONNECTED     22554    /tmp/orbit-aditya/linc-1be4-0-5c8d52832f0e8
unix  3      [ ]         STREAM     CONNECTED     22553    
unix  3      [ ]         STREAM     CONNECTED     22550    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     22549    
unix  3      [ ]         STREAM     CONNECTED     22540    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22539    
unix  3      [ ]         STREAM     CONNECTED     19108    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19107    
unix  3      [ ]         STREAM     CONNECTED     19106    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     19105    
unix  3      [ ]         STREAM     CONNECTED     19104    /tmp/orbit-aditya/linc-166a-0-711f20b425919
unix  3      [ ]         STREAM     CONNECTED     19103    
unix  3      [ ]         STREAM     CONNECTED     19100    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     19099    
unix  3      [ ]         STREAM     CONNECTED     19095    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19094    
unix  3      [ ]         STREAM     CONNECTED     19084    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19083    
unix  3      [ ]         STREAM     CONNECTED     19082    /tmp/orbit-aditya/linc-1593-0-355adfc91003e
unix  3      [ ]         STREAM     CONNECTED     19081    
unix  3      [ ]         STREAM     CONNECTED     19080    /tmp/orbit-aditya/linc-1663-0-398e3a46455bb
unix  3      [ ]         STREAM     CONNECTED     19079    
unix  3      [ ]         STREAM     CONNECTED     19072    /tmp/orbit-aditya/linc-1663-0-398e3a46455bb
unix  3      [ ]         STREAM     CONNECTED     19071    
unix  3      [ ]         STREAM     CONNECTED     19070    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     19069    
unix  3      [ ]         STREAM     CONNECTED     19068    /tmp/orbit-aditya/linc-1663-0-398e3a46455bb
unix  3      [ ]         STREAM     CONNECTED     19067    
unix  3      [ ]         STREAM     CONNECTED     19064    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     19063    
unix  3      [ ]         STREAM     CONNECTED     19059    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19058    
unix  3      [ ]         STREAM     CONNECTED     19022    /tmp/orbit-aditya/linc-15c8-0-4559a31d8f6
unix  3      [ ]         STREAM     CONNECTED     19021    
unix  3      [ ]         STREAM     CONNECTED     19020    /tmp/orbit-aditya/linc-1637-0-64e16f3f600f8
unix  3      [ ]         STREAM     CONNECTED     19019    
unix  3      [ ]         STREAM     CONNECTED     19016    /tmp/orbit-aditya/linc-1640-0-2aeb149fd1771
unix  3      [ ]         STREAM     CONNECTED     19015    
unix  3      [ ]         STREAM     CONNECTED     19014    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     19013    
unix  3      [ ]         STREAM     CONNECTED     19011    /tmp/orbit-aditya/linc-1640-0-2aeb149fd1771
unix  3      [ ]         STREAM     CONNECTED     19010    
unix  3      [ ]         STREAM     CONNECTED     19007    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     19006    
unix  3      [ ]         STREAM     CONNECTED     19004    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     19003    
unix  3      [ ]         STREAM     CONNECTED     18999    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18998    
unix  3      [ ]         STREAM     CONNECTED     18996    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18995    
unix  3      [ ]         STREAM     CONNECTED     18981    /tmp/orbit-aditya/linc-1637-0-64e16f3f600f8
unix  3      [ ]         STREAM     CONNECTED     18980    
unix  3      [ ]         STREAM     CONNECTED     18979    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     18978    
unix  3      [ ]         STREAM     CONNECTED     18975    /tmp/orbit-aditya/linc-1637-0-64e16f3f600f8
unix  3      [ ]         STREAM     CONNECTED     18974    
unix  3      [ ]         STREAM     CONNECTED     18967    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18964    
unix  3      [ ]         STREAM     CONNECTED     18949    /tmp/orbit-aditya/linc-15c8-0-4559a31d8f6
unix  3      [ ]         STREAM     CONNECTED     18948    
unix  3      [ ]         STREAM     CONNECTED     18947    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     18946    
unix  3      [ ]         STREAM     CONNECTED     18940    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     18939    
unix  3      [ ]         STREAM     CONNECTED     18172    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18171    
unix  3      [ ]         STREAM     CONNECTED     18169    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18168    
unix  3      [ ]         STREAM     CONNECTED     18167    /tmp/orbit-aditya/linc-15c8-0-4559a31d8f6
unix  3      [ ]         STREAM     CONNECTED     18166    
unix  3      [ ]         STREAM     CONNECTED     18163    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18162    
unix  3      [ ]         STREAM     CONNECTED     18160    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     18159    
unix  3      [ ]         STREAM     CONNECTED     18155    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18154    
unix  3      [ ]         STREAM     CONNECTED     18144    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18143    
unix  3      [ ]         STREAM     CONNECTED     18142    /tmp/orbit-aditya/linc-1593-0-355adfc91003e
unix  3      [ ]         STREAM     CONNECTED     18141    
unix  3      [ ]         STREAM     CONNECTED     18140    /tmp/orbit-aditya/linc-15f6-0-2dc1e41c90350
unix  3      [ ]         STREAM     CONNECTED     18139    
unix  3      [ ]         STREAM     CONNECTED     18136    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18135    
unix  3      [ ]         STREAM     CONNECTED     18122    /tmp/mapping-aditya
unix  3      [ ]         STREAM     CONNECTED     18112    
unix  3      [ ]         STREAM     CONNECTED     18111    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18110    
unix  3      [ ]         STREAM     CONNECTED     18101    /tmp/orbit-aditya/linc-15ec-0-2dc1e41c904c9
unix  3      [ ]         STREAM     CONNECTED     18100    
unix  3      [ ]         STREAM     CONNECTED     18099    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     18098    
unix  3      [ ]         STREAM     CONNECTED     18097    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     18096    
unix  3      [ ]         STREAM     CONNECTED     18095    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     18094    
unix  3      [ ]         STREAM     CONNECTED     18093    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18092    
unix  2      [ ]         DGRAM                    18091    
unix  3      [ ]         STREAM     CONNECTED     18090    /tmp/orbit-aditya/linc-15f6-0-2dc1e41c90350
unix  3      [ ]         STREAM     CONNECTED     18089    
unix  3      [ ]         STREAM     CONNECTED     18088    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     18087    
unix  3      [ ]         STREAM     CONNECTED     18086    /tmp/orbit-aditya/linc-15ec-0-2dc1e41c904c9
unix  3      [ ]         STREAM     CONNECTED     18085    
unix  3      [ ]         STREAM     CONNECTED     18082    /tmp/orbit-aditya/linc-15f6-0-2dc1e41c90350
unix  3      [ ]         STREAM     CONNECTED     18081    
unix  3      [ ]         STREAM     CONNECTED     18078    /tmp/orbit-aditya/linc-15d4-0-2dc1e41c8feda
unix  3      [ ]         STREAM     CONNECTED     18077    
unix  3      [ ]         STREAM     CONNECTED     18074    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18071    
unix  3      [ ]         STREAM     CONNECTED     18069    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     18068    
unix  3      [ ]         STREAM     CONNECTED     18064    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18063    
unix  3      [ ]         STREAM     CONNECTED     18073    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18060    
unix  3      [ ]         STREAM     CONNECTED     18058    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     18057    
unix  3      [ ]         STREAM     CONNECTED     18053    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18052    
unix  3      [ ]         STREAM     CONNECTED     18072    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18048    
unix  3      [ ]         STREAM     CONNECTED     18044    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18043    
unix  3      [ ]         STREAM     CONNECTED     17989    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17988    
unix  3      [ ]         STREAM     CONNECTED     17978    /tmp/orbit-aditya/linc-15d5-0-7bd943dff0416
unix  3      [ ]         STREAM     CONNECTED     17975    
unix  3      [ ]         STREAM     CONNECTED     17972    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17971    
unix  3      [ ]         STREAM     CONNECTED     17963    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17962    
unix  3      [ ]         STREAM     CONNECTED     17937    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17936    
unix  3      [ ]         STREAM     CONNECTED     17933    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17932    
unix  3      [ ]         STREAM     CONNECTED     17931    /tmp/orbit-aditya/linc-15a7-0-86d218bbde31
unix  3      [ ]         STREAM     CONNECTED     17930    
unix  3      [ ]         STREAM     CONNECTED     17927    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17916    
unix  3      [ ]         STREAM     CONNECTED     17894    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     17893    
unix  3      [ ]         STREAM     CONNECTED     17797    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17796    
unix  3      [ ]         STREAM     CONNECTED     17794    /tmp/orbit-aditya/linc-1594-0-278e50745fc33
unix  3      [ ]         STREAM     CONNECTED     17793    
unix  3      [ ]         STREAM     CONNECTED     17792    /tmp/orbit-aditya/linc-1593-0-355adfc91003e
unix  3      [ ]         STREAM     CONNECTED     17791    
unix  3      [ ]         STREAM     CONNECTED     17790    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     17788    
unix  3      [ ]         STREAM     CONNECTED     17789    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     17787    
unix  3      [ ]         STREAM     CONNECTED     17913    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     17782    
unix  3      [ ]         STREAM     CONNECTED     17778    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17777    
unix  3      [ ]         STREAM     CONNECTED     17764    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17763    
unix  3      [ ]         STREAM     CONNECTED     17762    /tmp/orbit-aditya/linc-15a5-0-4c7031ab23f7e
unix  3      [ ]         STREAM     CONNECTED     17761    
unix  3      [ ]         STREAM     CONNECTED     17758    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17757    
unix  3      [ ]         STREAM     CONNECTED     17754    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17753    
unix  3      [ ]         STREAM     CONNECTED     17743    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17742    
unix  3      [ ]         STREAM     CONNECTED     17722    /tmp/orbit-aditya/linc-1594-0-278e50745fc33
unix  3      [ ]         STREAM     CONNECTED     17721    
unix  3      [ ]         STREAM     CONNECTED     17718    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17717    
unix  3      [ ]         STREAM     CONNECTED     17715    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     17714    
unix  3      [ ]         STREAM     CONNECTED     17710    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17709    
unix  3      [ ]         STREAM     CONNECTED     17672    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17671    
unix  3      [ ]         STREAM     CONNECTED     17669    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17668    
unix  3      [ ]         STREAM     CONNECTED     17667    /tmp/orbit-aditya/linc-159a-0-278e5074178fe
unix  3      [ ]         STREAM     CONNECTED     17666    
unix  3      [ ]         STREAM     CONNECTED     17663    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17662    
unix  3      [ ]         STREAM     CONNECTED     17660    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     17659    
unix  3      [ ]         STREAM     CONNECTED     17655    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17654    
unix  3      [ ]         STREAM     CONNECTED     17649    /tmp/orbit-aditya/linc-1593-0-355adfc91003e
unix  3      [ ]         STREAM     CONNECTED     17648    
unix  3      [ ]         STREAM     CONNECTED     17645    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17644    
unix  3      [ ]         STREAM     CONNECTED     17640    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     17620    
unix  3      [ ]         STREAM     CONNECTED     17616    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17615    
unix  3      [ ]         STREAM     CONNECTED     17592    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     17591    
unix  3      [ ]         STREAM     CONNECTED     17558    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     17557    
unix  2      [ ]         STREAM                   17550    
unix  4      [ ]         STREAM     CONNECTED     17536    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17535    
unix  3      [ ]         STREAM     CONNECTED     17534    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17533    
unix  3      [ ]         STREAM     CONNECTED     17526    /tmp/orbit-aditya/linc-1584-0-43d0027118ce3
unix  3      [ ]         STREAM     CONNECTED     17525    
unix  3      [ ]         STREAM     CONNECTED     17522    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17521    
unix  3      [ ]         STREAM     CONNECTED     17517    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17516    
unix  3      [ ]         STREAM     CONNECTED     17511    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17510    
unix  3      [ ]         STREAM     CONNECTED     17505    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17504    
unix  3      [ ]         STREAM     CONNECTED     17477    /tmp/orbit-aditya/linc-1551-0-396aa4308c1da
unix  3      [ ]         STREAM     CONNECTED     17476    
unix  3      [ ]         STREAM     CONNECTED     17475    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17333    
unix  2      [ ]         DGRAM                    17319    
unix  3      [ ]         STREAM     CONNECTED     17313    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17312    
unix  3      [ ]         STREAM     CONNECTED     17308    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17307    
unix  3      [ ]         STREAM     CONNECTED     17306    
unix  3      [ ]         STREAM     CONNECTED     17305    
unix  3      [ ]         STREAM     CONNECTED     17008    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17007    
unix  2      [ ]         DGRAM                    16990    
unix  2      [ ]         DGRAM                    16869    
unix  2      [ ]         STREAM     CONNECTED     16661    /var/run/acpid.socket
unix  5      [ ]         STREAM     CONNECTED     17057    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16655    
unix  3      [ ]         STREAM     CONNECTED     16407    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16406    
unix  3      [ ]         STREAM     CONNECTED     16403    @/tmp/dbus-OAMcGU9hpb
unix  3      [ ]         STREAM     CONNECTED     16402    
unix  3      [ ]         STREAM     CONNECTED     16401    
unix  3      [ ]         STREAM     CONNECTED     16400    
unix  3      [ ]         STREAM     CONNECTED     16385    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16384    
unix  3      [ ]         STREAM     CONNECTED     16374    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16373    
unix  3      [ ]         STREAM     CONNECTED     16368    
unix  3      [ ]         STREAM     CONNECTED     16367    
unix  2      [ ]         DGRAM                    16365    
unix  3      [ ]         STREAM     CONNECTED     16339    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16338    
unix  2      [ ]         DGRAM                    16335    
unix  3      [ ]         STREAM     CONNECTED     16320    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16319    
unix  2      [ ]         DGRAM                    16318    
unix  3      [ ]         STREAM     CONNECTED     16314    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     16313    
unix  3      [ ]         STREAM     CONNECTED     16312    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16311    
unix  3      [ ]         STREAM     CONNECTED     15936    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15935    
unix  3      [ ]         STREAM     CONNECTED     15920    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     15919    
unix  3      [ ]         STREAM     CONNECTED     15910    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     15903    
unix  3      [ ]         STREAM     CONNECTED     15909    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     15901    
unix  3      [ ]         STREAM     CONNECTED     15896    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     15493    
unix  3      [ ]         STREAM     CONNECTED     15085    @/var/run/hald/dbus-Hy3hFNm6Lh
unix  3      [ ]         STREAM     CONNECTED     15084    
unix  3      [ ]         STREAM     CONNECTED     15081    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15080    
unix  3      [ ]         STREAM     CONNECTED     15064    
unix  3      [ ]         STREAM     CONNECTED     15063    
unix  2      [ ]         DGRAM                    15054    
Active IPX sockets
Proto Recv-Q Send-Q Local Address              Foreign Address            State
Active AX.25 sockets
Dest       Source     Device  State        Vr/Vs    Send-Q  Recv-Q
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.

```

i was running pidgin,ktorrent,firefox... how do i find port numbers used by these apps ?

---

### Post by sageb1 on 2007-12-31
From command line, SUDO netstat using the flags -atunp to get  the information you seek.

also google for the port number if it does not resolve to a service name.

Google for "[port #] +tcp" if it is tcp and "[port#] +udp" if udp.

Also Google for "port number" +service and try to get a complete list of port numbers.

Download and save the text file as "services".

Then you have the option to do the following:

Using prefix sudo copy /etc/services to /etc/services.backup.

Then SUDO copy (your_download_directory_path)/services /etc/

---

### Post by ghostdog74 on 2007-12-31
> **adityakavoor said:**
> this is the o/p of netstat

```
aditya@ubuntu:~$ netstat -v
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 ubuntu.local:45938      cs30.msg.dcn.yahoo:mmcc ESTABLISHED
tcp        1      0 ubuntu.local:53136      80.67.87.38:www         CLOSE_WAIT 
tcp        1      0 ubuntu.local:53137      80.67.87.38:www         CLOSE_WAIT 
tcp        0      0 ubuntu.local:40726      wf-in-f83.google.co:www ESTABLISHED
tcp        0      0 ubuntu.local:40724      wf-in-f83.google.co:www ESTABLISHED
tcp        0      0 ubuntu.local:40721      wf-in-f83.google.co:www ESTABLISHED
tcp       38      0 ubuntu.local:39003      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39002      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39001      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39006      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39005      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39004      colo-static.174.8:https CLOSE_WAIT 
tcp       38      0 ubuntu.local:39008      colo-static.174.8:https CLOSE_WAIT 
tcp        0      0 ubuntu.local:53967      po-in-f125.:xmpp-client ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ]         DGRAM                    8267     @/com/ubuntu/upstart
unix  2      [ ]         DGRAM                    8444     @/org/kernel/udev/udevd
unix  10     [ ]         DGRAM                    14973    /dev/log
unix  2      [ ]         DGRAM                    15090    @/org/freedesktop/hal/udev_event
unix  3      [ ]         STREAM     CONNECTED     36737    /tmp/ksocket-aditya/klauncherQDkPHb.slave-socket
unix  3      [ ]         STREAM     CONNECTED     36736    
unix  3      [ ]         STREAM     CONNECTED     36617    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     36616    
unix  3      [ ]         STREAM     CONNECTED     36613    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     36612    
unix  3      [ ]         STREAM     CONNECTED     36609    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     36608    
unix  3      [ ]         STREAM     CONNECTED     36555    
unix  3      [ ]         STREAM     CONNECTED     36554    
unix  3      [ ]         STREAM     CONNECTED     36552    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     36551    
unix  3      [ ]         STREAM     CONNECTED     36547    /tmp/orbit-aditya/linc-4302-0-5df776cf5321
unix  3      [ ]         STREAM     CONNECTED     36546    
unix  3      [ ]         STREAM     CONNECTED     36545    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     36544    
unix  3      [ ]         STREAM     CONNECTED     36543    /tmp/orbit-aditya/linc-4302-0-5df776cf5321
unix  3      [ ]         STREAM     CONNECTED     36542    
unix  3      [ ]         STREAM     CONNECTED     36539    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     36538    
unix  3      [ ]         STREAM     CONNECTED     36536    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     36535    
unix  3      [ ]         STREAM     CONNECTED     36531    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     36530    
unix  3      [ ]         STREAM     CONNECTED     36135    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     36134    
unix  3      [ ]         STREAM     CONNECTED     36131    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     36130    
unix  3      [ ]         STREAM     CONNECTED     36123    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     36122    
unix  3      [ ]         STREAM     CONNECTED     36120    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     36119    
unix  3      [ ]         STREAM     CONNECTED     35948    /tmp/orbit-aditya/linc-421e-0-5c68a1491779a
unix  3      [ ]         STREAM     CONNECTED     35947    
unix  3      [ ]         STREAM     CONNECTED     35944    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     35943    
unix  3      [ ]         STREAM     CONNECTED     35932    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     35931    
unix  3      [ ]         STREAM     CONNECTED     35660    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     35659    
unix  3      [ ]         STREAM     CONNECTED     35640    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     35639    
unix  3      [ ]         STREAM     CONNECTED     35501    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     35479    
unix  3      [ ]         STREAM     CONNECTED     35258    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     35257    
unix  3      [ ]         STREAM     CONNECTED     34613    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     34612    
unix  3      [ ]         STREAM     CONNECTED     33988    /tmp/ksocket-aditya/ubuntu-3e88-4684acfb
unix  3      [ ]         STREAM     CONNECTED     33987    
unix  2      [ ]         STREAM     CONNECTED     33962    /tmp/ksocket-aditya/kdeinit__0
unix  3      [ ]         STREAM     CONNECTED     33932    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     33931    
unix  3      [ ]         STREAM     CONNECTED     33930    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     33929    
unix  3      [ ]         STREAM     CONNECTED     33922    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     33921    
unix  3      [ ]         STREAM     CONNECTED     29463    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     29462    
unix  3      [ ]         STREAM     CONNECTED     28662    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     28661    
unix  3      [ ]         STREAM     CONNECTED     28660    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     28659    
unix  3      [ ]         STREAM     CONNECTED     28658    /tmp/orbit-aditya/linc-283d-0-68773cf687e8b
unix  3      [ ]         STREAM     CONNECTED     28657    
unix  3      [ ]         STREAM     CONNECTED     28654    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     28653    
unix  2      [ ]         STREAM     CONNECTED     27884    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     26851    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     26850    
unix  3      [ ]         STREAM     CONNECTED     26791    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     26790    
unix  3      [ ]         STREAM     CONNECTED     26787    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26786    
unix  3      [ ]         STREAM     CONNECTED     26781    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     26780    
unix  7      [ ]         STREAM     CONNECTED     26775    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26774    
unix  3      [ ]         STREAM     CONNECTED     26734    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26733    
unix  3      [ ]         STREAM     CONNECTED     26726    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     26725    
unix  3      [ ]         STREAM     CONNECTED     26718    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     26717    
unix  3      [ ]         STREAM     CONNECTED     26708    /tmp/.ICE-unix/dcop9211-1183049168
unix  3      [ ]         STREAM     CONNECTED     26707    
unix  3      [ ]         STREAM     CONNECTED     26705    
unix  3      [ ]         STREAM     CONNECTED     26704    
unix  2      [ ]         STREAM     CONNECTED     25477    /var/run/acpid.socket
unix  2      [ ]         STREAM     CONNECTED     22760    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     22556    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     22555    
unix  3      [ ]         STREAM     CONNECTED     22554    /tmp/orbit-aditya/linc-1be4-0-5c8d52832f0e8
unix  3      [ ]         STREAM     CONNECTED     22553    
unix  3      [ ]         STREAM     CONNECTED     22550    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     22549    
unix  3      [ ]         STREAM     CONNECTED     22540    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22539    
unix  3      [ ]         STREAM     CONNECTED     19108    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     19107    
unix  3      [ ]         STREAM     CONNECTED     19106    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     19105    
unix  3      [ ]         STREAM     CONNECTED     19104    /tmp/orbit-aditya/linc-166a-0-711f20b425919
unix  3      [ ]         STREAM     CONNECTED     19103    
unix  3      [ ]         STREAM     CONNECTED     19100    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     19099    
unix  3      [ ]         STREAM     CONNECTED     19095    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19094    
unix  3      [ ]         STREAM     CONNECTED     19084    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     19083    
unix  3      [ ]         STREAM     CONNECTED     19082    /tmp/orbit-aditya/linc-1593-0-355adfc91003e
unix  3      [ ]         STREAM     CONNECTED     19081    
unix  3      [ ]         STREAM     CONNECTED     19080    /tmp/orbit-aditya/linc-1663-0-398e3a46455bb
unix  3      [ ]         STREAM     CONNECTED     19079    
unix  3      [ ]         STREAM     CONNECTED     19072    /tmp/orbit-aditya/linc-1663-0-398e3a46455bb
unix  3      [ ]         STREAM     CONNECTED     19071    
unix  3      [ ]         STREAM     CONNECTED     19070    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     19069    
unix  3      [ ]         STREAM     CONNECTED     19068    /tmp/orbit-aditya/linc-1663-0-398e3a46455bb
unix  3      [ ]         STREAM     CONNECTED     19067    
unix  3      [ ]         STREAM     CONNECTED     19064    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     19063    
unix  3      [ ]         STREAM     CONNECTED     19059    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     19058    
unix  3      [ ]         STREAM     CONNECTED     19022    /tmp/orbit-aditya/linc-15c8-0-4559a31d8f6
unix  3      [ ]         STREAM     CONNECTED     19021    
unix  3      [ ]         STREAM     CONNECTED     19020    /tmp/orbit-aditya/linc-1637-0-64e16f3f600f8
unix  3      [ ]         STREAM     CONNECTED     19019    
unix  3      [ ]         STREAM     CONNECTED     19016    /tmp/orbit-aditya/linc-1640-0-2aeb149fd1771
unix  3      [ ]         STREAM     CONNECTED     19015    
unix  3      [ ]         STREAM     CONNECTED     19014    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     19013    
unix  3      [ ]         STREAM     CONNECTED     19011    /tmp/orbit-aditya/linc-1640-0-2aeb149fd1771
unix  3      [ ]         STREAM     CONNECTED     19010    
unix  3      [ ]         STREAM     CONNECTED     19007    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     19006    
unix  3      [ ]         STREAM     CONNECTED     19004    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     19003    
unix  3      [ ]         STREAM     CONNECTED     18999    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18998    
unix  3      [ ]         STREAM     CONNECTED     18996    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18995    
unix  3      [ ]         STREAM     CONNECTED     18981    /tmp/orbit-aditya/linc-1637-0-64e16f3f600f8
unix  3      [ ]         STREAM     CONNECTED     18980    
unix  3      [ ]         STREAM     CONNECTED     18979    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     18978    
unix  3      [ ]         STREAM     CONNECTED     18975    /tmp/orbit-aditya/linc-1637-0-64e16f3f600f8
unix  3      [ ]         STREAM     CONNECTED     18974    
unix  3      [ ]         STREAM     CONNECTED     18967    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18964    
unix  3      [ ]         STREAM     CONNECTED     18949    /tmp/orbit-aditya/linc-15c8-0-4559a31d8f6
unix  3      [ ]         STREAM     CONNECTED     18948    
unix  3      [ ]         STREAM     CONNECTED     18947    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     18946    
unix  3      [ ]         STREAM     CONNECTED     18940    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     18939    
unix  3      [ ]         STREAM     CONNECTED     18172    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18171    
unix  3      [ ]         STREAM     CONNECTED     18169    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18168    
unix  3      [ ]         STREAM     CONNECTED     18167    /tmp/orbit-aditya/linc-15c8-0-4559a31d8f6
unix  3      [ ]         STREAM     CONNECTED     18166    
unix  3      [ ]         STREAM     CONNECTED     18163    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18162    
unix  3      [ ]         STREAM     CONNECTED     18160    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     18159    
unix  3      [ ]         STREAM     CONNECTED     18155    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18154    
unix  3      [ ]         STREAM     CONNECTED     18144    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     18143    
unix  3      [ ]         STREAM     CONNECTED     18142    /tmp/orbit-aditya/linc-1593-0-355adfc91003e
unix  3      [ ]         STREAM     CONNECTED     18141    
unix  3      [ ]         STREAM     CONNECTED     18140    /tmp/orbit-aditya/linc-15f6-0-2dc1e41c90350
unix  3      [ ]         STREAM     CONNECTED     18139    
unix  3      [ ]         STREAM     CONNECTED     18136    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18135    
unix  3      [ ]         STREAM     CONNECTED     18122    /tmp/mapping-aditya
unix  3      [ ]         STREAM     CONNECTED     18112    
unix  3      [ ]         STREAM     CONNECTED     18111    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18110    
unix  3      [ ]         STREAM     CONNECTED     18101    /tmp/orbit-aditya/linc-15ec-0-2dc1e41c904c9
unix  3      [ ]         STREAM     CONNECTED     18100    
unix  3      [ ]         STREAM     CONNECTED     18099    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     18098    
unix  3      [ ]         STREAM     CONNECTED     18097    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     18096    
unix  3      [ ]         STREAM     CONNECTED     18095    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     18094    
unix  3      [ ]         STREAM     CONNECTED     18093    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     18092    
unix  2      [ ]         DGRAM                    18091    
unix  3      [ ]         STREAM     CONNECTED     18090    /tmp/orbit-aditya/linc-15f6-0-2dc1e41c90350
unix  3      [ ]         STREAM     CONNECTED     18089    
unix  3      [ ]         STREAM     CONNECTED     18088    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     18087    
unix  3      [ ]         STREAM     CONNECTED     18086    /tmp/orbit-aditya/linc-15ec-0-2dc1e41c904c9
unix  3      [ ]         STREAM     CONNECTED     18085    
unix  3      [ ]         STREAM     CONNECTED     18082    /tmp/orbit-aditya/linc-15f6-0-2dc1e41c90350
unix  3      [ ]         STREAM     CONNECTED     18081    
unix  3      [ ]         STREAM     CONNECTED     18078    /tmp/orbit-aditya/linc-15d4-0-2dc1e41c8feda
unix  3      [ ]         STREAM     CONNECTED     18077    
unix  3      [ ]         STREAM     CONNECTED     18074    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18071    
unix  3      [ ]         STREAM     CONNECTED     18069    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     18068    
unix  3      [ ]         STREAM     CONNECTED     18064    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18063    
unix  3      [ ]         STREAM     CONNECTED     18073    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18060    
unix  3      [ ]         STREAM     CONNECTED     18058    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     18057    
unix  3      [ ]         STREAM     CONNECTED     18053    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18052    
unix  3      [ ]         STREAM     CONNECTED     18072    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     18048    
unix  3      [ ]         STREAM     CONNECTED     18044    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     18043    
unix  3      [ ]         STREAM     CONNECTED     17989    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17988    
unix  3      [ ]         STREAM     CONNECTED     17978    /tmp/orbit-aditya/linc-15d5-0-7bd943dff0416
unix  3      [ ]         STREAM     CONNECTED     17975    
unix  3      [ ]         STREAM     CONNECTED     17972    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17971    
unix  3      [ ]         STREAM     CONNECTED     17963    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17962    
unix  3      [ ]         STREAM     CONNECTED     17937    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17936    
unix  3      [ ]         STREAM     CONNECTED     17933    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17932    
unix  3      [ ]         STREAM     CONNECTED     17931    /tmp/orbit-aditya/linc-15a7-0-86d218bbde31
unix  3      [ ]         STREAM     CONNECTED     17930    
unix  3      [ ]         STREAM     CONNECTED     17927    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17916    
unix  3      [ ]         STREAM     CONNECTED     17894    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     17893    
unix  3      [ ]         STREAM     CONNECTED     17797    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17796    
unix  3      [ ]         STREAM     CONNECTED     17794    /tmp/orbit-aditya/linc-1594-0-278e50745fc33
unix  3      [ ]         STREAM     CONNECTED     17793    
unix  3      [ ]         STREAM     CONNECTED     17792    /tmp/orbit-aditya/linc-1593-0-355adfc91003e
unix  3      [ ]         STREAM     CONNECTED     17791    
unix  3      [ ]         STREAM     CONNECTED     17790    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     17788    
unix  3      [ ]         STREAM     CONNECTED     17789    /tmp/orbit-aditya/linc-15a0-0-7b9bfd04cd4f0
unix  3      [ ]         STREAM     CONNECTED     17787    
unix  3      [ ]         STREAM     CONNECTED     17913    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     17782    
unix  3      [ ]         STREAM     CONNECTED     17778    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17777    
unix  3      [ ]         STREAM     CONNECTED     17764    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17763    
unix  3      [ ]         STREAM     CONNECTED     17762    /tmp/orbit-aditya/linc-15a5-0-4c7031ab23f7e
unix  3      [ ]         STREAM     CONNECTED     17761    
unix  3      [ ]         STREAM     CONNECTED     17758    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17757    
unix  3      [ ]         STREAM     CONNECTED     17754    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17753    
unix  3      [ ]         STREAM     CONNECTED     17743    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17742    
unix  3      [ ]         STREAM     CONNECTED     17722    /tmp/orbit-aditya/linc-1594-0-278e50745fc33
unix  3      [ ]         STREAM     CONNECTED     17721    
unix  3      [ ]         STREAM     CONNECTED     17718    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17717    
unix  3      [ ]         STREAM     CONNECTED     17715    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     17714    
unix  3      [ ]         STREAM     CONNECTED     17710    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17709    
unix  3      [ ]         STREAM     CONNECTED     17672    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17671    
unix  3      [ ]         STREAM     CONNECTED     17669    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17668    
unix  3      [ ]         STREAM     CONNECTED     17667    /tmp/orbit-aditya/linc-159a-0-278e5074178fe
unix  3      [ ]         STREAM     CONNECTED     17666    
unix  3      [ ]         STREAM     CONNECTED     17663    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17662    
unix  3      [ ]         STREAM     CONNECTED     17660    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     17659    
unix  3      [ ]         STREAM     CONNECTED     17655    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17654    
unix  3      [ ]         STREAM     CONNECTED     17649    /tmp/orbit-aditya/linc-1593-0-355adfc91003e
unix  3      [ ]         STREAM     CONNECTED     17648    
unix  3      [ ]         STREAM     CONNECTED     17645    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17644    
unix  3      [ ]         STREAM     CONNECTED     17640    /tmp/.ICE-unix/5457
unix  3      [ ]         STREAM     CONNECTED     17620    
unix  3      [ ]         STREAM     CONNECTED     17616    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17615    
unix  3      [ ]         STREAM     CONNECTED     17592    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     17591    
unix  3      [ ]         STREAM     CONNECTED     17558    /tmp/.esd-1000/socket
unix  3      [ ]         STREAM     CONNECTED     17557    
unix  2      [ ]         STREAM                   17550    
unix  4      [ ]         STREAM     CONNECTED     17536    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17535    
unix  3      [ ]         STREAM     CONNECTED     17534    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17533    
unix  3      [ ]         STREAM     CONNECTED     17526    /tmp/orbit-aditya/linc-1584-0-43d0027118ce3
unix  3      [ ]         STREAM     CONNECTED     17525    
unix  3      [ ]         STREAM     CONNECTED     17522    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17521    
unix  3      [ ]         STREAM     CONNECTED     17517    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17516    
unix  3      [ ]         STREAM     CONNECTED     17511    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17510    
unix  3      [ ]         STREAM     CONNECTED     17505    @/tmp/dbus-csLBFIxDwu
unix  3      [ ]         STREAM     CONNECTED     17504    
unix  3      [ ]         STREAM     CONNECTED     17477    /tmp/orbit-aditya/linc-1551-0-396aa4308c1da
unix  3      [ ]         STREAM     CONNECTED     17476    
unix  3      [ ]         STREAM     CONNECTED     17475    /tmp/orbit-aditya/linc-157f-0-78bb5c767da67
unix  3      [ ]         STREAM     CONNECTED     17333    
unix  2      [ ]         DGRAM                    17319    
unix  3      [ ]         STREAM     CONNECTED     17313    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17312    
unix  3      [ ]         STREAM     CONNECTED     17308    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     17307    
unix  3      [ ]         STREAM     CONNECTED     17306    
unix  3      [ ]         STREAM     CONNECTED     17305    
unix  3      [ ]         STREAM     CONNECTED     17008    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     17007    
unix  2      [ ]         DGRAM                    16990    
unix  2      [ ]         DGRAM                    16869    
unix  2      [ ]         STREAM     CONNECTED     16661    /var/run/acpid.socket
unix  5      [ ]         STREAM     CONNECTED     17057    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     16655    
unix  3      [ ]         STREAM     CONNECTED     16407    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16406    
unix  3      [ ]         STREAM     CONNECTED     16403    @/tmp/dbus-OAMcGU9hpb
unix  3      [ ]         STREAM     CONNECTED     16402    
unix  3      [ ]         STREAM     CONNECTED     16401    
unix  3      [ ]         STREAM     CONNECTED     16400    
unix  3      [ ]         STREAM     CONNECTED     16385    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16384    
unix  3      [ ]         STREAM     CONNECTED     16374    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16373    
unix  3      [ ]         STREAM     CONNECTED     16368    
unix  3      [ ]         STREAM     CONNECTED     16367    
unix  2      [ ]         DGRAM                    16365    
unix  3      [ ]         STREAM     CONNECTED     16339    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16338    
unix  2      [ ]         DGRAM                    16335    
unix  3      [ ]         STREAM     CONNECTED     16320    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16319    
unix  2      [ ]         DGRAM                    16318    
unix  3      [ ]         STREAM     CONNECTED     16314    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     16313    
unix  3      [ ]         STREAM     CONNECTED     16312    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16311    
unix  3      [ ]         STREAM     CONNECTED     15936    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15935    
unix  3      [ ]         STREAM     CONNECTED     15920    /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     15919    
unix  3      [ ]         STREAM     CONNECTED     15910    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     15903    
unix  3      [ ]         STREAM     CONNECTED     15909    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     15901    
unix  3      [ ]         STREAM     CONNECTED     15896    @/var/run/hald/dbus-5wj9KsB4xA
unix  3      [ ]         STREAM     CONNECTED     15493    
unix  3      [ ]         STREAM     CONNECTED     15085    @/var/run/hald/dbus-Hy3hFNm6Lh
unix  3      [ ]         STREAM     CONNECTED     15084    
unix  3      [ ]         STREAM     CONNECTED     15081    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     15080    
unix  3      [ ]         STREAM     CONNECTED     15064    
unix  3      [ ]         STREAM     CONNECTED     15063    
unix  2      [ ]         DGRAM                    15054    
Active IPX sockets
Proto Recv-Q Send-Q Local Address              Foreign Address            State
Active AX.25 sockets
Dest       Source     Device  State        Vr/Vs    Send-Q  Recv-Q
netstat: no support for `AF X25' on this system.
netstat: no support for `AF NETROM' on this system.

```

i was running pidgin,ktorrent,firefox... how do i find port numbers used by these apps ?

```

lsof -i | egrep "firefox|pidgin|ktorrent"

```

---

### Post by Mithrilhall on 2007-12-31
Install iftop and watch what's going on.

---

### Post by adityakavoor on 2007-12-31
> **ghostdog74 said:**
> ```

lsof -i | egrep "firefox|pidgin|ktorrent"

```

After finding the port numbers for ktorrent, I want to do port forwarding so that i can 

increase bandwidth for ktorrent and thereby increase the speed. Is Such a kind of a thing 

possible ?

---

