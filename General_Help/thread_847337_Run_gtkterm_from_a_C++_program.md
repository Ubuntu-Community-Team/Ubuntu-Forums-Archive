---
title: "Run gtkterm from a C++ program"
date: 2008-07-02
forum: General Help
---

### Post by jonlemur on 2008-07-02
I'm working on making a robot autonomous, and to do that, I plan on having a computer send commands to the robot (eventually via bluetooth, but initially via RS 232) after the computer has mapped out a route for the robot to take.  I'm needing a way then to send and receive information from the serial port automatically.  I'm hoping that there is a way to use C++ to write a program that will interact with something like gtkterm (minicom, picocom, and cutecom are also acceptable).  

Does anyone know of how to do this, or where I can find good resources that would explain it?  I'm pretty new to serial port communication, but I have a fair background in C++.

I think it's also possible to write a C++ program that would send and receive information from the serial port, but at my current level of understanding serial ports, I would prefer to have something like gtkterm take care of the details.  If you think that C++ would be easier in the end though, I'm willing to dive in and figure out what I have to to make it work.

---

### Post by jonlemur on 2008-07-03
bump

---

### Post by cszikszoy on 2008-07-03
Using gkterm or miniterm isn't needed in this case.  How strict are you about using C++?  I've done a lot of with with rs232 to embedded electronics and for my projects I use something called "pyserial".  It's basically just a serial communications library written in python.

Their website is [http://pyserial.wiki.sourceforge.net/pySerial](http://pyserial.wiki.sourceforge.net/pySerial)

Also, on their website they show just how easy it is to write and read data from a serial port.

This is taken from their website:
```

>>> import serial
>>> ser = serial.Serial(0)  #open first serial port
>>> print ser.portstr       #check which port was really used
>>> ser.write("hello")      #write a string
>>> ser.close()             #close port
```

The documentation also shows you how to open serial ports at different connection settings, and different locations as well.

You could even write a small serial program in python, that takes an input of whatever text you want to write to the serial port, and then just call that program from C++.  I'm sure that c++ has some way of executing a command through the system.

---

### Post by jonlemur on 2008-07-07
Thanks, I'll take a look at that.

---

### Post by cszikszoy on 2008-07-07
if this was useful for you, can you please go to thread tools > mark thread as solved.  This will help other people searching for a similar answer.

---

### Post by tonysonney on 2009-03-10
I tried the above code. But I get an error ImportError : No module named serial. So I thought it may be because I dont have the required modules. So I installed the packages 'python2.5-dev, python-dev and python-uspp'. But still I get the same error!!

---

