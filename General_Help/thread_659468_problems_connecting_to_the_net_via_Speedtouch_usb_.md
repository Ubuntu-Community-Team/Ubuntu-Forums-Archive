---
title: "problems connecting to the net via Speedtouch usb modem"
date: 2008-01-05
forum: General Help
---

### Post by supershin on 2008-01-05
I been using the ubuntu 6.10 live cd with the usb adsl modem manager by steven harper and now i've installed 7.04 and i went through the same process as i previously did and i cant connect.

  After a lot of searching and skimming through posts and webpages and numerous reboots[dual boot with XP] to try the some solutions[like updating to the latest version of modem manger] I realised from link1 that i need the library libatml. So i install that by downloading the deb file and installing the package but it still doesn't work.

link 1 [http://www.squeezedonkey.com/wiki/linux/index.php?title=Troubleshooting](http://www.squeezedonkey.com/wiki/linux/index.php?title=Troubleshooting)
link 2 [http://packages.ubuntu.com/feisty/libs/libatm1](http://packages.ubuntu.com/feisty/libs/libatm1)

  After some more booting into ubuntu and then XP. I saved a file with the output of two commands:
sudo ps -ef | grep ppp and usbadslmodemmanager , see attached file. I really have no clue why i can't authenticate, cause the firmware is ok and it synchronizes.
  I also tried ubudsl, edited addressxml to insert my country and vc and vi codes, even used another country with the same codes as mine but neither worked. 
 Forgot to mention i use pppoa and my vc and vi codes  are 0 and 35.

link 3 [http://ubudsl.ubuntu.pl/autorzy_en.html](http://ubudsl.ubuntu.pl/autorzy_en.html)

Summary: I'm exhausted and I basically need help connecting to the net.

---

### Post by supershin on 2008-01-07
:confused: still no solution .... help will be very much appreciated. If i left out important info please ask for it because i posted all relevant info i could think of.

---

### Post by supershin on 2008-01-13
Still no solution and someone else is having the same problem, see link. 
Solution will be highly appreciated.

[http://ubuntuforums.org/showthread.php?t=585647&page=9](http://ubuntuforums.org/showthread.php?t=585647&page=9)

---

### Post by adrian5632 on 2008-01-21
Hi!
Please try the 0.9 version of UbuDSL: [http://sourceforge.net/projects/ubudsl](http://sourceforge.net/projects/ubudsl)
If you still can't connect, please generate the log (run UbuDSL connection monitor and choose "Generate log" from the menu under ubudsl icon in tray) - there will be written where you should send the log. I'll look closer at your problem then.

---

### Post by Robin T Cox on 2008-01-21
Have you tried following these instructions:

[https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch")

---

### Post by supershin on 2008-01-21
Thanks Adrian, i'll go try that now.

Robin, i already tried that but thanks for mentioning it.

---

### Post by apjone on 2008-01-21
Although I can not help I recomend that you get a router as it is always best to have a Hardware firewall infront of any machine.

---

