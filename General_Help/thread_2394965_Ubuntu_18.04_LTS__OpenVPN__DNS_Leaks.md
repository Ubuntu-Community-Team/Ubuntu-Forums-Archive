---
title: "Ubuntu 18.04 LTS / OpenVPN / DNS Leaks"
date: 2018-06-24
forum: General Help
---

### Post by antigonish2 on 2018-06-24
Earlier last year, I went right out of my skull trying to solve a DNS leak problem when using a VPN on Ubuntu 16.04 LTS.  I found a [work around]("https://www.youtube.com/watch?v=hFbvrIQpeaQ") that has served me well.  It works flawlessly as a matter of fact and it amazes me that no further recognition of the problem can be found on searches, much less an acknowledgement that there even was a problem from Ubuntu.  If there was I'd love to see it.

Later on last year, I tried to upgrade to 17.10, but the same DNS leak problem cropped up again and this time there was no workable solution that I could find.  Adding to the frustration, my own VPN provider stated that in Linux, there is no such thing as a DNS leak and that if anyone posting to their forum pressed the matter, their posts would be deleted, so he wasn't any help.  I wound up reverting to 16.04 again.  I just discovered that the author of the solution for leaks in 16.04, linked to above in the first paragraph, has posted a [solution to leaks in Ubuntu 17]("https://www.reddit.com/r/PrivateInternetAccess/comments/8gvhyw/does_dns_leak_when_using_openvpn_in_ubuntu_1804/").  I don't know if it works, or if it would work in 18.04, hence I pose the question again:

[SIZE=4][B]Is anyone currently using 18.04 with a VPN, experiencing DNS Leaks?  
[/B][/SIZE]The only on line reference to there even being a dns leak problem with 18.04, is a question posed by [this chap]("https://www.reddit.com/r/PrivateInternetAccess/comments/8gvhyw/does_dns_leak_when_using_openvpn_in_ubuntu_1804/") on Reddit.  He seems to have found out the problem could still exist and is seeking information on a solution.  Read it and see how he gets the runaround and nobody answers the question.  I got much the same treatment on another forum, so I would hate to see this post follow the same pattern.  

So, again, is there a known problem?  Is there a known solution?

---

### Post by kazakore on 2018-06-24
I know the report page for the VPN I use says I don't have any, but I used to use their own app until I upgraded to 18.04 and it doesn't work so I'm now using WireGuard. Maybe see if your VPN supports WireGuard??

Sorry if that's not much help. Not gone with a straight OpenVPN install....

---

### Post by dwayne222 on 2018-07-06
I have also checked some time the DNS was leaking on 18.4, but it was the causing by VPN side then I have changed the VPN to [Ivacy VPN]("https://www.usavpn.com/ivacy-review/"), and the issue gets resolved. I think it depends on the VPN quality also.

---

### Post by capedbaldy on 2018-08-10
Tested on different VPNs and there was leak on all of them. So yeah, Ubuntu 18.04 leaking DNS with OpenVPN.

---

### Post by gerryg001 on 2018-09-25
This issue usually has little to do with the particular VPN. If you don't need local name resolution, you may be able to remove the local router or ISP dns when the VPN is active, and switch to the VPN's dns if it has one, or enter 1.1.1.1,8.8.8.8 or similar, which would be accessed via the VPN.

However, I have not seen any configuration entries that will do this, other than your entering up/down scripts with fixed IP's for dns. I don't recall if I've proven this, as what I needed to solve was the case with local name resolution.

Note that using the DNS Leak tests on the internet may return inconsistent results, so I directly monitored the requests using wireshark. Several people gave solutions that wireshark then proved to be false.

Now, if you need to retain local name resolution, nothing seems to work. The doc says it will handle up to 3 dns ip's, and only use the 2nd one if the 1st either doesn't find the name or takes too long. However, monitoring with wireshark proves this false. For 3 dns ip's, it will typically use all three, but not every time. Further, with the local router as the 3rd dns ip, it will sometimes stop at the first one (e.g. 1.1.1.1) and report not found. This is further complicated by it making requests for other DNS records that it doesn't need to satisfy your simple name resolution, and the order in which those requests are interleaved may vary. I cannot relate the behavior to the timing shown in wireshark, so something else is involved.

My testing was done in a fresh (and updated) install of 18.04, and rewritten from a backup after each attempt at a solution, to maintain a consistent starting point. Therefore, to answer your first question if anybody is experiencing 18.04 DNS leaks, I would say Yes, Most people are!

Curiously, a fresh 18.04 behaves somewhat differently than a fresh 16.04->upgraded-to-18.04 and I have not been able to determine the reason.

---

### Post by khalidxpert on 2018-10-19
i want to install vpn on my ubunto server any one can help me with step to step guide ?

---

