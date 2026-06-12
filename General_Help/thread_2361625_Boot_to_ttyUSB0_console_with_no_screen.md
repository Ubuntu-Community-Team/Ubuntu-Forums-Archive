---
title: "Boot to ttyUSB0 console with no screen"
date: 2017-05-18
forum: General Help
---

### Post by hillboy2 on 2017-05-18
I have a small xUbuntu 14.04 server doing instrumentation on my boat. I don't want to have a monitor for it, I just want to open a console from my Windows Nav using Putty. The box that xUbuntu is booting has a tty0 but there is no connection in copper to that port. I need to use a USB -> RS232 com port. 

I can't find any instructions on how to do this with anything but Ubuntu 6 and the directors are all different. Don't trust it.

Would anyone know where to look to find instructions on how to do this?

---

### Post by hillboy2 on 2017-05-19
Desparate...

---

### Post by dragonfly41 on 2017-05-19
If you are desperate, here are a couple of articles found in a two minutes search ..

[https://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](https://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

[https://ubuntuforums.org/showthread.php?t=1716756](https://ubuntuforums.org/showthread.php?t=1716756)

---

### Post by hillboy2 on 2017-05-19
Thank you. Those articles only tell you how to set up a serial adapter. The don't explain how to make the OS boot a console to them.

This article is right on point but it is for Ubuntu 6.06:  [https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)

I was hoping for something a little more current.

---

### Post by #&amp;thj^% on 2017-05-19
What windows version are you using?
Curious if you have seen this: [https://askubuntu.com/questions/592386/ubuntu-putty-and-serial-port](https://askubuntu.com/questions/592386/ubuntu-putty-and-serial-port)


Note: Don't forget to try different baud rates.


Another site that may help: [http://www.chipkin.com/using-putty-for-serial-com-connections-hyperterminal-replacement/](http://www.chipkin.com/using-putty-for-serial-com-connections-hyperterminal-replacement/)


And a few more methods here: [https://unix.stackexchange.com/questions/22545/how-to-connect-to-a-serial-port-as-simple-as-using-ssh](https://unix.stackexchange.com/questions/22545/how-to-connect-to-a-serial-port-as-simple-as-using-ssh)

---

### Post by hillboy2 on 2017-05-19
I'm thinking you don't understanding the question. I have the serial ports working. Putty on windows talks to putty on the Ubuntu machine already. What I need is for the Ubuntu to boot into and bring up a console on the serial port so that I can control the Ubuntu box from within putty on the windows box.

---

### Post by #&amp;thj^% on 2017-05-19
You would be right in not understanding question>;)
It's been a very long time since I've needed to do this...but have a look at this: [https://www.howtoforge.com/setting_up_a_serial_console](https://www.howtoforge.com/setting_up_a_serial_console)

---

### Post by hillboy2 on 2017-05-19
That file recommends editing the old grub /boot/grub/menu.lst

Like I said everything I can find written is pre upstart and grub2.

What are the configuration files and settings for grub2 as it relates to the serial ports?

---

### Post by hillboy2 on 2017-05-19
[SIZE=4][https://askubuntu.com/questions/99469/how-to-invoke-kernel-with-serial-console](https://askubuntu.com/questions/99469/how-to-invoke-kernel-with-serial-console)[/SIZE]

Following those direction got me a console window on my remote terminal. However I can't login. It doesn't like my password.

Edit: My login failure was due to using the wrong user name. duh.

I'm good now.

---

