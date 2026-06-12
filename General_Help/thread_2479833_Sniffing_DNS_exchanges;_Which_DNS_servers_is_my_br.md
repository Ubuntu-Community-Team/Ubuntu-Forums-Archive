---
title: "Sniffing DNS exchanges; Which DNS servers is my browser *actually* using."
date: 2022-10-09
forum: General Help
---

### Post by david503 on 2022-10-09
I'm having DNS problems in my browser (Chrome Version 99.0.4844.51 (Official Build) (64-bit)) 
Ubuntu 18.04 (yes I'm getting a new PC and installing 22 haha)

I change it in the settings, tried many different free DNS servers, starting with 8.8.8.8, and then many others as second.  I can list them but you get the idea.  I've tried doing the same thing with the router settings, restarting it, etc.  I looked at the proxy settings in chrome. 

I'm still getting flakey DNS errors in the browser, and (not surprisingly) problems on sites where like (pretty obviously) AJAX calls aren't coming back. 

So, I'm fed up and what I want to do is sniff the DNS transactions.  I want to know, unambiguously, what DNS severs the browser is *actually using*.  

As in, not settings and config files, no, I want to see the actual exchanges.

Thanks,

-dw

---

### Post by #&amp;thj^% on 2022-10-09
I hope I'm guessing right, but I'll use a few to check:
1st:
```
( nmcli dev list || nmcli dev show ) 2>/dev/null | grep DNS
```
2nd:
```
sudo tcpdump -vv -i eno1 -W 1200 | grep google.com
```
Change eno1 to what your sniffing from.
3rd:
```
nmcli dev show | grep DNS | sed 's/\s\s*/\t/g' | cut -f 2

```
EDIT: Crap I forgot one:
4th:
```
nslookup google.com 

```

---

### Post by MAFoElffen on 2022-10-10
One more... (LOL)
```

dig google.com

```

---

### Post by #&amp;thj^% on 2022-10-10
> **MAFoElffen said:**
> One more... (LOL)
```

dig google.com

```

Nice I forgot that one, to the OP, The dig command in Linux is used to gather DNS information. It stands for Domain Information Groper, and it collects data about Domain Name ...
if more info is needed I'll also use:
```
dig google.com ANY

```

---

### Post by Holger_Gehrke on 2022-10-10
You are aware that Chrome, Chromium and Firefox all like to do DNS over HTTPS ? Unless you switch this off, you can play around with system wide DNS settings all you want without changing anything as far as the browser is concerned ...

Holger

---

### Post by #&amp;thj^% on 2022-10-10
> **Holger_Gehrke said:**
> You are aware that Chrome, Chromium and Firefox all like to do DNS over HTTPS ? Unless you switch this off, you can play around with system wide DNS settings all you want without changing anything as far as the browser is concerned ...

Holger
Who we speaking to? But yes I am. :D
However that is good info for the OP to know. ;)
> Secure DNS

We weren&#8217;t able to detect whether you were using a DNS resolver over secure transport. Contact your DNS provider or try using 1.1.1.1 for fast & secure DNS.
```
Test complete

Query round	Progress...	Servers found
1		......		1
2		......		1
3		......		1
4		......		1
5		......		1
6		......		1

IP 	Hostname 	ISP 	Country
193.37.254.3 	None 	M247 Europe SRL 	Phoenix, United States 
```

---

### Post by The Cog on 2022-10-10
host -v google.com
is another one.

Also, remember that a browser may be using a proxy rather than doing DNS queries itself.

---

### Post by #&amp;thj^% on 2022-10-10
> **david503 said:**
> 
So, I'm fed up and what I want to do is sniff the DNS transactions.  I want to know, unambiguously, what DNS severs the browser is *actually using*.  

As in, not settings and config files, no, I want to see the actual exchanges.

Thanks,

-dw
I did guess wrong, for that I'd use: dnscap :[https://manpages.ubuntu.com/manpages/impish/man1/dnscap.1.html](https://manpages.ubuntu.com/manpages/impish/man1/dnscap.1.html)
Description:
```
dnscap  is  a  network capture utility designed specifically for DNS traffic.  It normally
       produces binary data in pcap(3) format, either on standard output  or  from  files.   This
       utility is similar to tcpdump(1), but has finer grained packet recognition tailored to DNS
       transactions and protocol options.  dnscap is expected to be used for gathering continuous
       research or audit traces.

```

---

### Post by #&amp;thj^% on 2022-10-10
> **The Cog said:**
> host -v google.com
is another one.



Nice, I like this one. First I've seen it, thanks.

---

