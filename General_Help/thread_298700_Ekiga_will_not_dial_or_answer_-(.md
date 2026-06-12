---
title: "Ekiga will not dial or answer :-("
date: 2006-11-13
forum: General Help
---

### Post by wiresquire on 2006-11-13
I installed Ekiga from the repository at
[http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) 
so have Ekiga 2.0.3

I am sitting behind a NAT, but forwarded ports 5000-5100, and Ekiga shows I am on Cone NAT, and I have enabled STUN. I also forwarded ports 30000-30010, though it doesn't seem to make any difference.

I have my own VOIP provider, and entered the details. Ekiga shows that it is Registered.

When I try ringing the VOIP number, Ekiga doesn't answer. When I try ringing a number from Ekiga, I can hear what sounds like ring, ring, ring from Ekiga, but nothing is happening - my real phone doesn't ring. Eventually I get a timeout.

X-Soft (xtensoftphone) works, so I know the problem isn't with the VOIP provider, but I'd like to use Ekiga. Can anyone help?

TIA
ws

PS: Mods: Apologies for dual posting - can someone delete the post at
[http://www.ubuntuforums.org/showthread.php?t=297758](http://www.ubuntuforums.org/showthread.php?t=297758) ? It's in the wrong section.

---

### Post by kitsos on 2006-11-13
Hi,
i've got similar problems with ekiga. I'm also behind cone NAT, using STUN and my account gets registered. However, I can only make calls and not receive any. 
Just checking... is the string that your are using to call the desired number in the following format?:
sip:phonenumber@sip.yourprovider.com

---

### Post by wiresquire on 2006-11-14
> **kitsos said:**
> Hi,
i've got similar problems with ekiga. I'm also behind cone NAT, using STUN and my account gets registered. However, I can only make calls and not receive any. 
Just checking... is the string that your are using to call the desired number in the following format?:
sip:phonenumber@sip.yourprovider.com

I've done all the permutations - with STUN, without STUN, without sip provider, with it, with the sip proxy, with a registrar etc ](*,) . I even started ekiga with the debugging on (ekiga -d4) to see what it was really sending. Debugging doesn't show me anything useful that I could see. :( 

It's almost like it's not really sending anything, so I thought it was something to do with STUN/NAT or something. 

Did you have to open/forward any ports from your NAT or are you lucky and have a router that is smarter than mine? Or can you work out which ports are active with it?

ws

---

### Post by kitsos on 2006-11-14
I have a speedtouch router. Had to login with telnet and change symmetric to cone nat. I have also tried forwarding ports and changing the ekiga setting to port forwarding instead of STUN, but nothing seems to work. Ekiga manual and other threads i've had a look at, recommend opening and forwarding ports 5000-5100. From my experience SIP usually needs port 5060.

In any case, if your problem was the NAT/STUN, ekiga should still send out SIP handshake messages, since outgoing traffic shouldn't been blocked.

Something interesting that i came accross somewhere is that if your router is VOIP enabled, it might be hijacking all SIP traffic and handling it by itself...if that is the case you need to disable VOIP in your router.

After trying a few different SIP softphones, Twinkle (included in ubuntu) is the only one that worked for me (straightway out of the box!!). you might want to give it a go...

---

### Post by wiresquire on 2006-11-15
Thanks for the tip. I'll give twinkle a go. Hope you don't mind me asking which version are you using and where did you get it from? I'm on Dapper, and it looks like there is only 0.4x available, and the website shows 0.9 :(

As I mentioned above, I got xtensoftphone to work, but after having a quick look at twinkle's website it looks a lot more friendly. xtensoftphone comes across as a port from some other OS.

I'm disappointed about Ekiga. I thought it looked good, but there was NO way I was going to run the firewall script they had, particularly after I saw somewhere that it had wrecked someone's internet connectivity....

Cheers
ws

---

### Post by kitsos on 2006-11-16
I'm using edgy so twinkle is the version that ships with it...can't exactly tell at the moment what version that is, cause i am not on my machine...the version that ships with edgy is very user friendly...have a look at this thread
[http://ubuntuforums.org/showthread.php?t=205318]("http://ubuntuforums.org/showthread.php?t=205318") ..there's some guy who made a package to get the edgy version of twinkle to work on dapper!

---

### Post by wiresquire on 2006-11-17
Thanks very much.

I'll give it a go when I have a chance and report back.

ws

---

### Post by wiresquire on 2006-11-17
I installed the 0.8x version from that thread. STUN doesn't seem to work, even though I forwarded the ports per the recommendations.

But it works fine :-D 

Thanks for your help
ws

---

