---
title: "ATT Hack: How to Secure Home Network and Ubuntu Computers??"
date: 2024-07-13
forum: General Help
---

### Post by Old Jimma on 2024-07-13
Hello Ubuntuers:

With the recent news about the ATT hack, I thought I'd ask how to secure my ome network and ubuntu computers from being hacked.

I have a VPN and use UFW to allow TCP traffic from a main server in my home... but nothing else.

What else should I do?

Thanks,
Old

---

### Post by TheFu on 2024-07-13
I cannot talk about AT&T hack stuff. Sorry.  Non-disclosure agreements. You understand.  I can assure people that AT&T does patch their CPE (customer premise equipment) as needed for their broadband customers. I worked that project to ensure patching happened.  The highest levels of AT&T were involved in the decision to patch and to validate that every CPE was patched.  Patching was easier than getting an accurate report about the current patch level on the devices.

If you aren't with AT&T, I wouldn't assume any provided router is patched until you check and validate that yourself.  I don't use AT&T for my ISP. I've verified they patch, but they aren't exactly quick about it.  Anytime a patch requires a reboot, that means downtime and downtime is bad for the type of SLA I have with the ISP.  I use the ISP's router just as a bridge.  I have my own router and patch it weekly.  About every other week, there are patches available for it.  I run OPNSense as the router software on a purpose-built AMD x86-64 SBC w/ 4GB RAM just for routing. I don't have wifi capability on my router.  wifi is just another attack vector and none of the current wifi standards should be considered as "secure".  Actually, no wifi standards have been secure that we know since 2000.  

If you use wifi, do it outside your LAN and use a VPN for all wifi using devices. For example, we have a roku streaming stick and it sits between the ISP's router and my router in an untrusted part of the network.  Other IoT stuff goes there too and cannot access any of my LAN stuff.  

If you have more questions, join ALE-NW on Sunday for more interactive answers.  There are many things you didn't answer which would determine what you need to do.  In general, use the fewest "features" of the router that you can. Disable all the others.  Patch frequently based on the router you have and their update periods. Most will update monthly or quarterly.  If you haven't patched your router in the last quarter, perhaps it is out of support and needs to be replaced?  If it can run dd-wrt or OpenWRT, you may be able to vastly extend the useful life.

The guidelines are the same for most computers.  Stay patched. Don't enable services you don't need or use.  If you do enable any listeners, lock those down to allow only the client connections you want. Never leave them open to the internet.  Beware of LAN-wide broadcast protcols like ZeroConf/Avahi and CUPS and DHCP.  These can be abused.  Heck all network protocols can be abused.  The idea that you don't need to protect systems that are on your LAN is something some people push.  There are different opinions about this. I think we should run a firewall on all our computers and only allow the specific protocols between the specific systems that need it.  Whether that is useful for your situation or not depends on many things.

---

### Post by currentshaft on 2024-07-13
Use a password manager and multi-factor authentication.

Install updates on time.

Don't click on silly stuff or install unknown software, i.e., use common sense.

The VPN and exposing your home network is not doing you any favors, either.

---

### Post by Old Jimma on 2024-07-13
Hello currentshaft,

YOu wrote, "The VPN... is not doing you any favors?" 

Why should we not use VPN?

---

### Post by currentshaft on 2024-07-13
Because you're literally sending all of your network traffic to a third party? Why does anyone think this is a good idea?

---

### Post by aljames2 on 2024-07-13
I use a VPN server at home for remote access to Nextcloud running at home.  The WG & NC servers are both on a separate subnet from my primary LAN. There is a 3rd subnet for IoT stuff & wireless. I use Nftables firewall on the WG/NC VMs, and their host. Mostly, my office computer will VPN back home for docs  and such. It replaced Dropbox.

Careful network and router configuration is important. Router should be updated regularly, and have a password that you could never memorize. My password is probably over 30 characters, not sure, but KeePass created it for me and it seems  to work. That gets changed periodically as well. Oh, and be stingy about opening up ports and services to the internet. I like to deny all to subnets at the router level, and I do not promote subnet hops. If I want a desktop at home to access NC at home, it goes out to the internet and back through the VPN.

I currently do not have a VPN for any outbound traffic but I am thinking about how I might do this for sensitive logins such as payroll, brokerage accounts, banks, etc.  This is probably the first thing I should have figured out how to do, oh well.  I do not yet have a grasp on how to best do this without using a commercial service which I do not want to use for sensitive stuff.  I probably would want to rent a VPS I think and run an outbound Wireguard server there, or perhaps run it from home, not sure.  I wrestle with this topic as well...
On a VPS I would avoid the one-click WG server setup that they provide and would rather set up my own server there and run it when I need it.

---

### Post by currentshaft on 2024-07-13
> **aljames2 said:**
> My password is probably over 30 characters,

