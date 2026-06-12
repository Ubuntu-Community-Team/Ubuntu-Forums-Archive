---
title: "Nvidia drivers on xubuntu 18.04.5"
date: 2021-05-14
forum: General Help
---

### Post by Furycd001 on 2021-05-14
HI Guys.. I had a post on here yesterday with the problem of my laptop failing to boot to the desktop. After spending a while trying to boot back into my desktop I gave up & opted for a reinstall. I reinstalled xubuntu 20.04.2 but again kept getting stuck at the same place & couldn't access the desktop. Reinstalled yet again thid time using xubuntu 18.04.5 & now I can access the desktop & do a bunch of things (all-be-it with a good amount of screen tearing).

My problem now is that whenever I install any nvidia drivers my laptop will fail to boot & sit at a black screen with a solid cursor in the top left of the screen. Sometimes I'll get as far as lightdm, before it locks up or I'll even get as far as the desktop, but it'll then decide to lockup several seconds later. I've also tried installing the latest nvidia drivers from the ppa, but they just leave me with the same black screen & solid cursor.

I've booted into recovery mode & ran "sudo apt-get remove --purge '^nvidia-.*'" to remove all nvidia drivers & rebooted using noveau drivers. To install drivers I go to Settings >> Additional Drivers. [**This is what I see.**]("http://i.imgur.com/UBkpjPS.png")

I've run the following..
    + ubuntu-drivers list >> **[https://termbin.com/z9u5](https://termbin.com/z9u5)** 
    + sudo ubuntu-drivers devices">> **[https://termbin.com/d65k](https://termbin.com/d65k)**

Could someone please help me becuase I'm not that great when it comes to debugging or fixing things & I would love to get my graphics card working again & have a stable xubuntu desktop experience. Many thanks in advanced....

---

### Post by Furycd001 on 2021-05-14
Ok so I removed the ppa & installed the standard nvidia-driver-460 & can get to a desktop using kernel 5.4.0-42-generic. Screen tearing is still a thing & when I try to fix it using [**"this post"**]("https://ubuntuforums.org/showthread.php?t=2365449&p=13663158&viewfull=1#post13663158") I receive this error in my terminal....

```
cat: /sys/module/nvidia_drm/parameters/modeset: No such file or directory
```

I uninstalled kernel linux-image-5.4.0-73-generic using apt-get purge & I can boot straight to the desktop now. My NVIDIA X Server Settings now has way less options and looks **["like this"]("http://i.imgur.com/SIy4VqA.png")**. I've probably screwed something up for my Nvidia setting to now look like that. Anyway now that I can boot straight to my desktop I just need someone to help with the screen tearing issue....

---

### Post by Yellow Pasque on 2021-05-15
What model laptop? Are there any Optimus settings in BIOS? I'd recommend using "ondemand" mode  and only run heavy 3D programs on the Nvidia GPU: [https://ubuntuforums.org/showthread.php?t=2454399&p=14004415#post14004415](https://ubuntuforums.org/showthread.php?t=2454399&p=14004415#post14004415)

---

### Post by Yellow Pasque on 2021-05-15
Also, be sure to disable Secure Boot in the BIOS/EFI.

---

### Post by Furycd001 on 2021-05-17
The laptop is a ThinkPad E470. There is no Optimus settings in the bios that I can see, but secure boot & uefi have been disabled. I decided to start fresh this morning using the netinstall to install a minimal xubuntu. Once booted to the desktop I installed the Nvidia 460 tested driver & now after rebooting I can't access the desktop again....


**[ EDIT ]**

I got back to the desktop by booting into recovery mode & uninstalling all nvidia stuff....

---

### Post by scorp123 on 2021-05-17
> **Furycd001 said:**
>  installed the standard nvidia-driver-460 ...

Are you sure that this is the correct driver for the Nvidia chip in your laptop? I ask this because some Nvidia chips (especially older models) might require a different driver package (a different *"nvidia-driver-xxxx"* something-number) because the new Nvidia driver packages no longer support them.

---

### Post by Furycd001 on 2021-05-17
> **scorp123 said:**
> Are you sure that this is the correct driver for the Nvidia chip in your laptop? I ask this because some Nvidia chips (especially older models) might require a different driver package (a different *"nvidia-driver-xxxx"* something-number) because the new Nvidia driver packages no longer support them.
 
How do I know which driver is the correct one ??
This is the output for **ubuntu-drivers devices** >> [https://termbin.com/z927](https://termbin.com/z927)
I also get the following output in the terminal....

```
 WARNING:root:_pkg_get_support nvidia-driver-390: package has invalid Support Legacyheader, cannot determine support level 
```

Here&#347; a current screen shot of what my Additional Drivers looks like >> [https://i.imgur.com/YOOGj4X.png](https://i.imgur.com/YOOGj4X.png)

---

### Post by scorp123 on 2021-05-17
> **Furycd001 said:**
> How do I know which driver is the correct one ?? 

I usually check with the **nvidia.com** web site: *DRIVERS > ALL NVIDIA DRIVERS*

If you go there to the *"All Nvidia drivers"* page you can search for and/or select your exact chip model and it will tell you which driver you need.
So if we search for ***"GeForce 940MX"*** (as per your screenshot) we get this answer: **"460.80"**.

```
... Supported products:

(... cut off ...)

GeForce 900M Series (Notebooks):
GeForce GTX 980, GeForce GTX 980M, GeForce GTX 970M, GeForce GTX 965M, GeForce GTX 960M, GeForce GTX 950M, GeForce 945M, **[COLOR="#FF0000"]GeForce 940MX[/COLOR]**, GeForce 930MX, GeForce 920MX, GeForce 940M, GeForce 930M

(... cut off ...)

```

so your initial choice of installing the *"nvidia-driver-460"* package was actually correct. It *should* work!? 

My bad, I was on the wrong track. ](*,)

I own several old Apple MacBook, some of which have old Nvidia chips inside. Mac OS stopped being compatible with these laptops a long long time ago. But Linux works tip top here. Sometimes it happens that a Linux installer detects those old Nvidia chips in there and then tries to install the absolutely newest Nvidia driver ... and it fails in my case because the chip I have is one of those that's no longer supported in those new packages. I always have to select one of the older alternatives. 

Sorry, I assumed that this is what might be causing your problems too... but that's not the case at all, you picked the right driver.

---

### Post by Furycd001 on 2021-05-17
> **scorp123 said:**
> I usually check with the **nvidia.com** web site: *DRIVERS > ALL NVIDIA DRIVERS*

If you go there to the *"All Nvidia drivers"* page you can search for and/or select your exact chip model and it will tell you which driver you need.
So if we search for ***"GeForce 940MX"*** (as per your screenshot) we get this answer: **"460.80"**.

```
... Supported products:

(... cut off ...)

GeForce 900M Series (Notebooks):
GeForce GTX 980, GeForce GTX 980M, GeForce GTX 970M, GeForce GTX 965M, GeForce GTX 960M, GeForce GTX 950M, GeForce 945M, **[COLOR=#FF0000]GeForce 940MX[/COLOR]**, GeForce 930MX, GeForce 920MX, GeForce 940M, GeForce 930M

(... cut off ...)

```

so your initial choice of installing the *"nvidia-driver-460"* package was actually correct. It *should* work!? 

My bad, I was on the wrong track. ](*,)

