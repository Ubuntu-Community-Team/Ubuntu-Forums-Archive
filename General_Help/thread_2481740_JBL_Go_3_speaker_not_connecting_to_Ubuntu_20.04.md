---
title: "JBL Go 3 speaker not connecting to Ubuntu 20.04"
date: 2022-12-07
forum: General Help
---

### Post by carega on 2022-12-07
Hi!

I acquired a new laptop some months ago and have happily been using  Ubuntu 20.04 but I've encountered a recent problem... My JBL Go 3  speaker is not connecting to the computer through bluetooth. I've read  that I could disconnect the Wifi and it did help but now it doesn't  connect at all. And when it does it works fine for a while but all of a  sudden the sounds begin to be all choppy (as if the connection was not  good) even when the speaker is right in front of the computer. If I  disconnect the device there's not way it will connect again.

Can anyone guide me on what's actually going on and if there's a way to  fix this? The speaker is not the problem at all, it connects fine to my  cellphone and my work computer. Other devices are not connecting through bluetooth either :(

Thanks in advance for your help! Let me know what you need from me.

---

### Post by tivp on 2023-03-07
:popcorn:

---

### Post by tivp on 2023-03-07
Hi carega ):P, I had a similar thing happen with a JBL GO2. I finally solved it by installing ```
**sudo apt install rfkill**
``` and using the command ```
**sudo hciconfig hci0 reset**
```
Once rfkill is installed you will be able to see if a device is locked with the command ```
**sudo rfkill list**
```
If you see that a bluetooth device is locked enter the locked number at the end of the following command e.g. ```
**rsudo rfkill unblock 7** 
``` in case number 7 is locked.

:KS Nice weather.

---

