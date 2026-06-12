---
title: "Making a Python Script into a Service"
date: 2020-03-24
forum: General Help
---

### Post by jt2k on 2020-03-24
It is CouchPotato program and the CouchPotato is a python script. However, when I start up the service it reloads the whole program and starts me at the wizard within the browser. So I stopped the service and then manually loaded the python file and everything was okay (I have information on CouchPotato so I hoping I don't have to migrate it). I am wondering what I am doing wrong? Why is the python script working correctly when I start is manually but not when the computer starts it. So this is what I have done so far.

[I]1. sudo nano /lib/systemd/system/CouchPotato.service
[/I]_________________________________
**Inside of the file I have - **
[Unit]
Description=Dummy Service
After=multi-user.target
Conflicts=getty@tty1.service


[Service]
Type=simple
ExecStart=/usr/bin/python2.7 /home/jt2k/CouchPotato/CouchPotatoServer/CouchPotato.py
StandardInput=tty-force


[Install]
WantedBy=multi-user.target

__________________________________




*2. sudo systemctl daemon-reload*
*3. sudo systemctl enable dummy.service*


*4. sudo systemctl start dummy.service*
*5. sudo systemctl status dummy.service*
[B]The status says active

(I have made the folder /CouchPotato/ chmod 777 and /.couchpotato/ as well)[/B]

---

