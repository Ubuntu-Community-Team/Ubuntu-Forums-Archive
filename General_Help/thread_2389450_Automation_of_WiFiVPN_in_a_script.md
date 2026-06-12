---
title: "Automation of WiFi/VPN in a script"
date: 2018-04-17
forum: General Help
---

### Post by leeryanrs on 2018-04-17
Here's my mission - 

  I need to create a "thinclient" on Ubuntu for some laptops. What i've  done so far, is cleaned out the ubuntu image from any un-needed  software and bundled stuff. Installed SSH for management, etc.
  I've created a script where it makes a user "kiosk", auto signs in  and opens up the xfreeRDP client instantly. If this is closed, it just  opens it again. No access to the desktop environment has been given  here.


  However, now I need to accomplish two steps before this being done - 


  1) Open a WiFi manager to allow the user to connect to his WiFi at home 
2) Automatically dial a VPN connection once internet access is available.


  I am completely stuck here as i'm not sure how to call up a network  manager and close it once a wifi connection has been established.
  This is the part of the script where it does the main stuff to bring up the application - 

  > sudo install -b -m 755 /dev/stdin /opt/kioskrdp.sh << EOF
  
#!/bin/bash 
 xset -dpms 
xset s off 
start-pulseaudio-x11
  while true; do
 xfreerdp /v:192.168.126.138 /u:'' /f /sec:tls /cert-ignore
 done 
EOF



  Any help would be appreciated!

---

