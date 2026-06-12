---
title: "Nvidia X Server Settings Missing GPU"
date: 2016-11-07
forum: General Help
---

### Post by theonlytalkinggoat on 2016-11-07
I have been having issues with Chrome on my Linux box, so I decided to try using a newer nvidia driver. I reinstalled it, but when it the displays came back to life, and I went to configure them, the XserverSettings looks different and configuration options are missing. See below:
[IMG]https://lh3.googleusercontent.com/Smoo4hwCRbv893NIbb7V8S0t3t1nioVsDDv80p11oPE3_qYCn0wHYFc5YZsyR5fanDTpDgZ4EHkO1D0tYUsctx8DB34vRyGkWaDHfaq0Zg60snGJvATuxWvkQMGCblsb-LQxdPoan0J-UNK3jBOXmq37AJUjF-5b1NxYARz43SB5ZGrkqWIxw4AElH6g3h0w94Xoaa0zNxKq_wOwRd08ffxQe_Vty4fAwZLiPZQkHeQ9_KFQrtIKezcwTFdmptu4UAThihJibDrVq4943qCCdsJcBRF2oohPSOk1De0NP0eSXBWJEuwoih-6wY4EsFLjPSkZUy0FBXBxe9HSryJuIFb0jVKbwUHDaOf2SpGdbPhdiRHVa88t8F9bpSbFXRIzmI6OjGKU260AVKPngaIf6eOGDr4GHNxxGJwvNTdtmKY_IdHWg5CB7xO8_JfTXybkanGG-PRSgEdnSYtuG5JnEHwqJ7GxspyoxJ_MlWtboYuC2lc_wxLOh0mcKQVDeLnDks0lO-QZAZ-frmTflESgBmNdjkGrEsyUA2ifVA4FRFkKIdeWJ6jHducb6w5d5sbQuwYV5HXRBSiIJreryNve9Bi_KH7MAcBuiiUG6Zq4530H8EV8DA=w910-h728-no[/IMG]

However, lspci shows the card, as it always has...

```
05:00.0 VGA compatible controller: NVIDIA Corporation G73GL [Quadro FX 560] (rev a1)
```

I have tried ```
apt-get remove --purge nvidia-*
``` which removes everything nvidia. Then, I reinstalled almost every driver that was in the apt-cacche. I even double checked that the drivers were being removed, with ```
dpkg --get-selections | grep nvidia
```

Nothing nvidia remains, when re-installed.
Why is this thing not showing the graphics card, anymore?



SOLUTION:

Went to System Tools > Preferences > Additional Drivers, (aka software & updates)
Set the default driver to Using X.Org X server.
Pressed ctrl+alt+f1 and logged in. 
Issued sudo service lightdm restart. 
IF* it restarts into lightdm, open a terminal and use the next step. If not, use tty1, as before. 
Issue sudo apt-get remove --purge nvidia-*.
Issue sudo dpkg --get-selections | grep nvidia - ensure nothing nvidia remains. 
Go back to System Tools > Preferences > Additional Drivers, (aka software & updates)
Choose the highest nvidia driver available. 
Go back to tty1 and issue sudo service lightdm restart 
Lightdm should restart and you should have the latest driver, for your system. 

[IMG]https://lh3.googleusercontent.com/TUfQAY5LXL-7-mKT25GJgY8z_NfusvpN_qs4jnpCga1E7dUPViF2C-amma_inTb4TqNcJLn9XGErL32mI46H4Fwj5gIo_-uOLVpe5-g4WP5RPdkJXt6SA8qD3EEg5My59yBUVp_BlCRQGaiDrQWJhbRwk7zoEsKm0a3uS5GuhG0DuFTKaQLCq7pRKTvRZl-LLGpmm3m39vzO9JrA2wWaWJhKZ6zasE1xLU8f11HkZJIhaXkJS7an-J-3vS1SmgmwDsJ2LLLw1IpHXuACLqoeW3z5bmmDZVs3shdMXLOVxEHkhZmo9_X24LfgI8KDCpq5CCq8T7Z8I2T-xojCLYj24K_67ujNe2AZ4zFhCt9mKkKK-j6pWky7RMsNpI9fPF0Y1gdU_WcMqdg9FKzKA5werFvSmuGfm37aaTx97j6IG--haS4OuxGC7L1OvH0310F3oB9TDg-yw2IpTW-nKcAu_OCn1OxGaEWc9KeTFp6D7StPCO-nrN1PO8c_o2DLI78lbqX0uAXbLXcOG3sJ_c7e9-VYgEMXZU1Lj0HA1Y_xO_iTVxit6Y_d8ZEDCHCo1FmG8kJywc9n8W3Qzkmf7kIrzEMMM5vabTgLd-26BwZIpmgQ-o7tWQ=w1171-h960-no[/IMG]

