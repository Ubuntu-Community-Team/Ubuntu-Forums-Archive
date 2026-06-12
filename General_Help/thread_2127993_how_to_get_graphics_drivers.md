---
title: "how to get graphics drivers?"
date: 2013-03-21
forum: General Help
---

### Post by geekhush on 2013-03-21
hi,
i just decided to make a complete switch to ubuntu from windows and have been going through some problems, one of them being the following
how do i check to see what graphics driver i have and if i dont have any where do i find it? i have a ubuntu 12.10 install on a acer aspire 571G machine with a Nvidia Geforce 620M card. anythel really appreciated :)

---

### Post by papibe on 2013-03-21
Hi geekhush.

Take a look at his tutorial: [Binary Driver Howto / Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").

Let us know how it goes.
Regards.

---

### Post by slickymaster on 2013-03-21
Run the following at a terminal window:
```
modinfo nvidia
```

---

### Post by mike555 on 2013-03-21
If you look in the menu you will see an icon for drivers or it may be called "additional drivers", click that and it will show you what is available.

---

### Post by geekhush on 2013-03-21
hi did as above and it says "ERROR: modinfo: could not find module nvidia"

---

### Post by slickymaster on 2013-03-21
Try this:
```
dpkg -l | grep nvidia
```

---

### Post by geekhush on 2013-03-21
nope, the dpkg -l |grep nvidia too didnt help.

---

### Post by geekhush on 2013-03-21
> **mike555 said:**
> If you look in the menu you will see an icon for drivers or it may be called "additional drivers", click that and it will show you what is available.

In ubuntu 12.10 additional driver isnt there and i read this that it is now replaced in system setting> software sources. checked it there too and couldn't find it there.

---

### Post by coffeecat on 2013-03-21
> **geekhush said:**
> In ubuntu 12.10 additional driver isnt there and i read this that it is now replaced in system setting> software sources. checked it there too and couldn't find it there.

Have another look. System Settings -> Software Sources, click on the "Additional Drivers" tab.

---

### Post by slickymaster on 2013-03-21
> **geekhush said:**
> nope, the dpkg -l |grep nvidia too didnt help.

You need a space between the pipe **|** and **grep**

---

### Post by kuifje09 on 2013-03-21
when ubuntu is installed you can choose to install the nvidia propriatry driver instead of nouveau.
After install it can be activated if not already with the jokey tool as mike555 suggested.

To see which best fits for you card, you can check at nvidia.com

---

### Post by geekhush on 2013-03-21
[SIZE=2][COLOR=#000000]slickymaster: yes i did the came thing... its a typo up there. and i returned nothing.


[/COLOR]coffeecat: i was talking about the same thing.. just forgot to mention the last part :P like before it was not in the system setting (in a tab) that was what i meant...

[/SIZE]

---

### Post by geekhush on 2013-03-21
Slickymaster: yes i did the same thing.. it was a typo above. sorry... and it didnt return anything...

coffeecat: yea i meant the same thing.. like before it wasnt in a tab in the software sources... and i checked it in there too couldnt find anything.

---

### Post by coffeecat on 2013-03-21
> **geekhush said:**
> coffeecat: i was talking about the same thing.. just forgot to mention the last part :P like before it was not in the system setting (in a tab) that was what i meant...


If you are using Ubuntu 12.10 with the Unity desktop and you open the Software Sources window from System Settings, you will see something like the screenshot below. The additional drivers tab is the rightmost one. You will see a different list of drivers though, because you are using a nvidia card and I have an AMD card.

[ATTACH=CONFIG]240421[/ATTACH]

---

### Post by geekhush on 2013-03-21
yes i checked it out and I couldnt find any driver listed in there...

---

### Post by papibe on 2013-03-21
Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by geekhush on 2013-03-24
here the result of the command....

> 00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
	Subsystem: Acer Incorporated [ALI] Device [1025:064b]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1140] (rev a1)
	Subsystem: Acer Incorporated [ALI] Device [1025:064c]
	Kernel modules: nouveau, nvidiafb


.

---

### Post by ManamiVixen on 2013-03-24
That Nvidia is a 610M card. You will have to install Bumblebee to get it working. Bumblebee is not included in Ubuntu, but there is a repo for it.

[http://askubuntu.com/questions/152808/nvidia-gforce-610m-drivers](http://askubuntu.com/questions/152808/nvidia-gforce-610m-drivers)

---

### Post by 3246251196 on 2013-03-24
What is the difference between getting nVidia's created driver from the apt-repo or just getting it from the nVidia website and installing through the *.run script?

---

### Post by ManamiVixen on 2013-03-24
The one from Nvidia as far as I'm aware DOES NOT support Optimus technology on Laptops. Bumblebee does though.

Of course, Bumblebee only works on Optimus. The standard Nvidia works for all other cards.

---

### Post by geekhush on 2013-05-10
hi
so i have been still searching around and haven't got the fix yet. i tried installing bumblebee and nothing happens. i tried a lot of stuffs nothing helps. my battery life is over 1.30hrs now far less than on windows and theres this heating problem too. so anyone please if u got some link or anything help me fix this problem.

---

