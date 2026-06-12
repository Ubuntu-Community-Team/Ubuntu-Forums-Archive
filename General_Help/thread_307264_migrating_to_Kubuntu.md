---
title: "migrating to Kubuntu"
date: 2006-11-26
forum: General Help
---

### Post by macm10 on 2006-11-26
hello, i have two laptops that i will be migrating to kubuntu linux 6.10. before i make the move i need to know a few things:
1. will i be able to get 1920x1200 resolution
2. do you have support for moblie ati cards
3. i need to be able to play most of the meida formats that are compatible with the iPod
4. can i get support for an 8GB iPod nano

any help on this is much appreaciated

---

### Post by 56phil on 2006-11-26
hello and welcome.:) You should be able to get full resolution, but it may take some extra effort on your part. See this link for more information:

[http://ubuntuforums.org/showthread.php?t=24557](http://ubuntuforums.org/showthread.php?t=24557)

I don't have an ipod so I can't help you there. Sorry.

---

### Post by macm10 on 2006-11-28
so i sent an email to alienware asking what the horizontal sync and vertical refresh rates where for my 17inch lcd screen. i got an email back with the following:
> 
Thank you for contacting the Alienware Technical Support Team.

In regards to your inquiry, please keep in mind that refresh rates would not apply to LCD screens as these are not refreshed. Instead, the term used for these monitors would be pixel response rate, which would be how fast the pixel can change color. In this specific case, the monitor referred to would have a response time of roughly 25 milliseconds. For more information, please refer to the following link


the link contained the following information on there website:

```
Thank you for your inquiry.

The Alienware Area-51 m5750 mobile desktop may feature one of the following LCD displays:

    * 17.0" WXGA 1440x900
    * 17.0" WUXGA 1920x1200

Specifications of the 17.0" 1920x1200 WUXGA display

    *
      Manufacturer: Samsung
    *
      Model Name: LTN170WU-L02
    *
      Clear Bright (Gloss finish): Yes (Haze 0 (Glare + ARC), Hard-Coating 2H)
    *
      Display Area [mm]: 367.20 (H) × 229.50 (V) 
    *
      Resolution: 1920 horizontal by 1200 vertical
    *
      Contrast Ratio:350:1
    *
      Aspect Ratio:16:10
    *
      Pixel Pitch[mm]: 0.19125 mm (H) x 0.19125 mm (V)
    *
      Number of Colors: 6-bit, 262,144 colors
    *
      Luminance[cd/m2]: 185 cd/m2(Typ.), 5 point
    *
      Weight[gr]: 750 gr (Max.)
    *
      Power Consumption:  4.68W
    *
      Viewing Angle:
          o
            Up 45°
          o
            Down 55°
          o
            Left 65°
          o
            Right 65°
    *
      Response Time[ms]:  25±
```

based off of this can anyone help me get the information for Xorg?

---

### Post by iamhugeinjapan on 2006-11-28
1920x1200 on a 17" screen!? Teeny tiny.

Short answer to all your questions is yes. Kubuntu uses the same base as Ubuntu just with KDE instead of GNOME. But that doesn't matter because you can still run any program you used under GNOME, if the KDE versions don't suit your tastes.

---

### Post by UberArchangel on 2007-06-28
I have an alienware m5750. All you have to do to fix this is hook up the lan cable. When it gets to the part where it locks up hit ctrl +c then hit enter.

then do this

Warning you may have to look up the driver download by going through the operating system card type version of card in windows and to get the most up to date link info for driver. Also remove inbetween https://   and www2.ati.com so it looks like whats below or for some reason it does not download.

```


cd ~/Desktop; mkdir atitemp; cd atitemp

wget --no-check-certificate https://www2.ati.com/drivers/linux/ati-driver-installer-8.38.6-x86.x86_64.run

chmod +x ati-driver-installer-8.38.6-x86.x86_64.run

sudo su

sudo mv /bin/sh /bin/sh.old

sudo ln -s /bin/bash /bin/sh

sh ./ati-driver-installer-8.38.6-x86.x86_64.run --install


```

Hit ok and enter all the way through but dont launch the web browser.

```


sudo rm /bin/sh

sudo mv /bin/sh.old /bin/sh

aticonfig --initial

killall gdm

gdm


```

It should then start the gui no problem.

You will have to do this a second time once you have installed Ubuntu/Feisty. Then it will be fine from then on out.


Also a side note with the m5750 to configure your wireless you will have to do it manually if you have wpa encryption [Read Here for WPA manual configuration]("http://ubuntuforums.org/showthread.php?t=419709&highlight=wpa+in+ubuntu")






I know this is an older post but i couldn't find the solution on the website for a couple of days so I am just listing it here.

---