---

### Post by omerceylan on 2016-12-12
I have same problem, I want to apply this method but I don't understand if I stop lightdm, how to connect to my desktop and additional driver, so my gpu 740m and i wanna install nvidia 375. :)

---

### Post by natesnape on 2017-03-03
> **theonlytalkinggoat said:**
> I have been having issues with Chrome on my Linux box, so I decided to try using a newer nvidia driver. I reinstalled it, but when it the displays came back to life, and I went to configure them, the XserverSettings looks different and configuration options are missing. See below:
[IMG]https://lh3.googleusercontent.com/Smoo4hwCRbv893NIbb7V8S0t3t1nioVsDDv80p11oPE3_qYCn0wHYFc5YZsyR5fanDTpDgZ4EHkO1D0tYUsctx8DB34vRyGkWaDHfaq0Zg60snGJvATuxWvkQMGCblsb-LQxdPoan0J-UNK3jBOXmq37AJUjF-5b1NxYARz43SB5ZGrkqWIxw4AElH6g3h0w94Xoaa0zNxKq_wOwRd08ffxQe_Vty4fAwZLiPZQkHeQ9_KFQrtIKezcwTFdmptu4UAThihJibDrVq4943qCCdsJcBRF2oohPSOk1De0NP0eSXBWJEuwoih-6wY4EsFLjPSkZUy0FBXBxe9HSryJuIFb0jVKbwUHDaOf2SpGdbPhdiRHVa88t8F9bpSbFXRIzmI6OjGKU260AVKPngaIf6eOGDr4GHNxxGJwvNTdtmKY_IdHWg5CB7xO8_JfTXybkanGG-PRSgEdnSYtuG5JnEHwqJ7GxspyoxJ_MlWtboYuC2lc_wxLOh0mcKQVDeLnDks0lO-QZAZ-frmTflESgBmNdjkGrEsyUA2ifVA4FRFkKIdeWJ6jHducb6w5d5sbQuwYV5HXRBSiIJreryNve9Bi_KH7MAcBuiiUG6Zq4530H8EV8DA=w910-h728-no[/IMG]

However, lspci shows the card, as it always has...

```
05:00.0 VGA compatible controller: NVIDIA Corporation G73GL [Quadro FX 560] (rev a1)
```

I have tried ```
apt-get remove --purge nvidia-*
``` which removes everything nvidia. Then, I reinstalled almost every driver that was in the apt-cacche. I even double checked that the drivers were being removed, with ```
dpkg --get-selections | grep nvidia
```

Nothing nvidia remains, when re-installed.
Why is this thing not showing the graphics card, anymore?



SOLUTION:

Went to System Tools > Preferences > Additional Drivers, (aka software & updates)
Set the default driver to Using X.Org X server.
Pressed ctrl+alt+f1 and logged in. 
Issued sudo service lightdm restart. 
IF* it restarts into lightdm, open a terminal and use the next step. If not, use tty1, as before. 
Issue sudo apt-get remove --purge nvidia-*.
Issue sudo dpkg --get-selections | grep nvidia - ensure nothing nvidia remains. 
Go back to System Tools > Preferences > Additional Drivers, (aka software & updates)
Choose the highest nvidia driver available. 
Go back to tty1 and issue sudo service lightdm restart 
Lightdm should restart and you should have the latest driver, for your system. 

[IMG]https://lh3.googleusercontent.com/TUfQAY5LXL-7-mKT25GJgY8z_NfusvpN_qs4jnpCga1E7dUPViF2C-amma_inTb4TqNcJLn9XGErL32mI46H4Fwj5gIo_-uOLVpe5-g4WP5RPdkJXt6SA8qD3EEg5My59yBUVp_BlCRQGaiDrQWJhbRwk7zoEsKm0a3uS5GuhG0DuFTKaQLCq7pRKTvRZl-LLGpmm3m39vzO9JrA2wWaWJhKZ6zasE1xLU8f11HkZJIhaXkJS7an-J-3vS1SmgmwDsJ2LLLw1IpHXuACLqoeW3z5bmmDZVs3shdMXLOVxEHkhZmo9_X24LfgI8KDCpq5CCq8T7Z8I2T-xojCLYj24K_67ujNe2AZ4zFhCt9mKkKK-j6pWky7RMsNpI9fPF0Y1gdU_WcMqdg9FKzKA5werFvSmuGfm37aaTx97j6IG--haS4OuxGC7L1OvH0310F3oB9TDg-yw2IpTW-nKcAu_OCn1OxGaEWc9KeTFp6D7StPCO-nrN1PO8c_o2DLI78lbqX0uAXbLXcOG3sJ_c7e9-VYgEMXZU1Lj0HA1Y_xO_iTVxit6Y_d8ZEDCHCo1FmG8kJywc9n8W3Qzkmf7kIrzEMMM5vabTgLd-26BwZIpmgQ-o7tWQ=w1171-h960-no[/IMG]

