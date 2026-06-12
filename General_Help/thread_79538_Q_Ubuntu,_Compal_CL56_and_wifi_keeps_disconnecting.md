---
title: "Q: Ubuntu, Compal CL56 and wifi keeps disconnecting all the time"
date: 2005-10-20
forum: General Help
---

### Post by The_Saint on 2005-10-20
Ladies and gentlemen,

I have again an issue with my computer, Ubuntu Breezy and networking.

So, to begin from the start - I've upgraded all drivers as described here: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

The Intel Pro Wireless 2200 card is working, everything is okay regarding recognizing the card and driver etc etc.

The only thing is that the wireless network keeps disconnecting all the time. Not like in every 10 or 20 or something minutes, but in every 1-2 minutes. How do I know? MSN and IRC disconnect all the time.

First I thought it's the issue of my wireless gateway (Intel Wireless Gateway), but there is a Windows machine here with a very crappy PCMCIA wifi-card and that one does not keep disconnecting all the time.

So, as I said, I upgraded drivers and firmware as described in the thread I pointed out before, and I don't know anything else I could possibly do to get rid of the disconnection issue.

If you have any suggestions regarding the issue, I am all ears :)

---

### Post by KingBahamut on 2005-10-20
Using a disconnection like a Messenger program does not automatically assess that its a problem with the connection, that may be something else entirely. What I would suggest is to open up Gnome-network-tools over in System Tools, and do a consistent ping to say , google.com , and see how many packets you get that actually drop. Take that output and dump it here.

---

### Post by The_Saint on 2005-10-20
Well, I am using a cable all of the day at work, but then nothing disconnects, IRC nor MSN. So I still presume it's about the connection.

I did ping google.com, but what exactly shoud I paste here? Transmitted and received 155 packets, average 55.6 ms, max 198 ms.

---

### Post by KingBahamut on 2005-10-20
**Transmitted and received 155 packets, average 55.6 ms, max 198 ms.**

This tells me that its not a connection issue. If your connection were in question, the sending of packets would not occur. You would be seeing Packet Loss, commonly called PLOSS. Can you exhibit the behavior in any other application other than your messengers?

---

### Post by The_Saint on 2005-10-20
Yes, I can - websites hang now and then and need a reload. Downloads get stuck and need a restart.

Nothing of the sort happens when I am using cable.

I did a search in this very forum here and found that people with Intel Pro Wireless 2200 cards do have the same problem. Well, at least some of the people.

From what I see here: [http://www.ubuntuforums.org/showthread.php?t=70764&page=2&highlight=ipw2200](http://www.ubuntuforums.org/showthread.php?t=70764&page=2&highlight=ipw2200) I understand that I need to downgrade the driver to 1.0.0. (maybe I don't have the same problem, as you suggest - I don't undermine your knowledge, you obviously know a lot more than I do :)), but when I do as it is described there, then I cannot manage patching the 1.0.0 driver like it's described there. sten@hankewitz:~/Desktop/ipw2200-1.0.0$ patch ieee80211-2.6.12.patch and it just stays there, does nothing, no errors or anything.

So, if you are right and I don't have a connection problem, then what should I do? And, if you are not right and I do have a connection problem, similar to the issue described in the thread I pointed out, then how on earth could I patch it successfully? (Sudo patch won't help either).

---

### Post by The_Saint on 2005-10-20
Anyway, now I managed to downgrade the drivers as it was taught in the thread I pointed out before.

It did not help me out - I still keep disconnecting all the time. I am sick and tired of this actually - can't really anyone help me out with this?

weep weep... :'(

---

### Post by The_Saint on 2005-10-20
I am gonna make another post here now.

I do realize that there's an 'edit' button, but if I make a new post, the thread comes upper in the thread list :)

Anyhow, I now downloaded the 686 kernel. For now it seems to be working. Before I had 386 kernel - could that have been a problem? Anyone knows?

Anyway, for now it seems to be working... for now... Ah, damned - I got disconnected again right when I am writing this here....

So it wasn't the kernel thing. Or, if I now downgraded the driver back to 1.0.0, could that be helpful?

