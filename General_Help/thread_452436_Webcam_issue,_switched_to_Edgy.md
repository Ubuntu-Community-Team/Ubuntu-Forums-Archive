---
title: "Webcam issue, switched to Edgy"
date: 2007-05-23
forum: General Help
---

### Post by SirPaPa on 2007-05-23
Okay, first let me say that Fiesty is a great distro. With the exception of not being able to run my Creative Live! webcam, even though I could see it in the Multimedia Systems Selector video input test. 

 You see, that's what I don't understand. I could see myself on the test video input, but when I opened up Camorama it displayed a distorted image of my desktop wallpaper.

 I noticed the Camorama window title border said  " Camorama - AverTv Go 007 FM Plus ". I guess it was trying to access my tv card instead of my webcam.](*,)

 I love Fiesty, now more than ever since I discovered  VMware and how well it worked in my system. But I really need that webcam support. 

Now I'm on Edgy and I can't get VMware to work on it, but the webcam works. If I could only get Fiesty back with Camorama working correctly.

 Any ideas as to why it would be noticed by the Multimedia Systems Selector app and not by Camorama?
 
And if not, why would my install of VMware  on my current version of Ubuntu(Edgy)not fire up after it said  VMware install completed successfully?

I hope one of you fellow Ubuntuers  can help me with this.:(

Thank you.

The screenshot below shows the message I got when I fire up the VMware console on Edgy.(my current Ubuntu)

---

### Post by reclusivemonkey on 2007-05-23
Camorama will take the first video device it finds, which is /dev/video0. If this is your TV card, then that's what it will show. If your webcam is on /dev/video1, just use

```

camorama -d /dev/video1

```

---

### Post by SirPaPa on 2007-05-23
> **reclusivemonkey said:**
> Camorama will take the first video device it finds, which is /dev/video0. If this is your TV card, then that's what it will show. If your webcam is on /dev/video1, just use

```

camorama -d /dev/video1

```

Thank you reclusivemonkey, I will try that. Now I will reboot using the live cd as I've already install Edgy but I hope it works I would rather use Fiesty.

I'll be back in a few minutes.

---

### Post by SirPaPa on 2007-05-23
> **SirPaPa said:**
> Thank you reclusivemonkey, I will try that. Now I will reboot using the live cd as I've already install Edgy but I hope it works I would rather use Fiesty.

I'll be back in a few minutes.

It worked. I truly appreciate your help. One thing though, I'm using the Fiesty live cd. Will I have to run that code every time I open Camorama?
 
When I closed the terminal and opened Camorama again it didn't work.
 
Is there a way to have Camorama detect the webcam always?

Thank you, very much.

BTW  using  Fiesty live cd right now.

---

### Post by reclusivemonkey on 2007-05-23
Yes, you will need to use that every time. However, you can do this easily in two ways;

[LIST=1]
[*]If you start camorama from the Applications menu, just add it to the Properties of Camorama (System --> Preferences --> Main Menu)
[*]If you start camorama from the terminal, in your ~/.bashrc, add;
```

alias camorama='camorama -d /dev/video1'

```
[/LIST]

Ah just thought this might not work if you are using the LiveCD. Once you install Feisty again though it will work.

---

### Post by SirPaPa on 2007-05-23
> **reclusivemonkey said:**
> Yes, you will need to use that every time. However, you can do this easily in two ways;

[LIST=1]
[*]If you start camorama from the Applications menu, just add it to the Properties of Camorama (System --> Preferences --> Main Menu)
[*]If you start camorama from the terminal, in your ~/.bashrc, add;
```

alias camorama='camorama -d /dev/video1'

```
[/LIST]

Ah just thought this might not work if you are using the LiveCD. Once you install Feisty again though it will work.

I added the command - "camorama -d /dev/video1" to Camorama's properties- command  using System --> Preferences --> Main Menu as you suggested, and it worked even on the live cd.

Now I just click Camorama on the Applications menu and it works fine.

I sincerely thank you reclusivemonkey, you have given back Fiesty with webcam support under Camorama.:D

---

