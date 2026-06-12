---
title: "Web filtering"
date: 2007-11-17
forum: General Help
---

### Post by seanyseansean on 2007-11-17
Hi, 

I need something that will block gambling sites from a ubuntu laptop. I'm normally not a fan of filtering the web, in my mind it's a poor substitute for trust and proper supervision, but my girlfriends sister has a gambling problem which just won't sort itself out.

She's got a windows (eek) computer in her room running K9 Web Protection, which is fantastic, but the family also have a laptop running Gutsy and i'll be damned if I can find a decent blocking tool. It's unfair to ban her from using the laptop (she's not a child), we just need to quietly block gambling sites without me having to monitor urls or otherwise embarrass her.

Lots of sites have blocklists, but they tend to be lacking when it comes to UK sites, which are all she can use with her debit card. I don't want keyword matching which is too hit and miss either. K9 is the only product i've found which blocks everything i've found (and they add new sites I recommend quickly)

I understand that Linspire has SurfSafe, which is essentially K9 for Linux using the same lists and allows me to block gambling without blocking, for example, porn, because if I blocked that i'd have to circumvent the filter myself :D

So has anyone got SurfSafe to work on Linux? Or are there any other suitable options? I'm aware of previous threads about this but they're pretty old. The only other option I can see is to monitor her URL access and block ones in the hosts file that are gambling related, but that is a bit too after the event, and it isn't in my nature to want to nosey into what she browses.

Thanks for any help,

Sean

---

### Post by x64Jimbo on 2007-11-17
Honestly, I don't think this is a job for software. Is she aware that online gambling is illegal and could get her arrested? If you absolutely must have a blocking solution rather than correcting the problem at its source, then I recommend [BadHosts]("http://www.hostsfile.org/hosts.html"). But you're really not solving anything. She'll just start going to the library or a friend's house, and then her debit card number could be in greater risk because you never know what kind of spyware she might run into there. Gambling is an addiction and should be addressed in the same way as a drug addiction - active intervention by friends and family, and counseling.

---

### Post by seanyseansean on 2007-11-17
With all due respect, there is a whole world outside of your home country that isn't in the United States :)

In case that wasn't clear enough - I am in the UK, where online gambling isn't illegal in a vain attempt to prop up state sanctioned and taxed gambling.

She doesn't have a problem in real life, which is where her friends and family look out for her. She lets her guard slip however when online, which is why i'd like her to not have the temptation in front of her.

---

### Post by mellowd on 2007-11-17
I'm not sure if this will work, but there is a program called Moblock that autoupdates itself and runs as a daemon that blocks ranges of ip's. It's mainly used for p2p but I know that it can load various blocklists. Have a look and see if there is a blocklist for these kind of sites.

---

### Post by seanyseansean on 2007-11-17
> **mellowd said:**
> I'm not sure if this will work, but there is a program called Moblock that autoupdates itself and runs as a daemon that blocks ranges of ip's. It's mainly used for p2p but I know that it can load various blocklists. Have a look and see if there is a blocklist for these kind of sites.


Thanks for the reply - unfortunately i've not found a blocklist that is effective for UK gambling sites apart from that used by K9, which isn't publicly available.

---

### Post by x64Jimbo on 2007-11-18
What about using the Windows machine as a proxy for the Ubuntu machine? I know it's a stretch, but it could work.

---

### Post by pgreenberg on 2008-02-28
It is a real problem to block gambling access from Linux or Mac machine (currently there is no good tools to do that). I am a developer for [www.stopchildgambling.org](www.stopchildgambling.org), and we will release new MAC and Linux versions of our tool very soon. Can you tell me which websites or applications she is using? contact me: info at stopchildgambling.org
Popular are FullTiltPoker and PokerStars...

---

### Post by x64Jimbo on 2008-02-29
I don't know how well she knows computers, but you might be able to use a firefox extension to do it. I use LeechBlock to keep myself from wasting time on the Internet in the mornings before I go to work, which seems to work pretty well :)

---

### Post by HermanAB on 2008-02-29
Filtering the web is a job for Squid-proxy and SquidGuard (or Dansguardian).

See this guide: [http://aeronetworks.ca/squidguard-howto.html](http://aeronetworks.ca/squidguard-howto.html)

With SquidGuard, you can easily set up your own rules, while Squid-proxy will make the valid pages load faster, so it is a win-win situation.

For best results, you need to run this on the firewall and set up iptables rules to route port 80 to Squid-cache, to make it 'transparent' - then you don't have to change the configuration of any other machines and it also becomes impossible to avoid.

BTW, Mandriva has a wizard for Squid-cache which turns the whole setup ordeal into a few clicks of a mouse...

Cheers,

Herman

---

