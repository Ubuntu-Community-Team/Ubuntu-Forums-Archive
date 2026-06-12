---
title: "How to install Arduino IDE 1.5.6-r2"
date: 2014-05-01
forum: General Help
---

### Post by Sebastiaan_Draaism on 2014-05-01
Hi there. 

I have the latest upgrade from Ubuntu (14.04 32 bit) and have the Arduino Yun which means I can not use the Arduino IDE in the Ubuntu Software Centre (does not support the Yun board). I downloaded the the 32 bit file from the official website, I have followed the instructions on [http://www.pluggy.me.uk/arduino-ubuntu/](http://www.pluggy.me.uk/arduino-ubuntu/) and have installed:
[LIST]
[*]Openjdk-7-jre 
[*]gcc-avr 
[*]avr-libc 
[/LIST]

I did not follow the dmesg section as this board is being programmed over wifi.
When I rightclick on the executable text file and choose run as program, nothing happens. Opening it with Java doesn't do anything either.

I have no experience with makefile and always install from an apt link or software centre. I tried using the Windows version under wine which loads fine but no ports are vissible (on my windows computer I see the Arduino wifi access point there)

Is there a way for me to get this working or am I foced to rely on Bill Gates here? :-)

---

### Post by sandyd on 2014-05-01
Have you tried navigating to the file using the terminal and executing it there?

We can then see any errors the script may ouput.

---

### Post by Sebastiaan_Draaism on 2014-05-01
Hi Sandy.

To be honest I have no idea how to do that. The file is located in the folder /home/sebastiaan/Downloads/arduino-1.5.6-r2

when I type this in my terminal: sebastiaan@sebastiaan-Laptop:~$ /home/sebastiaan/Downloads/arduino-1.5.6-r2/arduino 
and press enter, nothing happens

---

### Post by sandyd on 2014-05-01
try```

cd /home/sebastiaan/Downloads/arduino-1.5.6-r2
source arduino
./arduino

```

---

### Post by Sebastiaan_Draaism on 2014-05-02
Hi Sandy!

Thaks. Your code works excellent. The program started after using:
cd /home/sebastiaan/Downloads/arduino-1.5.6-r2
source arduino

I then right clicked on the icon and chose "Lock to launcher".
The icon is now in my launcher but does not start the program when clicking on it.
If its not to much to ask, I would really appreciate it if you could tell me how to get the icon to work.

If not, than I'm still happy that I can start the program through the terminal.

Thanks in advance!
Kind regards,
Sebastiaan

---

