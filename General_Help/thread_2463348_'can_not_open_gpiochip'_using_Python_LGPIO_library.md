---
title: "'can not open gpiochip' using Python LGPIO library ubuntu 21.04 on raspberry 4"
date: 2021-06-09
forum: General Help
---

### Post by michael-brown-049 on 2021-06-09
Hi Guys

I'm trying to control the GPIO pins of my Raspberry PI 4.  I have followed this guide [https://ubuntu.com/tutorials/gpio-on-raspberry-pi#1-overview](https://ubuntu.com/tutorials/gpio-on-raspberry-pi#1-overview)

Raspberry has Ubuntu 21.04 desktop on it.  I have installed the LGPIO library as described.  However when I run the example code:

```
#  Blink an LED with the LGPIO library
#  Uses lgpio library, compatible with kernel 5.11
#  Author: William 'jawn-smith' Wilson

import time
import lgpio

LED = 23

# open the gpio chip and set the LED pin as output
h = lgpio.gpiochip_open(0)
lgpio.gpio_claim_output(h, LED)

try:
    while True:
        # Turn the GPIO pin on
        lgpio.gpio_write(h, LED, 1)
        time.sleep(1)

        # Turn the GPIO pin off
        lgpio.gpio_write(h, LED, 0)
        time.sleep(1)
except KeyboardInterrupt:
    lgpio.gpio_write(h, LED, 0)
    lgpio.gpiochip_close(h)
```

I get the following trace back:

```

python3 LED_Demo.py 
Traceback (most recent call last):
  File "/home/net2edge/LED_Demo.py", line 19, in <module>
    h = lgpio.gpiochip_open(0)
  File "/usr/lib/python3/dist-packages/lgpio.py", line 648, in gpiochip_open
    return _u2i(handle)
  File "/usr/lib/python3/dist-packages/lgpio.py", line 461, in _u2i
    raise error(error_text(v))
lgpio.error: 'can not open gpiochip'

```

If I try at the interpreter prompt I get the same:

```

>>> import lgpio
>>> lgpio.gpiochip_open(0)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python3/dist-packages/lgpio.py", line 648, in gpiochip_open
    return _u2i(handle)
  File "/usr/lib/python3/dist-packages/lgpio.py", line 461, in _u2i
    raise error(error_text(v))
lgpio.error: 'can not open gpiochip'
>>> 

```

I have previously successfully used Raspian and RPi.gpio previously to control the gpio pins but wish to use ubuntu.  Any suggestions or pointing out my obvious mistake would be appreciated.

---

### Post by michael-brown-049 on 2021-06-09
Ok, so if I use sudo or run as root it is fine.  Newby issue.

---

### Post by kbasaran on 2021-11-21
Hello. I have the same problem. Running the code as sudo is not an option for me. Can anyone offer another solution?

---

