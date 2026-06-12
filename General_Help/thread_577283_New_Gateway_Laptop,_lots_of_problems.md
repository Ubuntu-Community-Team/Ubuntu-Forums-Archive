---
title: "New Gateway Laptop, lots of problems"
date: 2007-10-16
forum: General Help
---

### Post by bg1256 on 2007-10-16
I just purchased a new Gateway MT 3423 laptop today, and I've got a host of problems after a new install of Feisty.

1. Wireless card does not work, and I can't even figure out what wireless card it has!  According to Gateway's website, it looks like a bcm4318, but none of the commands I've run show anything like that - only the realtek controller shows up.

2. I have no sound. BUT, I did have sound when using the Live CD!

3. I cannot manually dim or brighten my screen.  When I unplug the laptop, the screen dims, but fn+up or down arrow doesn't work.

4. Suspend and hibernate do not work.

The question is, can anyone point me in the right direction?  I'm not even really sure where to look... I really want to use Ubuntu as my primary OS, and if I can't get this stuff figured out, there is a really good chance I could bring this laptop back to Circuit City and buy something different.

Here is a link to the manufacturerer's website that may help someone more knowledgeable than me to make sense of things:
[http://support.gateway.com/s/Mobile/2007/Apache/1014654R/1014654Rnv.shtml](http://support.gateway.com/s/Mobile/2007/Apache/1014654R/1014654Rnv.shtml)

Thanks for any help you could give!

---

### Post by swisscow on 2007-10-16
If it makes you feel any better I bought a Sony Vaio, had a load of similar problems - sold it on ebay a week later (actually for the same amount I paid for it which was nice). It was a big mistake, impulse buy and all that and the lesson I learnt is research before you buy.

If you can't solve your problems, I say take it back.

Sorry not to be more helpful

---

### Post by bg1256 on 2007-10-16
That's okay.  It's not quite what I was hoping for, but it's something.

---

### Post by bg1256 on 2007-10-16
It seems like I have made at least some progress:

I still don't know where to find sound drivers.

But, I determined what my wireless chip was: RTL8185L (produced by realtek).

The windows drivers download page is here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8185L)

Does anyone know how to install this via ndiswrapper?

---

### Post by miguelcs on 2007-10-18
Hi,

I purchased a Gateway ML3109 from Best Buy last friday, now I'm happily running Ubuntu and I succeed in setting wireless and sound up. I'm just getting into Linux world, so I'm not very experienced.

I think you should check this page

[http://donnieknows.com/bin/view/Main/GatewayML3109](http://donnieknows.com/bin/view/Main/GatewayML3109)

first wireless didn't work, until I used wifi-radar.

luck

---

### Post by bg1256 on 2007-10-19
Thanks much!  I am travelling for th week and simply don't have time to apply those instructions right now - plus I only have wifi access for the next week.  And since wifi isn't working right now, well, you get the point.

I appreciate you taking the time to post this for me.  I wll have a look at it next week!

---

### Post by kdladage on 2007-10-29
> **miguelcs said:**
> Hi,

I purchased a Gateway ML3109 from Best Buy last friday, now I'm happily running Ubuntu and I succeed in setting wireless and sound up. I'm just getting into Linux world, so I'm not very experienced.

I think you should check this page

[http://donnieknows.com/bin/view/Main/GatewayML3109](http://donnieknows.com/bin/view/Main/GatewayML3109)

first wireless didn't work, until I used wifi-radar.

luck

Followed the instructions as presented to the letter... now the machine no longer knows it has sound capabilities (i.e.: I try to adjust volume and it tells me that no devices that can have the volume adjusted exist in the computer) and the boot up takes over 9 minutes to complete (UUID issues). In other words, it made things worse.

Just completed re-installing VISTA on the laptop. I am not happy, I have to say...

I will most likely be returning this laptop.

---

### Post by headtowall on 2007-10-29
Oh man, don't give up.  I just purchased a Gateway model very close to the one that you have.  I just installed Ubuntu 7.1 and dual boot with Vista Home Premium.  My installation process went fine, but I can't get the thing to connect to my wireless network.  Just freezes up when logging in.  Totally frustrating.  I really just thought that I would be able to install and go.

I spent the weekend searching for how fix these problems.  I haven't tried the instructions that these people have posted in this thread yet, but I am really looking forward to it.

Hang in there.  Let me know if I can help or try or something out.  I really won't get a lot of time until the weekend to really dig in.  But I am collecting information for my all out assault on my 'Bu.

---

### Post by bg1256 on 2007-10-29
You should tr wicd for wireless. 

If you search the forums, you'll get all the info you need.

---

### Post by lvleph on 2007-11-19
Gateway is clueless about their own hardware. I had a long discussion with them about their wireless card. They insisted it was Broadcom, but it is most definitely Realtek. I too am having the freezing problem when connecting to wireless. I know that wireless works in 6.10. They changed the wireless network manager and that is when all my wireless problems began. I have never once gotten the sound to work yet, but wireless is more important to me. So I have not even tried the sound in 7.10.

---

### Post by bg1256 on 2007-11-19
I've actually given up hope for this particular machine.  

I am only going to try two more linux ideas:

Install Open SuSE.

Try running Ubuntu using VMware from Vista.

For me, it's just not worth the hassle.

Ah well, at least the desktop is still running smoothly... except for open office not working.

---

### Post by borris.morris on 2007-12-02
I have sound working on my MT3418 (I think)... and Wi-fi too! I use ndiswrapper, but version 1.39. it works like a charm with Wicd!

---

### Post by bg1256 on 2007-12-02
If it's not too much trouble: how did you get sound working, Borris?

---

### Post by borris.morris on 2007-12-02
2. go to [www.alsa-project.org](www.alsa-project.org) and download these files :
alsa-driver-1.0.15rc1.tar.bz2
alsa-lib-1.0.15rc1.tar.bz2
alsa-utils-1.0.15rc1.tar.bz2

Open a terminal and type : sudo -i then make a directory called alsa into /usr/local/src. Copy the files to this directory and unpack them (tar xjvf alsa-... for every file).

3. go to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036) and download the file patch_sigmatel.c.patch-1.0.15rc1-simple. Copy the patch to /usr/local/src/alsa.

4. type this :
patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple.

5. do this:
cd alsa-lib-1.0.15rc1/
./configure && make && make install
cd ../alsa-utils-1.0.15rc1/
./configure && make && make install
cd ../alsa-driver-1.0.15rc1/
./configure && make && make install

If the configure script complains about missing some libraries yum for them and try again.

6. reboot

---

