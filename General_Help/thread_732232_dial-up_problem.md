---
title: "dial-up problem"
date: 2008-03-22
forum: General Help
---

### Post by banditxkr on 2008-03-22
hi everyone thanks in advance for the help

i've been working on getting dial-up to work with 7.04 for a couple of months now and i finally got it to work sort of.

through GnomePPP and KPP it will connect but only for 10 to 15 seconds then i get exit code 16.

with wvdial it says i don't have a valid number username and password even though they show up on the wvdial.conf

any help would be greatly appreciated.

---

### Post by alwayshere on 2008-03-22
if you are using a full hardware external modem
go to "system" on your desktop
then addministration
then network

put your dailup number in phone number area
put your dailup user name and password in

now set up modem if you have a serial conection use "/dev/ttyso from drop box
or if your using a usb conection change /dev/ttyso to /dev/ttyUSB0 (note manualy change it point click and edit it)
set dail type to tones

tick all boxs in options tab

once all done click save tick box at top left

now when you turn on your pc it will dail up straight away

if your using a pci modem it will be an uphill battle best to get full hardware external modem
as i did .they're cheap as chips

im using a dynalink v1456vqe serial conection ) a bit old school v90

i set up a dlink dfm-562e serial conection ) on my mates macbook which is a v92

no serial port no worries just get a serial to usb adapter cord and use the /dev/ttyUSB0 as i said above

---

### Post by Shazaam on 2008-03-22
Also have you been here yet?.........

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by banditxkr on 2008-03-23
> **alwayshere said:**
> if you are using a full hardware external modem
go to "system" on your desktop
then addministration
then network

put your dailup number in phone number area
put your dailup user name and password in

now set up modem if you have a serial conection use "/dev/ttyso from drop box
or if your using a usb conection change /dev/ttyso to /dev/ttyUSB0 (note manualy change it point click and edit it)
set dail type to tones

tick all boxs in options tab

once all done click save tick box at top left

now when you turn on your pc it will dail up straight away

if your using a pci modem it will be an uphill battle best to get full hardware external modem
as i did .they're cheap as chips

im using a dynalink v1456vqe serial conection ) a bit old school v90

i set up a dlink dfm-562e serial conection ) on my mates macbook which is a v92

no serial port no worries just get a serial to usb adapter cord and use the /dev/ttyUSB0 as i said above

didn't work, it dials then i can hear the operator say "if you would like to make a call, please hang up and try again"

could this be because it is not waiting for the dialtone and if so how do i fix it.

---

### Post by banditxkr on 2008-03-31
the how-to didn't help either.  still looking for solutions.

---

