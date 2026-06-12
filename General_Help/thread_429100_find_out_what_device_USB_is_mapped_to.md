---
title: "find out what device USB is mapped to?"
date: 2007-04-30
forum: General Help
---

### Post by aka_bigred on 2007-04-30
I have several USB devices on my system.  How do I figure out which one maps to each entry in the /dev folder?  For example here's my lsusb output:

[PHP]
user@pc:/dev/x10# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04fa:2490 Dallas Semiconductor DS1490F 2-in-1 Fob, 1-Wire adapter
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 050d:0910 Belkin Components
Bus 001 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
Bus 001 Device 001: ID 0000:0000
[/PHP]

I'm looking for the Prolific serial emulator - How can I tell which is which:

ttyUSB0
ttyUSB1
ttyUSB2

---

### Post by MilosDusan on 2007-04-30
Have you tried unplugging and replugging in the USB to do a 'dmesg | tail' (without the quotes of course) ;)

---

### Post by ebash on 2007-05-01
You can use udev to list all the information about each device. For instance, if you want to get the information for the device ttyUSB0 do:

```
udevinfo -a -n /dev/ttyUSB0
```

The previous command will list a lot of information. The driver which creates the device entry in /dev should be listed under the attribute DRIVERS:

```
udevinfo -a -n /dev/ttyUSB0 | grep DRIVERS
```

---

### Post by aka_bigred on 2007-05-01
ebash -

That command was pretty close, but isn't quite right.  With a little help from my best friend Google, and your udevinfo command I found this which works:


```

udevinfo -a -p /class/tty/ttyUSB0 | grep SYSFS{product}=="USB-Serial Controller"

```


Using that I can just test all the ttyUSB devices and find the right one for use in my starup script.

```
#! /bin/sh

#change to /dev dir
cd /dev

#loop through any ttyUSB devices to find the active USB serial one
for file in ttyUSB*
do
    echo checking $file
    # Test if this is the USB Serial interface
    if udevinfo -a -p /class/tty/$file | grep "SYSFS{product}==\"USB-Serial Controller\""
        then 
            echo device at $file
        else 
            echo not found at $file
    fi
done


```

Thanks!

---

### Post by ebash on 2007-05-02
Glad to know that I helped a little bit. Probably you should remove your shell script and replace if by an udev rule. Udev is quite a powerfull mechanism, among all things that it can do it can create automatically a symlimk to the device of your choice. Take a look at the file /etc/udev/rules.d/60-symlinks.rules, there's an example on how to create a synlink for a Palm Pilot:

```

# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \
					SYMLINK+="pilot"

```

I suggest that you create your own rule file, this way you will not interfer with Ubuntu's update mechanism. Create the file /etc/udev/rules.d/69-custom-symlinks.rules and add:

```

# Create /dev/my-usb-controller symlink for the USB serial controller
KERNEL=="ttyUSB*", ATTRS{product}=="USB-Serial Controller", SYMLINK+="my-usb-controller"

```

As you recall from my previous post I can sometimes be wrong :). Thus, you might need to play a little bit with the udev rules, take a look at the existing rules in /etc/udev/rules.d and at the man page for udev:

```
man udev
```

To try the rules simply reload (or force-reload or restart) the udev daemon (you might need to unplug and replug your USB controller):

```
sudo /etc/init.d/udev reload
```

---

### Post by aka_bigred on 2007-05-02
Very interesting...  I'll have to read up on udev.

I was just going to use my logic in the startup script for WISH to automatically locate my x10 device so that I didn't have to feed it the device name - it would just choose it when launching the daemon.  I like the idea of mapping it to the same location all the time whenever it is attached.

Thanks!

---

