---
title: "usb wake up - Logitech mk 250 mouse and keyboard"
date: 2013-02-03
forum: General Help
---

### Post by clauswilson on 2013-02-03
I am trying to get my desktop computer wake up from sleep when I touch the mouse. The Logitech MK 250 is connected with a 2,4 Hz wireless usb stick.
I have been trying different things but only succeeded in having a computer that will never sleep. So I removed my solutions (tried two).
Here is another. But I will have to understand what it does in case it doesn't work. My usb stick is on usb bus 3 (It seems that this uses bus 5): 

((echo '#!/bin/sh' && sed -rn 's/^.*(USB[0-9E]+|EUSB).*$/echo \1 > \/proc\/acpi\/wakeup/pg' /proc/acpi/wakeup) | sudo tee /etc/pm/sleep.d/05_usb && sudo chmod +x /etc/pm/sleep.d/05_usb)

Is there some hardware help for Ubuntu that I didn't find with google?

In /proc/acpi/wakeup I would like to change S-state to S3. How do I do that?

---

