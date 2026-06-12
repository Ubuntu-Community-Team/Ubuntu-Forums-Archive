---
title: "Ubuntu does not recognize 7.1 channels"
date: 2017-05-06
forum: General Help
---

### Post by offir on 2017-05-06
Hope this is the right forum for the question


I have a Pioneer receiver Model vsx-ax5i [http://www.pioneer-latin.com/downloads/arb7286a.pdf]("http://www.pioneer-latin.com/downloads/arb7286a.pdf")
I want to connect it to the computer
It's a 7.1-channel receiver
It has a USB connection
So I connected it to the computer using a USB cable
Ubuntu 16.04 recognizes the AVR as a [COLOR="#0000FF"]Texas Instruments PCM2902 Audio Codec[/COLOR]
I have no option to choose 7.1
Just a stereo or mono

Before installing Ubuntu 16.04
I had Ubuntu 15.10 or 12.04
And they did recognize the AVR as multichannel

---

### Post by mörgæs on 2017-05-07
A bug might have been introduced in 16.04 (just guessing here, don't know for a fact). 
If so then it's worth a try to see if it's fixed in later releases. How does it work in a live boot of 17.04?

---

### Post by offir on 2017-05-07
> How does it work in a live boot of 17.04? 
didnt try that
will try now

---

### Post by offir on 2017-05-07
After restarting the computer
This line appears
Is the pl3.5 port
Can also output digital signal ?

---

### Post by offir on 2017-05-08
Is there software that allows more settings for sound card ?

---

### Post by mörgæs on 2017-05-08
> **offir said:**
> 
Can also output digital signal ?

Yes, it looks like 17.04 gives both analog and digital where 16.04 only gave analog. I would try installing 17.04 for comparison, maybe in a dual boot.

I am not an expert in sound matters, though. If anyone is then feel free to contribute.

---

### Post by oldrocker99 on 2017-05-08
> **offir said:**
> Is there software that allows more settings for sound card ?


PulseAudio Volume control will do that.```
sudo apt install pavucontrol
```

---

### Post by offir on 2017-05-08
> 
Yes, it looks like 17.04 gives both analog and digital where 16.04 only gave analog
I have not yet reached the stage of trying to run Ubuntu 17.04 from a startup disk
This image from 16.04


> 
PulseAudio Volume control will do that.


```
sudo apt install pavucontrol
```



I installed the software and it shows me these options
Only I do not have this connection on my computer (s/pdif)

---

