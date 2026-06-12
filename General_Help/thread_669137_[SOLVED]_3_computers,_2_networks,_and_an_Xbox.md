---
title: "[SOLVED] 3 computers, 2 networks, and an Xbox"
date: 2008-01-16
forum: General Help
---

### Post by Capricori on 2008-01-16
I have a gigabit switch in the post, so I'm looking at a few ways of integrating it into my existing network.
I've got a setup in mind, just wondering if it's possible, and/or the best way of doing it.

Right now, I have a laptop, a Linux desktop, and an XP desktop. The Linux desktop is wired to a router, the XP desktop has a wireless connection to the same router, and the Linux laptop alternates between wired and wireless with the router.

I'm intending to connect the Linux desktop, Linux laptop, and an Xbox Media Centre to the switch with Cat6 cables, so the laptop and xbox can get media from a samba share on the desktop (at a decent speed).

My questions are:

1) Is it possible for the desktop and Linux laptop to have two connections active at once? i.e. connected to the switch, and the internet (via the wireless router).

2) Is there a better way of doing this that I'm just not seeing?

3) Would there be any advantage to plugging the switch into one of the router LAN ports? Then if I tried to move a file from one machine to another, would it automatically pick the best route?

Any thoughts welcome, I can try and make a diagram if anything needs more clarity.
Regards.

---

### Post by geirha on 2008-01-16
> **Capricori said:**
> 3) Would there be any advantage to plugging the switch into one of the router LAN ports? Then if I tried to move a file from one machine to another, would it automatically pick the best route?

Yes, it should.

---

### Post by danwood76 on 2008-01-16
Connect the new switch into the router and you have no need to plug the linux desktop into the router aswell.
You only need one network with that setup as direct file transfers will just go through the switch.

So you have the wireless router plugged into the gigabit switch with your xbox and desktop connected to it with the lappy on either wireless or connected to the gigabit through cat5/6, as your lappy wont have a gigabit connection will it?

hope it helps,
Danny

---

### Post by Capricori on 2008-01-16
I'm not sure...
I googled the laptop's ethernet controller a while back and found something that said it can handle gigabit ethernet, but I can't find that page now, or any other reference to the speed...  

I decided on two networks mainly because it meant I didn't have to touch the existing network, just build around it. And because it meant all the internet traffic would go through the router, which has a built-in firewall.

So, if I plug the switch into one of the router LAN ports, and then all the other devices (except the wireless ones) into the switch, that should work OK?
Port forwarding etc should all be fairly straightforward?

Thanks for the help! :)

---

### Post by geirha on 2008-01-16
The computers you connect would behave as if you connected them directly to the router, so port forwarding should be the same procedure as previously. 

On the laptop you can run ```
sudo lshw -C network
``` to see what speed it has.

---

### Post by Capricori on 2008-01-16
Well, as it turns out, it only does up to 100MB/s....
So I guess the switch has little use after all :)

Ah well, thanks for all the help.

---

### Post by danwood76 on 2008-01-16
Basically your router is a router and a switch combined, and adding another switch into it will just increase the number of ports and in your case increase the speed for a couple of your devices.
So plugging into the switch will be the same as plugging them directly to the router.

Yeah I didnt think many laptops came with gigabit as its really un-necessary for a laptop.

regards,
Danny

---

### Post by Capricori on 2008-01-18
Yeah, I get the whole router/switch theory, the whole reason I was doing it was for the speed boost, was hoping to maybe stream some video and stuff.

Just a quick update, I ran the command suggested above (sudo lshw -C network) on the desktop... and it can only do 100MB/s as well :D

So, I've learnt my lesson about believing what random websites tell me about my hardware, and my brand new, 5-port, gigabit doorstop will serve as a reminder :D

Thanks guys!

---

### Post by danwood76 on 2008-01-18
> **Capricori said:**
> 
So, I've learnt my lesson about believing what random websites tell me about my hardware, and my brand new, 5-port, gigabit doorstop will serve as a reminder :D


Depending on how much your new 'doorstep' cost you may aswell buy a gigabit card for your desktop.
They are quite cheap now, I guess you need to get one linux compatible though.

It may be that your desktop can do gigabit but the drivers you are using dont.
What Desktop do you have exactly?

regards,
Danny

---

### Post by Capricori on 2008-01-18
> **danwood76 said:**
> 
It may be that your desktop can do gigabit but the drivers you are using dont.
What Desktop do you have exactly?

It's a Dell 4600, and according to lspci, it has a Intel Corporation 82562EZ ethernet controller, and it's using the e100 driver.

But, surely if the laptop and xbox can only handle 100MB/s, then upgrading the desktop to a gigabit won't make file transfers any quicker?

Regards, 
Capricori

---

### Post by danwood76 on 2008-01-18
SOrry I thought you meant a 360, my bad.
But it depends how much you will be streaming off it, I would have thought a 100Mb lan connection could serve 3-4 computers streaming video.
But any more than that would give jerkey streaming performance.

Yeah your card can only do 10/100 Mb.

Upgrading to gigabit would mean that if both the laptop and xbox are pulling files off at full speed then they could both reach 100 Mb/s where as if you had a 100 Mb/s connection they could only do 50 Mb/s.
Mind you thats still quite fast and easily enough to stream video on both.

regards,
Danny

---

### Post by Capricori on 2008-01-18
> **danwood76 said:**
> SOrry I thought you meant a 360, my bad.
That's ok, I didn't specify either way. It's an original Xbox that I picked up for £35 last week. Replaced the standard dashboard with a Linux-based one, and installed Xbox Media Centre. It's doing a great job with my music, which is why I wanted to try video as well :)

> **danwood76 said:**
> I would have thought a 100Mb lan connection could serve 3-4 computers streaming video.
So would I... there's something wrong, either with my network, or with my logic.
As an example, I just tried to pull a video from the desktop to the laptop. Both are wired to the router right now, with Cat5e cables.
The speed varied between 8MB/s and 11MB/s. Now, I know that 100MB/s is the theoretical speed, and I'm never gonna actually get 100MB/s transfers, but 11MB/s seems a bit slow, no?

---

### Post by danwood76 on 2008-01-18
Its 100 Mb not 100MB, so 100 Mega Bit / second, 8 bits in a byte, so 100/8 = 12.5 MB/s theoretical maximum.

Its a common miss conception, as it is with disk sizes and the like.

100 Mb/s is 12.5 MB/s
1Gb/s is 125 MB/s

But for a HD video stream the bitrate is around 2-3 Mb/s so streaming will be fine.

hope this clears things up for you,
Danny

---

### Post by Capricori on 2008-01-18
I get the theory and everything (at least, I think I do - Computer Science exam in 4 days), but 'sudo lshw -C network' shows the speed, size, and capacity of the ethernet controller to be 100MB/s (rather than 100Mb/s).

I'm guessing it's an oversight on the part of whoever wrote the lshw utility, but it's little things like that, that make me start big threads like this :)

Anyways, again, thanks for all the help :)

Regards, 
Capricori

---

