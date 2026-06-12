---
title: "How to burn DVD's?"
date: 2007-12-18
forum: General Help
---

### Post by benniebrown07 on 2007-12-18
I have a dvd burner it works I know becuase Ive burned cd's and I copied my Linux cd but I cant figure out how to burn dvd's. I have mplayer, devede, cucsoft mepg/avi/ogg burner, smart dvd creator, and even nero 8 express/rom burner, the list goes on. The problem is, I've used a couple of different programs over time ive picked up on the process a little can someone explain it to me and help me with some software. When i say the process Im talking about you have to transcode it put it in the right format and run it through all thesse programs just to get it to burn. With my cousins pc all we do is pick the file use roxio and burn simple but mines is a different thing. Any advice will be greatly appreciated. Thanks in advance.

---

### Post by HermanAB on 2007-12-18
Use Mandriva's K3B.  It should be in Synaptic.

Cheers,

Herman

---

### Post by benniebrown07 on 2007-12-18
I think I do have K3b already but prolly havent used it yet neway will it run the whole process of transcoding or whatever and burning it to dvd with out having to use another program?

---

### Post by ugm6hr on 2007-12-18
> **benniebrown07 said:**
> The problem is, I've used a couple of different programs over time ive picked up on the process a little can someone explain it to me and help me with some software. When i say the process Im talking about you have to transcode it put it in the right format and run it through all thesse programs just to get it to burn. 

You need to be clear about exactly what you are trying to do.  Are you trying to create a Video DVD (to play on a regular DVD player) from various video files, or simply trying to put files on to a DVD-R?

If the former, what format are the video files in?

I have created a Video DVD from multiple .avi (divx) files with DeVeDe and GnomeBaker.

---

### Post by stchman on 2007-12-18
K3B is the best CD and DVD burning app for Ubuntu.  It does video and data DVDs.  It also makes audio CDs.  Gnombaker is good but K3B is better.  When you install K3B use the following line:

```
sudo apt-get install k3b libk3b2-mp3
```

This will install the mp3 plugin as well to create an audio CD from MP3s.

---

