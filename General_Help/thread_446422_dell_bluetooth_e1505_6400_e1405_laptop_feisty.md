---
title: "dell bluetooth e1505 6400 e1405 laptop feisty"
date: 2007-05-16
forum: General Help
---

### Post by syadnom on 2007-05-16
Here is a solution for all of you that have dell laptops and have failed to get your bluetooth devices working

first:
make sure your 
/etc/default/bluetooth 
has "HIDD_ENABLED=1" uncommented so your mouse and keyboard will work.

 second:
edit the /etc/bluetooth/hcid.conf
has security set to "auto" and the change your passkey from "1234" if you like.

third:
make your /etc/rc.local look like:
hciconfig hci0 reset
hciconfig hci0 inqmode 0
exit 0

now run:
sudo hciconfig hci0 reset
sudo /etc/init.d/bluetooth restart

now install gnome-bluetooth:

sudo apt-get install gnome-bluetooth


now bluetooth should be working for you.  to get your HID devices(mice, keyboards, joystick, etc)
put your device in discover mode.
run:
sudo hidd --search

it should find any keyboard or mouse your have.

hidd --help should give you some good info on connected devices. you can also manually connect via

hcitool -scan
and then put the xx.xx.xx.xx.xx number in
hidd --connect xx.xx.xx.xx.xx

:) good luck

---

### Post by Dougle on 2007-08-31
Thanks for the post, my Dell XPS seems to have the adapter switched on, on boot, as per the BOIS settings, but feisty seems to overlook it untill i use:

sudo hciconfig hci0 up

or hit Fn+F2 twice

I've added the line above to my session startup list, so here's hoping.

Thanks again

---

### Post by syadnom on 2007-08-31
kinda strange, i dont have to problem.   bluetooth is looked at as a type of networking so it behaves as such.  just like an ethernet interface wont come up automatically unless it is told to in /etc/interfaces

there must be a config file with that line commented out or missing.

---

### Post by David Oxland on 2008-06-03
Thanks to syadnom;
I used your procedure on a Dell Inspiron 9300 and it worked perfectly.
Thanks again 
David

---

### Post by AiBo on 2008-06-12
I have a E1405 running 8.04.  Bluetooth is enabled in BIOS.  But no light come on the panel.  Followed instructions all the way through with these unexpected results:

sudo hciconfig hci0 reset
Can't get device info: No such device

Still continued to the end, no luck, still no bluetooth, any suggestions?

---

### Post by AiBo on 2008-07-03
got a cheap bluetooth dongle, worked from the second it was plugged in.  Anyone have any thoughts on why the built in doesn't work or another work around to discover the problem?

---

### Post by sayantandas on 2008-07-05
hi, can anyone tell me how to turnoff the bluetooth led on Inspiron 6400/e1505 in ubuntu 8.04. i can seperately turn the bluetooth off but the light remains on.
instructions are given for sony laptop bluetooths but they have a differnt power souce at/sys/device/platform/..../bluetoothpower, which i dint find in mine. 
thanks in advance.

---

