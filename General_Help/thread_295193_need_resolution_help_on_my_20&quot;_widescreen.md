---
title: "need resolution help on my 20&quot; widescreen"
date: 2006-11-07
forum: General Help
---

### Post by noktekniq on 2006-11-07
i finally got my ubuntu to work with beryl and aigxl with the beta drivers from nvidia. i realized that the screen refresh rate and resolution is not high enough. my moniter is set on 1680x1050 in windows. But when i'm on ubuntu under the system i can't seem to set the resolution to that. the only setting i can get it to (highest) is 1250x1050. i was wondering how i can get the resolution of 1680x1050 on ubuntu. will this mess up my beryl config? 

the next thing is the refresh rate. in ubuntu the refresh rate for my moniter is 55hz. but in windows i can get 60hz. how do i fix that also? 

thanks for the help

---

### Post by taurus on 2006-11-07
You can change your settings by editing /etc/X11/xorg.conf.  And before you start to mess around with it, make a backup first just in case you need to bring it back...

```
sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by noktekniq on 2006-11-07
sorry i'mnew to ubuntu... i know how to get to the config in xorg. but iono where to add the scripts how to

---

### Post by taurus on 2006-11-07
Open a terminal by Applications -> Accessories -> Terminal.

On my computer, I have this for refreshing rates so use your own numbers, okay...

```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV36 [GeForce FX 5700LE]"
    Driver         "nvidia"
EndSection

```
And further down, you can add whatever resolution you want to use.

---

### Post by noktekniq on 2006-11-07
what is the difference from horizSync and vertrefresh? which was is the actual refresh rate? 

and how do i change the 1680x1050.

sorry i ask for detail info. thanks

---

### Post by taurus on 2006-11-07
> **noktekniq said:**
> what is the difference from horizSync and vertrefresh? which was is the actual refresh rate? 

and how do i change the 1680x1050.

sorry i ask for detail info. thanks
You need to know the refreshing rates for your monitor!!!  You can get those either on the back of your monitor or from the manual.  And if you don't have the manual for your monitor, look it at from the manufacture's site for one!!!

```

    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

```

---

### Post by noktekniq on 2006-11-07
doesn't seem to change anything

---

### Post by noktekniq on 2006-11-07
i added the resolution and i see the settings in system->preference->screen resolution... but when i set the resolution to the 1680x1050 and click apply nothing happens.

---

### Post by noktekniq on 2006-11-07
bump, someone help me please? thanks

---

### Post by noktekniq on 2006-11-08
bump, someone help me please? thanks

---

### Post by noktekniq on 2006-11-08
bump, someone help me please? thanks

---

### Post by noktekniq on 2006-11-09
still have not found a resolution help. someone help me thanks

---

### Post by ner0tic on 2006-11-09
try this in terminal:> sudo dpkg-reconfigure -phigh xserver-xorg


---

### Post by noktekniq on 2006-11-09
so i run that in the terminal and then add the settings?

---

### Post by ner0tic on 2006-11-09
run that and then restart X11

and see if it's a valid option that works.

it's going to create a backup file of your current config file (the extention will have the current date)

to restart X hit ctrl+ alt+backspace (this will log you out so save anything your doing first)

---

