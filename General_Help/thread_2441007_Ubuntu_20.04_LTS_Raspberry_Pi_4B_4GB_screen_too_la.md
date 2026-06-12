---
title: "Ubuntu 20.04 LTS Raspberry Pi 4B 4GB screen too large to fit tv"
date: 2020-04-17
forum: General Help
---

### Post by ibrahimk157 on 2020-04-17
Hello,

Ever since I bought my raspberry pi 4B, i noticed an issue with the screen being too big to fit my tv and ends up being cut off from the edges (this was not an issue with my 3B+). However, on raspbian, adding “dtoverlay=vc4-fkms-v3d” to config.txt did the trick.

But, with Ubuntu 20.04 LTS, doing the same didn’t seem to work at all. Same goes with adding “disable_overscan=1” to the usercfg.txt (same outcome using config.txt even though for ubuntu it clearly says to not modify config.txt and use usercfg.txt instead).

I tried everything I could possibly find online to no avail. 

Here’s my current setup:

Raspberry Pi 4B 4GB RAM (first version)
64GB SANDISK A2 SD Card
Ubuntu 20.04 LTS (64-bit ARM) from here: ([http://cdimage.ubuntu.com/ubuntu-server ... EADER.html]("http://cdimage.ubuntu.com/ubuntu-server/daily-preinstalled/current/HEADER.html"))
1920x1080 TV (with no setting for overscan... i tried every one of its few settings and none have anything to do with overscan... i even tried all the hdmi ports)

I’m looking forward to your help 

Thanks

---

### Post by CelticWarrior on 2020-04-17
Welcome.

Do yourself a favor and set it directly on the TV. Any modern TV as in from the last 15 years or so has several screen modes. One of them works for computers and similar devices while others work better for different types of cable TV boxes.

---

### Post by ibrahimk157 on 2020-04-17
> **CelticWarrior said:**
> Welcome.

Do yourself a favor and set it directly on the TV. Any modern TV as in from the last 15 years or so has several screen modes. One of them works for computers and similar devices while others work better for different types of cable TV boxes.

As I’ve mentioned in my post, mine does not have that option. I went through all of its very limited settings and tried them one by one. None of which would disable overscan. Even trying all the hdmi ports didn’t seem to do it.

---

### Post by CelticWarrior on 2020-04-17
Wanna bet? Many in the past said the exact same thing and I always found out where and how, even in models I have never heard of before, just by checking online user's manuals and/or pictures of the remote.

Please post your exact brand and model of your HD TV. We'll see...

---

### Post by DuckHook on 2020-04-17
Welcome to the forums, ibrahimk157

Please do not use non-standard fonts or formatting. It is difficult to see on some monitors and for those using mobile devices.

---

### Post by ibrahimk157 on 2020-04-18
> **CelticWarrior said:**
> Wanna bet? Many in the past said the exact same thing and I always found out where and how, even in models I have never heard of before, just by checking online user's manuals and/or pictures of the remote.

Please post your exact brand and model of your HD TV. We'll see...

here you go:

Supra 32” LED TV 
Model: SLED32OT9001R

(Yes I know, it’s probably a brand you never heard of before)

---

### Post by ibrahimk157 on 2020-04-18
> **DuckHook said:**
> Welcome to the forums, ibrahimk157

Please do not use non-standard fonts or formatting. It is difficult to see on some monitors and for those using mobile devices.

thank you!

the reason why the font is all messed up is because I actually typed this in the raspberry pi forums (it looked normal there) as well and just copy pasted because I’m lazy. I tried using the formatting tools here to get it to look normal but couldn’t figure it out. Apologies.

---

### Post by CelticWarrior on 2020-04-18
> **ibrahimk157 said:**
> here you go:

Supra 32” LED TV 
Model: SLED32OT9001R

(Yes I know, it’s probably a brand you never heard of before)

True, never heard of it but probably a rebranded Sansui. If so, in the OSD menus you should have a menu section for Picture > Picture size. Select "Full" (or try the other options).

---

### Post by ibrahimk157 on 2020-04-18
> **CelticWarrior said:**
> True, never heard of it but probably a rebranded Sansui. If so, in the OSD menus you should have a menu section for Picture > Picture size. Select "Full" (or try the other options).

I’ve already tried fiddling with these... to no avail 

there are three options:

full -> the default and still has the issue
16:9 -> acts exactly the same as full
4:3 -> the picture becomes quashed from the sides with huge black bars from each side, and the screen is still chopped off from all sides even though the sides are empty. And you can tell that it’s squashed.

---

### Post by ibrahimk157 on 2020-04-18
I just discovered something 

when going to the display settings in ubuntu, and changing to any (4:3) resolution, all of a sudden everything fits perfectly on the tv. The issue is that everything becomes huge and the resolution turns into crap. Usable but nowhere close to ideal.

---

### Post by ibrahimk157 on 2020-04-18
I figured it out!

while looking at the usercfg.txt, I remembered something.

The guide that I used to install ubuntu desktop 20.04LTS from the Ubuntu server image mentioned adding the following to the usercfg.txt to set the resolution to 1080p:

```
hdmi_group=2
hdmi_mode=82
```

So I thought I’d try removing that... and sure enough, that fixed it!

Then I added:

```
hdmi_group=1
hdmi_mode=16
```

And when i tried that, i no longer get the issue!

No clue what’s different between the two hdmi groups that will make group 1 work but group 2 cause the issue.

---

### Post by DuckHook on 2020-04-18
> **ibrahimk157 said:**
> …No clue what’s different between the two hdmi groups that will make group 1 work but group 2 cause the issue.
This might help: [https://www.raspberrypi.org/documentation/configuration/config-txt/video.md](https://www.raspberrypi.org/documentation/configuration/config-txt/video.md)

Especially this part:
> The hdmi_group command defines the HDMI output group to be either CEA (Consumer Electronics Association, the standard typically used by TVs) or DMT (Display Monitor Timings, the standard typically used by monitors). This setting should be used in conjunction with hdmi_mode.

```
hdmi_group 	result

0 		Auto-detect from EDID
1 		CEA
2 		DMT
```
Depending on your TV, you may also want to look at the hdmi_mode settings and define one that better conforms to your res/freq/aspect_ratio.

---

### Post by ibrahimk157 on 2020-04-18
> **DuckHook said:**
> This might help: [https://www.raspberrypi.org/documentation/configuration/config-txt/video.md](https://www.raspberrypi.org/documentation/configuration/config-txt/video.md)

Especially this part:

Depending on your TV, you may also want to look at the hdmi_mode settings and define one that better conforms to your res/freq/aspect_ratio.

thanks a lot! That explains it quite well!

---

### Post by DuckHook on 2020-04-18
It is I who must thank you. Without your thread, I would never have bothered researching this. I also have a RPi 4B+ and have been having a devil of a time trying to get Focal to properly display on a 4K monitor. I'm going to try implementing some of the stuff on that reference page now. You also saved me a ton of blood, sweat and tears by pointing me to usercfg.txt

Would you kindly provide the path to this file?

---

### Post by ibrahimk157 on 2020-04-18
> **DuckHook said:**
> It is I who must thank you. Without your thread, I would never have bothered researching this. I also have a RPi 4B+ and have been having a devil of a time trying to get Focal to properly display on a 4K monitor. I'm going to try implementing some of the stuff on that reference page now. You also saved me a ton of blood, sweat and tears by pointing me to usercfg.txt

Would you kindly provide the path to this file?

you’ll find it in /boot/usercfg.txt

however, i suggest popping your microsd card into a microsd reader and plugging it onto a pc, from there you’ll find a “system-boot” partition that displays as a plugged in drive, there you can also find the usercfg.txt file which makes it even easier to modify. 

I’m glad this is actually helping someone!

---

### Post by DuckHook on 2020-04-18
> **ibrahimk157 said:**
> you’ll find it in /boot/usercfg.txt
Thanks!
> however, i suggest popping your microsd card into a microsd reader and plugging it onto a pc, from there you’ll find a “system-boot” partition that displays as a plugged in drive, there you can also find the usercfg.txt file which makes it even easier to modify.
Excellent suggestion!
> I’m glad this is actually helping someone!
The power of the community…

Hope you stick around and find more useful stuff. That's how I started my journey to participating long-term on these forums.

---

### Post by ibrahimk157 on 2020-04-19
> **DuckHook said:**
> Thanks!

Excellent suggestion!

The power of the community…

Hope you stick around and find more useful stuff. That's how I started my journey to participating long-term on these forums.

It is indeed the power of the community!

I would love to stick around and be a full-time contributor, but I’m currently extremely busy, making it nearly impossible. Definitely something I’d consider in the near future though!

---

