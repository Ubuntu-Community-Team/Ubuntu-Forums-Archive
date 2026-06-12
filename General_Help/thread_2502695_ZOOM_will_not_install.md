---
title: "ZOOM will not install"
date: 2024-11-25
forum: General Help
---

### Post by Autodave on 2024-11-25
Xubuntu 24.04.  I d-led Zoom from their site.  Tried to install with gdebi.  Had a notice that dependencies were needed.  I installed all of them.  Tried again to install: no dependencies listed any longer, but no installation happened.  Just sits there.  I have tried many times, redownloaded Zoom, rebooted, still no install.  Any ideas?

---

### Post by 1fallen on 2024-11-25
Try this Autodave
```
sudo apt install ### and just throw the .deb in there
```
Mine went like 
```
 sudo apt install '/home/me/Downloads/zoom_amd64.deb' 

```
That should take care of all deps.
```
 zoom
ZoomLauncher started.
Zoom path is: /opt/zoom
cmd line: 
Start subprocess: /opt/zoom/zoom sucessfully,  process pid: 37977 
Can't load/home/me/.config/zoomus.conf
no pactl and  pacmd found at this system.                             Class      App      Lib Possible Culprit Flags
                resip::Connection      656      656 
                      resip::Data       36       36 
                 resip::DnsResult     1080     1080 
                   resip::Headers        1        1 
          resip::MsgHeaderScanner       40       40 
                resip::SipMessage     5224     5224 
         resip::TransportSelector      896      896 
                     resip::Tuple      128      128 
              resip::UdpTransport     1144     1144 
          resip::GenericIPAddress       28       28 

zoom started.
Client: Breakpad is using Single Client Mode! client fd = -1
loadZoomWebviewHostProcess newPath is /opt/zoom/ZoomWebviewHost
loadZoomWebviewHostProcess libpath is /opt/zoom/Qt/lib:/opt/zoom/cef:/opt/zoom
Start subprocess: /opt/zoom/ZoomWebviewHost sucessfully,  process pid: 37987 
Interface: ipv4 enp1s0, IP Address: 192.168.1.158
Interface: ipv4 surfshark_wg, IP Address: 10.14.0.2
no pactl and  pacmd found at this system error!no pactl and  pacmd found at this system error![37987:37987]ZoomCollabHost started,isSupportCef=1
[37987:37987]CefInitialize init --
[38008:38008]ZoomCollabHost started,isSupportCef=1
[1:1]ZoomCollabHost started,isSupportCef=1

```

---

### Post by Autodave on 2024-11-25
Thank you!

---

### Post by 1fallen on 2024-11-25
:)

---

