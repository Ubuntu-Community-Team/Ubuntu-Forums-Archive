---
title: "How-To use lirc to control receiver and tv power"
date: 2012-10-23
forum: General Help
---

### Post by gilson585 on 2012-10-23
Ever wish your TV and receiver would power on and off with your PC and screensaver? With these scripts and instructions you can.

Now there are some assumptions here and you would have to tailor this to your setup as this is only an example of mine.
Most importantly I'm using mythbuntu and xscreensaver is the screensaver used in this distribution for which my script has been written for. I have conf files for the devices I want to control and the scripts are setup for my home directory and devices.

Now on to the fun stuff.

You'll need conf files for the devices you want to control.
[http://lirc.sourceforge.net/remotes/]("http://lirc.sourceforge.net/remotes/")
If you can't find your device here or in /usr/share/lirc/extras/transmitters/ you can create one using irrecord but that is beyond the scope of this how-to. I'll reply with that if you ask though.
If you have more than one device, you obviously need more than one transmitter but the thing I'd like to stress is that you can copy and paste all the devices into one conf file for lirc to load.
It should look like my example master.conf below.
```
# this config file was automatically generated
# using lirc-0.9.0(default) on Mon Oct 22 12:53:42 2012
#
# contributed by David Gilson <gilson585@gmail.com>
#
# brand: Westinghouse
# model no. of remote control: UNKNOWN
# devices being controlled by this remote: 40" Westinghouse TV VR-4085DF
#
# This TV was only available on Black Friday of 2011 in limited quantities
# from Target
#

begin remote

  name  VR4085DF
  bits           16
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9000  4500
  one           563  1687
  zero          563   562
  ptrail        563
  repeat       9000  2250
  pre_data_bits   16
  pre_data       0x807F
  gap          108000
  toggle_bit_mask 0x0
  frequency    38000
  duty_cycle   33

      begin codes
          KEY_POWER                0x08F7
          KEY_MUTE                 0x8877
          KEY_1                    0x807F
          KEY_2                    0x40BF
          KEY_3                    0xC03F
          KEY_4                    0x20DF
          KEY_5                    0xA05F
          KEY_6                    0x609F
          KEY_7                    0xE01F
          KEY_8                    0x10EF
          KEY_9                    0x906F
          KEY_LAST                 0xDA25
          KEY_0                    0x00FF
          KEY_MINUS                0x50AF
          KEY_VOLUMEUP             0x708F
          KEY_VOLUMEDOWN           0xF00F
          KEY_CHANNELUP            0x30CF
          KEY_CHANNELDOWN          0xB04F
          KEY_DISPLAYTOGGLE        0xC837
          KEY_ZOOM                 0x42BD
          KEY_MENU                 0xA857
          KEY_EXIT                 0x6897
          KEY_SLEEP                0xE817
          KEY_SWITCHVIDEOMODE      0x48B7
          KEY_A                    0x2AD5
          KEY_B                    0x32CD
          KEY_C                    0x6A95
          KEY_D                    0xAA55
          KEY_UP                   0x9867
          KEY_LEFT                 0xD827
          KEY_ENTER                0xB847
          KEY_RIGHT                0x38C7
          KEY_DOWN                 0x58A7
          KEY_TEXT                 0xEA15
          KEY_FAVORITES            0x1AE5
          KEY_LIST                 0x9A65
          KEY_LANGUAGE             0x5AA5
      end codes

end remote

#
# this config file was automatically generated
# using lirc-0.8.1-CVS(default) on Sat Oct 21 18:34:58 2006
#
# contributed by Ben Bronk <rukh13|hotmail.com>
#
# brand:                       Kenwood
# model no. of remote control: RC-R0813
# devices being controlled by this remote: Kenwood VR-6070
#

begin remote

  name  Kenwood_RC-R0813
  bits           24
  flags SPACE_ENC|CONST_LENGTH
  eps            30
  aeps          100

  header       9065  4480
  one           580  1660
  zero          580   550
  ptrail        580
  repeat       9060  2230
  pre_data_bits   8
  pre_data       0x1D
  gap          108434
  toggle_bit      0


      begin codes
        power       0x00B946
        thx         0x8043BC
        listenmodeup 0x00fb04
        listenmodedown 0xe0f807
        activeeq    0x60e21d
        speakereq   0x60926d
        inputmode   0x20f906
        dspmode     0x8030cf
        mute        0x0039c6
        stereo      0x00eb14
        vol+        0x00d926
        vol-        0x0059a6
        setup       0xc09867
        sound       0x80ea15
        up          0x80aa55
        down        0x802ad5
        left        0x4000ff
        right       0x40807f
        tunerev     0x4040bf
        tunefwd     0x40c03f
        flip        0xc0906f
        band        0xc0609f
        inputsel    0xc06a95
        a/b         0x0010ef
        auto        0x4020df
        dimmer      0x40b847
        dvd6ch      0xc001fe
        cd/dvd      0x0049b6
        phono       0x0009f6
        tuner       0x008976
        video1      0x006996
        video2      0x0040bf
        video3      0xc0b847
        md/tape     0x00a956
        avaux       0x00c936
        loudness    0x00fa05
        tone        0x80AB54
        bass        0x40EA15
        
        
        1       0x00817E
        2       0x0041be
        3       0x00c13e
        4       0x0021de
        5       0x00a15e
        6       0x00619e
        7       0x00e11e
        8       0x0011ee
        9       0x00916e
        0       0x0001fe
        +10     0x00b04f
        +100    0x40f20d
        

      end codes

end remote
```
Put that file in /usr/share/lirc/extras/transmitters/
If you're wondering how use, where master.conf is the file you want to use
```
sudo cp master.conf /usr/share/lirc/extras/transmitters/master.conf
```

Now configure lirc so it knows what to transmit.
```
sudo gedit /etc/lirc/hardware.conf
```
and edit TRANSMITTER_LIRCD_CONF
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Kenwood"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="master.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

We also need to edit lircd.conf to include master.conf
```
sudo gedit /etc/lirc/lircd.conf
```
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Transceivers/Remotes (all) remote:
include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"

#Configuration for the Microsoft Windows Media Center V2 (usb) : Master:
include "/usr/share/lirc/extras/transmitters/master.conf"
```


[INDENT][/INDENT]OK cool lirc is now configured. Reboot and see if lirc can actually send ir commands.
I would hope you already have an ir transmitter setup in front of the ir eye of the device you are controlling.
Using the format *irsend DIRECTIVE REMOTE CODE* for example
```
irsend SEND_ONCE VR4085DF KEY_POWER
```
Should net the desired action. (FYI remote and code names are in your conf file.)
If not fix your lirc config before continuing.

---

### Post by gilson585 on 2012-10-23
Now for the scripting goodness.
Lets start with xscreensaver.sh
```
gedit xscreensaver.sh
```
```
#!/bin/bash
cd /home/gilson585/
xscreensaver-command -watch|
while read STATUS; do
  case "$STATUS" in
    BLANK*)
      /home/gilson585/sysoff.sh;blanked=1;echo $blanked > blanked
      ;;
    UNBLANK*)
      /home/gilson585/syson.sh;blanked=0;echo $blanked > blanked
      ;;
  esac
