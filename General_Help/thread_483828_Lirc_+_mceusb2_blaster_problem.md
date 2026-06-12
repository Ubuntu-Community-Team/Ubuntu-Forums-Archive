---
title: "Lirc + mceusb2 blaster problem"
date: 2007-06-25
forum: General Help
---

### Post by BillDozer on 2007-06-25
Hi,

I installed lirc following the [Install Lirc Feisty]("https://help.ubuntu.com/community/Install_Lirc_Feisty") guide and got the remote to work with mythtv.

But I cannot get the blaster to work. The guide says
> Feisty packages include support for the mceusb2 IR transmitter. Usage is the same as standard serial transmitters.So I copied the following code (from the standard serial transmitter) into the lircd.conf file. (Not for my satellite receiver, but just for trying whether it works or not).
```

begin remote

  name          blaster
  bits          32
  flags         RAW_CODES
  eps           0
  aeps          0
  plead         0
  gap           333333
  repeat_bit    0
  begin raw_codes
  name 0_85_KEY_POWER
  5570570
 end raw_codes
end remote

```

But it does not seem to work, when I send the command
```
irsend SEND_ONCE blaster 0_85_KEY_POWER
```
I get the followin response: ```
irsend: timeout
```
After this mythtv does not respond anymore to the normal remote. I have to restart lircd and mythtv to get the remote working in mythtv again.

Anyone a clue in what I'm doing wrong?

---

### Post by BillDozer on 2007-07-06
Anyone...

---

### Post by zig_k on 2007-07-19
I found the answer for my particular cable box in step 13 buried on [this page ]("http://wsthune.public.iastate.edu/cgi-bin/spring2007/portfolio/showDocument.pl?studentID=superm1&course=314&term=spring2007&as=4").  i followed the ubuntu community howto to get everything else setup.  

Basically, you just want to get your remote definition from [here]("http://lirc.sourceforge.net/remotes/") and tack that into lircd.conf rather than try the blaster defintions for the hauppage blaster.

---

### Post by BillDozer on 2007-08-06
:) Finally it works. Tried to get a remote from the sourceforge site and after adding this one to the lircd.conf file the irsend sent the information without hanging.

So it seems the documentation on the community page is a bit incorrect.

I coiuld not find a remote that worked with my sattelite receiver, so I recorded a new one with irrecord and that worked.. The next thing I have to do is to get the channel changer script to work in MythTV, it changes the channel on the sattelite receiver but MythTV responds with a screen telling me that the channel changing failed. But I have my hopes up ;)

---

