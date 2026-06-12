---
title: "How to keep the vnc running the process after close the RDP ? ubuntu 14.04"
date: 2015-12-21
forum: General Help
---

### Post by wellington2 on 2015-12-21
Hey guys, i'm new at linux and buy 1 vps yesterday to test
the comands i send to install the desktop is:

[COLOR=#000000][FONT=lucida grande]sudo -i 
apt-get update
[/FONT][/COLOR][COLOR=#000000][FONT=lucida grande]apt-get upgrade
[/FONT][/COLOR][COLOR=#000000][FONT=lucida grande]apt-get install xorg xrdp lxde

then i install firefox. But the problem is: when i close the rdp it close my firefox and this cancel my downloads
i tried in a terminal: [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo nano /etc/xrdp/xrdp.ini 
[/FONT][/COLOR][COLOR=#000000][FONT=lucida grande]but says "command not found"
then i tried apt-get install nano then say this 
"[/FONT][/COLOR]dopkg: warning: 'ldconfig' not found in PATH or not executable
dpkg: warning: 'start-stop-daemon' not found in PATH or not executable
dpkg: error: 2 expected programs not found in PATH or not executable
Note: root's PATH should usually contain /usr/local/sbin, usr/sbin and /sbin
E: Sub-process /usr/bin/dpkg returned an error code (2)"

what i can do ? i just want send a command to my process still alive 24/7 running
i will be glad if someone can help me 
[COLOR=#000000][FONT=lucida grande]
[/FONT][/COLOR][COLOR=#000000][FONT=lucida grande]
[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-12-21
Simply minimize (instead of terminating) your RDP window to keep Firefox running.
Please show us the complete output of 'sudo apt install nano' 

For long downloads, use a better application than Firefox.
For example I use wget for big downloads. Controlled from shell or remotely using the 'ssh' command, reliable and robust, fast, resumable downloads, included in the default Ubuntu install.

An application that needs you to be logged in 24/7 is badly designed, or you are misusing it. 
A well-designed application (like *wget*), used properly (with a terminal multiplexor lke *screen*), will work in the background whether you are logged in or not.

---

