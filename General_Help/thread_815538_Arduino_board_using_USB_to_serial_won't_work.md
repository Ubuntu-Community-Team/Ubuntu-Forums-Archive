---
title: "Arduino board using USB to serial won't work"
date: 2008-06-01
forum: General Help
---

### Post by optique on 2008-06-01
I have the Arduino microcontroller (Dec. clone bare bones board with 168 ) and the ftdi USB to serial cable.
Ref: [http://www.moderndevice.com/Images/BBBRevD800.jpg]("http://www.moderndevice.com/Images/BBBRevD800.jpg")
Ref: [http://www.ftdichip.com/Products/EvaluationKits/TTL-232R.htm]("http://www.ftdichip.com/Products/EvaluationKits/TTL-232R.htm")

I am running under 8.04 on ia386. My problem is that I can not get the Arduino environment to program the board. 

I followed the instructions to install Arduino as per:[http://www.arduino.cc/playground/Linux/Ubuntu]("http://www.arduino.cc/playground/Linux/Ubuntu")
Which I am recapping below:

1. Using synaptic mgr, installed sun-java6-jre*, gcc-avr, avr-libc. 
2. Downloaded the arduino environment (arduino-0011-linux-tgz)
3. Attempted to sudo update-alternatives --config java, but the msg stated it was not necessary since only one Java was found. 
4. Double clicked the Arduino file in the Arduino app folder.
5. Application runs, I select an example sketch and compile it. Arduino Tools->Serial port shows /dev/usbtty0 selected as expected. 
6. When I attempt to upload, I get: 
avrdude: stk500_recv(): programmer is not responding
avrdude: stk500_recv(): programmer is not responding

Thinking that brltty was interfering, I uninstalled it. No change. *Then, thinking that since the instructions called for java5-jre instead of Java6-jre, I uninstalled the 6 and installed the 5. No change. Hardware Led is on, cables are attached. Rebooted, pressed reset before/after programming--all without effect.

I know the hardware is likely ok since I can program it under winxp.

I would like to hear from anyone who has this hardware/software combination that got it to work. Or, any other tips are welcome.

Thanks in advance.
Steve.

---

### Post by optique on 2008-06-03
Come on, guys. Someone has to know this!

Thanks.
Steve.

---

### Post by optique on 2008-06-06
See Arduino forum for possible work to fix this.

---

### Post by Keen101 on 2008-06-07
I'm not a linux guru, but i got the Arduino software to run on my 8.04 Heron system the other day. 

[http://www.arduino.cc/playground/Learning/Linux](http://www.arduino.cc/playground/Learning/Linux)

Step one: get java runtime (jre. I searched for "jre" in synaptic package manager, and installed the "openjdk-6-jre" packages. Works great.

Step two: install the "gcc-avr" tools. also, the "binutils-avr", and the "avrdude" packages from the repositories. also the "acr-libc" package.

Step three: searched for the "brltty" package in synaptic, and removed it just in case.

Step four: copy and extract the arduino software to my desktop. Open the folder. And double click on the "arduino" script file. When prompted what to do click "run"

hope that helps.

-Andrew
-keen101

---

### Post by Keen101 on 2008-06-07
I don't know, but it might be a problem with your version of java. I coulden't get sun's version of java working, so i tried the "openjdk-6-jre" packages instead. Works great for me.

My suggestion is to try removing sun java, and trying the "openjdk-6-jre" version.

---

### Post by optique on 2008-06-07
Hi, keen101

Pls see the hardware I am using.

**Especially note the programming cable.**
Is this the same as yours?

Please give me a shout back.
Thanks.
Steve.

---

### Post by Keen101 on 2008-06-08
hmm... well,

I'm not using the exact same hardware as you, but i don't think that really matters. And as for the cable, all ftdi cables and chips are pretty much the same as far as i know. I don't think it's the cable.

this is the version I'm using ***[here]("http://www.adafruit.com/index.php?main_page=product_info&cPath=17&products_id=50&zenid=6163aed6a770bb0ed68b7d62ceb430fa")***

here is a link to someone who had a similar problem with a similar arduino. ***[http://forum.sparkfun.com/viewtopic.php?t=10403&highlight=stk500recv]("http://forum.sparkfun.com/viewtopic.php?t=10403&highlight=stk500recv")***

turns out that they had a broken bootloader. But, since you said works on xp, then it's probably not that.



I suspect it's either your version of java, or maybe you don't have all the required avrdude packages installed. Try using external power, see if that helps too. I don't know.

But, i really can't say for sure. I'm not an arduino expert. That's just my opinion.'

I really hope you get it working though.

-Andrew
-keen101

---

### Post by hellmasker2002 on 2009-01-12
> **Keen101 said:**
> I'm not a linux guru, but i got the Arduino software to run on my 8.04 Heron system the other day. 

[http://www.arduino.cc/playground/Learning/Linux](http://www.arduino.cc/playground/Learning/Linux)

Step one: get java runtime (jre. I searched for "jre" in synaptic package manager, and installed the "openjdk-6-jre" packages. Works great.

Step two: install the "gcc-avr" tools. also, the "binutils-avr", and the "avrdude" packages from the repositories. also the "acr-libc" package.

Step three: searched for the "brltty" package in synaptic, and removed it just in case.

Step four: copy and extract the arduino software to my desktop. Open the folder. And double click on the "arduino" script file. When prompted what to do click "run"

hope that helps.

-Andrew
-keen101


Very helpfull! thanks! just a small thing...its not  "acr-libc" its "avr-libc" in the synaptic package manager.For me , a fairly new linux and arduino user was a big deal... :P

Dimitri

---

### Post by hanzomon4 on 2009-10-28
I have the same problem.. It works in OSX but not linux.

---

### Post by neirons on 2009-12-07
Hi,
sorry about bad english. Is not may native language but anyway I will tray to help.

So, I'm Arduino user and use them in Ubuntu like Linux. Linux Mint. So, it's the same thing.

There is little pyhon code. This code make Arduino bootloader wake up.

```

import serial
import time
import sys

if len(sys.argv) != 2:
    print "Please specify a port, e.g. %s /dev/ttyUSB0" % sys.argv[0]
    sys.exit(-1)
    
ser = serial.Serial(sys.argv[1], 19200, timeout=1)
ser.setDTR(1)
time.sleep(0.5)
ser.setDTR(0)
ser.close()

```

There is shell script for uploading to Arduino board:
```

#!/bin/bash

# There is 2 parameters. First is HEX faile name and second one is port adress. Example /dev/ttyUSB0

if [ -z "$1" ]; then 
              echo Use: $0 blablabla.hex /dev/ttyUSB0
              exit
          fi

python ./unix_pulsedtr.py $2
./arduino-0017/hardware/tools/avrdude -p m168 -C /etc/avrdude.conf -c avrisp -P $2 -b 19200 -F -U flash:w:$1

```

Thats code realy work. Is tested and help for me.
I'm opened for questions about Arduino using with Linux and GCC. With or without Arduino IDE.

Thanks for Your attention

---

### Post by p_breakfast on 2010-10-09
I solved it by changing the /home/YOURNAMEHERE/.arduino/preferences.txt

changed the line that said

> serial.port=com1


to 

> serial.port=ftdi_sio

this allowed me to select /dev/ttyUSB0 from the tools>serial port menu

---

### Post by ferkoferko on 2010-10-30
I don't know how much active this thread is but I had the very exact problem and I just downloaded an older version of arduino IDE (had 0021 and downloaded 0019) and it totally worked...

Good luck

---

### Post by bodymind on 2010-11-04
I changed my board in: Tools > Board

And it was fine! :P

---

