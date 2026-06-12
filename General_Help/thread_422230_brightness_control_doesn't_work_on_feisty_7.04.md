---
title: "brightness control doesn't work on feisty 7.04"
date: 2007-04-25
forum: General Help
---

### Post by llib1234 on 2007-04-25
I have the final 7.04 feisty version of ubuntu. However the brightness slider for power management does not work at all. Im using a 3 month old sony vaio n17g laptop. the brightness slider worked under 6.06

thanks in advance

---

### Post by llib1234 on 2007-04-25
I've found the solution!

Edit the two files:

/usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux

and

/usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux

For each file, change the first line of each file from

#!/bin/sh

to

#!/bin/bash

This fix for sony vaio brightness slider disabled problem is from homepages.cae.wisc.edu/~kraftche/ubuntu-7.04-bugs.html
Thanks to the author.

This should work for most laptops. There is a slight change in directory of the two files in Feisty from Edgy. Anyways hope it will work for you.

---

### Post by mskadu on 2007-04-25
Perfect. Worked for me too. I am running 7.04 on Sony VAIO PCG-K115Z.

thanks

---

### Post by sslizz on 2007-04-28
also in my PCG-k115s.but only two level of brightness:confused: 
P.S:any driver for MS reader under ubuntu 7.04?

---

### Post by torpethin on 2007-05-08
i have been using kubuntu(7.04) for 2 days now...so bear with me. 

I am having the same problem with brightness control on a sony vaio fe 770. 

My question is where and how, do i change those files as posted by lib1234?

I tried going through konqueror to the file, and opened it with kate, but i am unsure of how to change it like lib1234 recommended. 

also...is any one else running a vaio having troubling with the wireless card? 
i can connect, but the system seems to be having trouble during startup. For instance, when i start the computer, the kubuntu loading screen runs and then hangs for while about one third of the way through, and the led light on the WLAN flashes like mad. 
I don't know if this is a problem, or if my diagnosis is correct, but it takes a while to load, which is sort of annoying. if anyone knows anything...please share. 

Thank you

---

### Post by llib1234 on 2007-05-08
Go to your Terminal

Type in: sudo kedit /usr/lib/hal/scripts/linux/hal-system-lcd-get-brightness-linux

Enter your password.

In the file that open up in KEdit, at the top replace  #!/bin/sh with  #!/bin/bash
 Save the file.
Do the same for /usr/lib/hal/scripts/linux/hal-system-lcd-set-brightness-linux

---

### Post by Trixtua on 2007-05-08
Cool. It worked for me and my Vaio VGN-N130.

If I could only fix the suspend to ram issue, I'd definitaly scrap Vista from my laptop.

thanks for the tip.

---

### Post by torpethin on 2007-05-08
hooray!

:grin: Expression of Gratitude! 

I figured out the wlan problem as well, although perhaps not in the best way. During start up, I just switch it off, everything loads quickly, and then once logged on I can switch the wlan back on and it connects.

---

