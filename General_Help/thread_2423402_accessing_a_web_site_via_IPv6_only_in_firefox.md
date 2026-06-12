---
title: "accessing a web site via IPv6 only in firefox"
date: 2019-07-22
forum: General Help
---

### Post by Skaperen on 2019-07-22
there is a web site that has both IPv4 and IPv6.  i would like to access it in IPv6, not in IPv4. its DNS has very short TTL and the AAAA records keep changing and the old addresses quit working after about a minute, so, putting its IPv6 in [FONT=courier new]/etc/host[/FONT] will not work. is there a way to get firefox to access it in IPv6, always?  if this causes it to access everything else in IPv6 only, that's even better (e.g i don't need for it to do this with just one domain).

*edit*:

looking in about:config and searching for "dns" i see it has "network.dns.disableIPv6" but nothing like that for IPv4.

it might work to have a DNS cache server (resolving server) that can be configured or patched to delay or drop A records but not AAAA records.

---

### Post by #&amp;thj^% on 2019-07-23
For command line or for browser IPv6 addresses need to be specified by enclosing addresses in square brackets like [2001:4860:0:2001::68].
Then to see if you can use ipv6:
or If you just want the address
```

/sbin/ifconfig tun0 |  awk '/inet6/{print $3}'
```
Change 'tun0' to your net device

---

### Post by Skaperen on 2019-07-23
using IP address in URL results in the HTTP(S) Host: header also having the IP address instead of the domain.  HTTP(S) 1.1 and later servers won't match that unless the IP address is configured as a site.  IOW, it won't work that way on 99.9% of web sites.

---

### Post by #&amp;thj^% on 2019-07-24
Also i completly skipped the fact you may need to edit "/etc/gai.conf"
Mine Now looks like this:
```
cat /etc/gai.conf
# Configuration for getaddrinfo(3).
#
# So far only configuration for the destination address sorting is needed.
# RFC 3484 governs the sorting.  But the RFC also says that system
# administrators should be able to overwrite the defaults.  This can be
# achieved here.
#
# All lines have an initial identifier specifying the option followed by
# up to two values.  Information specified in this file replaces the
# default information.  Complete absence of data of one kind causes the
# appropriate default information to be used.  The supported commands include:
#
# reload  <yes|no>
#    If set to yes, each getaddrinfo(3) call will check whether this file
#    changed and if necessary reload.  This option should not really be
#    used.  There are possible runtime problems.  The default is no.
#
# label   <mask>   <value>
#    Add another rule to the RFC 3484 label table.  See section 2.1 in
#    RFC 3484.  The default is:
#
label ::1/128       0
label ::/0          1
label 2002::/16     2
label ::/96         3
label ::ffff:0:0/96 4
label fec0::/10     5
label fc00::/7      6
#label 2001:0::/32   7
#
#    This default differs from the tables given in RFC 3484 by handling
#    (now obsolete) site-local IPv6 addresses and Unique Local Addresses.
#    The reason for this difference is that these addresses are never
#    NATed while IPv4 site-local addresses most probably are.  Given
#    the precedence of IPv6 over IPv4 (see below) on machines having only
#    site-local IPv4 and IPv6 addresses a lookup for a global address would
#    see the IPv6 be preferred.  The result is a long delay because the
#    site-local IPv6 addresses cannot be used while the IPv4 address is
#    (at least for the foreseeable future) NATed.  We also treat Teredo
#    tunnels special.
#
# precedence  <mask>   <value>
#    Add another rule to the RFC 3484 precedence table.  See section 2.1
#    and 10.3 in RFC 3484.  The default is:
#
#precedence  ::1/128       50
#precedence  ::/0          40
#precedence  2002::/16     30
#precedence ::/96          20
#precedence ::ffff:0:0/96  10
#
#    For sites which prefer IPv4 connections change the last line to
#
#precedence ::ffff:0:0/96  100

#
# scopev4  <mask>  <-value>
#    Add another rule to the RFC 6724 scope table for IPv4 addresses.
#    By default the scope IDs described in section 3.2 in RFC 6724 are
#    used.  Changing these defaults should hardly ever be necessary.
#    The defaults are equivalent to:
#
#scopev4 ::ffff:169.254.0.0/112  2
#scopev4 ::ffff:127.0.0.0/104    2
#scopev4 ::ffff:0.0.0.0/96       14

```

