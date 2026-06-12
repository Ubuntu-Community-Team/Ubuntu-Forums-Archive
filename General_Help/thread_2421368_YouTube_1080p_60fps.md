---
title: "YouTube 1080p 60fps"
date: 2019-06-20
forum: General Help
---

### Post by Shibblet on 2019-06-20
Whichever browser I use, seems to stutter the playback slightly, or sporadically in Kubuntu.

Firefox, Chromium, and Epiphany all seem to have this issue.

Any ideas?

---

### Post by CatKiller on 2019-06-20
Browsers on Linux often don't enable hardware acceleration for video decoding. There is a build of Chromium that does, though.

---

### Post by Shibblet on 2019-06-20
> **CatKiller said:**
> Browsers on Linux often don't enable hardware acceleration for video decoding. There is a build of Chromium that does, though.

I wondered if that wasn't the case.  Is there another app for viewing YouTube with that will playback video without stuttering?  And how do I get that build of Chromium?

---

### Post by CatKiller on 2019-06-20
> **Shibblet said:**
> I wondered if that wasn't the case.  Is there another app for viewing YouTube with that will playback video without stuttering? 
There are scripts and things for downloading stuff off YouTube, but I've not used them. 
> And how do I get that build of Chromium?

[https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html](https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html)

---

### Post by Claus7 on 2019-06-21
Hello,

something that I consider relevant is the speed of your network. It might be that this stuttering might be because of this. This you can verify using vlc as well: open vlc and then go to Media->open network stream... and paste the address of the 1080p 60fps video you have problems with. If the same happens with vlc then this eliminates the problem of browsers. One more thing I can think of is minor issue with your graphics card... 

Using ubuntu I might not be able to provide more info, yet vlc might provide you some insight to your issue.

Regads!

---

### Post by Shibblet on 2019-06-24
> **Claus7 said:**
> Hello,

something that I consider relevant is the speed of your network. It might be that this stuttering might be because of this. This you can verify using vlc as well: open vlc and then go to Media->open network stream... and paste the address of the 1080p 60fps video you have problems with. If the same happens with vlc then this eliminates the problem of browsers. One more thing I can think of is minor issue with your graphics card... 

Using ubuntu I might not be able to provide more info, yet vlc might provide you some insight to your issue.

Regads!

Hey, thanks Claus7 for the info.

I have a great internet connection (1 Giga-Bit), and my router is well equipped to handle it.

I am also a dual-booter, because I still use Adobe Software.  So, I tend to boot into Windows 10 every so-often to get some work done.

This isn't an issue in Windows 10 with Chrome, Edge, or Firefox.  But it is an issue in Kubuntu with Chromium, Firefox, and Epiphany.
I am going to try the Chromium Build that uses Graphic Acceleration, and see how that works.

At one time, there was a program called "Mini-Tube" (I think), that was a YouTube viewer.  I don't really need to download the videos, just watch them without screen tearing.  So, if there are any other programs out there that play you-tube videos with graphic acceleration, that would be fine too.

Any suggestions?

---

### Post by Claus7 on 2019-06-25
Hello,

> **Shibblet said:**
> 
I am going to try the Chromium Build that uses Graphic Acceleration, and see how that works.

... So, if there are any other programs out there that play you-tube videos with graphic acceleration, that would be fine too.

Any suggestions?

good luck with chromium build, yet have you checked vlc? You could check mpv player as well, which can be found in the repos...

Regards!

---

### Post by SeijiSensei on 2019-06-25
SMPlayer includes a companion application that will display YouTube videos called SMTube.  If you install it with the mpv engine, you might have better results than using a browser.

```
sudo apt install smplayer mpv
```

---

### Post by andraantariksa on 2019-06-25
> **Shibblet said:**
> This isn't an issue in Windows 10 with Chrome, Edge, or Firefox.  But it is an issue in Kubuntu with Chromium, Firefox, and Epiphany.
I am going to try the Chromium Build that uses Graphic Acceleration, and see how that works.

It should be fine for both OS though. I think you have problem with the driver or something, not the browsers.

Cheers.

---

### Post by oldos2er on 2019-06-25
> **andraantariksa said:**
> It should be fine for both OS though. I think you have problem with the driver or something, not the browsers.

Cheers.

Given the information [here]("https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html"), can you explain exactly what problems with the drivers you refer to?

---

### Post by oldos2er on 2019-06-25
> **andraantariksa said:**
> It should be fine for both OS though. I think you have problem with the driver or something, not the browsers.

Cheers.

Given the information [here]("https://www.linuxuprising.com/2018/08/how-to-enable-hardware-accelerated.html"), can you explain exactly what problems with the drivers you refer to?

---