That gets changed periodically as well.

If I want a desktop at home to access NC at home, it goes out to the internet and back through the VPN.

I currently do not have a VPN for any outbound traffic but I am thinking about how I might do this for sensitive logins such as payroll, brokerage accounts, banks, etc.  


All of these things may make you feel good, but they are security anti-patterns which actually worsen your posture.

30 character password is so overkill it borders on ridiculous. Yet it also gets changed, which is a total contradiction.

Then you claim to send traffic out through the Internet to access servers inside your own private LAN, which is so unbelievable, I'm honestly not even sure what to say.

Respectfully, a classic example of trying to implement solutions without asking what problem is being solved. I only say this because OP is asking how to secure their network and this ain't it.

---

### Post by dragonfly41 on 2024-07-13
I have recently turned to deploying Proton developed by CERN engineers.
Proton Mail
Proton VPN
Proton Vault
Proton Pass


[https://proton.me/pass/password-generator](https://proton.me/pass/password-generator)

---

### Post by donald187 on 2024-07-13
> **currentshaft said:**
> Because you're literally sending all of your network traffic to a third party? Why does anyone think this is a good idea?

Because you've picked one that promises no logging and they've passed privacy and security audits?

---

### Post by currentshaft on 2024-07-13
> **donald187 said:**
> Because you've picked one that promises no logging and they've passed privacy and security audits?

Like a pinky promise?

Honest question, do you think scammers and bad actors are capable of setting up "totally private, trust us bro" VPN services, or do only Good Guys (tm) run them, in your opinion?

---

### Post by donald187 on 2024-07-13
> **currentshaft said:**
> Like a pinky promise?

Honest question, do you think scammers and bad actors are capable of setting up "totally private, trust us bro" VPN services, or do only Good Guys (tm) run them, in your opinion?

I'm no expert but I did use Mullvad VPN for a while.  They pass an audit from time to time.  They were written up in pcmag.com as being trustworthy and their top budget VPN.  And they are the VPN used by Mozilla for their Mozilla VPN.  So I think they're one of the good guys.  But sure, bad guys can set up a VPN too.  I just don't think they could get the same testimonies as Mullvad has.  And there are others of course that have similar testimonies.

Do you think the audits make a difference in establishing trustworthiness?  That's why I brought it up.

---

### Post by aljames2 on 2024-07-13
> **currentshaft said:**
> All of these things may make you feel good, but they are security anti-patterns which actually worsen your posture.

30 character password is so overkill it borders on ridiculous. Yet it also gets changed, which is a total contradiction.

Then you claim to send traffic out through the Internet to access servers inside your own private LAN, which is so unbelievable, I'm honestly not even sure what to say.

Respectfully, a classic example of trying to implement solutions without asking what problem is being solved. I only say this because OP is asking how to secure their network and this ain't it.

Doesn't make me feel good, other hobbies I have do however. To the contrary, it's a bit of work but worth the effort in my opinion.
I understand the concept of large numbers, hide in plain sight. No  reason not to for most things. For connections involving wireless and information such as SPI, PHI, financial, & trade information, all seem to be worth the effort to use an encrypted tunnel. But again, I don't have it all figured out, just practicing what I am learning to the best of my abilities.  As I learn new information, no doubt I will make adjustments.

---

### Post by currentshaft on 2024-07-13
> **donald187 said:**
> I'm no expert but I did use Mullvad VPN for a while.  They pass an audit from time to time.  They were written up in pcmag.com as being trustworthy and their top budget VPN.  And they are the VPN used by Mozilla for their Mozilla VPN.  So I think they're one of the good guys.  But sure, bad guys can set up a VPN too.  I just don't think they could get the same testimonies as Mullvad has.  And there are others of course that have similar testimonies.

Do you think the audits make a difference in establishing trustworthiness?  That's why I brought it up.

Are you familiar with Equifax? [https://en.wikipedia.org/wiki/Equifax#Security_failings](https://en.wikipedia.org/wiki/Equifax#Security_failings)

They held ISO 27001 certification, which requires much more extensive audits than some vague endorsement, at the time of the 2017 security breach which led to the theft of personal information of over 100 million people.

Even if the good guys set up a VPN, it's a massive target for attackers - a proverbial watering hole. Do not waste your time with one.

---

### Post by donald187 on 2024-07-13
> **currentshaft said:**
> Are you familiar with Equifax? [https://en.wikipedia.org/wiki/Equifax#Security_failings](https://en.wikipedia.org/wiki/Equifax#Security_failings)

They held ISO 27001 certification, which requires much more extensive audits than some vague endorsement, at the time of the 2017 security breach which led to the theft of personal information of over 100 million people.

Even if the good guys set up a VPN, it's a massive target for attackers - a proverbial watering hole. Do not waste your time with one.

Ok, thanks!

---

### Post by TheFu on 2024-07-14
> **currentshaft said:**
> Because you're literally sending all of your network traffic to a third party? Why does anyone think this is a good idea?

Either your ISP sees it or your VPN provider (and their hosting company) sees it.  Many locations have little choice about their ISP and it is often run/controlled by the govt.  Where I live, I don't trust the ISPs, since they've been caught, multiple times, 
a) being cracked
b) selling private information en masse to 3rd parties, including the govt.

The 2 ISPs in my location are 2 of the most hated companies in my country.  One of those companies is a customer of the other for all traffic outside the country, so effectively what 1 does, the other gets for free. Sadly, the main telecom is known for using deep packet inspection and bluecoat equipment to classify traffic beyond what most people do.

It is a lessor of evils choice.  Most of the time, I don't use a VPN.  I only use them when needed for a variety of reasons.  Sometimes it is work related. Other times it is to get passed geo-blocking and sometimes it is for very light privacy (though TOR would be better).

For anyone using a free VPN, I think your statement is 100% true.  For anyone using a VPN tied to a huge Asian country somehow, I think it is even more risky.  That govt already stole much of my private information from my govt, including details that were never supposed to become public. Things my family doesn't know.  I don't recall exactly when, but a few years ago a VPN watching organization researched about 50 VPN providers for which where worthy of our trust. I don't recall the final number, but between 60% and 80%  were untrustworthy based on their criteria.  After reading that article, I stopped using 3rd party VPNs and just spin up my own randomly on different VPS providers with systems around the world.  Usually takes about 3 minutes from "give me a server" until I have a VPN connection working making all my traffic appear to be from that remote (or local) city.  Where the exit node/server is located depends on the specific need.

Most people concerned about privacy would be better off using TOR and changing the exit node every few hours.  Many spy organizations around the world run TOR nodes hoping to catch the last packets leaving the TOR network. Hopefully, everyone understands that.  On those servers, it is just like they are the ISP and able to see where are traffic is really headed and the TLS packets, if used.

---

### Post by dragonfly41 on 2024-07-14
Why not adopt end-to-end encryption (desktop to desktop)?
A zerotrust policy.

Example: [https://www.bouncycastle.org/](https://www.bouncycastle.org/)

---

### Post by TheFu on 2024-07-14
Not doing anything because there's 1 example where they did it poorly doesn't make sense.
The equifax breach had NOTHING to do with VPNs.

Securing a multi-national company is much harder than securing a home network.  Multi-national companies have thousands of points of entry.  Most home networks have 2 - wifi and the cable from their ISP.  Don't use wifi (turn it off) and 50% of the network attack vectors are handled (in theory).



>     Why not adopt end-to-end encryption (desktop to desktop)?

Because we don't control the other side of the link?

---

### Post by currentshaft on 2024-07-14
> **TheFu said:**
> 
For anyone using a free VPN, I think your statement is 100% true.  For anyone using a VPN tied to a huge Asian country somehow, I think it is even more risky.  That govt already stole much of my private information from my govt, including details that were never supposed to become public. Things my family doesn't know.  I don't recall exactly when, but a few years ago a VPN watching organization researched about 50 VPN providers for which where worthy of our trust. I don't recall the final number, but between 60% and 80%  were untrustworthy based on their criteria.  After reading that article, I stopped using 3rd party VPNs and just spin up my own randomly on different VPS providers with systems around the world.  Usually takes about 3 minutes from "give me a server" until I have a VPN connection working making all my traffic appear to be from that remote (or local) city.  Where the exit node/server is located depends on the specific need.

Most people concerned about privacy would be better off using TOR and changing the exit node every few hours.  Many spy organizations around the world run TOR nodes hoping to catch the last packets leaving the TOR network. Hopefully, everyone understands that.  On those servers, it is just like they are the ISP and able to see where are traffic is really headed and the TLS packets, if used.

It's spelled Tor, not "TOR".

The same adversaries setting up malicious exit nodes (hint: it's most of them) are also setting up "totally private, hosted in switzerland, trust us bro" VPN services (hint: it's most of them).

---

### Post by currentshaft on 2024-07-14
> **dragonfly41 said:**
> Why not adopt end-to-end encryption (desktop to desktop)?
A zerotrust policy.

Example: [https://www.bouncycastle.org/](https://www.bouncycastle.org/)

End to end encryption of what? Encryption to whom?

Start with a threat model, not window shopping for solutions.

---

### Post by TheFu on 2024-07-14
> **currentshaft said:**
> It's spelled Tor, not "TOR".

The same adversaries setting up malicious exit nodes (hint: it's most of them) are also setting up "totally private, hosted in switzerland, trust us bro" VPN services (hint: it's most of them).

You understood what was written, so it worked.  And the BBC says Nasa and Noaa and Fbi and Cia  and does the same for lots of abbreviations.  Is this really worth our time?   **TOR** = _T_he _O_nion _R_outer

Call it Tor, if you like.  You can BBC are welcome to that.  [https://en.wikipedia.org/wiki/The_Tor_Project](https://en.wikipedia.org/wiki/The_Tor_Project) makes it seem they "rebranded" just like different sports stadiums do.  Fine. Whatever.  Probably happened sometime when they decided that people weren't able to setup TOR themselves and started packaging a browser, pre-configured, to use it.  Probably smart for making it more accessible to more people. I can see that.

All software is in the "trust us Bro" category, unless you create the linker.  Since very few people do that, we are all in the "trust us bro" group.   I've had to audit linkers and compilers in a former job. It was amazing the number of bugs we'd find.  I suppose they weren't really bugs, just unexpected optimizations that didn't create code to do what the application language programmer expected.  ;)   Since only about 30 people in the world wrote code using that language, it didn't impact many people directly, but for the people who depended on it, their lives were at risk, literally. Fortunately, no software error killed anyone, but a number of people did die due to hardware failures and poor management choices (unrelated to software).  What the compiler does and what the linker decided to do  (or worse, interpreted languages) isn't really in our control. We have to "trust them bro".  This trust is for the entire stack of every OS in the world.

Or we can stop using all technology that has computing and software involved and live in a remote cave.

But this isn't exactly practical for most people on these forums.  Smart people would guess the risks in doing X and weigh those risks against all the others in their use scenarios.

BTW, you know that all login programs are setuid root, on every OS, right?  You shouldn't login on any computer either.

---

### Post by dragonfly41 on 2024-07-14
In reply to post #19 which sagely opines:

[COLOR=#000000]"Start with a threat model, not window shopping for solutions."

I refer to zerotrust.

[/COLOR][https://www.cisa.gov/zero-trust-maturity-model](https://www.cisa.gov/zero-trust-maturity-model)

---

### Post by currentshaft on 2024-07-15
> **TheFu said:**
> You understood what was written, so it worked.  And the BBC says Nasa and Noaa and Fbi and Cia  and does the same for lots of abbreviations.  Is this really worth our time?   **TOR** = _T_he _O_nion _R_outer

Call it Tor, if you like.

It's not "what I like" - it's what it is called.

[https://support.torproject.org/about/why-is-it-called-tor/](https://support.torproject.org/about/why-is-it-called-tor/)

> Even though it originally came from an acronym, Tor is not spelled "TOR". Only the first letter is capitalized. In fact,** we can usually spot people who haven't read any of our website (and have instead learned everything they know about Tor from news articles) by the fact that they spell it wrong**.

(emphasis mine)

---

### Post by currentshaft on 2024-07-15
> **dragonfly41 said:**
> In reply to post #19 which sagely opines:

[COLOR=#000000]"Start with a threat model, not window shopping for solutions."

I refer to zerotrust.

[/COLOR][https://www.cisa.gov/zero-trust-maturity-model](https://www.cisa.gov/zero-trust-maturity-model)

You can refer to it all you want, it still is not threat modeling: the only way to objectively guarantee security on a system.

---

### Post by dragonfly41 on 2024-07-15
In context [https://www.reversinglabs.com/blog/zero-trust-and-threat-modeling-is-it-time-for-appsec-to-get-on-board](https://www.reversinglabs.com/blog/zero-trust-and-threat-modeling-is-it-time-for-appsec-to-get-on-board)

Actually I follow *failure avoidance* modelling (another term in corpus linguistics). Human and system failure. Cause and effect.

---

### Post by currentshaft on 2024-07-15
> **dragonfly41 said:**
> In context [https://www.reversinglabs.com/blog/zero-trust-and-threat-modeling-is-it-time-for-appsec-to-get-on-board](https://www.reversinglabs.com/blog/zero-trust-and-threat-modeling-is-it-time-for-appsec-to-get-on-board)

Actually I follow *failure avoidance* modelling (another term in corpus linguistics). Human and system failure. Cause and effect.

I don't know what any of that means, but once again, it is not threat modelling, so ultimately it won't help you.

---

### Post by dragonfly41 on 2024-07-15
We have strayed off piste from OP question.

In simple terms every mission has a probability of success and counter probability of failure. 

If the mission is to protect digital assets against perceived "threats" then both success vectors and failure vectors need to be analysed. Human and system and other dimensions.  Only then can threat modelling come into play based on analysis of multiple opinions by "experts". The principles go back decades to pre Internet. But human failure is often downplayed. There is a Sargossa sea of security and human failures.

[https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html)

END

---

