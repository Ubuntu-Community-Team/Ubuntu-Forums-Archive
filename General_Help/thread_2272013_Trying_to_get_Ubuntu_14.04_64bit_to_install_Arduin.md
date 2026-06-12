---
title: "Trying to get Ubuntu 14.04 64bit to install Arduino Libary ! Help needed !"
date: 2015-04-03
forum: General Help
---

### Post by Tim036 on 2015-04-03
The software I want to run on the Arduino needs two libraries to install.

I've found the main depository of librarias here:-

/root/usr/share/arduino/libraries/

But from desktop it refuses as 'admin' priviledges block and normal gui transfer.

there is a secondary home folfer called sketchbook with a directory called /libraries/

but placing the library files don't work when invoking the Arduino to compile known good code.

Whithin The arduino ide there is a 'add' library option but it doesn't.

It it possible to create an 'Admin '  user and give that user full graphics control of where these libraries can be placed ?

Any body got any ideas at all ?

A very puzzled,

Tim
going over to W7  is an option I really don't want to do....

---

### Post by sotiris2 on 2015-04-03
I don't have an Arduino so you may have to clarify some things. How do you connect to the arduino? Ethernet? Usb? 
Do you get it's filesystem mounted like you would get with a usb stick? 
If you get denied because of permissions (and not perhaps because the filesystem is read only mounted) you could try running nautilus as root with ```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY nautilus
```.

Though if you are trying to compile on the arduino I presume you have some sort of command line access? If so you could simply copy the files from sketchbook to the proper folder via cp

---

### Post by Tim036 on 2015-04-03
The Arduini IDE runs in the PC it merely compiles the code including parts from the library to the Arduino itself which is connected by a usb cable.

Tried the CP but it does not let me transfer anything to the Library directory 

Many thanks for your support !

:  )))

Tim

---

### Post by sotiris2 on 2015-04-03
Ok I did some digging on arduino's forum. As I understand it compiles on the host and then uploads the compiled program and presumably the compiled to the board.

I believe you have to put the files in the sketchbook/libraries folder in your own home folder on the HOST (PC) and compile via the IDE. Could you perhaps link to he instructions of the libraries you are trying to install?

---

### Post by Tim036 on 2015-04-03
Quote
there is a secondary home folder called sketchbook with a directory called /libraries/

but placing the library files don't work when invoking the Arduino to compile known good code.

end quote

Now the instructions for the librarys are on the third page of this:-

[https://learn.adafruit.com/tsl2561/](https://learn.adafruit.com/tsl2561/)

Many many thanks for your help, very greatly appreciated.

:  ))))

Tim

---