### Post by david503 on 2022-10-10
[COLOR=#000000]@MAFoElffen[/COLOR]
> 

[COLOR=#000000]Nice I forgot that one, to the OP, The dig command in Linux is used to gather DNS information. It stands for Domain Information Groper, and it collects data about Domain Name ...[/COLOR]
[COLOR=#000000]if more info is needed I'll also use:[/COLOR]



Yea, I'm very well aware of that. (I've been writing software 25 years after graduation.)  
Not that I'm ungrateful, I'm just way past that.


The browser could be doing something sneaky.  There are actually settings in the browser that can mess with what the OS wants, as another commenter after you alluded too.  

In general there's a handful of ways DNS is actually determined.

And for that matter- even with dig- remember I said the DNS is "flaky".  It doesn't outright "not work", it works "most of the time".  I've seen that happen with DNS before- flakey behavior like 5 or 10 years ago and I had solved it by just switched to different DNS servers, but that's not working here. 

So even if the browser actually was using the OS's DNS settings, I couldn't tell from just running some digs.  It "mostly works but it's flaky". The digs would seem normal.  

I could be nutty and write some script that perioedically does digs and logs the results... or instead I could just sniff the damn exchanges, hence why I'm here. 

Hence you see, I want to throw everything out and sniff so I get the *ACTUAL* DNS.

thanks,

dw

---

### Post by MAFoElffen on 2022-10-10
@David503

LOL. You quoted fallen1. It seems you referred to my one short post for everyone's page of answers. You seemed somewhat offended. I am respectful and not in the least offended by any of your responses. (I see your frustration.) So I will respond. 

Yes. DNS behavior can be overridden by the browser app and also in the nsswitch settings of /etc/nsswitch (setting precedence and behaviors). I usually refer back to reminders at [https://docs.oracle.com/cd/E19683-01/806-4077/6jd6blbbb/index.html](https://docs.oracle.com/cd/E19683-01/806-4077/6jd6blbbb/index.html) for making changes to nsswitch, even though dated... (I used to support Solaris.) It is still pertinent.

Yes, you are in good company then. I've been Programming for over 40 years now, and been an Information Technology Professional for almost as long. I've also taught college level Computer Science.

I do understand what you are doing. If I am doing 'sniffing', I still use WireShark to look at the actual network packets and then set filters ( udp.port == 53 ) to just what I want to capture and look at. That way you can see the exact exchange and conversation between. That is a lot more user friendly than using tcpdump, and more real-time than using dig in a script (which is not going to tell you what was said).

It's funny how not a lot of people remember that WireShark exists and know how to use it. That might be just what you are looking for, for what level you want to see.

---

### Post by david503 on 2022-10-10
Oh oops yea I quoted the wrong guy, sorry

No not offended at all hence the "not that I'm ungrateful". 

I figured if someone's giving advice to run dig, I should indicate that I'm way past that, yknow.  It's more efficient.

I never heard of [COLOR=#000000]WireShark, thanks, it looks good.

Weird thing is that the DNS doesn't seem to be flaking out as much now. (Fingers crossed).  I don't know what happened, maybe it was something on google's side (8.8.8.8)?  

Or maybe my isp was just flakey in general and the most evident visible way to notice it was DNS fails.    

But y'know, I'm still gonna look at wireshark just for fun.

40 years, cool, yea, I just figured if I'm getting advice like running dig, then I should give background to show that I'm deeper into the jungle of the problem and why.

thanks again,

dw
[/COLOR]

---

### Post by The Cog on 2022-10-11
If you really want to see what's happening, then sniffing is the way to go. If you're on a server, then I would suggest tcpdump because it's always there. But on a workstation where you have a GUI, wireshark is really the tool to use. You can learn a lot about the protocols with wireshark because it shows how the packets break down into individual fields (provided that the connections is not encrypted). In comparison, the tcpdump output is limited and quite cryptic.
When sniffing DNS queries (UDP port 53) remember that the PC can do an amount of local caching - you may have to query made-up names rather than repeatedly query the same name if you want to capture queries on the wire.

---

### Post by dragonfly41 on 2022-10-11
Perhaps a free account with opendns.com might help. The dashboard is useful.
You can switch to their DNS servers.

---

### Post by david503 on 2022-10-11
Thanks, yea, I had tried some recommended by this page:

[https://linuxize.com/post/how-to-set-dns-nameservers-on-ubuntu-18-04/](https://linuxize.com/post/how-to-set-dns-nameservers-on-ubuntu-18-04/)

The excerpt:
> 
Google (8.8.8.8, 8.8.4.4)
Cloudflare (1.1.1.1 and 1.0.0.1)
OpenDNS (208.67.222.222, 208.67.220.220)
Level3 (209.244.0.3, 209.244.0.4)


Still got the flakiness (which is mysteriously resolved). 
But yea that's a good recommendation but I already did that.
(btw you don't need an account to use their DNS servers, obviously.)

Well hence my frustration trying those with no success and as I said in my op post "fed up, I want to just sniff it". ha.

but thanks, that's a good recomendation,

dw

---

### Post by dragonfly41 on 2022-10-11
> [COLOR=#000000](btw you don't need an account to use their DNS servers, obviously.)[/COLOR]

The account gives you access to dashboard history of usage which can be very useful if, say, you are in a shared home where you need to manage parental control. In my case I don't need that but access log is useful.

P.S. adding this other tool for tracking external domains web sites etc..

[http://dns.squish.net/](http://dns.squish.net/)

---

### Post by #&amp;thj^% on 2022-10-11
> **david503 said:**
> Oh oops yea I quoted the wrong guy, sorry

No not offended at all hence the "not that I'm ungrateful". 

I figured if someone's giving advice to run dig, I should indicate that I'm way past that, yknow.  It's more efficient.

It's always a good idea to post what you have tried, so I/we don't waste each other time. just makes good sense right?

The Cog's #13 is the way I set up for sniffing.
> **The Cog said:**
> If you really want to see what's happening, then sniffing is the way to go. If you're on a server, then I would suggest tcpdump because it's always there. But on a workstation where you have a GUI, wireshark is really the tool to use. You can learn a lot about the protocols with wireshark because it shows how the packets break down into individual fields (provided that the connections is not encrypted). In comparison, the tcpdump output is limited and quite cryptic.
_When sniffing DNS queries (UDP port 53) remember that the PC can do an amount of local caching - you may have to query made-up names rather than repeatedly query the same name if you want to capture queries on the wire._
Nicely put.
Very Important for anyone.
I'll check open ports as well:
```
sudo ss -tulpn
[sudo] password for me: 
Netid   State    Recv-Q   Send-Q     Local Address:Port      Peer Address:Port  Process                                                                         
udp     UNCONN   0        0                0.0.0.0:41446          0.0.0.0:*      users:(("nordvpnd",pid=1659,fd=31))                                            
udp     UNCONN   0        0                0.0.0.0:58010          0.0.0.0:*                                                                                     
tcp     LISTEN   0        1              127.0.0.1:9349           0.0.0.0:*      users:(("eddie-cli-eleva",pid=645,fd=3))                                       
tcp     LISTEN   0        128            127.0.0.1:631            0.0.0.0:*      users:(("cupsd",pid=644,fd=7))                                                 
tcp     LISTEN   0        128              0.0.0.0:22             0.0.0.0:*      users:(("sshd",pid=647,fd=3))                                          
```
Added info may be useful for someone besides the OP:
```
sudo lsof -i -P -n | grep LISTEN
cupsd       644 root    7u  IPv4  22945      0t0  TCP 127.0.0.1:631 (LISTEN)
eddie-cli   645 root    3u  IPv4  25004      0t0  TCP 127.0.0.1:9349 (LISTEN)
sshd        647 root    3u  IPv4  26665      0t0  TCP *:22 (LISTEN)


```

---

### Post by david503 on 2022-10-11
> **1fallen said:**
> It's always a good idea to post what you have tried, so I/we don't waste each other time. just makes good sense right?



Well I can push back on that- my post was specifically asking about how to sniff the DNS transactions that the browser is making.  (I mean look at the title.)  
And afaik you can't sniff with dig, right? And it's totally outside of the browser.  So ironically mentioning (or even involving) dig would be, as you put it "wasting each other's time".  No?   Can it sniff browser transactions?  I mean I get that we're all brainstorming, but I rightfully didn't mention it. 

Nonetheless!  You guys are great, and I'll install wireshark and even though the browser isn't acting up any more I'll try some of the CLI stuff here just because I like learning stuff. 

Thanks again!!

---

### Post by dragonfly41 on 2022-10-12
> [COLOR=#000000]And it's totally outside of the browser. [/COLOR]

There is Developer Tools in my browser(s) which give more insights.

Click on the "hamburger" icon, top right, them More Tools > Developer Tools.

---

### Post by david503 on 2022-10-12
> **dragonfly41 said:**
> There is Developer Tools in my browser(s) which give more insights.

Click on the "hamburger" icon, top right, them More Tools > Developer Tools.

Oh for sure I was in there, but I don't think it lets you sniff dns transactions.  Hmm there's a lot in there, maybe you might know something I don't (not suprisingly!)  There might be a way for it to show individual http transactions, but DNS too?  hmm but the browsers can do dns over http....  

Anyway I'll go with the other (great) suggestions for now, but as a curiosity I might check and see if it's possible in the dev side panel.

---

### Post by MAFoElffen on 2022-10-12
One more thing... You had mentioned that you are using Google Chrome...

Google Chrome has a setting under Settings > Security > Secure DNS, to use the system DNS or Custom, where you can choose different DNS sources...

If that option is choosen, it would change your DNS source for that browser..

For network sniffing, for servers and such, I use my own laptop (with WireShark) and plug in with my own "hub" ***between*** connections. I don't need to run a network sniff from an existing machine on the network. That is how I "*listen in*" to diagnose customer networks and their troubles. Most commercial networks have their unused switch and router ports turned off in their configs for security.

---

### Post by #&amp;thj^% on 2022-10-12
> **david503 said:**
> Well I can push back on that- my post was specifically asking about how to sniff the DNS transactions that the browser is making.  (I mean look at the title.)  
And afaik you can't sniff with dig, right? And it's totally outside of the browser.  So ironically mentioning (or even involving) dig would be, as you put it "wasting each other's time".  No?   Can it sniff browser transactions?  I mean I get that we're all brainstorming, but I rightfully didn't mention it. 

Nonetheless!  You guys are great, and I'll install wireshark and even though the browser isn't acting up any more I'll try some of the CLI stuff here just because I like learning stuff. 

Thanks again!!
Well there is this as well>>"Which DNS servers is my browser *actually* using."
But yes dig is not a good tool for DNS sniffing, it can be done but it's over my pay scale here. ;)
```
dig +trace www.example.com

```
You had a whole day of letting all involved here posting/offering useless "to you" information.
Now we know what your truly after, the provided info has meaning and use for yourself.

---

### Post by #&amp;thj^% on 2022-10-12
> **MAFoElffen said:**
> 
For network sniffing, for servers and such, I use my own laptop (with WireShark) and plug in with my own "hub" ***between*** connections. I don't need to run a network sniff from an existing machine on the network. That is how I "*listen in*" to diagnose customer networks and their troubles. Most commercial networks have their unused switch and router ports turned off in their configs for security.

Brilliant, I'll still *at* times to resort to terminal.
I wrote an old script about a year ago for my server, using "tcpdump" and found it worth while for "me" .
It went as follows:
```
sudo tcpdump -vvli eth0 port 53 | grep --line-buffered " q: A? " | cut -d' ' -f16- >dns-sniff.txt
```
Change "eth0" to your device to sniff from. IE, eno1, tun0, etc, etc.
That will print to a text document, as nothing should show from the terminal, and to view it I use:
```
less dns-sniff.txt
```
For Desktops I always use Wireshark period, outside of checking ports manually.

---

### Post by david503 on 2022-10-12
> **1fallen said:**
> Well there is this as well>>"Which DNS servers is my browser *actually* using."
But yes dig is not a good tool for DNS sniffing, it can be done but it's over my pay scale here. ;)
You had a whole day of letting all involved here posting/offering useless "to you" information.
Now we know what your truly after, the provided info has meaning and use for yourself.

Ummmm... "truly after"? The title alone makes it vividly clear that DNS transaction sniffing was what I was "truly after", let alone the content my op post.  It's not ambiguous.  The beginning of the tile; "Sniffing DNS exchanges".  Well hence almost all of the comments were (brillinatly) about that, so apparently everyone else got it.  
Speaking of which- I've said twice how useful the majority information has been for the "whole day".  Useless "to me" information? Um only the dig recommendation.

---

### Post by #&amp;thj^% on 2022-10-12
> **david503 said:**
> Um only the dig recommendation.

**There is more to "dig" than meets the eye.**
My apologies then for wasting your time, it won't happen again.
All I did for clarity is offer the DIG definition, which you already knew, and showed your frustration I guess I should be a mind reader as well.
We all tend to believe that someone who thinks differently from us is poorly informed or dangerously misinformed. 
Be Well!

---

### Post by david503 on 2022-10-12
> **1fallen said:**
> **There is more to "dig" than meets the eye.**
All I did for clarity is offer the DIG definition, which you already knew, and showed your frustration I guess I should be a mind reader as well.


It doesn't take a mind reader, it takes a title and post reader.  Again, everyone else got it. 

But I'm definitely intrigued to know that dig has like, a "listen mode", or something? I'll make a new post asking about that. So it can see sniff all the transactions going by, not just it's own queries?  (Well I guess admittedly I should post the question in a general linux forum like linuxquestions.org.)

But that's amazing to know, thanks.

---

