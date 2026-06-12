---
title: "help with USB to serial converter"
date: 2008-01-07
forum: General Help
---

### Post by jasonpeinko on 2008-01-07
So i joined my robotics team at school and am the lead programmer :) 

We eventually need to get our whole system moved to a laptop which i am working on with mine. The problem software is windows based which i solved using wine and a linux port of the loader software (picloader).

The real problem, i dont have a serial port on my laptop so i got my teachers usb to serial converter.

I have plugged it in and did an lsusb which it was recognized. 
```

Bus 001 Device 004: ID 06cd:0118 Keyspan USA-19QW PDA

```
I am stuck here, the picloader uses the following syntax

```

Syntax: picloader <filename> <serial device>

``` 

I have no idea what to put for serial device

---

### Post by jasonpeinko on 2008-01-08
anyone i need this soon.

---

### Post by Ivorydawn on 2008-01-08
Mine appears as /dev/ttyUSB0

---

### Post by Ivorydawn on 2008-01-08
Might also try com1, com2, com3 or so on as it's a windows prog. I'm not sure how wine translates ports from Linux to windows apps.

---

### Post by jasonpeinko on 2008-01-08
how did you find it was on /dev/ttyUSB0?

the picloader is a native linux program

---

### Post by Ivorydawn on 2008-01-08
Ahh! sorry, did not know that it was a Linux app.  I guessed that it would be under /dev/ttyUSB0 because that's where it always was under Suse :)

---

### Post by jasonpeinko on 2008-01-08
alright, i will test it this afternoon

---

### Post by Ivorydawn on 2008-01-08
One more thing, if it does not appear under /dev/ttyUSB0 you might have to remove brltty, there is a well known problem where brltty tries to grab the USB-Serial device first then stops other apps accessing it.

Once I removed brltty all was well and it was loaded as /dev/ttyUSB0

---

### Post by jasonpeinko on 2008-01-08
i am unable to get this to work

```

jasonpeinko@jasonpeinko-laptop:~/Robotics/FrcCode_2007_8722$ sudo picloader FRC_Default.hex /dev/ttyUSB0
787
Could not open socket!: No such file or directory


```

---

### Post by geraldm on 2008-01-08
You should find the name of the serial device in the log file.  It is best to have the serial device inserted when booting, as then it will be detected and its modules loaded.  If the device is plugged in after boot, you may need to load dependency modules such as usbserial.ko
Look in the file /var/log/syslog for the name of the serial device.  ttyUSB{number} is normal, but some may use alternative names like cuusb{number}.

Gerald

---

### Post by jasonpeinko on 2008-01-08
i cannont seem to find it
could this be it
```

Jan  8 15:22:37 jasonpeinko-laptop kernel: [   23.196000] ppdev: user-space parallel port driver
Jan  8 15:22:37 jasonpeinko-laptop kernel: [   23.356000] audit(1199834557.295:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5196 profile="/usr/sbin/cupsd"

```

---

### Post by geraldm on 2008-01-08
No, that is not it.  This is a line from mine, which is a prolific device, not a keyspan device:

Jan  8 15:21:35 lo kernel: usb 1-1.1: pl2303 converter now attached to ttyUSB0

The keyspan serial device requires a firmware upload, which is in the keyspan serial driver.
check the /boot/config-{version} file (substitute your kernel version)
```

grep  CONFIG_USB_SERIAL_KEYSPAN_USA19QW /boot/config-{version}

```

I am a little suspicious of the driver message with "PDA" in it, because there is a separate driver for the keyspan PDA that is different from the keyspan serial driver.  You need the keyspan serial driver, not the keyspan_pda driver.

Gerald

---

### Post by jasonpeinko on 2008-01-08
grep returns nothing, if it is supost to.

---

### Post by jasonpeinko on 2008-01-08
so how do i load the dirver? 

I need this working by tomorrow

---

### Post by geraldm on 2008-01-08
Double check again, grep for KEYSPAN, as I am a bit suprised that it is not in there.
You need these to be selected as "=m" or "=y" for either a loadable module, or integrated in the kernel.
You also need to select "CONFIG_USB_SERIAL"
Then you would have to compile a kernel.  There are HOWTOs for that.

If you plug in the device before you boot, the module driver would be autoloaded.
The driver name should be keyspan.ko   If you also have the module keyspan_pda.ko then I would suggest unloading that when testing the driver, and I would suggest also keeping the 
keyspan_pda as a module and not compile this into the kernel.

I think the task is a bit too much for an overnight project for school.  Better to get a good night's sleep.  Good luck

Gerald

---

