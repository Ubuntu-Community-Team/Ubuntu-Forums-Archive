---
title: "Difficultly with serial Lirc device after upgrade from Feisty"
date: 2008-01-09
forum: General Help
---

### Post by pete-woods on 2008-01-09
I've been using the IR port on my laptop (Dell D610) as a receiver for my remote control for a while now under Feisty.

Under Feisty I was using the lirc_serial driver with all the setserial stuff sorted out and it was working very nicely. I recently upgraded to Gutsy for the improved support for my DVB card, but I can no-longer get the IR port to receive anything.

When I start the Lirc daemon everything reports as okay:
```
Stopping lirc daemon: lircmd lircd.
Starting lirc daemon: lircd.
```

And the dmesg output looks reasonable:
```
[ 1231.708000] lirc_dev: IR Remote Control driver registered, at major 61 
[ 1232.216000] lirc_serial: auto-detected active high receiver
[ 1232.216000] lirc_dev: lirc_register_plugin: sample_rate: 0
```

I've taken the lircd.conf from here:
[http://www.hauppauge.co.uk/board/showthread.php?t=8048]("http://www.hauppauge.co.uk/board/showthread.php?t=8048")
as my smart remote is pretending to be an MCE remote for MythTV.

My hardware.conf is as follows:
```
# /etc/lirc/hardware.conf
#
# Arguments which will be used when launching lircd
LIRCD_ARGS=""

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD=false

#Try to load appropriate kernel modules
LOAD_MODULES=true

# Run "lircd --driver=help" for a list of supported drivers.
DRIVER=""
# If DEVICE is set to /dev/lirc and devfs is in use /dev/lirc/0 will be
# automatically used instead
DEVICE=""
MODULES="lirc_dev lirc_serial"

# Default configuration files for your hardware if any
LIRCD_CONF=""
LIRCMD_CONF=""
```

When I run irw (or mode2) it reports nothing when I press buttons on the remote (this always used to work in Feisty).

I've tried the lirc_sir module too, but get exactly the same results.

Any ideas anyone?

---

### Post by AlecJ on 2008-01-10
Try this link for the right event input number..

[http://parker1.co.uk/mythtv_ubuntu2.php](http://parker1.co.uk/mythtv_ubuntu2.php)

---

### Post by pete-woods on 2008-01-11
The serial port doesn't appear as an event device (I don't think it should?). It's the laptop's built in port, it's not part of the DVB device or anything. Thanks for the suggestion, though!

---

### Post by AlecJ on 2008-01-11
Oh ok, so it looks like Lirc_serial is not linked to the right com's port

Had this on an old laptop, found the answer here

[http://www.knoppmythwiki.org/index.php?page=LIRCHowTo](http://www.knoppmythwiki.org/index.php?page=LIRCHowTo)

---

### Post by pete-woods on 2008-01-11
I think it is looking at the correct port, as I have to use setserial to disable kernel support for it or the lirc driver won't load. I have it assigned to COM1 in the BIOS and setserial is configured to work on COM1. If setserial is not run (or is run to hand it back to the kernel) I get problems.

---

### Post by AlecJ on 2008-01-11
Ok  the problem still seems to be that lirc is not looking at the right input, or is looking but can't make sense of the data from that input. unless the batteries have gone flat in the remote.

So we need to follow the route in from the IR to the system.
I found the following at [http://mysettopbox.tv/phpBB2/viewtopic.php?t=15114](http://mysettopbox.tv/phpBB2/viewtopic.php?t=15114)
Which seems to fit the bill?

I've been reading and reading on how to get my generic serial infrared receiver working. So here is a quick small guide and the one item that gave me headaches for days! 

1)
Code:
setserial /dev/ttyS0 uart none

2)
Code:
modprobe lirc_serial type=4

They key to the WHOLE problem was "type=4". This was the small option that tied me up for days digging through guides, documentation, BIOS setting after BIOS setting. Cursing at my computer.

3)
Code:
/usr/sbin/lircd

