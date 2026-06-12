---
title: "22:04 1 LTS ifi &amp; Wired Network Problem"
date: 2022-11-13
forum: General Help
---

### Post by Ignorance Isnt Bliss on 2022-11-13
Hi All,
On Friday I was unable to connect to the internet using Ubuntu 22:04 1 LTS. I assumed it was my router and restarted it which made no difference and my wife pointed out she had an internet connection. I noticed I had a full wife signal and when I used an ethernet cable I got the wired connection signal. If I look at either wifi or wired connection in setting it tells me I have a connection.
After Googleing a bit I thought I could reinstall drivers and following the step by step I guide I failed to be able to get my computer to mount a USB stick using the sudo mount -t loop /media/cdrom command.
Now I am very limited in my computing knowledge and was never sure reinstalling drivers was the way to go and have no idea why I can't mount the USB stick with an ISO image on it. I tried when in my home directory and also when in media/cdrom but still no joy.
So basically I have two problems:-
1. Why do I have a connection but cannot open a web page, download an email or even open up the Software Centre.
2. Why can't I mount my USB
I'd be happy if I could answer even the first of these questions.
Any help would be much appreciated

---

### Post by Ignorance Isnt Bliss on 2022-11-13
**Sorry please disregard my question. It turned out to be a Proton VPN bug. solved with **sudo nmcli connection delete pvpn-ipv6leak-protection  **Just for the record**

---