### Post by Whiffle on 2008-01-09
try unpluging it, waiting a few seconds, and then plugging it in again.  Wait a few more second, then run dmesg in terminal, it might show you where its connecting the serial device.

---

### Post by jasonpeinko on 2008-01-09
still nothing, im going to try to get it to work with a win xp pro VM temporarly

---

### Post by jasonpeinko on 2008-01-09
this is what is added when i remove and re plugin the device
```

Jan  9 06:14:47 jasonpeinko-laptop kernel: [  102.788000] wlan0: no IPv6 routers present
Jan  9 06:16:45 jasonpeinko-laptop kernel: [  221.572000] usb 2-6: USB disconnect, address 3
Jan  9 06:16:45 jasonpeinko-laptop NetworkManager: <debug> [1199888205.883778] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_6cd_118_noserial_if0'). 
Jan  9 06:16:45 jasonpeinko-laptop NetworkManager: <debug> [1199888205.953936] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_6cd_118_noserial_usbraw'). 
Jan  9 06:16:45 jasonpeinko-laptop NetworkManager: <debug> [1199888205.972196] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_6cd_118_noserial'). 
Jan  9 06:16:47 jasonpeinko-laptop kernel: [  223.140000] usb 2-6: new full speed USB device using ohci_hcd and address 5
Jan  9 06:16:47 jasonpeinko-laptop kernel: [  223.336000] usb 2-6: configuration #1 chosen from 1 choice
Jan  9 06:16:47 jasonpeinko-laptop NetworkManager: <debug> [1199888207.716488] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6cd_118_noserial'). 
Jan  9 06:16:47 jasonpeinko-laptop NetworkManager: <debug> [1199888207.843443] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6cd_118_noserial_if0'). 
Jan  9 06:16:47 jasonpeinko-laptop NetworkManager: <debug> [1199888207.918986] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_6cd_118_noserial_usbraw'). 

```

---

### Post by jasonpeinko on 2008-01-09
[  432.768000] usb 2-6: USB disconnect, address 4
[  434.244000] usb 2-6: new full speed USB device using ohci_hcd and address 6
[  434.444000] usb 2-6: configuration #1 chosen from 1 choice
jasonpeinko@jasonpeinko-laptop:~$

---

### Post by Ivorydawn on 2008-01-09
Is there anything showing up in your /dev directory? such as ttyUSB0 ?

---

### Post by Ivorydawn on 2008-01-09
Also, have you looked under system-> preferences -> hardware information ? what does it say in the USB device parts?

---

### Post by ARhere on 2008-01-09
> **jasonpeinko said:**
> i am unable to get this to work

```

jasonpeinko@jasonpeinko-laptop:~/Robotics/FrcCode_2007_8722$ sudo picloader FRC_Default.hex /dev/ttyUSB0
787
Could not open socket!: No such file or directory


```

Jason,

We use these a lot at work under Fedora.  The USB emulator should be ttyUSB(0, 1, ...) but it may not always be ttyUSB0, especially if you unplug the device while something is using it.

Simply plug in the device, do a...
```
ls /dev/ttyUSB*
```
and your PC will list the serial USB devices it can see.  If you do not see any, then make sure you have the driver installed.

Then verify it works with minicom or something similar
```
minicom -s
```
I am sure you can install minicom with apt-get.

If this does nto work, go get another USB to serial converter.  They are cheap!  If you continue to get stuck, let me know and I can suggest a good cheap one.  