done
```
Please edit this so that that all 3 instances of my home folder point to yours.
Fix permissions
```
chmod 777 xscreensaver.sh
```
Now put it in your startup applications.
In mythbuntu thats Applications > Settings > Session and Startup
In Ubuntu thats System > Preferences > Sessions (or Startup Applications)
Create a new entry, name it, and use example below to create the command.
```
/home/gilson585/xscreensaver.sh
```

Now lets add the scripts xscreensaver.sh calls
```
gedit syson.sh
```
```
#!/bin/sh
cd /home/gilson585/
blanked=`cat blanked`
if [ $blanked -eq 0 ] ; then
	blanked=1;echo $blanked > blanked
else
	irsend SEND_ONCE VR4085DF KEY_POWER;irsend SEND_ONCE Kenwood_RC-R0813 power;blanked=0;echo $blanked > blanked
	sleep 1
	irsend SEND_ONCE Kenwood_RC-R0813 cd/dvd
fi
```
Obvious edits required here, one for home directory, then the devices and codes sent.
This should also be added to your startup applications.
I think you know how now ;-)
Fix permissions
```
chmod 777 syson.sh
```

```
gedit sysoff.sh
```
```
#!/bin/sh
cd /home/gilson585/
blanked=`cat blanked`
if [ $blanked -eq 0 ] ; then
	irsend SEND_ONCE Kenwood_RC-R0813 power;irsend SEND_ONCE VR4085DF KEY_POWER;blanked=1;echo $blanked > blanked
