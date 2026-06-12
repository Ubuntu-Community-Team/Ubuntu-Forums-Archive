---
title: "VNC has stopped working on Ubuntu 18.04 server"
date: 2019-11-17
forum: General Help
---

### Post by markosjal on 2019-11-17
I have an Ubuntu 18.04.1 LTS server. I have used some different VNC Cients in the past however after installing Real VNC Viewer for a Raspberry PI I have used RealVNC Client with no issues , well until now I can no longer seem to get a VNC session going


when I run 
```
server:/etc$ sudo netstat -plnt
[sudo] password for pnap18969: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      847/systemd-resolve 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1919/sshd           
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      991/cupsd           
tcp        0      0 0.0.0.0:9999            0.0.0.0:*               LISTEN      1723/tinyproxy      
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      9725/Xvnc4          
tcp6       0      0 :::22                   :::*                    LISTEN      1919/sshd           
tcp6       0      0 ::1:631                 :::*                    LISTEN      991/cupsd           
tcp6       0      0 :::5901                 :::*                    LISTEN      9725/Xvnc4          
tcp6       0      0 :::9999                 :::*                    LISTEN      1723/tinyproxy    
```

I have the following in 
/home/server/.vnc/xstartup
```
#!/bin/bash
startxfce4 &
```


As stated the above config did work before. I do not always need the VNC server nor desktop and only start VNC when I need it. It says its starting and listenting but unable to connect over internet from Ubuntu 16.04.

Any ideas?


THanks

Mark

---