If you want to have fun and impress your professor, you can always build your own USB to serial emulator into your robot.  It is REALLY easy as many companies offer one chip USB solutions that you can just drop in to your design.  They probably have DIP packages as well so you can wire wrap it virtual COM port drivers are available for Linux and Windows.
1.  [Future technology]("http://www.ftdichip.com/")
2.  [http://www.silabs.com/tgwWebApp/public/web_content/products/Microcontrollers/Interface/en/interface.htm](http://www.silabs.com/tgwWebApp/public/web_content/products/Microcontrollers/Interface/en/interface.htm)

You might as well do this, becasue you will need a TTL to RS232 converter if you build a serial interface in your robot.  The USB chip will talk TTL to USB and can replace the RS232 driver.  TRUST ME, you can do it.

-AR

---

### Post by ARhere on 2008-01-09
If you need this to work by tomarrow, then go buy one that I know works from [Mouser]("http://www.mouser.com/Search/Refine.aspx?Ntt=*UC232*&N=1323038&Ntx=mode%2bmatchall&Ns=P_SField&OriginalKeyword=UC232&Ntk=Mouser_Wildcards").  It will be far less headache then workiing all day to get your current USB device to work.

While you are at it, you might want to go ahead and order the [chips too]("http://www.mouser.com/Search/Refine.aspx?FS=TRUE&Ntt=*FT232*&N=1323038&Ntx=mode%2bmatchall&Ns=P_SField&OriginalKeyword=FT232&Ntk=Mouser_Wildcards") so you can plug them into your robot.

NOTE: Do NOT let your junior E.E's try and wire wrap a USB connector.  Break out your soldergun and solder in the four wires.  Wire wrap adds a LOT of R, C, and L to your circuit!

-AR

---

### Post by jasonpeinko on 2008-01-09
The robot has the serial controller on it already. I think i will just pick a new one up which model from mouser works best?

---

### Post by jasonpeinko on 2008-01-09
> **Ivorydawn said:**
> Is there anything showing up in your /dev directory? such as ttyUSB0 ?

No, 

ls /dev/ttyUSB* says
no such file or directory,

there is usb1
usb2
usbdev1.1 ......


im just going to buy an adapter that i know works, whcih one would you recomend.

---

### Post by ARhere on 2008-01-09
> **jasonpeinko said:**
> The robot has the serial controller on it already. I think i will just pick a new one up which model from mouser works best?

You see how the word "Mouser" in my previous post is underlined?  That is a link to one of the serial converters we use.  They are English and have a good driver base.

-AR

---

### Post by jasonpeinko on 2008-01-09
do you know if best buy or radio shack would have one, dont really have the time to wait right now

---

### Post by Ivorydawn on 2008-01-10
I think ARhere is talking about any adapter that uses the FTDI FT232r chip.  That is the one in my USB-Serial adapter,  The FTDI chipset is very well supported under linux, You could always take your laptop with you to RS and try the ones they have on sale, I believe some of the ones they sell do use the FTDI chip.

Also as ARhere suggested you could put the FT232r chip in the robot and then you could judt use a USB - USB lead to connect to the PIC Programmer.

Hope you get it sorted

Best of luck

---

### Post by Ivorydawn on 2008-01-10
If you do try some out BEWARE of the Brltty problem I mentioned earlier. Uninsttall Brltty first, It's the software that links between a Braille adapter and the PC, only problem is it tends to hog the USB-Serial adapter. I had to remove it before I could see my /dev/ttyUSB0 device.

---

### Post by jasonpeinko on 2008-01-10
Yeah i have removed Brltty 

I dont know about the USB to USB this is what i am programing

[http://ifirobotics.com/rc.shtml](http://ifirobotics.com/rc.shtml)

---

### Post by Ivorydawn on 2008-01-10
I see what you mean. Makes sense to stick with a USB-Serial interface.  If you can find a n interface with the FTDI chip you will have no problems. they are well supported under Linux.

---

### Post by ARhere on 2008-01-10
HOLY COW!

I took a look at your hardware, a little pricey for just a PIC and some servos.  It does not seem to come with any IR or RF hardware, which is commonplace now with most college robotic courses.  It appears that they have sealed up the unit as well, so what do the EE's get to do? :confused:

Did the professors pick this for you?

EDIT:  Wow, they are really gouging you!  I show concern because when I was in college and did my robotics course, we had a set amount we where allowed to spend, and most of it came from our own pocket.  Even [radio shack has cheaper prices](http://www.radioshack.com/family/index.jsp?categoryId=2818347&cp=2032056.2818124) then the website you gave and that is sad.  You can get an embedded Linux development board for robotic for about $240, and a servo+motor control board for $150.  Total would be about $400, cheaper then you PIC box, and you could develop in Linux with MB of RAM, not just KB.  If you are allowed to use your own hardware, I will give you some links.

---

### Post by jasonpeinko on 2008-01-10
well its not mine, it is part of the first compitition a team pays around 5,000 $ i think and it includes compition fees with hardware including wheels, IR reciever (new this year) radio sender, and a bunch of other stuff and parts.

---

### Post by jasonpeinko on 2008-01-10
Just letting you all know, i went out and bought a new converter today, and i got home and plugged it in and what do you know 

IT WORKED!!!!

dont you just love it when stuff works when you plug it in :)

I have yet to test if it works with the robot, but it does show up under /dev/ttyUSB0

---

### Post by ARhere on 2008-01-11
Very glad for you.

Please remember to mark this post as solved if you are happy.  Good luck on your robotics course.  It will be the most fun you have ever had, and the most arguing you will ever do! hehe
:guitar:
-AR

---

### Post by jasonpeinko on 2008-01-18
I have one more question, is it possible to translate the /dev/ttylUSB0 to a com port to use in wine? if so how?

---

