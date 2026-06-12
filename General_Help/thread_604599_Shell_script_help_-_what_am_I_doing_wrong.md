---
title: "Shell script help - what am I doing wrong?"
date: 2007-11-06
forum: General Help
---

### Post by technikalKP on 2007-11-06
I can't figure out what I'm doing wrong with this shell script.  I want the results of the command:

> 
hal-find-by-property --key info.product --string 'Lid Switch'


to be assigned to the 'UDI' variable so that I can use it as an argument in a hal-set-property call.  Here's the script:

> 
#!/bin/bash

lidkey="'Lid Switch'"
UDI='hal-find-by-property --key info.product --string $lidkey'
echo UDI:
echo $UDI


however, when I run it, UDI is not set to the results of the hal-find-by-property call, but to the actual command string instead, ex:

> 
UDI:
hal-find-by-property --key info.product --string $lidkey


What am I doing wrong?  How do I get the results from the call (/org/freedesktop/Hal/devices/computer_logicaldev_input_2 when run from the Terminal on this machine) into the UDI variable?

Thanks!

---

### Post by technikalKP on 2007-11-06
Never mind - figured it out.  There's a difference between "`" and "'"

---

