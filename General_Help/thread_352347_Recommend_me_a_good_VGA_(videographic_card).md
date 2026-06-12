---
title: "Recommend me a good VGA (video/graphic card)"
date: 2007-02-03
forum: General Help
---

### Post by shironeko on 2007-02-03
Currently I'm using an ATI X300. Not the best Graphic Card.
Since I heard that Nvidia has a better perfomance and shouldn't have problems with graphic acceleration and drivers, I was thinking about switching to an nVidia VGA.

Just recommend me a good not so expensive (<50€ = <75$) graphic card. 7300 maybe?

---

### Post by igknighted on 2007-02-03
hmm, I think the best you will be able to do in that range is an FX5x00 card, maybe a 6200 if you get lucky.  The 6200 might be a slight upgrade over your x300, but not likely.  Unless you are willing to go ~$125 USD and get something newish it wouldn't be worth it to upgrade from what you have.

---

### Post by laidback on 2007-02-03
Look here to see compatability before you buy:-

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

### Post by ardchoille42 on 2007-02-03
I recently got a brand new nvidia GeForce 6200 (128Mb) video card for $40.00 USD and I am loving it. Installing the nvidia drivers for it on Dapper was easy:

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo dpkg-reconfigure xserver-xorg   (change to the nvidia driver)
sudo /etc/init.d/gdm restart

Now chromiumBSU runs fast and smooth :)

---

### Post by shironeko on 2007-02-03
> **igknighted said:**
> hmm, I think the best you will be able to do in that range is an FX5x00 card, maybe a 6200 if you get lucky.  The 6200 might be a slight upgrade over your x300, but not likely.  Unless you are willing to go ~$125 USD and get something newish it wouldn't be worth it to upgrade from what you have.


I found a good deal I think:

ASUS GeForce 7 7300LE for 45€
But it's LE not GT, and don't know if there's any difference or if there'll be any problem.
LE is not listed here:, well yes the 6800LE works fine... but it says nothing about 7300. Also: Which is the difference?

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

If this is not a good one I'll probably stick with a 6800GT.

BTW: Thanks Ardchoille42, I'll keep that in mind when installing.

---

### Post by ardchoille42 on 2007-02-03
> **shironeko said:**
> I found a good deal I think:

ASUS GeForce 7 7300LE for 45€
But it's LE not GT, and don't know if there's any difference or if there'll be any problem.
LE is not listed here:, well yes the 6800LE works fine... but it says nothing about 7300. Also: Which is the difference?

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

If this is not a good one I'll probably stick with a 6800GT.

BTW: Thanks Ardchoille42, I'll keep that in mind when installing.

You're welcome. Here's a link to the nvidia tutorial I used and it worked great for me:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

You might have a look at it when you're ready :)

---

