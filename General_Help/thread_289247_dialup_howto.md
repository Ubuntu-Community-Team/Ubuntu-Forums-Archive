---
title: "dialup howto"
date: 2006-10-30
forum: General Help
---

### Post by mikeymouse on 2006-10-30
How do I make a dialup connection??
 In dapper there was network and you could set it up and go online and download gnomeppp to setup for dialup connections.
 In edgy there seems to be no way to connect to the internet using network for dialup modems.
 Is there anyone out there who can explain how to get online using dialup modem?
 All help will be  appreciated:
 thanks mikeymouse

---

### Post by autocrosser on 2006-10-30
Look at Menu>System>Administration>Networking--Although, I'd get something like Gnome-PPP & to just connect you can use WVdial--it's there with every install--you would need to create a /etc/wvdial.conf file (as sudo)--if you need a example--I'll upload mine for you to look at---

---

### Post by yabbadabbadont on 2006-10-30
Just to be a little more clear, run "sudo wvdialconf" to configure wvdial.

---

### Post by mikeymouse on 2006-10-30
I have run 'sudo wvdialconf now what do i do?
 I have setup newtworking. I still dont know how to get online.
 Your help is appreciated and sooner or later it will get thru my thick head.
 thanks mikeymouse

---

### Post by mikeymouse on 2006-10-31
I ran sudo wvdialconf and wvdial.conf was created.
 I entered in wvdial.conf the info needed to go online, now how do i save wvdial.conf with the new data?
 thanks mikeymouse

---

