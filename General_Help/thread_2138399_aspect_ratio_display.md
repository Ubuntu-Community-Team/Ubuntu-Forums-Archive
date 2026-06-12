---
title: "aspect ratio display"
date: 2013-04-23
forum: General Help
---

### Post by rolfUser on 2013-04-23
I have this strange problem with my computer.
I have Ubuntu 12.04 installed on my PC and I notice how the aspect ratio is 4:3. Under Settings, I check Displays and see that only two configurations are available and they are both 4:3 resolutions. Isn't there also supposed to be a 16:9 aspect ratio?
My monitor is actually an hdtv with tv, video, hdmi, and vga outputs. The VGA is the one I use to use the computer.
So what I am curious to know is why I cannot get a 16:9 aspect ratio, and if it is possible, how do I get the 16:9 aspect ratio?

---

### Post by Impavidus on 2013-04-24
I once had a similar problem on my laptop, not connecting to a TV but with the 16:9 screen fixed at 4:3 aspect ratio, giving an ugly, stretched image. It was solved by upgrading from 10.04 to 11.04, then the latest version, which contained the drivers for my hardware. So if you've got some recent hardware you may want to try switching to 12.10 or 13.04 (will be released in a few days). Or check for available proprietary drivers. Depends on your graphics hardware.

---

### Post by rolfUser on 2013-04-27
Okay. I'm willing to upgrade if it may improve the situation. It sounds exciting.  But one question: Are there any precautions I should take? 

When switching from Windows XP to Ubuntu 12.04, I needed to extract all of my files to this huge 35gb usb drive and then put the files back in after installation was complete.

---

### Post by Impavidus on 2013-04-28
You switched from win XP to Ubuntu? In that case you probably don't have very recent hardware, so upgrading is not very likely to help (if you wish, you can upgrade, but it may be easier to stay with the LTS release). Can you tell us exactly what hardware is in that computer? Specifically the video card? And did you install proprietary drivers?

---

### Post by Yellow Pasque on 2013-04-28
Post your /var/log/Xorg.0.log

---

### Post by rolfUser on 2013-05-02
Well I'm not that savvy with computers. I can tell you that this computer is roughly 13 or 14 years old or maybe older and it is from HP.
A sticker on the front of the motherboard reads, "Pentium 4". 

I'm not sure how to answer the question about the video card on the pc, or proprietary drivers.
[COLOR=#000000]/var/log/Xorg.0.log  ______   I don't understand that either.[/COLOR]

---

### Post by Impavidus on 2013-05-02
That's an old one.

Concerning the Xorg.0.log, you can add an attachment to your post. Just navigate to /var/log/Xorg.0.log, which is a file somewhere on your system, and attach it.

Entering the command```
lspci | grep VGA
```(copy-paste to a terminal) should give us the graphics controller of your machine. It may be too old for current Ubuntus.

---

### Post by rolfUser on 2013-05-10
[FONT=book antiqua]Using Ubuntu 12.04 LTS, I looked up File System, selected **var** folder, then **log** folder, and found **Xorg.0.log** file which opened in gedit. 
**Xorg.0.log** is a big long document filed with hard data.   I don't know what to make of any of it. 

What am I looking for? 
[/FONT][FONT=book antiqua]What does[/FONT] [COLOR=#000000][FONT=Ubuntu Mono]lspci | grep VGA [/FONT][/COLOR]mean?

---

### Post by rolfUser on 2013-05-10
More importantly, how do I know I am not unknowingly giving away my IP Address when I attach this file? I want to know.

---

### Post by Impavidus on 2013-05-10
In the Xorg.0.log we are mostly interested in any statements on monitors and drivers. During boot, Ubuntu detects monitors and loads drivers. Something goes wrong there. The Xorg.0.log file doesn't contain your IP address, which is already known to every website you ever visited, but it does contain detailed info on your hardware and kernel and the name you gave to your computer. This is not enough information to hack your machine. To be sure, you can always edit the file before you send it.

The **lspci | grep VGA** command consists of two parts. The first part, before the |, lists information about your hardware as it is recognised by your system, the second part filters that information to keep only the lines containing "VGA", listing information on your graphics.

---

### Post by Yellow Pasque on 2013-05-10
Extracting information from some people is like pulling teeth..

---

### Post by rolfUser on 2013-05-24
Hang on. I just prefer to devote my UNDIVIDED attention to what I do.
Now that I am here, I have another question before I share that file.
By sharing this information, File:** log/var/Xorg.0.log**,  does it mean that a solution to my aspect ration problem would be as straight-forward as editing the file? 

Why should I talk about it? All I need is a new motherboard, right?
But when this same PC ran on Windows XP, it did used to have the 16:9 aspect ratio option. That is true. I did not mention that before.

---

### Post by Yellow Pasque on 2013-05-25
Nvm: I've lost patience for you to post a simple log, and I'm unsubscribing from this thread. Hopefully, someone else can help you...

---

### Post by Impavidus on 2013-05-25
(Sigh) I've got the same feeling.

It may be that you don't have the right drivers for your video card, or that for some reason the OS is not able to find the supported resolutions. Maybe you can force the resolution anyhow. I think there are some threads about that. Log files may tell it.

But frankly, I would get an old 4:3 monitor from somewhere if I liked to play with that old box and get a somewhat more modern computer for daily stuff. Even a five year old second hand one will do fine for Ubuntu. You can get those almost for free.

---

### Post by rolfUser on 2013-05-30
What I am going to take from this is that this is a rather serious, very active, and very intelligent community.
Also, I actually tried to upload the file and received an error message saying that it isn't valid.
I could just paste the data, but I need to make sure someone is willing to read it.

---