fi
```
Again same obvious edits as before.
Fix permissions
```
chmod 777 sysoff.sh
```
We will call this script upon shutdown from within the lirc init.d script.
```
sudo gedit /etc/init.d/lirc
```
Now if you search for *Stopping remote control daemon* you will happen across a section of code.
```
		if [ "$START_LIRCD" = "true" ]; then
			log_daemon_msg "Stopping remote control daemon(s): LIRC"
			start-stop-daemon --stop --quiet --exec /usr/sbin/lircd
			log_end_msg $?
			[ -h "$OLD_SOCKET" ] && rm -f $OLD_SOCKET
			[ -h "${OLD_SOCKET}1" ] && rm -f ${OLD_SOCKET}1
		fi
```
add *su gilson585 -c "/home/gilson585/sysoff.sh"* where gilson585 is your username so it looks like this
```
		if [ "$START_LIRCD" = "true" ]; then
			log_daemon_msg "Stopping remote control daemon(s): LIRC"
			su gilson585 -c "/home/gilson585/sysoff.sh"
			start-stop-daemon --stop --quiet --exec /usr/sbin/lircd
			log_end_msg $?
			[ -h "$OLD_SOCKET" ] && rm -f $OLD_SOCKET
			[ -h "${OLD_SOCKET}1" ] && rm -f ${OLD_SOCKET}1
		fi
```
Awesome now if you reboot it should turn on and off like we wanted, same goes for the screensaver state changes. If not check your work.
Also If you don't use xscreensaver that script won't do anything when your screensaver state changes. You can either rewrite it for your sys or use xscreensaver.

---

### Post by gilson585 on 2012-10-23
Last but not least, lets add your remotes power button to the mix.
```
gedit pwrbutton.sh
```
```
#!/bin/sh
cd /home/gilson585/
blanked=`cat blanked`
if [ $blanked -eq 1 ] ; then
	xscreensaver-command -deactivate -display :0.0
else
	if [ $blanked -eq 0 ] ; then
		xscreensaver-command -activate -display :0.0
	fi
fi
```
Again fix home directory, then permissions (you've got this)

Then we'll modify our irexec config to assign the power button of your remote to the script.
```
gedit .lirc/irexec
```
```
# LIRCRC Auto Generated by Mythbuntu Lirc Generator
# Author(s): Mario Limonciello, Nick Fox, John Baab
# Created for use with Mythbuntu
begin
    remote = mceusb
    prog = irexec
    button = KEY_POWER
    config = /home/gilson585/pwrbutton.sh
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_CLEAR
    button = KEY_CLEAR
    config = /home/gilson585/restart_myth.sh
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_VOLUMEUP
    config = irsend SEND_ONCE Kenwood_RC-R0813 vol+ vol+ vol+ vol+ vol+ 
    repeat = 2
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_VOLUMEDOWN
    config = irsend SEND_ONCE Kenwood_RC-R0813 vol- vol- vol- vol- vol-
    repeat = 2
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = KEY_MUTE
    config = irsend SEND_ONCE Kenwood_RC-R0813 mute
    repeat = 0
    delay = 0
end
```
You might need to change things here like;
remote, button, and the location of the script.
I also included the rest of my irexec config as an example of using the remote to transmit commands like volume and mute to the receiver.

Now if you reboot this should work granted your system was already configured to use irexec.
Your .lircrc should have an include for irexec like so
```
gedit .lircrc
```
```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa
include ~/.lirc/irexec
```

Furthermore there should be a irexec daemon running, if after modifying the config and rebooting it doesn't do a thing try this from the terminal
```
irexec -d
```
If that gets you up and going then use that command as a startup application. If not I'm truly sorry as fixing irexec is beyond the scope of this how-to.

---

### Post by msvenkateshbabu on 2013-02-04
Hello,

I am new to lirc. Can you please explain how to use irrecord? I am using USB IR receiver and installed FTDI driver for the same. When i do a dmesg(in new tab) after i start lircd and run irrecord, i see the message "FTDI device disconnected". The result of irrecord will be "No signal received for 10 seconds". 

Thanks,
Venkatesh Babu

---

### Post by gilson585 on 2013-02-05
That sounds like a device driver issue and I'm not sure how to proceed with that specific one sorry.

---

