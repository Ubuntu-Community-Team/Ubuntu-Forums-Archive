---
title: "How do you install Bin files?"
date: 2008-05-27
forum: General Help
---

### Post by jras20 on 2008-05-27
I downloaded Google earth for Linux, its a Bin file, I dont understand some of the commands, is there a easy way to install it?
Thanks.

---

### Post by nick_h on 2008-05-27
[How to install ANYTHING in Ubuntu!](http://monkeyblog.org/ubuntu/installing/)

---

### Post by danwood76 on 2008-05-27
You just run the .bin file.

First you need to make it executable by opening its properties box and clicking the executable checkbox.

Then navigate to the directory where its housed with the terminal and run it like so:
```

./GoogleEarthLinux.bin

```

---

### Post by tgrimley on 2008-05-27
Instead of the check box you can also do

chmod u+x GoogleEarthLinux.bin

which will make the file executable for the user/owner

---

### Post by jras20 on 2008-05-27
Thanks will try it.

---

### Post by jras20 on 2008-05-27
I did the installing over the terminal, but after that when I tried to load google earth it went and re-started Ubuntu.  What did I do wrong?

---

### Post by nick_h on 2008-05-27
Does it work now or does it reboot every time you try to run it?

---

### Post by jras20 on 2008-05-27
It reboots every time, I un installed it.

---

### Post by nick_h on 2008-05-27
Is there any reason why you didn't install it from the [medibuntu](https://help.ubuntu.com/community/Medibuntu) repositories?

---

### Post by PadreSol on 2008-05-27
I always do bash -x file.bin so I can see what's happening.

---

### Post by jras20 on 2008-05-27
I wish there was a easier way to do all of this!

---

### Post by PadreSol on 2008-05-27
> **jras20 said:**
> I wish there was a easier way to do all of this!

I wish there was an easier way to do most everything.  (^;

What's not working? Did you try the Medibuntu suggestion?

---

### Post by nick_h on 2008-05-27
You can install it in just 3 easy steps.

1. Add the medibuntu repository to your software sources.  If you are using Hardy type:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

2. Add the GPG key.  Type:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

3. Install the package:
```
sudo apt-get install googleearth
```

You could use the Synaptic Package Manager for the last step.

---

### Post by danwood76 on 2008-05-28
what graphics card do you have?
I would expect that is whats causing the issue here.

---

### Post by jras20 on 2008-05-28
Even after I did the 3 steps to install it, it still did the same thing.  I use a ATI graphics card, which is running fine.  Google earth ran fine on Vista.

---

### Post by ultrapatmos on 2008-05-28
Nick, thanxs it works fine
Ultrapatmos

---

### Post by nick_h on 2008-05-28
> I use a ATI graphics card
There seem to be some known issues with ATI cards - [link](http://earth.google.com/support/bin/answer.py?hl=en&answer=21448).  Do you have one of these cards?

---

### Post by RayArdia on 2008-05-28
> **nick_h said:**
> You can install it in just 3 easy steps.

1. Add the medibuntu repository to your software sources.  If you are using Hardy type:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

2. Add the GPG key.  Type:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

3. Install the package:
```
sudo apt-get install googleearth
```

You could use the Synaptic Package Manager for the last step.

Thanks for the above. All seemed to go well but at the end of the EULA I seemed to have no option but to close the terminal . Google Earth appears in the Internet Applications list but when I select it I get "Could notlaunch menu item. Failed to execute child process "googleearth" no such file or directory"

---

### Post by danwood76 on 2008-05-28
Which ATI card do you have?
Google earth is slow on my x1950 and wont run properly with compiz.
Mind you its a poor quality app and got removed soon after I installed it. (it entertained me for 30 mins or so)

You have to realise there is a huge difference between the windows drivers and the linux drivers.
Think how much more money ATI have thrown at windows drivers compared to their linux equivelants, and also how much more they make from doze in comparison.

---

### Post by RayArdia on 2008-05-29
> **danwood76 said:**
> Which ATI card do you have?
Google earth is slow on my x1950 and wont run properly with compiz.
Mind you its a poor quality app and got removed soon after I installed it. (it entertained me for 30 mins or so)

You have to realise there is a huge difference between the windows drivers and the linux drivers.
Think how much more money ATI have thrown at windows drivers compared to their linux equivelants, and also how much more they make from doze in comparison.

Using  ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)

---

### Post by danwood76 on 2008-05-29
My response was directed at the OP (jras20)

for you I would say you should install from the bin package as opposeds to medibuntu repositories and see if it works that way.
Though I doubt you will get good performance from such an old card.

---

### Post by jras20 on 2008-05-29
My Graphics card is a ATI radeon express if that helps

---

### Post by danwood76 on 2008-05-29
Do you know which exact one?

This command in the terminal will tell you:
```

lspci | grep -i 'VGA'

```

---

### Post by jras20 on 2008-05-29
> **danwood76 said:**
> Do you know which exact one?

This command in the terminal will tell you:
```

lspci | grep -i 'VGA'

```

01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]

---

### Post by danwood76 on 2008-05-29
Are you using the restricted drivers for your card?
Do you have compiz eye candy enabled? Try disabling it and starting google earth, I had to do that on my laptop (Xpress 200M) but it just rendered flickery before disabling compiz.

There is another thread on these forums relating to complete reboots.
[http://ubuntuforums.org/showthread.php?t=796639](http://ubuntuforums.org/showthread.php?t=796639)
Though hes running within a VM I assume that the problem may be related.

---

### Post by jras20 on 2008-05-29
> **danwood76 said:**
> Are you using the restricted drivers for your card?
Do you have compiz eye candy enabled? Try disabling it and starting google earth, I had to do that on my laptop (Xpress 200M) but it just rendered flickery before disabling compiz.

There is another thread on these forums relating to complete reboots.
[http://ubuntuforums.org/showthread.php?t=796639](http://ubuntuforums.org/showthread.php?t=796639)
Though hes running within a VM I assume that the problem may be related.

Thanks I will try that..

---

### Post by jras20 on 2008-05-31
How do I un install google earth?

---

### Post by nick_h on 2008-05-31
> How do I un install google earth?
If you installed it with apt-get then you can remove it with:
```
sudo apt-get remove googleearth
```

---

### Post by jras20 on 2008-05-31
> **nick_h said:**
> If you installed it with apt-get then you can remove it with:
```
sudo apt-get remove googleearth
```

Thanks I may not put it on here, I dont know why it wont load right.

---

