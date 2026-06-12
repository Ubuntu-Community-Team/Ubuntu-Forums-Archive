---
title: "Anyone using Asterisk or doing SIP VOIP calls using Ubuntu?"
date: 2013-04-25
forum: General Help
---

### Post by fixitdude on 2013-04-25
Asterisk was working really good here and then something changed. I'm also wondering if other people have been using Asterisk on Ubuntu and enjoying the free calls. I actually have dial tone that is from my box, which to me is strange since all my life the phone company provided that. Got to love it!

Here's my problem and I am really stuck and stumped as to why this is a problem. It's going to get a little technical.

I need to know if I covered everything or I missed something.

I took my entire system over to another location and confirmed that it was working OK, all packets get sent and REGISTRATION happens OK and all that, calls go out etc...

For some reason I can't register anymore with the SIP provider. I recorded packets using tcpdump at both locations so I could compare a good registration vs. a bad one.

Everything is the same (except the outside IP) the IPs for the provider are correct and the same.

When it's bad - I see a OPTIONS packet go out and a OK packet comes back from the provider just like it does at the good location. So I know the NAT routing is working and allows the UDP packets back to the originating computer.

The next thing that is sent is REGISTRATION, and nothing comes back! At the good location, it registers and sends a final OK at the end like it should.

I don't know what changed, but everything is open on all the routers, no firewall blocking, and when you think about it, if port 5060 was blocked, why do I get back the OPTION "OK" packet?

Remember, this is not a password problem, I don't think the packet ever gets to the SIP provider or somehow it doesn't get back to this computer. Minimum I should get a un-authorized or something from the SIP provider if it was something like a password problem, or even a format problem in the packet, NOTHING comes back.

This is very strange and I don't understand why. All other stuff like web browsing works, doing ssh etc.. And I also tried using a program called "Ekiga" which is a program based SIP call program and it has the same registration problem even with the Ekiga SIP servers! So it's not the SIP provider in particular.

The only thing that would do this is possibly a "stateful" packet filter that sees REGISTRATION and blocks it. Which my ISP shouldn't be doing because they allow VOIP such as magic jack etc...

Any ideas? I'm stuck!

---

### Post by carl4926 on 2013-04-25
I use Linphone with great success

---

### Post by fixitdude on 2013-04-25
> **carl4926 said:**
> I use Linphone with great successThanks for taking the time to reply.

I tried with Linphone (which has a good debug feature under "help") and also "Twinkle" with the same results. You see REGISTRATION packets go out but nothing comes back and OPTIONS packets get acknowledged from the SIP server and come back on port 5060 like they should so NAT has to be working. The OPTIONS packets and REGISTRATION packets are close together most times so it's not like the NAT table is timing out, I think standard timeout on them is 180 seconds anyway.

Like I said, I tried this at another location with this exact computer and calls work fine, registration happens and the packets are identical except for the IP address of course.

I am really at a loss on this one to understand what is happening.

---

