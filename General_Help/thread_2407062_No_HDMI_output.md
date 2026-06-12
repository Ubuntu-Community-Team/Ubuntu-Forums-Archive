---
title: "No HDMI output"
date: 2018-11-29
forum: General Help
---

### Post by ncfcdaniel on 2018-11-29
My TV does not recognise the laptop being connected.
It works fine in Windows.
Any idea how to fix?
Thanks

---

### Post by Autodave on 2018-11-29
Some info on your laptop would help.  Have you installed any video drivers?  If so, what one and where did you get it from?

While waiting for you to get back with that info, you may want to try this: power down the laptop. Turn the TV on and put it to the proper input.  Connect it to the laptop. Now, power on the PC and see if the TV is recognized.

---

### Post by ncfcdaniel on 2018-11-29
I have a ASUS Tuf 504 with a NVIDIA GTX 1060 graphics card, I have installed the NVIDIA drivers from the additional drivers section.
I am on kernel 4.19
I have tried connecting the TV on power on and it didnt make any difference

---

### Post by Autodave on 2018-11-29
Have you gone into the sound panel and redirected the output to HDMI?  Click on your volume icon and then go to the settings and then to output.  Use the dropdown menu.

---

### Post by ncfcdaniel on 2018-11-30
Unfortunately there is not any HDMI output in the sound settings.

---

### Post by NM5TF on 2018-11-30
please post the output of 

```
inxi -G
```

also

```
xrandr
```

tommy

---

### Post by pqwoerituytrueiwoq on 2018-11-30
Can you check in nvidia settings?
i also attached what the sounds configs look like (xubuntu 18.04)
*the correct hdmi audio output seems to change between reboots for me with my GTX 1060 3GB, i am using a desktop system

---

### Post by Autodave on 2018-11-30
I seem to remember that I had to enable the HDMI sound in the Nvidia panel.........

---

