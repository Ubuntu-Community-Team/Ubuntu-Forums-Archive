---
title: "Crash  report each time the computer is booted"
date: 2017-03-10
forum: General Help
---

### Post by john_OBrien on 2017-03-10
I am new. Please be patient with me.  I think I have Ubunutn - 12.  I have Xfce desktop enviroment. My laptop  is a Gateway with a celeron  processor.  It is a Gateway 3018.
The system runs fast enough.  I do not know the amount of memory the computer has. I use this laptop when I travel.
The problem is that each time I boot the computer I get a red symbol next tp the wireless indicator and when I click on it  the words "Crash report" appears. I have no idea where to go on the computer to read about the crash report and what generated it.  
If it is suggested that I upgrade, what version should I use? This is a very old, small processor but it seems to run my softwear just fine.
Please help me. I am traveling tuesday

---

### Post by howefield on 2017-03-10
> **john_OBrien said:**
> I am new. Please be patient with me.  I think I have Ubunutn - 12.

Please post the output of the terminal command..

```
cat /etc/*-release
```

which should confirm what release you are using, if it is 12.04 then the support cycle for it will end next month meaning an upgrade is likely to be the best option.

---

### Post by john_OBrien on 2017-03-10
I have 12.04.5 LTS Precise Pangolin.
Considering the processor and the small amount of memory this complter is likely to have, what version do you suggest I update to?
Thanks

---

### Post by howefield on 2017-03-10
OK, with the detail that you have provided I would suggest creating a Live media of something currently supported, eg Xubuntu 16.04.2 and run it for a couple of hours, firstly to make sure everything works and the system is generally responsive enough, allowing for it running from a DVD/USB media. Lubuntu is the lightest of the Ubuntu family.

If you want to share your machine specifications or even just for yourself, inxi is a good application to use. It doesn't come by default so would need to be installed, it is a tiny download.

```
sudo apt-get inxi
```

then something like..

```
inxi -c 5 -b
```

will give you a good idea of the hardware that you have.

---

### Post by john_OBrien on 2017-03-10
I will try that. I got the message that  my PAE is not enabled.
It gave me a link to follow to enable it. But I will skip that for now and try your suggestion

Is it safe to enable the processors PAE?

I was directed to this address.
It seems that the page has been removed?/
[https://www.ubuntu.com/enablingPAE](https://www.ubuntu.com/enablingPAE)

---

### Post by mörgæs on 2017-03-11
This one works:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by john_OBrien on 2017-03-11
Thank you very much.  I switched to a sony laptop wit  a pentium processor. The  need for PAE enabling went away. I was able to install 16.4.  However the update to 16.6(?) did not install and I had to refornat and reinstall 16.4.  I get a consistent crash report each time I boot.  THe message said I can ignore this sort of error or I can send it in to the Ubunutu website. So I send it in by clicking on continue.  I am not sure how to determine exactly what is crashing or how to fix it.

---

### Post by howefield on 2017-03-11
> **john_OBrien said:**
> I am not sure how to determine exactly what is crashing or how to fix it.

Anything in /var/crash ?

```
ls -al /var/crash/
```

---

### Post by john_OBrien on 2017-03-11
thank you

---