Now I can't remember if a re-start is required.
Addressing can be a bit of a pain, for Example if I ping Google>>**"ping google.com"** I can then get the ipv6 address which produces,**"2607:f8b0:4004:803::1000"** but the address needs to be>**"[2607:f8b0:4004:803]"** or : **"http://[2607:f8b0:4004:803]/"**
I'm no Ipv6 guru by any stretch, in fact I keep it disabled, but took the challenge with your thread, so thanks for that. :)
Also keep in mind, As of recent, Chrome, Firefox as well as derived browsers actually avoid IPv6 if a site responds faster over IPv4. It is not possible to change this behavior by means of a configuration setting.

The feature itself is probably reasonable for the common user but it almost drives me mad that you cannot disable it. IPv6 connectivity is pretty good nowadays and sometimes IPv6 has several advantages over connecting through IPv4 even if latency - due to tunneling - is higher.

---

### Post by Skaperen on 2019-07-24
when you specify the IP address in the URL, how can you also specify the host name (e.g. the name that goes on the HTTP Host: header)?

there is no way to do the above, that i'm aware of.  without the host name in the HTTP(S) request, the vast majority (i could be overestimating this and it might be just a normal majority) of web sites will not deliver the content.  100% of web sites i have set up with Apache are this way.  i have automated the config file generation for Apache at 3 ISPs and ever web site is that way because they all run shared servers.  with HTTPS requiring a domain specific certificate before the headers are received, each web site is on a specific IP address.  but the practice of configuring Apache with host names is still usually done.  now days, there are wild card certificates that allow multiple domains on a single IP address in HTTPS.

i will try configuring [FONT=courier new]/etc/gai.conf[/FONT].

---

### Post by Skaperen on 2019-07-24
in *your* copy of [FONT=courier new]/etc/gai.conf[/FONT], you have uncommented some "label" lines but not any "precedence" lines.  what's up with that?

is [FONT=courier new]::ffff:0:0/96[/FONT] (equivalent to [FONT=courier new]::ffff:0.0.0.0/96[/FONT]) being used for all IPv4 or just IPv4 mapped in IPv6?

which *really* controls sorting,  "label" or "precedence"?

> Also keep in mind, As of recent, Chrome, Firefox as well as derived  browsers actually avoid IPv6 if a site responds faster over IPv4. It is  not possible to change this behavior by means of a configuration  setting.

that's why i am looking for a DNS caching server the is easy to patch (and if needed, build).  there looks to a few written in Python.  my thought is to make delay A-records by 1-2 seconds until it sees a negative response for a AAAA-record.

---

### Post by 1clue on 2019-07-24
There are quite a few common websites which have both ipv4 and ipv6 support.  Based on my experience:
[LIST]
[*]Some of them work correctly.
[*]Some of them have basic IPV6 support but reference things which do not have IPV6 support.
[*]A few of them are ipv6-only
[*]Most have no ipv6 support.
[/LIST]

My router sometimes drops ipv4 support until I reboot it. I don't know why. So major sites (google sites, netflix, etc) still work but most smaller sites don't have support at all. It took me a long time to figure it out the first time.

In my experience, even though wireless routers seem to enable ipv6 by default, many people shut it off.

In my experience, most web site maintainers ignore IPV6 or explicitly disable it in order to only need one set of firewall rules (maybe? IDK)

You can find some ipv6-only sites, such as ipv6.google.com.


