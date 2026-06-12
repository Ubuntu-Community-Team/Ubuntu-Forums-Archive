---
title: "Wine and Counter-Strike Source Low FPS and high CPU"
date: 2007-12-09
forum: General Help
---

### Post by TechnoJunky on 2007-12-09
really want to get CS:S working on my Linux box.  I have a 3.2GHz box with 1GB RAM, and a Nvidia 7600 with 512 MB Ram.  Originally I was using Wine ver. 0.9.46 and the Kubuntu supplied propriatary video driver.  I downloaded and installed Steam, then downloaded CSS.  I had 100% CPU utilization while playing and FPS at about 20.  I deleted the CSS directory, and copied the one from my WIndows drive and thing improved some.  Currently when I try running CSS I get 20-50 FPS, fluctuating between while playing, and the CPU fluctuating between 30-80% utilization. Next I updated Wine to ver 0.9.50 and  Nvidia video driver version 100.14.23.  Still my FPS and CPU are the same.  I have lowered all the settings inside of CSS (i.e. Model detail=med, texure detail=medium, shader=low, water=simple, shadow=low, color=enabled, anti-alias=None, Filtering=Trilinear, wait for vsynch=disabled, High Dynamic Range=Full).  Hardware and Software=DirectX v9.0.  Any tips would be greatly appriciated.  If I could get CSS going on my Linux box then I don't think I'd have anything to dual boot for anymore.

---

### Post by blazercist on 2007-12-09
Questions about running application under wine should be posted on winehq.org in the AppDB in the appropriate game section.  I too use wine to run CS:S and get poor FPS.  I don't think there is much that can be done about it.  Try to lower your DX level and try disabling HDR and lowering the video settings.  I doubt that it will help much but hey its worth a try.  Also If you are using a compositing manager such as Compiz or Beryl then you should turn that off.

---

### Post by oodledoodle on 2007-12-09
css by default attempts to use as much cpu as possible in windows. maybe its doing the same thing via wine, i'm not sure. but i know that using as much cpu as possible is normal css behavior.

---

### Post by TechnoJunky on 2007-12-10
No I don't use Compiz or Beryl anymore.  Previously I had a Fedora build on my comp and I was using Cedega, emulating Win98 and running CS:S just fine.  The reason I don't use Cedega anymore is because Steam dropped Win98 support and I couldn't get it to work emulating any other ver of Windows.  Using Cedega, frame rate was lower than it was on my Windows box but it wasn't aweful, and it was consistant.  it's the inconsistant frame rate that I'm getting now makes for some bad lag spikes.

---

### Post by mikibg on 2008-01-01
i have same problem but not with fps . here is Q6600 and nvidia 8600 gts ,,,cpu is so high, fps 100.
hm????
look picture
[[IMG]http://img231.imageshack.us/img231/9712/86197881tk6.th.jpg[/IMG]](http://img231.imageshack.us/my.php?image=86197881tk6.jpg)

---

### Post by l_ballbag on 2008-02-05
Probs here too - I have an AMD Athlon Dual Core 6000+, 2GB DDR2 800MHz C4 and an nVidia 8800GTS 650MB, running Ubuntu 7.10GG with inbuilt visual desktop effects turned off. I'm running Wine version 0.9.54. Getting less than 20fps so haven't bothered playing thru wine... sad coz I really want to ditch as much of WinXP as I can... any help appreciated.

---

### Post by advilandy on 2008-06-18
same problem and my game crashes at server connect (while loading the webpage for a server)

---

