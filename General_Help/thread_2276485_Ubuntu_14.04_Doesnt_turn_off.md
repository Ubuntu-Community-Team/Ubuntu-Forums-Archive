---
title: "Ubuntu 14.04 Doesnt turn off?"
date: 2015-05-02
forum: General Help
---

### Post by gabrielverly on 2015-05-02
Alright , It's my first post , And it's about this , Since my pc got a specific part with a problem , it wouldnt turn on , but got okay just by buying a new one , However , a few days later , I've  noticed it will not turn off.
It will close every thign that was running , but it will get stuck at the ubuntu loading screen (either with 2 dots or with just one left for go) 
I will happily use any command to tell more about my system in case it is needed for help me.

---

### Post by Portaro on 2015-05-02
You can use sudo poweroff on terminal to system go off.

For the plymouth problem with freeze loading screen I suggest try to enable text mode , you can do this with Grub Customizer program "change - quiet splash to text"  and try to login in text mode to see if appear any message.

---

### Post by gabrielverly on 2015-05-03
> **Portaro said:**
> You can use sudo poweroff on terminal to system go off.

For the plymouth problem with freeze loading screen I suggest try to enable text mode , you can do this with Grub Customizer program "change - quiet splash to text"  and try to login in text mode to see if appear any message.

Alright , Imma do it , Also , a little off-topic , But i also discovered that my pc will ocasionally freeze the mouse and keyboard (and screen.) and o some odd eletric noises at my headset , this only happened after i put 2 extra gigas to my ram.
Do you think it's because of that?

---

### Post by sammiev on 2015-05-03
> **gabrielverly said:**
> Alright , Imma do it , Also , a little off-topic , But i also discovered that my pc will ocasionally freeze the mouse and keyboard (and screen.) and o some odd eletric noises at my headset , this only happened after i put 2 extra gigas to my ram.
Do you think it's because of that?

You can select memtest on boot from the grub menu and let it run over night to see if there is problems with your memory. You can also try the test with and without the new memory.

---

### Post by gabrielverly on 2015-05-03
> **sammiev said:**
> You can select memtest on boot from the grub menu and let it run over night to see if there is problems with your memory. You can also try the test with and without the new memory.
Kay , Imma see if it gets better.
Also , Going on text-mode just made things worse (As i'm not good with it) And , It didnt changed , sudo power off also didnt work , Got back to quiet-splash.

---

### Post by gabrielverly on 2015-05-03
Any other ideas before i try to remove the ram and see if it was it's fault?

---

### Post by matt_symes on 2015-05-03
Hi

> **gabrielverly said:**
> Any other ideas before i try to remove the ram and see if it was it's fault?

If this only started happening after you installed the ram, i would remove it and try to shutdown.

Try to shutdown a number of times, then reinsert the ram and try to shutdown again.

Does it shutdown without the ram in ? If so then i would highly suspect the ram and test it.

Kind regards

---

### Post by gabrielverly on 2015-05-05
The lags n freezes stopped as i removed the ram , but not the problem for shutdown , might try to reset the pc to defaults , see if it gets better with a fresh install.

---