Things to keep in mind:
[LIST=1]
[*]DNS works both with IPV4 and IPV6 protocols on the same server.
[*]When you put an IPV4 address in /etc/resolv.conf and that server supports ipv6 (doesn't have it turned off) then you get both versions of addresses.
[*]If the entire chain of dependencies (device, browser, router, ISP, DNS, web site, ...) supports both ipv4 and ipv6, AND everything is correctly working, then the default version used seems to be ipv6.
[*]If a name is registered with both ipv4 and ipv6, the dns software will return all addresses.
[/LIST]

---

### Post by #&amp;thj^% on 2019-07-24
> **Skaperen said:**
> in *your* copy of [FONT=courier new]/etc/gai.conf[/FONT], you have uncommented some "label" lines but not any "precedence" lines.  what's up with that?


It causes confusion.
> **Skaperen said:**
> 

is [FONT=courier new]::ffff:0:0/96[/FONT] (equivalent to [FONT=courier new]::ffff:0.0.0.0/96[/FONT]) being used for all IPv4 or just IPv4 mapped in IPv6?

which *really* controls sorting,  "label" or "precedence"?


 /etc/gai.conf control address selection by label and preferences. ... So far only configuration for the destination address sorting is needed. ... precedence # Add another rule to the RFC 3484 precedence table.

Some other default configuration of glibc on some distros are still to have problems with /etc/hosts. Make sure you have this line in **/etc/host.conf** if you want dual stack to work as it should. 
```

multi on
```
 

This line is required to allow glibc to return multiple addresses when using /etc/hosts, otherwise it will return only the first match. IPv4 or IPv6 only applications.
I should have guessed though that this is on a sever side for you, as I've said I  don't allow ipv6, this was just a effort to help you, not to add frustration.;)
I will wait for it to mature or get implemented when it's picked up by more ISP's.
I remembered your thread a while back here: [https://serverfault.com/questions/824803/make-firefox-and-other-clients-prefer-ipv6](https://serverfault.com/questions/824803/make-firefox-and-other-clients-prefer-ipv6)
that kind of illustrates my point.
Though I can make my browser on a Desktop Work with Ipv6.
here is another site: [http://sf-alpha.bjgang.org/wordpress/2012/08/linux-prefer-ipv4-over-ipv6-in-dual-stack-environment-and-prevent-problems-when-only-ipv4-exists/](http://sf-alpha.bjgang.org/wordpress/2012/08/linux-prefer-ipv4-over-ipv6-in-dual-stack-environment-and-prevent-problems-when-only-ipv4-exists/)
And one more for your reading pleasure:[http://biplane.com.au/blog/?p=122](http://biplane.com.au/blog/?p=122)
You have peaked my interest here and will watch for your input.

---

### Post by 1clue on 2019-07-24
Sorry, more to say about single-stack ipv6-only networks:

Currently the state of the Internet is a dual-stack network. You have:
[LIST=1]
[*]A bunch of IPV4-only sites
[LIST=1]
[*]Old sites set up before ipv6 was taken seriously
[*]Sites which have specifically disabled IPV6 for some reason because their admins:
[LIST=1]
[*]Don't understand ipv6 security
[*]Are too lazy to set up ipv6
[*]Somehow think ipv6 is less worthy?
[*]Simply haven't thought of it (maybe?)
[*]Smell bad and they're stupid.
[/LIST]
[/LIST]

[*]Some IPV6-only sites have been set up by:
[LIST=1]
[*]IPV6 nerds who just want a single stack ipv6 clubhouse, only those who have "graduated" can come in.
[*]Sites hosted in countries with very few IPV4 addresses and can't get anything but IPV6
[LIST=1]
[*]The IPV4 addresses are controlled by the USA, and the addresses are "owned" by the entity they were allotted to. Allocation of IPV4 addresses is highly political.
[*]Countries who don't get along well with the USA tend to not have many ipv6 addresses.
[*]IPV6 addresses are all a temporary pool and can be revoked and repossessed once allocated, and there are so many of them that it would be very difficult to run out of them.
[/LIST]

[*]Companies like Hurricane Electric or Google who are really knowledgeable and have made significant efforts to get the Internet into IPV6.
[/LIST]

[*]Some dual-stack sites:
[LIST=1]
[*]Most mainstream ones are pretty seamless.  Google, news, etc are usually pretty good.
[*]Some misconfigured sites.
[LIST=1]
[*]Corporate sites which are administered by people who do not fully understand but are trying.
[*]Sites whose admins have been pestered for ipv6 support but don't want to take the time to do it right.
[*]???
[/LIST]
[/LIST]
[/LIST]

You can run pretty flawlessly on ipv4-only. There's lots of testing that way, and ipv4 has high visibility.

You can run dual stack pretty flawlessly. This is where the majority of effort is being spent.

You can't run very well on ipv6-only. This is because so much core support is IPV4-only.

If you want flawless Internet from a 6-only network, you will need some sort of 6to4 reverse gateway. This gateway needs to try ipv6 first, and then on a failure try to find the resource on ipv4 and then translate packets from 6 to 4 and back. Most computers are configured for dual stack, so this "gateway" is not necessary. 

The IPV4 Internet exists within the IPV6 address space, but the packets have different formats. Which is why we need a gateway.

Normally 6to4 is used to allow your network to have ipv6 support (probably dual-stack) when your ISP only provides ipv4. I've never tried a 6to4 when the ISP supports IPV6 and you want to add IPV4 access to your 6-only network.

I'm going to go out on a limb here and say that a consumer router will not do this. You'd have to use a highly configurable router, like a Linux box with two or more NICs.

---

### Post by Skaperen on 2019-07-24
i have heard, but not verified, that some porn sites offer more, or more freebies, via IPv6.  i don't know if they do that on their main site or via a different virtual-host that can only be reached by IPv6 and/or only has AAAA records.

yes, you can ask for A records and/or AAAA record from DNS servers via either IPv4 or IPv6.  now i am thinking that adding A record lag to a DNS caching server might best be done for queries received over IPv6.  that way it can be used to serve networks making the transition ... "why is my web site so slow?" ... "because the hosting provider is still using the old internet."

i would put AWS under 3. 2. 3. ??? ... they do have IPv6 in their cloud but not every service can do it (S3 needs to go through CloudFront to be reached via IPv6) and not all elements work smoothly (launching an EC2 instance in the console to listen to a specified IPv6 address in your /64 instead of a randomly chosen one).

only 1 of the 5 colleges i have worked at or attended has their primary web site on IPv6.  another has an AAAA record for an IPv6 address that i have never seen take a connection (or refuse one).

i've visited web sites that do have IPv6 working correctly but i only get an IPv6 connect sometimes.  this is why i wanted to have a way to disable IPv4 in firefox or do something with DNS to favor AAAA records (like delay A records for hosts that AAAA was asked for until a negative answer arrives for AAAA for that host).

Windows and Linux both do IPv6 (so does BSD and OSX ... i don't know about OS/2) so the computer end of things is ready.  too many consumer routers still don't.  too many consumers and small businesses are using old stuff.  i've even seen Windows 95 in use.

reddit.com is still not on IPv6.  their hosting provider (fastly) can do it.

---

### Post by 1clue on 2019-07-24
If you're looking for fingers to point, neither Ubuntu nor Gentoo use ipv6 on their web servers. Several other Linux distribution web sites and forum sites appear to not have ipv6 support either. That said, I'm not sure we really need to push on that. They'll get the message sooner or later, and it also seems that most of the Linux forums are hosted on a third-party website. So the lack of ipv6 support isn't really their fault.

Last time I was on a university network, they were still arguing about whether root domains like .com would be a thing or not, and gopherspace still saw traffic. So I have no idea about ipv6 implementations there.

I don't know about partial implementations of ipv6 on porn (or any other) sites as a security mechanism. That seems like WAY more work than it's worth. IPV6 implementations and defaults are a moving target and that's not likely to change soon. Modern sites have excellent security if it's implemented correctly, no need for ipv4-vs-ipv6 anywhere, or even a real need to put more restricted documents on another site.

What I was talking about is more the idea that some hard-coded link on the site goes to an ipv4-only server, and if that link has functionality instead of just ad space then the site is broken.

---

### Post by Skaperen on 2019-07-24
```

lt2a/forums /home/forums 2> cat /etc/host.conf
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on
lt2a/forums /home/forums 3> 

```
it's already on.

---

### Post by Skaperen on 2019-07-24
[here]("http://ipal.net/osu.tcpdump.xz") is some [FONT=courier new]tcpdump[/FONT] output of me browsing around the [FONT=courier new]www.osu.edu[/FONT] ([FONT=century gothic]The Ohio State University[/FONT]) web site with firefox 68.  there were a number of AAAA records returned, but no connections were ever made in the IPv6 stack.  maybe something is misconfigured?  the only network change i have made is adding the VPN to my VPS server to get IPv6 and obscure my real location ([SIZE=1]although Google figured it out[/SIZE]).

the file is compressed with xz.

---

### Post by Skaperen on 2019-07-25
> **1clue said:**
> If you're looking for fingers to point, neither Ubuntu nor Gentoo use ipv6 on their web servers. Several other Linux distribution web sites and forum sites appear to not have ipv6 support either. That said, I'm not sure we really need to push on that. They'll get the message sooner or later, and it also seems that most of the Linux forums are hosted on a third-party website. So the lack of ipv6 support isn't really their fault.

i guess i can ride the merry-go-round and point outward.

when we start to get lag in IPv4, maybe they will get things going on IPv6.  i want to be a part of that lag.  if i can make things that create the lag where it can result in more pressure on IPv4-only websites to upgrade, then i think that is a good thing.

> **1clue said:**
> Last time I was on a university network, they were still arguing about whether root domains like .com would be a thing or not, and gopherspace still saw traffic. So I have no idea about ipv6 implementations there.

gopher over IPv6 ... i guess that's not a thing.

> **1clue said:**
> I don't know about partial implementations of ipv6 on porn (or any other) sites as a security mechanism. That seems like WAY more work than it's worth. IPV6 implementations and defaults are a moving target and that's not likely to change soon. Modern sites have excellent security if it's implemented correctly, no need for ipv4-vs-ipv6 anywhere, or even a real need to put more restricted documents on another site.

i think it's the porn site operators trying to boost IPv6 by making their sites "better" for those who access via IPv6.  i can envision a few ways to do that.  one way would be [https://ipv6.example.com/](https://ipv6.example.com/) offering more stuff and/or more of it being free instead of pay.  i have talked with one porn site operator and he was very technical and knew his way around Linux and networking (but this was about 20 years ago, before i saw pressure to bring up IPv6 (and before Cisco routers normally did it).

> **1clue said:**
> What I was talking about is more the idea that some hard-coded link on the site goes to an ipv4-only server, and if that link has functionality instead of just ad space then the site is broken.

i think it's just the operators wanting to see more IPv6.  but they don't need to break links to do it.  whatever means they use to deny access for those who have not logged in with their payment authorized account can check if the request is via IPv6 or is in their IPv6-only mirror site and allow the access that way.  or they can have a "ipv6 pw=freebies" userid, or such, that only works if coming in via IPv6.

there are many ways to program web sites.

---

### Post by 1clue on 2019-07-26
> **Skaperen said:**
> ...

i think it's the porn site operators trying to boost IPv6 by making their sites "better" for those who access via IPv6.  i can envision a few ways to do that.  one way would be [https://ipv6.example.com/](https://ipv6.example.com/) offering more stuff and/or more of it being free instead of pay.  i have talked with one porn site operator and he was very technical and knew his way around Linux and networking (but this was about 20 years ago, before i saw pressure to bring up IPv6 (and before Cisco routers normally did it).

i think it's just the operators wanting to see more IPv6.  but they don't need to break links to do it.  whatever means they use to deny access for those who have not logged in with their payment authorized account can check if the request is via IPv6 or is in their IPv6-only mirror site and allow the access that way.  or they can have a "ipv6 pw=freebies" userid, or such, that only works if coming in via IPv6.

there are many ways to program web sites.

I can't say I have familiarity with porn sites in general, and can't understand why you're focused on that.

In general, they are interested in generating revenue from anyone willing to pay for it. So the very idea of limiting access to revenue-generating content based on something the end user has no control of is not at all logical. It's very clearly a way to get less money than you could without the restriction.

There may be some commercial for-profit site operator somewhere who chooses to use IPV6 as a selector for access to special features, but I'd have to call that an aberration.

In the case I mentioned before, organizations who are trying to promote IPV6 for anyone interested in IPV6, it makes sense to offer some sites ONLY to IPV6 capable systems, for testing and validation purposes.

---

### Post by Skaperen on 2019-07-26
i'm not focused on porn sites.  i've heard that or read it somewhere.  given that and the possibility of them being techies who run some of them and some advantages of IPv6, i'm just speculating about that reason.  perhaps they believe that in the future, more people using IPv6 will improve their revenue.  i can believe that it could, given that much of IPv6 runs on newer routers.  i heard this about 7 years ago, and they may have stopped giving stuff away on IPv6.  i have no intention to go find out.

the one operator i talked to hired me from remote to go to his colo and bring his servers back up.  5 of them didn't come back up after a power failure.  he lived over 1000 miles away and could not get a flight to do it himself because it was the week right after 9/11.  he even offered free access but i preferred the money instead.  he paid promptly.

i do plan to make more of my stuff available to IPv6 users, once i figure out the best way to do that on AWS.

i remember back in the 1960s when the UHF TV band was said to offer more TV.  we just got a new TV with a UHF dial.  i bought a UHF antenna and set it up.  i got 2 new channels (WTAP and WOUB) and later a 3rd (WPBO).  i have since moved from that area and have heard that WPBO is no longer on the air.

---

### Post by #&amp;thj^% on 2019-07-26
Glad to hear your not focused on the sites mentioned, notice my brief lack in reply's.
Adoption of IPv6 has been delayed in part due to network address translation (NAT), which takes private IP addresses and turns them into public IP addresses. That way a corporate machine with a private IP address can send to and receive packets from machines located outside the private network that have public IP addresses. (For one example)

Carrier networks and ISPs have been the first group to start deploying IPv6 on their networks, with mobile networks leading the charge. For example, T-Mobile USA has more than 90% of its traffic going over IPv6, with Verizon Wireless close behind at 82.25% (I'm on Verizon now). Comcast and AT&T have its networks at 63% and 65%, respectively, according to the industry group.

When will more deployments occur?

The Internet Society said the price of IPv4 addresses will peak in 2019, and then prices will drop after IPv6 deployment passes the 50% mark. Currently, according to Google, the world has 20% to 22% IPv6 adoption, but in the U.S. it&#8217;s about 32%).

As the price of IPv4 addresses begin to drop, the Internet Society suggests that enterprises sell off their existing IPv4 addresses to help fund IPv6 deployment. The Massachusetts Institute of Technology has done this, according to a note posted on GitHub. The university concluded that 8 million of its IPv4 addresses were &#8220;excess&#8221; and could be sold without impacting current or future needs since it also holds 20 nonillion IPv6 addresses. (A nonillion is the numeral one followed by 30 zeroes.)
Whew I don't have enough fingers and toe's for that one. ;)
Discussion found here: [https://gist.github.com/simonster/e22e50cd52b7dffcf5a4db2b8ea4cce0](https://gist.github.com/simonster/e22e50cd52b7dffcf5a4db2b8ea4cce0)
[At our current rate of progress, IPv6 will be fully implemented on May 10, 2148]("https://venturebeat.com/2013/06/07/at-our-current-rate-of-progress-ipv6-will-be-fully-implemented-on-may-10-2048/")

---

### Post by Skaperen on 2019-07-27
yeah, lots of big numbers. i have many /56s in AWS where i can divide each one into a /64 per subnet.  basically have a huge number of addresses but it's hard to make use of them, especially if i pick one address in all those /56s and try to use it.  i have find whap VPC it's on and create a subnet with its /64.  then i can launch an instance there.

/56 = 4,722,366,482,869,645,213,696 addresses

---

