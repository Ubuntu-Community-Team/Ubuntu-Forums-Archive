---
title: "Ubuntu 20.04 takes long time to boot"
date: 2020-11-21
forum: General Help
---

### Post by jcss86 on 2020-11-21
Hello guys, I'm new using Ubuntu, and I have a problem.
I did an upgrade from Ubuntu 18.04 to Ubuntu 20.04, but the problem is that Ubuntu takes long time to boot.
Could you help me, please?


My computer has 6Gb of Ram Memory, and I've attached some screenshots to show you my laptop's resources.

Best regards.

---

### Post by TheFu on 2020-11-21
A core i5-2450 isn't exactly fast. I have one.

Also, please don't post images for text output. Just copy/paste the text and post that.

By default, Ubuntu installs and sets up everything you might want whether you want it or not. You have to decide what you need. We can't do that for you.  I see you have a bunch of snaps installed.  Those are known to drastically slow booting. Many will have non-snap package versions available which you may want to consider.

Also, probably want to see the **systemd-analyze critical-chain** output more than the "blame" output.
```
$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @8.925s
&#9492;&#9472;multi-user.target @8.924s
  &#9492;&#9472;postfix.service @8.916s +5ms
    &#9492;&#9472;postfix@-.service @3.463s +5.451s
      &#9492;&#9472;basic.target @3.243s
        &#9492;&#9472;sockets.target @3.243s
          &#9492;&#9472;snapd.socket @3.241s +1ms
            &#9492;&#9472;sysinit.target @3.235s
              &#9492;&#9472;systemd-timesyncd.service @2.928s +307ms
                &#9492;&#9472;systemd-tmpfiles-setup.service @2.692s +233ms
                  &#9492;&#9472;local-fs.target @2.672s
                    &#9492;&#9472;run-user-1000.mount @5.010s
                      &#9492;&#9472;swap.target @2.302s
                        &#9492;&#9472;dev-vgubuntu\x2dmate-swap_1.swap @2.278s +23ms
                          &#9492;&#9472;dev-dm\x2d1.device @2.276s
```
Here's mind.  I disable many things that aren't needed.
```
$ systemd-analyze blame 
5.451s postfix@-.service                                    
2.273s x2goserver.service                                   
1.998s networkd-dispatcher.service                          
1.891s snapd.service                                        
1.724s dev-mapper-vgubuntu\x2d\x2dmate\x2droot.device       
1.718s accounts-daemon.service                              
1.705s udisks2.service                                      
1.457s avahi-daemon.service                                 
1.173s systemd-logind.service                               
1.142s thermald.service                                     
1.096s dev-loop0.device                                     
1.081s dev-loop2.device                                     
1.075s dev-loop1.device                                     
1.001s lightdm.service                                      
 989ms dev-loop4.device                                     
 972ms dev-loop3.device                                     
 969ms plymouth-quit-wait.service            
```
See all those dev-loop.... lines? Those are snaps, but they don't show up in the critical path, so they don't slow down the actual boot. I'm not sure what accounts-daemon.service does. There was a critical flaw in that a few weeks ago. I have no idea what that actually does and don't think it is needed. Same for thermald. I've masked thermald so it won't run anymore.  I know avahi isn't needed, but it is really handy for locating printers on the subnet.

If you set a static IP address using config files, then network-manager won't be needed and the slowness of NM stuff won't exist. But if you want point-n-click network control, then disabling network manager wouldn't be a good idea.

If you want a faster system, choose a lighter desktop like XFCE and avoid Gnome3.

---

### Post by jcss86 on 2020-11-21
```
[COLOR=#4E9A06]**carlos@Salmeron**[/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @2min 1.444s
&#9492;&#9472;multi-user.target @2min 1.444s
  &#9492;&#9472;[COLOR=#CC0000]**snapd.seeded.service @39.955s +26.322s**[/COLOR]
    &#9492;&#9472;[COLOR=#CC0000]**snapd.service @41.819s +22.949s**[/COLOR]
      &#9492;&#9472;basic.target @38.444s
        &#9492;&#9472;sockets.target @38.444s
          &#9492;&#9472;[COLOR=#CC0000]**snapd.socket @38.442s +1ms**[/COLOR]
            &#9492;&#9472;sysinit.target @38.374s
              &#9492;&#9472;swap.target @38.374s
                &#9492;&#9472;[COLOR=#CC0000]**dev-disk-by\x2duuid-cf5ae7b8\x2d5f15\x2d4eb4\x2d8f72\x2dd8488**[/COLOR][COLOR=#2E3436]>[/COLOR]
                  &#9492;&#9472;dev-sda5.device @38.170s
```

---

### Post by SeijiSensei on 2020-11-21
Replacing the boot drive with an SSD can greatly improve boot times. Newegg runs sales on SSD drives all the time. I upgraded two laptops with these: [https://www.newegg.com/western-digital-blue-500gb/p/N82E16820250087?Item=N82E16820250087](https://www.newegg.com/western-digital-blue-500gb/p/N82E16820250087?Item=N82E16820250087)

---

### Post by jcss86 on 2020-11-28
My case
```
graphical.target @1min 55.888s&#9492;&#9472;multi-user.target @1min 55.888s
  &#9492;&#9472;teamviewerd.service @50.917s +12.091s
    &#9492;&#9472;network-online.target @50.778s
      &#9492;&#9472;network.target @50.777s
        &#9492;&#9472;NetworkManager.service @38.379s +12.397s
          &#9492;&#9472;dbus.service @38.374s
            &#9492;&#9472;basic.target @38.007s
              &#9492;&#9472;sockets.target @38.007s
                &#9492;&#9472;uuidd.socket @38.007s
                  &#9492;&#9472;sysinit.target @37.901s
                    &#9492;&#9472;swap.target @37.901s
                      &#9492;&#9472;dev-disk-by\x2duuid-cf5ae7b8\x2d5f15\x2d4eb4\x2d8f72\x2>
                        &#9492;&#9472;dev-disk-by\x2duuid-cf5ae7b8\x2d5f15\x2d4eb4\x2d8f72\>

```

---

### Post by TheFu on 2020-11-28
Please use "code tags." [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how.

Looks like NetworkManager and teamviewerd are problems that you can avoid.
a) use a static IP, configured in the netplan config directory - i.e. don't use network manager.
b) only start teamviewer when you actually need it. Certainly that isn't more than once a month, if not less.

---

