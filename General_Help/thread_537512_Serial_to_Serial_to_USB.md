---
title: "Serial to Serial to USB"
date: 2007-08-29
forum: General Help
---

### Post by orotrev on 2007-08-29
I have two servers and I want to connect them via serial cable as a backup for when network problems occur. Here is what I have

Server one Serial port at ttyS0
Server two Serial port at ttyUSB0 (using USB to serial adapter)


Following this tutorial:
[http://www.howtoforge.com/setting_up_a_serial_console](http://www.howtoforge.com/setting_up_a_serial_console)

I setup a connect from Server two to server one using minicom as the client. The problem arises when I want to go from Server one to Server two using minicom. I get no console response from Server two. I think the problem is in this line in the /boot/grub/menu.lst:

serial --unit=0 --speed=38400 --word=8 --parity=no --stop=1

I think --unit=0 refers to ttyS0 which I am not using. Has anyone gotten anything like this working? how can I tell grub that unit 0 is ttyUSB0? How can I tell which "COMM" port ttyUSB0 is mapped to?

---

### Post by orotrev on 2007-08-30
Anyone?

---

### Post by wirelessmonkey on 2007-08-30
Do you have minicom running on both sides of the link at the same time?

---

