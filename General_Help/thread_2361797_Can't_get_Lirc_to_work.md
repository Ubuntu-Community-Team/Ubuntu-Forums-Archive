---
title: "Can't get Lirc to work"
date: 2017-05-20
forum: General Help
---

### Post by benlyboy on 2017-05-20
Hi all hope some one can help:)
As mythbuntu is no more, I decided to go ahead and build a new frontend system using lubuntu 17.04 as a base. All went pretty well apart from not being able to get Lirc to work. I'm getting nothing out of irw.

This is the lircd.conf file im using.
```

 #
# this config file was automatically generated
# using lirc-0.7.1-CVS(serial) on Fri Feb  4 23:20:56 2005
#
# contributed by Christoph Bartelmus
#
# brand:                       Streamzap
# model no. of remote control: PC Remote
# devices being controlled by this remote: USB receiver
#

begin remote

  name  Streamzap_PC_Remote
  bits            6
  flags RC5|CONST_LENGTH
  eps            30
  aeps          100

  one           889  889
  zero          889  889
  plead         889
  pre_data_bits   8
  pre_data       0xA3
  gap          108344
  toggle_bit      2


      begin codes
          KEY_0                        0x00
          KEY_1                        0x01
          KEY_2                        0x02
          KEY_3                        0x03
          KEY_4                        0x04
          KEY_5                        0x05
          KEY_6                        0x06
          KEY_7                        0x07
          KEY_8                        0x08
          KEY_9                        0x09
          KEY_POWER                    0x0A
          KEY_MUTE                     0x0B
          KEY_CHANNELUP                    0x0C
          KEY_VOLUMEUP                   0x0D
          KEY_CHANNELDOWN                  0x0E
          KEY_VOLUMEDOWN                 0x0F
          KEY_UP                       0x10
          KEY_LEFT                     0x11
          KEY_OK                       0x12
          KEY_RIGHT                    0x13
          KEY_DOWN                     0x14
          KEY_MENU                     0x15
          KEY_EXIT                     0x16
          KEY_PLAY                     0x17
          KEY_PAUSE                    0x18
          KEY_STOP                     0x19
          KEY_PREVIOUS                 0x1A
          KEY_NEXT                     0x1B
          KEY_RECORD                   0x1C
          KEY_REWIND                       0x1D
          KEY_FORWARD                       0x1E
          KEY_RED                      0x20
          KEY_GREEN                    0x21
          KEY_YELLOW                   0x22
          KEY_BLUE                     0x23
      end codes

end remote


```
 
This is the out put from ir-keytable

```

Found /sys/class/rc/rc0/ (/dev/input/event9) with:
	Driver streamzap, table rc-streamzap
	Supported protocols: unknown other lirc rc-5 rc-5-sz jvc sony nec sanyo mce_kbd rc-6 sharp xmp 
	Enabled protocols: lirc rc-5-sz 
	Name: Streamzap PC Remote Infrared Rec
	bus: 3, vendor/product: 0e9c:0000, version: 0x0100
	Repeat delay = 500 ms, repeat period = 125 ms



```
Don't really know what else I can tell you. please ask for any other info that might help.

Oh one other thing, if i leave the default lircd file in place I get an output from irw. its using the devinput driver, this works ok until you use the arrows. Then it just madly repeats till you hit esc.

Any help would be gratefully accepted  

thanks:)

---

### Post by TheFu on 2017-05-21
The actual remote you have might help? If you are just starting, perhaps 17.04 isn't the best choice?  Support for it ends this year!  Use an LTS release if you don't want to be futzing around with this front-end too much.

IME, just removing the existing link for the licd.conf and pointing it to the correct remote in the already installed conf files has been working for me.  I have an rc-6 remote, so using the 
**lircd.conf -> rc6-mce-lircd.conf** works.
There are 35 pre-installed remotes in my lirc directory. Do those not work for you?

---

