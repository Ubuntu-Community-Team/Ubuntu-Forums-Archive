---
title: "Running network dependent scripts on boot"
date: 2013-04-26
forum: General Help
---

### Post by tobiz on 2013-04-26
I'm running an ubuntu 8.10 mythtv system which is a 'production' system, ie I don't want to upgrade to a later version as it just 'works'. At boot I'd like to call a script which sends commands over the network to a Raspberry Pi which is connected to my AV amp to wake it up and select the correct HDMI channel for input (from the ubuntu 8.10 system). (Note I have two mythv systems so on start each one would send the appropriate commands to select the appropriate HDMI input port on the AV amp).   I've written a (python) script to do this which is run on the ubuntu platform and know it works (when not run during boot), ie sends the correct commands to the AV amp (in particular I can see on the Raspi that the AV amp sleep commands are sent and received). However, I've not been able to get the correct AV amp wakeup command to be sent during the ubuntu 8.10 boot sequence even though I know it is  run during the /etc/rd.d sequence.  My guess is even though my script tests for and shows eth0 is up and has an IP address no command is sent over the network. Examining syslog it seems there are some network setup processes run after my script is run which suggests the network is not fully operational until after the user has logged and it is this which prevents my network commands being sent (and why the corresponding commands on shutdown are sent).  I need the script to run before user login otherwise there is no monitor/keyboard on which to effect the login!  The question is: how do I run a script at boot time which depends on the network being fully working? Any help would be welcome.

---

