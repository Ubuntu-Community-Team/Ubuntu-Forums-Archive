---
title: "My laptop battery drains when lid is closed"
date: 2019-01-25
forum: General Help
---

### Post by Maheriano on 2019-01-25
I just bought an Asus UX433 laptop and one of the many issues I'm having with it is that it doesn't seem to sleep like my old laptop does. Here is some troubleshooting I've already done:

1. I set the computer to sleep when the lid is closed but when I leave it overnight, it's dead in the morning.
2. I run the suspend command from the command line before leaving my computer overnight and it's still dead in the morning.
3. I turn off the computer before going to bed and the battery is not dead in the morning, it remains at the percentage at which I turned it off.
4. I run the hibernate command from the command line and it shuts the computer down like expected. I press the power button to wake it up and it appears to simply do a cold start and doesn't show any of the programs I had open prior, I have to open them all again.

Is it possible I don't have a swap partition or it's too small? How do I know? I did the normal Ubuntu 18.10 install with all the normal settings. What else might cause this? I'm tired of my battery dying every night, thanks a lot.

---

### Post by him610 on 2019-01-25
FWIW, Alternative Three (3.) is the way forward.

---

### Post by Maheriano on 2019-01-28
I'm really hoping someone can tell me how to make this operate like all my other laptops have.

---

### Post by oldrocker99 on 2019-01-29
Here are some terminal commands which will suspend a Linux system:
[https://www.cyberciti.biz/faq/linux-command-to-suspend-hibernate-laptop-netbook-pc/](https://www.cyberciti.biz/faq/linux-command-to-suspend-hibernate-laptop-netbook-pc/)

---

### Post by Maheriano on 2019-08-28
I figured this out after buying a new laptop and having the same issue.
It turned out the problem was with the proprietary Nvidia graphics driver. Once I switched the driver to the open source one, it works perfectly now. Another indicator it was related to graphics was that every time I turned the computer back on, the desktop wallpaper would be all discoloured and didn't display properly. So now that I'm using the open source graphics driver, my computer suspends properly now and doesn't die over night.

---

