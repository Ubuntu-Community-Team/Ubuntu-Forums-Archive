---
title: "How can I identify a gpiochip listed under /dev"
date: 2021-06-15
forum: General Help
---

### Post by tc2020 on 2021-06-15
I have multiple i2c devices of the same type on RPi4 i2c-1 bus, particularly mcp23018. How can I identify their i2c addresses from gpiochip number?.

Below is the list of devices under /dev directory:

```

crw------- 1 root root 254, 0 Jun 15 15:49 /dev/gpiochip0
crw------- 1 root root 254, 1 Jun 15 15:49 /dev/gpiochip1
crw------- 1 root root 254, 2 Jun 15 15:49 /dev/gpiochip2
crw------- 1 root root 254, 3 Jun 15 15:49 /dev/gpiochip3
crw------- 1 root root 254, 4 Jun 15 15:49 /dev/gpiochip4
crw------- 1 root root 254, 5 Jun 15 15:49 /dev/gpiochip5
crw------- 1 root root 254, 6 Jun 15 15:49 /dev/gpiochip6
crw------- 1 root root 254, 7 Jun 15 15:49 /dev/gpiochip7
crw------- 1 root root 239, 0 Jun 15 15:49 /dev/gpiomem

```

and the corresponding "sudo gpiodetect":

```

gpiochip0 [pinctrl-bcm2835] (54 lines)
gpiochip1 [raspberrypi-exp-gpio] (8 lines)
gpiochip2 [MAX14830] (16 lines)
gpiochip3 [mcp23018] (16 lines)
gpiochip4 [mcp23018] (16 lines)
gpiochip5 [mcp23018] (16 lines)
gpiochip6 [MAX14830] (16 lines)
gpiochip7 [spi1.2] (8 lines)

```

Can this be done using Python?. Any help would be greatly appreciated. Thanks.

---

### Post by MAFoElffen on 2021-06-15
I'm not really a Raspberry Pi Guy. (Though my son is Senior Systems Engineer who has many...)

I'm thinking something like this(?)
```

#!/usr/bin/python3

import os
import subprocess
import re


p = subprocess.Popen(['i2cdetect', '-y','1'],stdout=subprocess.PIPE,)
#cmdout = str(p.communicate())


for i in range(0,7):
  line = str(p.stdout.readline())


  for match in re.finditer("[0-7][0-7]:.*[0-7][0-7]", line):
    print (match.group())

# I think that is a start...

```
But that just automates the tool: ic2detect
RE: [Ubuntu Man Page: i2cdetect]("http://manpages.ubuntu.com/manpages/trusty/man8/i2cdetect.8.html#:~:text=i2cdetect%20is%20a%20userspace%20program%20to%20scan%20an%20I2C%20bus%20for%20devices.&text=i2cbus%20indicates%20the%20number%20or,%3A%20from%200x03%20to%200x77).")

Is that what you where looking for?

---

