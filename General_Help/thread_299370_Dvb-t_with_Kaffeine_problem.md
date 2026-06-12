---
title: "Dvb-t with Kaffeine problem"
date: 2006-11-14
forum: General Help
---

### Post by aum11 on 2006-11-14
Have been trying to get digitalnow tinyusb dvb-t (twinhan) working with kaffeine under 6.10.

Kaffeine seems to recognise it but I cannot locate any channels.

Maybe I have not set it up correctly.  Any advice?

Thanks.

---

### Post by aum11 on 2006-11-14
Anybody experienced in this?
.
Thanks

---

### Post by RikoW on 2006-11-14
I assume, you did perform a channel scan in kaffine using the location appropritate for where you are?

I had the problem, that kaffeine would only find very few channels when scanning when using the dingy-little antenna which came with my DVB-T card. After I plugged in a biggeer one with an amplifier, I found plenty.

Cheers,

             Riko

---

### Post by aum11 on 2006-11-14
Thanks RikoW for Your reply.

Yes have tried the local stations as well as auto ....no stations at all found.  And yes I am using a roof antenna.  It works superbly under windows so the problem is to do with either the way I set it up or that I am not using Kaffeine properly.

How can I check for sure that the device is setup correctly?

Really appreciate Your help.

---

### Post by aum11 on 2006-11-14
Success!!!!

Have television working right now. 

The console scan function was required to initiate the receiver. 

In summary, it is very simple to get the Digitalnow tinyusb dvb-t(twinhan) working successfully with Kaffeine under Ubuntu....but only after the channel scan was initiated via the scan command on the console.

The website [www.wi-bw.tfh-wildau.de/...te=dvb-usb-howto](www.wi-bw.tfh-wildau.de/...te=dvb-usb-howto)
was helpful, especially in regards to scanning.

---

### Post by RikoW on 2006-11-15
Just wanted to suggest to check what happens when you scan from the console :)

Well, I'm glad it works now .... enjoy your digital TV :)

- Riko

---

### Post by aum11 on 2006-11-15
Thanks Riko...that was all that was needed.

---

### Post by rhodry on 2006-11-24
> **aum11 said:**
> Success!!!!

Have television working right now. 

The console scan function was required to initiate the receiver. 

In summary, it is very simple to get the Digitalnow tinyusb dvb-t(twinhan) working successfully with Kaffeine under Ubuntu....but only after the channel scan was initiated via the scan command on the console.

The website [www.wi-bw.tfh-wildau.de/...te=dvb-usb-howto](www.wi-bw.tfh-wildau.de/...te=dvb-usb-howto)
was helpful, especially in regards to scanning.

I am in the same position as you were, but I cannot seem to find the actual console command you issue to initiate the scan? Could you please advise what it was you typed in?

Thanks,
Paul.

---

### Post by r76 on 2006-11-28
I believe the full web address got shortened there - it doesn't work for me either.  I think the one you're looking for is :
[http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto](http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto)
http://www.wi-bw.tfh-wildau.de/~pboettch/home/index.php?site=dvb-usb-howto

or take a look at the description in my signature, I scanned using a tool from the package dvb-utils and it was a great success for me! Good luck

---

