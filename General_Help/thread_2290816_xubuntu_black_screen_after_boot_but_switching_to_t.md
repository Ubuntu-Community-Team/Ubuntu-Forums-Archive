---
title: "xubuntu black screen after boot but switching to terminal works"
date: 2015-08-15
forum: General Help
---

### Post by davidv1992 on 2015-08-15
Before I start: If this is not the correct subforum for this question, feel free to move the question to a more appropriate location

I am running xubuntu 14.04.3 LTS. Since the kernel upgrade to 3.13.0-61 I am having problems getting that specific kernel version to display the login screen. Everything before that point is displayed as usual, including the logo screen with the rotating part-circle. Furthermore I can confirm that the system is alive by logging in, opening a terminal and shutting down via this terminal (doing this blind using the keyboard) but so far haven't managed to get the screen to work again. I can also switch to another virtual terminal using the combination ctrl-alt-f6, which displays text correctly. trying to switch on the backlight with xbacklight -inc 50 doesn't do squat, and the command works with 3.13.0-59.

What are probable causes for these symptoms, what are my options for testing those hypotheses and are there any potential solutions?

Just in case it is relevant, my laptop is an ASUS N751JK, with an nVidia optimus setup.

---

### Post by Bashing-om on 2015-08-15
davidv1992; Humm ...

Proprietary graphics driver in use ; and in the update that driver module is broken ?

Maybe try and purge the present driver and (Re-)install the graphics driver ?

[INDENT][INDENT]kernel has got to have a way to talk to the hardware
[/INDENT][/INDENT]

---

### Post by davidv1992 on 2015-08-22
Ok, I have removed the nvidia driver and it indeed does fix the issue, but i'd really like to use an nvidia prop. driver since that enables me to play games on the laptop and makes power management work. Currently the driver functions properly in the session in which I install it, but reboots then give black screen. I think this is because Xorg thinks it can use the nvidia card for it's main output when in reality this card is not attached to any display (optimus setup), is there a way to force Xorg to use the intel graphics card?

---

### Post by Bashing-om on 2015-08-22
davidv1992; Yeah ;

There is a way to choose the graphics set; nvidia-prime is the more recommended with the Intel/Nvidia optimus technology.
When you installed the driver ( from our sources ) nvidia-prime should have also installed by default.
Let's look at what is installed for Nvidia, as Intel fully supports us and what you have for the Intel driver is the best there is ; the Intel driver is not a focus of concern.....
```

dpkg -l | grep -i nvidia

```

What is supposed to be installed ?
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
Not a bad idea to confirm with Nvidia what they recommend for the graphics driver:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Once we know what is and what should be we can take appropriate action.

[INDENT][INDENT]all in the care and feeding of your 'buntu
[/INDENT][/INDENT]

---

### Post by davidv1992 on 2015-08-24
I did some further digging. The X-server logs do really suggest the issue was it taking the nvidia card to produce images (and then miserably failing as this was not attached to any monitor). Putting the nvidia drivers on a modprobe blacklist solved the issue and made X.org use the intel card again.

---

