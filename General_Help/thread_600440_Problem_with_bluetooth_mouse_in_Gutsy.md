---
title: "Problem with bluetooth mouse in Gutsy"
date: 2007-11-02
forum: General Help
---

### Post by zilbere on 2007-11-02
Hello !
I tried to solve it myself - but now it is time to get your help.

I have Lenovo T60 laptop and Logitech V270 BlueTooth mouse.
In Windows XP mouse working 99% ok, 1% of time it has a lag while you move it.
In Gutsy it is working 50% and 50% have a lag.
In Windows I was able to solve the problem by changing priority for BT process.
In Linux I did not find a way to do that. I saw two processes related to BT :
[COLOR="Red"]root      5271  5264  0 14:19 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-input
root      5272  5264  0 14:19 ?        00:00:00 /usr/lib/bluetooth/bluetoothd-service-audio
[/COLOR]
But changing there priority did not help (I did renice with (-20) for process priority). 

I can probably accept that mouse is lagging when system is busy - but this happening when my T60 is idle - 10% of CPU only is used. RAM - 1.5GB is free.

So the question is :
Can I do anything about this ? Is there is a way to set high priority for BT ? 

Any ideas ?

Thank you,

---

### Post by gearshifter on 2007-11-26
since my upgrade to gutsy, I have been having really bad lag in my mx1000 bluetooth mouse.  Not sure if it's related to your issue or not.

---