This is assuming I guess of /dev/lirc0, otherwise specify your device:
Code:
/usr/sbin/lircd -d /dev/lirc0


4) To test:
Code:
xmode2 -d /dev/lirc0


5) Point your remote to test the signal!! It finally worked for me!


My next thing to do is create my config files and figure out how to make sure the "type=4" is set for good, even after rebooting.

---

### Post by pete-woods on 2008-01-11
Thanks for trying again, but trying a multitude of kernel module options for the thing seems to have gotten me nowhere! I'm going to try turning off the IrDA -> serial port thing in the BIOS and see if just using the SiR driver helps...

Update: I've tried all sorts of combinations with the com ports being disable, enabled, set to COMM1, COMM2, and it doesn't seem to have helped. :(

---

### Post by kdeiss on 2008-01-12
hi pete,

Sorry I can't help, but I was glad to find your posting cause I have exactly the same problem and it drives me crazy ,,,

Perhaps it is a bug, please see my post here: [http://ubuntuforums.org/showthread.php?t=665313](http://ubuntuforums.org/showthread.php?t=665313)

Which kind of hardware do you use ?

thx


Klaus

---

### Post by pete-woods on 2008-01-12
My hardware is a Dell notebook - a D610. I'm using its built-in IrDA port (which has always worked in the past under Feisty).

---

### Post by pete-woods on 2008-01-31
I've tried a fresh install of Hardy Alpha 3 now. The setup has improved (it does the setserial stuff for you), but it still doesn't work :(

---

### Post by atkellyx on 2008-04-08
I am having exactly the same problem.  After taking days to sort out a really simple myth tv bug in Gutsy, I couldn't get LIRC serial working.  This seems a common problem and I did find a open bug report about it which acknowledged it as a bug in both Gutsy and Hardy.  I can't re-find the but though, sorry.

I have since upgraded to Hardy and the problem is still there.  

Daemon loads, logs are happy, just nothing happens. 

I have a homebrew serial receiver and a Hollywood RealMagic serial receiver which I have custom compiled the latest LIRC snapshot on and get the same with both.  The Hollywood actually has a LED which flashes when it receives the remote signal (as long as it's talking to something on the COM port) but LIRC stoically ignores it.

I did find a thread that suggested the latest LIRC CVS would fix the problem, but when I tried it wouldn't configure properly let alone compile.

I would loooove an answer to this.

Cheers

---

### Post by atkellyx on 2008-04-08
Just found this, allegedly a fix.

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=728540](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=728540)

---

### Post by atkellyx on 2008-04-08
Aha, I got it working.

Refer last post - link to thread provides fix.  It's still not automatic and I must manaually start lirc but it's a start.   I could only get it working for homebrew serial device.  Heres what I did

1. download, extract, configure and compile lirc 0.8.3pre2 for homebrew serial receiver
2. created file /etc/modprobe.d/lirc_serial
3. put following in file:

options lirc_serial irq=4 io=0x3f8 softcarrier=1

Interestingly, these are the options I choose when configuring lirc before compilation, I guess this just forces the issue.

4.  Execute these comands:
setserial /dev/ttyS0 uart none
modprobe lirc_serial
lircd -d /dev/ttyS0

lircd is now running

5.  irrecord -d /dev/lirc0 /tmp/testIR

I now get output in irrecord, I can get 2 rows of dots but doesn't go further at this point but at least irrecord is seeing some IR activity.  I also seem to have some stability problems with the entire system temporarily hanging for a few seconds every now and then when lirc is running, but I think I've seen this posted as another problem.  Hopefully they will have the answer.

Now that this works, I thought I'd try the apt-get version of lirc instead of compiling but this did not work.  It wasn't until I followed my successful steps above that I noticed that removal of my version of lirc removed the /etc/modprobe.d/lirc_serial file, so the apt-get lirc version may still work with this.

Hope this helps someone.

---

