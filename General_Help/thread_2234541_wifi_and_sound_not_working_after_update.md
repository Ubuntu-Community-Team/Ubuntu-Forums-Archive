---
title: "wifi and sound not working after update"
date: 2014-07-15
forum: General Help
---

### Post by joem2305 on 2014-07-15
I recently upgraded my version of ubuntu 12.04, now I cannot access  wifi. I have managed to get the icon up for the wireless connectivity as  intitially when I loaded my computer there wasn't. Now in spite of  there being a wireless network avaliable it does not recognise wifi and  the wireless services seem to have deleted all trace of previous wifi  networks that I have connected to. When I checked the Network in network  manager it said that the network services are not compatible with this  version. I have tried various things suggested on the internet but with  no luck. When I ran the command nm-applet in my terminal I got the error  message> (nm-applet:484):  warning could not intiialize NMC client/org/freedesktop/networkManager  rejected send message 2 matched rules; type="methodcall" sender=  ":1.102" interface="orgfreedesktop. DBus: properties" member= "GetAll"  errorname="(unset)" requested reply=0 destination=  "org.freedesktop.NetworkMnager
**message applet now removed from notification area
*(nm-applet) :484:  (Warning failed to register as an agent) ; (32)  error starting file /var/run/consoleKit/database no such file or  directory 			 		
      			 				

 
 
 I also cannot access sound, if that makes a difference to the problem I face

---

### Post by varunendra on 2014-07-19
Welcome to Ubuntu Forums! :)

The first thing I'd suggest is to try reinstalling the network-manager-gnome package. Since you don't have an internet connection, you must do it the longer way. Try -
```
apt-get install --reinstall --print-uris network-manager-gnome
```
This should give you the download URIs of the packages needed to install the network-manager again. Use them to download them on a different computer with internet connection, and post back here the list of downloaded packages for further instructions.

---

