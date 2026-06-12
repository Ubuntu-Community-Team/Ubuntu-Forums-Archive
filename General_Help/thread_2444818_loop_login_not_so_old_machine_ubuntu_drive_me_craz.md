---
title: "loop login not so old machine ubuntu drive me crazy pls help"
date: 2020-06-04
forum: General Help
---

### Post by wiileewaller on 2020-06-04
Hello guys !
Im desperate, i've tried to install ubuntu 16.04 for 2 whole days and still trying, this drive me completely crazy !

I m stuck with a login loop, fortunately the cmd line with alt f1, and I tried many stuff i ve found on discussions and forums, 

when i login i have no desktop with a windows asking i i want to upgrade to 18.xx it flicker a bit and then generally turn black or white, but it can also be random color, i have encountered sky blue deep blue pink red gray orange and purple too

too bad its hard for me to share log cause i cant copy past here
im with an (not so) old configuration pc,  

intel core2duo 
graphic nvidia fx 5600
2go ram
motherboard 4coredualvsta

ive tried xauthority, nvidia, apt get upgrade install etc.... 
im not a it guy but i try to do my best

 sorry for my approx english.
and thank you all

---

### Post by grahammechanical on 2020-06-04
The first point to take note of is that Ubuntu 16.04 has now reached end of life (It is not supported) and that is why you are getting the option to upgrade to Ubuntu 18.04.

Second point: I have an Intel Core 2 Duo and I am running Ubuntu 18.04, Ubuntu 20.04 and Ubuntu 20.10 on this machine but it does have 4 GB Ram. Which helps a lot. You might want to think about installing a flavor of Ubuntu that does not require as much memory such as Xubuntu or Lubuntu. Just a thought.

Third point: You may need to install Ubuntu using alternative boot options and selecting nomodeset. This will install Ubuntu without loading a video driver and will use the BIOS video modes until the X-server (display server) is loaded.

In this link go to Ubuntu CD Advanced Welcome Page Options and then down to Section 6 - F6.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

At the purple screen with the icon of a keyboard and a human press any key. Then press F6 - Other Options. Scroll down the menu that appears and select nomodeset and press ESC. And continue with the installation.

When the installation is finished and you are at a desktop (hopefully) you will be using the open source video driver. You might find that good enough. I do. Or you can go to the Applications screen and load Software and Updates>Additional Drivers tab. With the machine connected to the internet and after a little wait you may get offered a proprietary driver.

P.S. Over time proprietary video drivers drop support for older video cards. So we have to use the open source video driver.

Regards.

---

### Post by CelticWarrior on 2020-06-04
Not so old? It's the same as saying a 10 years old dog is not so old... It isn't in human years but in dog years...

That said, you need Nvidia 340 drivers for the Quadro FX5600, not any other driver. Newer ones do NOT support that legacy card. And why 16.04 which has less than a year of support left?

---

### Post by wiileewaller on 2020-06-04
Okay thanks you for your fast replies its a relief, i feel less alone. 
@celticwarrior actually it s not a quadro, it  just a fx5600, i trid the 340 driver and the loop still continue.
@grahammechanical ok i ll give a try to xubuntu or lubuntu with your tutorial link, if i coud add 2 more go i would but this motherboard is limited to 2 go, i ve read somewhere that if i update the bios i could reach 3.18go but anyways i dont have the required ram at home

thanks again

---

### Post by wiileewaller on 2020-06-04
edit: Lubuntu works like a charm !

i still have few  question, its very strange, cause with the same config, my ubuntu use to work well, sometime it was slow but graphicaly it work, does that mean that apt-get upgrade/update messed up with my old machine, i really thought that all those linux/unux purpose/spirit was to support every machine.

Anyways thanks, hope that lubuntu will work for at least 10 more years =P i dont plan to move to puppy linux.

---

