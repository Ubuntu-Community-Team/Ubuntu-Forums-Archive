---
title: "lgpio.error: 'can not open gpiochip'"
date: 2023-03-02
forum: General Help
---

### Post by lm782 on 2023-03-02
Ubuntu 22.04 LTS on a Raspberry Pi 4B (8GB). In the long-run, among other functions, I need to drive a stepper motor. (Confirmed hardware and motor control works with RPi OS.) To start, I am following Canonical's lgpio tutorial ([https://ubuntu.com/tutorials/gpio-on-raspberry-pi#1-overview](https://ubuntu.com/tutorials/gpio-on-raspberry-pi#1-overview)) and got some errors. 

Simplifying the flashing-an-LED tutorial further, I ran a couple stand-alone lgpio commands in the Python IDLE shell (details below). If someone can point me to a better location, the lgpio docs I found are here [https://abyz.me.uk/lg/py_lgpio.html](https://abyz.me.uk/lg/py_lgpio.html).

Ultimately this is part of a larger system, so running as sudo is not an option. Came across a few posts that mention creating a gpio group, but am  not sure if that's what causing this error. Turning to the forum in case  someone has better insight on what's going on and/or how to use gpio... 

IDLE Shell 3.10.6
import lgpio

lgpio.get_module_version()
'lgpio.py_0.1.0.1'

h = lgpio.gpiochip_open(0)
Traceback (most recent call last):
  File "/usr/lib/python3.10/idlelib/run.py", line 578, in runcode
    exec(code, self.locals)
  File "<pyshell#8>", line 1, in <module>
  File "/usr/lib/python3/dist-packages/lgpio.py", line 648, in gpiochip_open
    return _u2i(handle)
  File "/usr/lib/python3/dist-packages/lgpio.py", line 461, in _u2i
    raise error(error_text(v))
lgpio.error: 'can not open gpiochip'

lgpio.gpiochip_open(0)
Traceback (most recent call last):
  File "/usr/lib/python3.10/idlelib/run.py", line 578, in runcode
    exec(code, self.locals)
  File "<pyshell#10>", line 1, in <module>
  File "/usr/lib/python3/dist-packages/lgpio.py", line 648, in gpiochip_open
    return _u2i(handle)
  File "/usr/lib/python3/dist-packages/lgpio.py", line 461, in _u2i
    raise error(error_text(v))
lgpio.error: 'can not open gpiochip'

---

### Post by lm782 on 2023-03-10
Update in case anyone finds this in the future. 
RPi OS uses a 'gpio' group where Ubuntu uses 'dialout'. Need to add your username to the dialout group AND reboot. 
(Even though 'cat /etc/group' will show your username after you make the  change in the dialout group - changes do not go into effect, and  therefore lgpio function will not work, until you reboot.)

---

