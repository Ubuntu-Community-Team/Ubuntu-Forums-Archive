---
title: "Is it normal for a LiveUSB to freeze after long hours of usage?"
date: 2017-05-23
forum: General Help
---

### Post by ardouronerous on 2017-05-23
I have a LiveUSB of Lubuntu 16.04.2 booted on a Dell Inspiron E1505. The USB I'm using is a Generic 8GB.

Usually after 8 or more hours of usage, my laptop completely freezes, including the mouse and keyboard, and it mostly happens when I watch Youtube videos.

Is that normal behavior?

---

### Post by LastDino on 2017-05-23
8GB is too small to be functioning as a live boot+ your regular OS use. 

You might want to consider "persistent" (which basically saves changes to OS like updates and downloads etc) booting with 32Gb USB 3.0 or even an SSD if you're using this method to use use Ubuntu. 

With 8 Gb, it is good for only trial and install and maybe troubleshoot. I wouldn't have been surprised if it freezes, try something bigger, if problem persists, then we can look in other ways maybe.

---

### Post by ardouronerous on 2017-05-23
Thanks for the reply.
Okay, just for clarification, the reason for the freezes after long hours of usage is because my USB is too small?

---

### Post by LastDino on 2017-05-23
Most likely. Because as you use your OS, it is going to consume space. 

It would've been different issue if it was freezing at bootup or during first few seconds after boot up, then we would've to look at your graphic card compatibility and system specs and what not. But here you are doing all the regular operations fine, it is after continuous heavy use that you're experiencing freeze. 

Also, try using good brand USB, sometimes your generic ones have low compatibility with advanced use like Live booting. And also check ISO integrity, sometimes during download they can get corrupted, you should always check MD5 checksum.

Edit: Just to be sure and to eliminate possibility, keep an eye on your GPU usage, sometimes after use of long hours,  it may get overworked and heated and freeze your system on you if it is having compatibility issues. What GPU do you have? What drivers are you using? Is the kind of info you need to check.

---

### Post by ardouronerous on 2017-05-23
Okay, thanks for that info. Right now I'm two hours into using my LiveUSB, so far so good, no freezing.  I did check the hashes after downloading the Lubuntu iso, I also do. How do I check GPU  usage and what GPU I have?

---

### Post by LastDino on 2017-05-24
[https://askubuntu.com/questions/5417/how-to-get-gpu-info](https://askubuntu.com/questions/5417/how-to-get-gpu-info)

Bit old but commands work. Check if you have gpu which compatible, if it is third part like Nvidia, check what drivers are you using. If you want to install 3rd party in such a case, you might want to make USB persistent, as you will be saved trouble of installing it again on each boot up. That is if this is your problem, which is very faint possibility. I don't know any direct way to check gpu temp

---

### Post by dragonfly41 on 2017-05-24
GKrellM System Monitor with plugins might show GPU temp if nvidia-settings is installed.


[https://billw2.github.io/gkrellm/gkrellm.html](https://billw2.github.io/gkrellm/gkrellm.html)


> On Linux, you can also monitor disk temperatures from the hddtemp daemon and nvidia GPU temperatures if nvidia-settings is installed.

---

