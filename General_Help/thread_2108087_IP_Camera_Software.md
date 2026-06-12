---
title: "IP Camera Software"
date: 2013-01-23
forum: General Help
---

### Post by x C0MMAND0 x on 2013-01-23
I'm looking for some software that will allow me to do the following:

1 - Connect to IP cameras at various locations (I know how to setup all of the port forwarding and everything - I just need software that doesn't requre to be ran locally

2 - Software that ideally has the ability to record video/do motion capture

3 - Software that has the ability to send out alerts via email or SMS

I have found Windows software that does this quite easily, but I am wondering about some Linux software that is ideally free.

---

### Post by alphacrucis2 on 2013-01-23
A quick google search turned up this:

[http://www.zoneminder.com/](http://www.zoneminder.com/)

I can't say if it is any good as I haven't tried it


Edit:

Looks like it is in the universe repo:

[http://packages.ubuntu.com/search?keywords=zoneminder&searchon=names](http://packages.ubuntu.com/search?keywords=zoneminder&searchon=names)

---

### Post by x C0MMAND0 x on 2013-01-23
Thank you for the info - I did come across that before, but the major issue is that is designed for CCTV systems - which my understanding means closed circuit IE local network.

I need to be connecting to monitor different sites (5-10 with multiple cameras at each location - all feeding back to a central location that is not onsite, IE not CCTV.

I haven't looked into it and I could definately be wrong in my understanding.

---

### Post by alphacrucis2 on 2013-01-23
> **x C0MMAND0 x said:**
> Thank you for the info - I did come across that before, but the major issue is that is designed for CCTV systems - which my understanding means closed circuit IE local network.

I need to be connecting to monitor different sites (5-10 with multiple cameras at each location - all feeding back to a central location that is not onsite, IE not CCTV.

I haven't looked into it and I could definately be wrong in my understanding.

The wiki for the zoneminder says it supports network cameras as long as they stream mjpeg. There is a list of tested network cameras in the wiki:

[http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List](http://www.zoneminder.com/wiki/index.php/Hardware_Compatibility_List)

---

### Post by matt_symes on 2013-01-23
Hi

I set up something similar on a Windows box using iSpy and WatchBot cameras. We were able to view the video feed on a smartphone.

As the previous poster suggested, i think zoneminder should work for you if it handles streaming network webcams and you have enough bandwidth.

There is also motion but i have used neither motion or zoneminder.

Kind regards

---