I own several old Apple MacBook, some of which have old Nvidia chips inside. Mac OS stopped being compatible with these laptops a long long time ago. But Linux works tip top here. Sometimes it happens that a Linux installer detects those old Nvidia chips in there and then tries to install the absolutely newest Nvidia driver ... and it fails in my case because the chip I have is one of those that's no longer supported in those new packages. I always have to select one of the older alternatives. 

Sorry, I assumed that this is what might be causing your problems too... but that's not the case at all, you picked the right driver.

I have a 2009 standard white macbook with an nvidia card. Been running Linux on it since purchase without ever having any problems. My last ever Linux installation on actual hardware was in 2017 whenever I bought this Thinkpad E470. Back then I remember installing nvidia drivers the same way I am today & never having any problems other than having to issue two or three simple commands to fix screen tearing. I´ve tried installing a few different nvidia-driver this morning, but they all lead to the same black screen with solid cursor. Is there a log file of any sort that I could share here that may help show what my problem might be ?? Also many thanks for replying and trying to help me :)

---

### Post by Furycd001 on 2021-05-17
I tried install hwe kernel but &#7831;hat didnt do anything....

```
 sudo apt-get install --install-recommends linux-generic-hwe-18.04 xserver-xorg-hwe-18.04 
```

---

### Post by Furycd001 on 2021-05-17
Ok so update.. The ever awesome and amazing ioria over on the #ubuntu irc helped me get logged in with nvidia-drivers installed. Screen tearing is still present, but I do not care about that right now. I&#314;l mark thhis thread as solved :)

---

