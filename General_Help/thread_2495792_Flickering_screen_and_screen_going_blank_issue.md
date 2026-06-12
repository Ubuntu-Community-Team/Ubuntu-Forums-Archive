---
title: "Flickering screen and screen going blank issue"
date: 2024-03-01
forum: General Help
---

### Post by swangnation on 2024-03-01
Hi guys, i recently posted this on the multimedia forum so if anyone in admin can kindly delete it that would great.

My problem. I have a lenovo t570 thinkpad laptop with Ubuntu 22.04.4. My  screen began to flicker recently ( a few weeks ago ), so after doing  some googeling i discovered that I did not have the correct graphics  driver. I have a Nvidia GeForce940MX graphics card. In software updates  additional drivers, the recommended driver was Nvidia Server Driver  metapackage from nvidia-driver-470-server (proprietary).

After installing the above mentioned and recommended driver, all seemed  well however when i use telegram, the flickering makes itself present,  and i think this would have been the fourth time now that the screen has  gone completely blank which forces me to power off and reboot. When i  use VLC media player and i need to skip during a video, the sound turns  off temporarily and then returns. Also, during the boot process i get a a number of failed messages on the screen, and sometimes instead of getting my login prompt from light dm, i get the login sound and i get a blank screen with a blinking curser in the top left corner of the screen. These things were not happening before  I installed the recommended driver. When i purged the graphics driver, i got the flickering screen issue again only a lot more constantly.

I don't know what to look for so what is the best way to investigate this problem in order to find a solution?s

---

### Post by Autodave on 2024-03-02
I don't know what told you that the 470 driver was recommended.  And why the server one??  I would go with the 535 driver and NOT the server one.  nVidia's site says that you can even use a newer one than that, but I prefer to wait until all the bugs are worked out.  Additionally, you will also need the 6.1 kernel......any 5.?? kernel will probably not support the 535 driver.

---

### Post by swangnation on 2024-03-03
I'm on 6.5.0-21-generic at the moment and as i explained in the post, it was the recommended driver in the software and updates section in settings, under additional drivers. All i did was follow the recommendation. Thanks for the reply though and i will look into right now seeing i have nothing overly important to do right now

---

### Post by swangnation on 2024-03-05
> **Autodave said:**
> I don't know what told you that the 470 driver was recommended.  And why the server one??  I would go with the 535 driver and NOT the server one.  nVidia's site says that you can even use a newer one than that, but I prefer to wait until all the bugs are worked out.  Additionally, you will also need the 6.1 kernel......any 5.?? kernel will probably not support the 535 driver.


So i installed the nvidia 550 driver. Great. The flickering has stopped but i have another problem. I know nvidia will not save preferences as it anticipates other users using the same computer ( i read that some where in their fine print ) so when i boot the system, sometimes i get a blank screen in which i have to press ALT F6 which gives me a plain login prompt, not the light dm prompt which normally comes up. But my login doesn't work. I keep getting incorrect login. It's only when i reboot that i get the normal light dm prompt and ONLY when i have the charging cable plugged in.

Is there a way around this?

---

