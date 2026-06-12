---
title: "Linux phone dialer?"
date: 2007-06-24
forum: General Help
---

### Post by disturbedite on 2007-06-24
simple question.  is there a program like the (windows) phone dialer for linux?

i'm on kubuntu with voip broadband but i only want a program that is made for or features dialing like the (windows) phone dialer, so something like skype isn't what i'm looking for.

i found ekiga, it supports pc-to-phone calling, but that feature apparently costs money cuz its a service?
isn't there something that just dials using your existing phone service provider/isp (whether its dial-up or broadband)?

---

### Post by OzzyFrank on 2007-06-24
There's actually a whole bunch of them, some already installed, like pppdial etc. However, the best (or easiest to set up in my experience) is wvdial (once again, I am pretty sure it is installed by default). For dial up like me, you would use wvdialconf to test for the presence of the modem (if it can't find it, then it isn't hooked up right or something), then hand edit the generated wvdial.conf file (all you stick in is your username, isp phone number and password). After that, all you do is run wvdial and you're away. I dragged it to the right side of the bottom panel and so launches with one easy click. A couple others that I tried earlier let you specify the dial up info in a gui, but never worked for me, but wvdial was worth setting up.

---

### Post by OzzyFrank on 2007-06-24
Oh, and wvdial will also connect via dial up or broadband.

---

### Post by disturbedite on 2007-06-24
i can't try it out now, but you are right, it is installed by default.  i will try it tomorrow.

thank you very much!

---

### Post by zorkerz on 2007-06-25
The wiki has a good  page on dial up modems: [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Its a little old in places but is still good. gnome-ppp is a good gui for connecting
cheers

---

### Post by disturbedite on 2007-06-25
@zorkerz
i'm not sure you understood, i want to dial from pc-to-phone (cell phone in particular), not dial-up since i'm on broadband w/ voip phone service.

---

### Post by zorkerz on 2007-06-25
you are right I missed your problem entirely. My bad guess i stayed up too late. Was on a bit of a one track mind trying to slve my own modem problems.
good luck

---

### Post by OzzyFrank on 2007-06-25
Same here... saw "phone dialler" like in Windows... so what is actually sought after is actually a bit more than just a phone dialler? Is there a name for these types of programs (assuming phone dialler means just a phone dialler to establish dialup connection)? I would try looking for that... or even something like "skype for linux" or something should produce some kind of result.

---

### Post by disturbedite on 2007-06-26
well sorta...
1.  by phone dialer i mean just that, something that can dial pc-to-phone, the ability to establish a dial-up connection doesn't matter to me, since i'm on broadband.

2.  skype is overkill for what i want & so is ekiga, kinda, but more specifically the reason why those two programs aren't what i'm looking for is cuz they both cost for pc-to-phone service!

i just want a (free) dialer...

---

### Post by YannickDefais on 2007-08-06
Hi,

You can't dial for free PC-to-phone (especially cell phones). Thus sometimes it seems close to free; see:
[Betamax price chart]("http://backsla.sh/betamax") (you pay a fee and you've some days to call landline phones for free).

Maybe your ISP provides you a phone service? In this case ask them on which technology it relies on. If it's SIP or H.323 you can configure Ekiga to use this service.

Regards,
Yannick

---

### Post by jniebles on 2008-01-14
hi, 

i was wondering if you could find this kind of software? if so, could you share it with others?

thanks

> **disturbedite said:**
> well sorta...
1.  by phone dialer i mean just that, something that can dial pc-to-phone, the ability to establish a dial-up connection doesn't matter to me, since i'm on broadband.

2.  skype is overkill for what i want & so is ekiga, kinda, but more specifically the reason why those two programs aren't what i'm looking for is cuz they both cost for pc-to-phone service!

i just want a (free) dialer...

---

### Post by luke16 on 2008-04-20
I'm surprised that there are no landline phone dialers for linux. You would think that it wouldn't be that hard to make, especially with all the other weird programs you can find for linux. Plus I believe windows can do this by default.

---

### Post by ryanhaigh on 2008-04-20
I think you need to better clarify what you are looking for. My impression was that you wanted a program that would allow you to call using your modem and computer as a phone so that your using your normal phoneline to make the call as though your computer was a normal telephone.

On the other hand if you are looking for something that will allow you to connect the the voip service offered by your isp you might want to look at twinkle or wengophone. Wengophone has its own provider but can also be configured to use other providers.

---

### Post by Pollywoggy on 2008-05-17
> **ryanhaigh said:**
> I think you need to better clarify what you are looking for. My impression was that you wanted a program that would allow you to call using your modem and computer as a phone so that your using your normal phoneline to make the call as though your computer was a normal telephone.

On the other hand if you are looking for something that will allow you to connect the the voip service offered by your isp you might want to look at twinkle or wengophone. Wengophone has its own provider but can also be configured to use other providers.

I found this thread with Google and I think I know what the OP wants, and I am looking for the same thing.

Windows has a dialer that allows one to make a regular phone call from the computer, using a plain modem and a microphone/headset.  I would like to get something like this for Linux so that I do not need to pick up my standard telephone when using something like Webex to listen to the audio part of a web seminar.  At present, I get the video portion of the seminar on Firefox, then I have to pick up my regular telephone and dial a phone number to get the audio part.  This is cumbersome, having to hold the handset to my ear for 45 minutes to an hour.

I could just buy a more advanced telephone, one that has a plug for a headset and microphone but I would rather just use the computer if that is possible.

---