Oh, btw the 1.0.6 version of the driver worked fine in Hoary. How can this be?

---

### Post by KingBahamut on 2005-10-20
How far away are you from the AP/Router?

---

### Post by The_Saint on 2005-10-20
[QUOTE=KingBahamut]How far away are you from the AP/Router?[/QUOTE] 2 meters/yards :) signal is always 98-100 %

---

### Post by circussideshow on 2005-10-21
Hey there, I'm sporting a CL56 as well and I found that the 1.0.5 driver works the best for the ipw2200.  I did have to load the acer kill switch module though for the 2200 to work at all.  whatever came with breezy didn't work for me.  see this page:

[http://heim.ifi.uio.no/~krisvh/linux/cl56.html]("http://heim.ifi.uio.no/~krisvh/linux/cl56.html")

It's for hoary, but still worked for me; i just used the 1.0.5 driver.  But i still sometimes have to run dhclient several times for it to work (which may be my poorly managed openwrt wrt54g router).  usually i just use my WG511 or SMC card because IMO the 2200 sucks in general.

---

### Post by The_Saint on 2005-10-21
[QUOTE=circussideshow]Hey there, I'm sporting a CL56 as well and I found that the 1.0.5 driver works the best for the ipw2200.  I did have to load the acer kill switch module though for the 2200 to work at all.  whatever came with breezy didn't work for me.  see this page:

[http://heim.ifi.uio.no/~krisvh/linux/cl56.html]("http://heim.ifi.uio.no/~krisvh/linux/cl56.html")

It's for hoary, but still worked for me; i just used the 1.0.5 driver.  But i still sometimes have to run dhclient several times for it to work (which may be my poorly managed openwrt wrt54g router).  usually i just use my WG511 or SMC card because IMO the 2200 sucks in general.[/QUOTE] Thank you - i'll try this out absolutely.

Meanwhile, let me help you with something as well :) The switch thing is easily fixed - this site [http://mercury.walagata.com/w/epb613/cl56_guide.html](http://mercury.walagata.com/w/epb613/cl56_guide.html) suggests you upgrade your bios to 1.40 (it's normally 1.20). On this page there's an explanation how to upgrade the bios and also the link to the place you can download the new bios.

I did this, although I was a little sceptical about upgrading the bios, it worked out fine and now the switch is like totally hardware based - always loaded before you reach GRUB, of course when the switch is on :)

So, from my own experience, I say try it out (just don't blame me if something gets f'ed :P)

---

### Post by The_Saint on 2005-10-21
I am now continuing my whining.

I couldn't install 1.0.5 version because I kept getting errors of some sort, something related to ipw_sw_reset. Any suggestions what I should do about it?

I did try out the newest driver (isn't the newest supposed to be the best?), 1.0.7 and the problem remains - I still keep disconnecting all the time.

Any suggestions? I am becoming desperate :(

---

### Post by epb613 on 2005-10-21
It's nice to see people look at my page.

As an idea, I would try posting your problem on the iwp2200's bugzilla. The people there in general are quick to respond and very helpful.

Also, out of curiosity, have you tried installing that pcmcia card that you have into the laptop?

---

### Post by The_Saint on 2005-10-21
[QUOTE=epb613]It's nice to see people look at my page.

As an idea, I would try posting your problem on the iwp2200's bugzilla. The people there in general are quick to respond and very helpful.

Also, out of curiosity, have you tried installing that pcmcia card that you have into the laptop?[/QUOTE] No, I actually haven't. You think I should give it a try? I mean, I could try to install it, but I don't think that there are drivers for this PCMCIA card for Linux. It's some sort of an old D-Link card. And I couldn't use it like for good because my wife is using it :)

BTW, I am the person who sent you an e-mail a couple of weeks ago asking about the acerhk driver, if you remember :)

And I already took a more radical step and e-mailed to James Ketrenos, who's e-mail address and name was on the ipw2200 page... I am now counting on him... :)

---

### Post by epb613 on 2005-10-21
Oh, Sten.

Well, I see you upgraded the BIOS instead in the end.

As I updated my site last night, the acerhk module still is useful for enabling the the 2 ez buttons next to the power button. As I recall these 2 buttons wont work without it. And thinking about it some more, I wonder if it would also get the sleep button to work. I'll have to play with this over the next couple days.

To install the dlink card, you could probably just use ndiswrapper ([https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)) and the windows drivers (just copy them off your wife's PC). If the card doesn't have the dropping problem, then you'll know your problem is with the ipw2200 drivers, and if it does have the dropping problem, then you'll know your problem is one with the os itself.

---

### Post by The_Saint on 2005-10-21
I upgraded the bios when I moved on to Breezy. Because I couldn't for some reason get it to work in Breezy. In Hoary it worked very well.

When I get the chance, I'll try to test this PCMCIA card. It wouldn't be easy to get this from here while she's using the PC :P

Anyway, from the Intel driver gentleman I mentioned before I got instructions to load the driver with debug level set to 0x43fff and check my system
log for errors (firmware restarts, etc.) So I did it and I have no idea what to look for in the system log.

I do see things like this there: localhost kernel [4300907.007000] ipw2200: I ipw_handle_missed_beacon Missed beacon: 1
localhost kernel [4300907.528000] ipw2200: I ipw_rx_notification type = 25 (4 bytes)

But what is this missed beacon or something... I have no idea.

Update: I also see things like this in the log: localhost dhclient DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13

Why? I have no idea again. The interesting thing is that eth0 is my lan card, eth1 is ipw2200. And I am not on eth0 at the moment.

Oh, and another, probably stupid question - could I use this ndiswrapper also for using win drivers with the ipw2200 card? Or what?

---

### Post by The_Saint on 2005-10-21
Anyhow, I think i reached the conclusion that the thing in system log saying "localhost kernel [4304122.602000] ipw2200: I ipw_handle_missed_beacon Missed beacon: 1" means that the disconnection happened.

Any suggestions anyone?

---

### Post by epb613 on 2005-10-21
I would send the guy back a copy of your system log. Or post it on their buzilla.

A DHCPDISCOVER is a normal process that your card with attempt when it wants an ip address from your router. In English, it's not a bug.

Also, whether or not you are using the adaptor, Ubuntu still records the built in lan as eth0 and the wifi as eth1. When you install the pcmcia card, whether or not you use it, Ubuntu will assign it the name eth2 (or wlan1).

Yes, you should be able to use the windows drivers for the 2200bg through ndiswrapper. That's a really interesting idea, let me know how if it fixes your problem.

---

### Post by The_Saint on 2005-10-21
[QUOTE=epb613] Yes, you should be able to use the windows drivers for the 2200bg through ndiswrapper. That's a really interesting idea, let me know how if it fixes your problem.[/QUOTE] It did not turn out very well. root@hankewitz:/usr/src# ndiswrapper -l
Installed ndis drivers:
w22n51  invalid driver!

So it did not work out very well :P

I am already considering moving back to Hoary. Breezy does have issues, starting with the keyboard layout problem that has been mentioned a lot everywhere and now this one I am dealing with right now...

---

### Post by epb613 on 2005-10-21
I'm bogged down for today with college work but on Sunday I'll see if I can get it working with ndiswrapper. If you haven't done it yet, I'll advise you once again to file a bug report.

---

### Post by The_Saint on 2005-10-21
[QUOTE=epb613]I'm bogged down for today with college work but on Sunday I'll see if I can get it working with ndiswrapper. If you haven't done it yet, I'll advise you once again to file a bug report.[/QUOTE] I haven't done it yet. I'll wait until tomorrow if the Intel gentlemen replies something. If he doesn't, I'll file a bug report.

Thanks for your help, I really appreciate it :)

---

### Post by The_Saint on 2005-10-22
I now filed a bug report in the ipw2200 bugzilla... Let's see if it helps me out here...

---

### Post by Paperjam on 2005-10-23
Maybe you should try to switch the channel of your access point. If there are other access points around that send on the same channel, this may be the source of your troubles...

---

