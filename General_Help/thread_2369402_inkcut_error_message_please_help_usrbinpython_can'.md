---
title: "inkcut error message please help /usr/bin/python: can't find '__main__' module in '.'"
date: 2017-08-22
forum: General Help
---

### Post by red-diesel on 2017-08-22
Hi
I am new to ubuntu and very new to this whole programming thing. However to cut long story short I have manage to install Inkcut extension in inkscape. However when i try to open it i just keep getting the same error message.   /usr/bin/python: can't find '__main__' module in '.' Have know idea what it means or how to solve it please help?? if you can help could you explain it in very simple terms for me to follow please.

jamie

---

### Post by dragonfly41 on 2017-08-22
Welcome.

You have posted a real first problem to crack.

First it is important to post details of your environment.
Ubuntu 16.04 64bits in my case.

Otherwise readers waste time in guessing.

I decided to look at your extension since I use Inkscape from time to time and have yet to explore adding extensions.
So it was a good test.

On installing Inkcut initially it did not work.

So the detective work then starts.

Reading ... [http://inkcut.sourceforge.net/](http://inkcut.sourceforge.net/)

it says ...

> Before starting, ensure that the target machine has the required dependencies
&#8226; pygtk and gtk
&#8226; pyserial
&#8226; librsvg2-common

Now a simple way of checking if you have these libraries installed is to go to your terminal and run

```
python
```

Now at the prompt >>>

try to import the dependencies as a test in python.
```

>>>import pygtk
>>>import gtk
>>>import pyserial

```
In my case the first two dependencies (libraries) were already installed but pyserial was missing.

I ran ..

```
sudo pip install pyserial
```

which installed that library.

You can check your installed libraries by running

```
pip list
```

and you will see .. pyserial (3.4)

But running Inkscape with the extension still hit errors.

There was reference to "import cups" in an error message but I already have cups installed.

I found that libcups2-dev needs to be installed but I could not find it in my Software Centre using Synaptic.

So I hunted around and found 

[https://pkgs.org/download/libcups2-dev](https://pkgs.org/download/libcups2-dev)

I installed this download deb package using GDebi Package Installer and then ran the command

```
sudo pip install pycups
```

which installed cups successfully.


Now after this workflow I was able to use the extension without error messages appearing.

However testing on some simple object in Inkscape froze so I used System Settings > System Monitor to find the Inkscape process under Processes Tab and killed the process.

Tried on a straight line object in Inkscape but I'm getting a panel 

```
Inkcut V1.0 working. please wait ...
```

That is as far as I got, at least troubleshooting some of the dependency issues.

I'm posting this as an example of detective work you may need to go through on occasions.

I see that the source page [http://inkcut.sourceforge.net/](http://inkcut.sourceforge.net/) has 2010 at bottom of page so I'm not sure how up to date it might be.

---

### Post by dragonfly41 on 2017-08-22
Example here of using Inkcut

[http://binaryimpulse.com/tag/inkcut/](http://binaryimpulse.com/tag/inkcut/)

This gave me a better understanding of where it is used.

I don't have a plotter (I see now that this is where cups is used) but I created in Inkscape a single numeric character &#8220;1&#8221;.

Then I went to top toolbar Path > Object to Path.

Next I selected Extensions > Cutter/Plotter >  Inkcut

This opens the Inkcut panel.

I could not do any further testing since I don't have a plotter.

Over to you to take it further.

---

### Post by red-diesel on 2017-08-23
This is the first time I ever used a forum so would just like to say a massive thank you, for the reply and taking your time to look at this.
I have started to work through your instruction and came up with message that not sure what to do next? I have tried to attach it as a screen to make more scene. what should i do next.???

jamie

---

### Post by dragonfly41 on 2017-08-23
First as the message says use the -H argument with sudo.

```
sudo -H pip install pyserial
```

However first upgrade your pip

```
sudo -H pip install --upgrade pip
```

this is what I see ..

```
sudo -H pip install --upgrade pip
[sudo] password for xxxx: 
Requirement already up-to-date: pip in /usr/local/lib/python2.7/dist-packages
```


Now in your terminal run command 
```

pip list | grep pip &&
pip list | grep pyserial &&
pip list | grep pycups
```



.. and copy and paste to this thread the output text shown in terminal bounded by code tags.

```
 ... text here ... 
```

We can then see whether you have dependencies installed via pip.

This is what I see ..

```

> pip list | grep pip &&
> pip list | grep pyserial &&
> pip list | grep pycups
DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.
pip (9.0.1)

DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.
pyserial (3.4)

DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.
pycups (1.9.73)


```


...

Now regarding the error message ...

/usr/bin/python: can’t find ‘__main__’ module - in ‘.’

Here is one thread discussing identical error message  ...

[https://stackoverflow.com/questions/24723547/received-cant-find-main-module-in-packagename-with-python-package](https://stackoverflow.com/questions/24723547/received-cant-find-main-module-in-packagename-with-python-package)

...


Also you might browse through the inkscape forum ... search inkcut

[http://www.inkscapeforum.com/viewtopic.php?t=4987&start=100](http://www.inkscapeforum.com/viewtopic.php?t=4987&start=100)

---

### Post by dragonfly41 on 2017-08-23
Added note ...

I noticed from your error message ..

```
Requirement already satisfied (use --upgrade to upgrade): pyserial in ./.local/lib/python2.7/site-packages/
```


Whereas my output in terminal is

```
Requirement already satisfied: pyserial in /usr/local/lib/python2.7/dist-packages
```

Notice the difference in ./.local in your output.  i.e. you are using $HOME/.local/lib/python2.7/.....


I do have $HOME/.local/lib/python2.7/site-packages
and also ...

[/usr/local/lib/python2.7/site-packages]("file:///usr/local/lib/python2.7/site-packages") (empty) and dist-packages (which contain active python modules).

---

### Post by red-diesel on 2017-08-23
This what I now have ???

red-diesel@reddiesel-OptiPlex-790:~$ sudo -H pip install pyserial
[sudo] password for red-diesel: 
Requirement already satisfied: pyserial in /usr/local/lib/python2.7/dist-packages
red-diesel@reddiesel-OptiPlex-790:~$ sudo -H pip install --upgrade pip
Requirement already up-to-date: pip in /usr/local/lib/python2.7/dist-packages
red-diesel@reddiesel-OptiPlex-790:~$ pip list | grep pip &&
> pip list | grep pyserial &&
> pip list | grep pycups
DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.
pip (9.0.1)
DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.
pyserial (3.4)
DEPRECATION: The default format will switch to columns in the future. You can use --format=(legacy|columns) (or define a format=(legacy|columns) in your pip.conf under the 
[list] section) to disable this warning.
pycups (1.9.73)
red-diesel@reddiesel-OptiPlex-790:~$

---

### Post by dragonfly41 on 2017-08-23
That is exactly what I have .. you can ignore the Deprecation warning messages.  They simply say that the format is due to change in the future.

This output tells me that you have 

pip (9.0.1)
pyserial (3.4)
pycups (1.9.73)

which are the dependencies required by Inkcut (apparently).

Now to assist in managing Ubuntu packages I suggest that you install Synaptic Package Manager by running this command:

```
sudo apt-get install synaptic
```

You can then go to System Tools > Administration > Synaptic Package Manager to launch the application.

Now with this tool open go to search and search for 

```
python-serial
```

Although I had installed pyserial through pip the readme at 

```
$HOME/.config/inkscape/extensions/inkcut/readme
```

reads as follows:

(Note that in your file manager you will need to enable &#8220;view hidden files&#8221;).

```

Requirements
-------------------------------------------
pyserial must be installed (UPDATE: this is now included in 1.0)
visit [http://pyserial.sourceforge.net/](http://pyserial.sourceforge.net/)

on ubuntu:
sudo apt-get install python-serial

```

So it does no harm to also install python-serial (although I would have thought that pyserial was sufficient).

While in Synaptic Package Manager just check that you have 

```
librsvg2-common
```

installed too.

Now with all these dependencies installed in my Ubuntu 16.04 setup I can go to Inkscape, draw a test square object, go to plot path and launch Inkcut.

I can also click on Preview to see the cutting path.

---

### Post by red-diesel on 2017-08-25
Hi, I feel we are moving forward all credit to you. 

after running code [COLOR=#000000][FONT=&amp]$HOME/.config/inkscape/extensions/inkcut/readme [/FONT][/COLOR]this screen shot was result, not sure what it met but does error, is it relivent?? (see screen shot one)

opened up inkscape and got error message (screen shot 2) ???

When trying one of the steps in your instruction got this response it may help it may not??!!

Traceback (most recent call last):
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS20: [Errno 13] Permission denied: '/dev/ttyS20'
Traceback (most recent call last):
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS31: [Errno 13] Permission denied: '/dev/ttyS31'
Traceback (most recent call last):
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/main.py", line 427, in on_test_connection_clicked
    dev.plot(os.path.join(appPath,'tests','test.hpgl'))
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS0: [Errno 13] Permission denied: '/dev/ttyS0'
Traceback (most recent call last):
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/main.py", line 283, in on_send_clicked
    dev.plot(os.path.join(appPath,'tmp','plot.hpgl'))
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/device.py", line 98, in plot
    toSerial(f.read(),self.serial)
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/device.py", line 75, in toSerial
    ser.open()
  File "/home/red-diesel/.config/inkscape/extensions/inkcut/app/bin/serial/serialposix.py", line 276, in open
    raise SerialException("could not open port %s: %s" % (self._port, msg))
app.bin.serial.serialutil.SerialException: could not open port /dev/ttyS0: [Errno 13] Permission denied: '/dev/ttyS0'

so what do you think???

jamie

---

### Post by dragonfly41 on 2017-08-25
Regarding the first image you posted I think that you simply ran ..
```
$HOME/.config/inkscape/extensions/inkcut/readme
```

instead of ..
```
cat $HOME/.config/inkscape/extensions/inkcut/readme
```

Note the use of cat command.

Now reading the traceback logs you seem to have a ports permission report.   

```
 ..... SerialException: could not open port /dev/ttyS0: [Errno 13] Permission denied: '/dev/ttyS0'
```

Can you run this command and paste back results between code tags.

```
lsusb
```

Using some of the traceback patterns you posted I found this forum thread which has similar traceback reports ..

[https://ubuntuforums.org/showthread.php?t=2358894](https://ubuntuforums.org/showthread.php?t=2358894)

and the above thread posted these links which might offer more clues  ..

[http://securetech-ns.ca/tuxplot.html](http://securetech-ns.ca/tuxplot.html)

[https://forums.linuxmint.com/viewtopic.php?f=51&t=240180&p=1282102&hilit=vinyl+cutter#p1282102](https://forums.linuxmint.com/viewtopic.php?f=51&t=240180&p=1282102&hilit=vinyl+cutter#p1282102)


Indeed if you search &#8220;Inkcut&#8221; in this forum you will see several other threads which might shed some light.

[https://ubuntuforums.org/search.php?searchid=15641712](https://ubuntuforums.org/search.php?searchid=15641712)

e.g. Read here .. [https://ubuntuforums.org/showthread.php?t=2360909&highlight=Inkcut](https://ubuntuforums.org/showthread.php?t=2360909&highlight=Inkcut)

I would try Tux Plotter, as well as continuing with Inkcut.

As I explained I can only go so far in troubleshooting since I don't use a vinyl cutter.

---

### Post by red-diesel on 2017-08-26
Hi when i ran this code....

lsusb
i got 2 different results, first set of result was with my plotter connected to pc via USB
red-diesel@reddiesel-OptiPlex-790:~$ lsusb
Bus 002 Device 006: ID 413c:2111 Dell Computer Corp. 
Bus 002 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

second set of results when i connect my plotter vis serial to serial connector.
red-diesel@reddiesel-OptiPlex-790:~$ lsusb
Bus 002 Device 006: ID 413c:2111 Dell Computer Corp. 
Bus 002 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

does'nt seem to be picking up the serial to serial connection???

your thoughts??

---

### Post by red-diesel on 2017-08-26
[COLOR=#000000]Hi when i ran this code....[/COLOR]

[COLOR=#000000]lsusb[/COLOR]
[COLOR=#000000]i got 2 different results, first set of result was with my plotter connected to pc via USB[/COLOR]
[COLOR=#000000]red-diesel@reddiesel-OptiPlex-790:~$ lsusb[/COLOR]
[COLOR=#000000]Bus 002 Device 006: ID 413c:2111 Dell Computer Corp. [/COLOR]
[COLOR=#000000]Bus 002 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical[/COLOR]
[COLOR=#000000]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 001 Device 005: ID 1a86:7523 QinHeng Electronics HL-340 USB-Serial adapter[/COLOR]
[COLOR=#000000]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]

[COLOR=#000000]second set of results when i connect my plotter vis serial to serial connector.[/COLOR]
[COLOR=#000000]red-diesel@reddiesel-OptiPlex-790:~$ lsusb[/COLOR]
[COLOR=#000000]Bus 002 Device 006: ID 413c:2111 Dell Computer Corp. [/COLOR]
[COLOR=#000000]Bus 002 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical[/COLOR]
[COLOR=#000000]Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
[COLOR=#000000]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]
[COLOR=#000000]Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub[/COLOR]
[COLOR=#000000]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/COLOR]

[COLOR=#000000]does'nt seem to be picking up the serial to serial connection???[/COLOR]

[COLOR=#000000]your thoughts??[/COLOR]

---

### Post by dragonfly41 on 2017-08-26
I'm guessing that you need to install an HL-340 driver .. perhaps post on a forum such as Inkscape to pickup more experience with this device ...


[https://unix.stackexchange.com/questions/189896/testing-qinheng-electronics-hl-340-usb-serial-adapter](https://unix.stackexchange.com/questions/189896/testing-qinheng-electronics-hl-340-usb-serial-adapter)

[https://www.google.co.uk/search?q=driver+for+QinHeng+Electronics+HL-340+USB-Serial+adapter&oq=driver+for+QinHeng+Electronics+HL-340+USB-Serial+adapter&aqs=chrome..69i57.5781j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8](https://www.google.co.uk/search?q=driver+for+QinHeng+Electronics+HL-340+USB-Serial+adapter&oq=driver+for+QinHeng+Electronics+HL-340+USB-Serial+adapter&aqs=chrome..69i57.5781j0j7&client=ubuntu&sourceid=chrome&ie=UTF-8)


[https://0xcf.com/2015/03/13/chinese-arduinos-with-ch340-ch341-serial-usb-chip-on-os-x-yosemite/](https://0xcf.com/2015/03/13/chinese-arduinos-with-ch340-ch341-serial-usb-chip-on-os-x-yosemite/)

[https://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html](https://blog.mypapit.net/2008/05/how-to-use-usb-serial-port-converter-in-ubuntu.html)

---

### Post by dragonfly41 on 2017-08-26
Another link found .. might give more clues on how to setup connection ..
[URL="https://forums.linuxmint.com/viewtopic.php?t=135914"]
https://forums.linuxmint.com/viewtopic.php?t=135914[/URL]

And reading further here ...

[https://askubuntu.com/questions/343522/usb-to-serial-adapter-doesnt-works](https://askubuntu.com/questions/343522/usb-to-serial-adapter-doesnt-works)

you _must_ clarify what version of Ubuntu and kernel you have and USB 2.0 or USB 3.0 ports.

---

### Post by red-diesel on 2017-08-28
:D;):lolflag:It's official Dragonfly41 is a legend !!!!):P:p:D I now have my Pixmax plotter working on Inkcut, Thanks to his hard work and computer like thinking brain. THANK YOU! We have lift off!

---