I have the same issue and followed the steps mentioned above with no luck. :(

---

### Post by Bashing-om on 2017-03-03
natesnape; Hello;
> 
I have the same issue and followed the steps mentioned above with no luck.


Try the more direct approach for installing the correct nVidia driver:
```

sudo apt purge nvidia*
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
Let the system choose what it thinks is best - from what it has to choose from.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Portaro on 2017-03-03
> **Bashing-om said:**
> natesnape; Hello;


Try the more direct approach for installing the correct nVidia driver:
```

sudo apt purge nvidia*
sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
Let the system choose what it thinks is best - from what it has to choose from.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


In some cases is more effcient try to install the drivers that you choose manually by terminal or in synaptic.

My examples in the last months I buy a new PC that coms with a APU radeon r3 so  think in buy a new GPU and I choose an NVIDIA GT710 2GB.
I buy the new GPU specially to blender cycles render , but the driver that I install via Ubuntu driver tool dont active cuda on Blender so I need to test other drivers that comes provided by the repositories on ubuntu and in this case I need to test some of the versions to find one that activate cuda option on blender.

There is the steps, in general we have two methods to do this, make shure that you have nouveau in blacklist &#8594; [http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver](http://askubuntu.com/questions/112302/how-do-i-disable-the-nouveau-kernel-driver)  , [http://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau](http://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau).

Text mode install or synaptic :

Text mode :
Pass to tty in text mode example &#8594; CTRL+ALT+F2
sudo apt-get --purge remove nvidia*
apt-cache search nvidia (you will be find some versions of drivers choose one to test install)
sudo service lightdm stop
sudo apt-get install nvidia-375 (for example)
sudo service lightdm start
Login on graphic mode and try to  test the nvidia (launch nvidia-settings ;

Synaptic :
sudo apt-get --purge remove nvidia*
open synaptic and search the tag nvidia
choose one driver version install and reboot to see if works .

In the both cases if you lost X you also can do this to use a simply xorg to login in graphic moe and continues search for other versions:
sudo service lightdm stop
sudo apt-get --purge remove nvidia*
sudo X -configure 
sudo mv /home/user/xorg.conf.new /etc/X11/xorg.conf
sudo service lightdm start
* You also can use a kernel parameter like :
nomodeset, vesa etc [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) , 
press 'e' on boot for edit line kernel boot and add nomodeset.

Login and retry to test other versions of drivers.


-- There are a some versions of drivers in repositories but the descriptions are very difficult to access or understand 
to find the target  models of graphic cards that the drivers works and active correctly. Maybe this is the real problem in some cases.

[IMG]https://framapic.org/vouY07Tsb1GE/XY265Rwl8k7e.png[/IMG]

Ref:[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau](http://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau)
[https://ubuntuforums.org/showthread.php?t=1975428](https://ubuntuforums.org/showthread.php?t=1975428)
[https://gnulinuxvagos.es/topic/3979-gr%C3%A1ficas-ati-xorg-config/](https://gnulinuxvagos.es/topic/3979-gr%C3%A1ficas-ati-xorg-config/)

---

### Post by ahmed.mlj81 on 2017-08-14
I have had the same problem. I installed nvidia binary driver -version 375.66 using ubuntu software and updates. (ubuntu 16.04 LTS)
After applying changes and waiting for a while the procedure stops and a request to change the UEFI secure boot state is lanched (third party drivers can't be installed with secure boot enabled). I followed the guiding window (set a passeword for the boot, enter the indexed character each time ->click ok and reboot ) .
Entering the nvidia x server the informations (screen0 and GPU informations and configurations were missing).
But I choosed to go through a second reboot before taking your solution, and it worked. I have all the informations displayed on the nvidia x server window.
Some times it takes only to reboot.

---

