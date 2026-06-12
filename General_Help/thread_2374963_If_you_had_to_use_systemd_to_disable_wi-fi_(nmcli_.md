---
title: "If you had to use systemd to disable wi-fi (nmcli radio wifi off) on every reboot, ho"
date: 2017-10-20
forum: General Help
---

### Post by hey2 on 2017-10-20
Hi.  

Ubuntu 16.04 have a bug that is making my laptop bios freeze on every reboot when the wireless is activated before the reboot.  

I tried some things on systemd, but it doesn't seem to work all the times. I suspect that is because of the order that the services end.  

Does anybody have a idea how to make a service that runs on every reboot (desktop, login screen, tty etc..)?  

Thanks.

---

### Post by hey2 on 2017-10-27
Toshiba a210, Ubuntu 16.04 makes Bios freeze after a reboot if the wireless is enabled.

This is how i solved it: 

  
[LIST]
[*]Update your Ubuntu installation. 
[*]Make a folder and inside it create two empty files named start and stop. 
[*]Make them both executable. 
[*]On the start insert this text: 
[/LIST]
  nmcli radio wifi on
 service network-manager restart


  
[LIST]
[*]On the stop insert the following text: 
[/LIST]
  
nmcli radio wifi off


  
[LIST]
[*]Make an empty file named wireless-fix.service and move it to /etc/systemd/system/ 
[*]Copy the following text to this file: 
[/LIST]
  
[Unit]
Description=Fix Wireless
After=network-online.target  

  
[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=
ExecStop=  

  
[Install]
WantedBy=network-online.target
  

  
[LIST]
[*]On the ExecStart and ExecStop paste the location of the start and stop files created at the beginning. 
[*]on the terminal run this commands: 
[/LIST]
  sudo systemctl daemon-reload

  sudo systemctl enable wireless-fix.service

  sudo systemctl start wireless-fix.service

  sudo systemctl daemon-reload


  
[LIST]
[*]reboot the computer and it should be fixed. 
[/LIST]

---

