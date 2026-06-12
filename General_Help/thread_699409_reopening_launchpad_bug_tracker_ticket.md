---
title: "reopening launchpad bug tracker ticket"
date: 2008-02-17
forum: General Help
---

### Post by Ba66e77 on 2008-02-17
I've been having a problem with my Gutsy laptop not being able to connect to my linksys WRE54g expander and found a bug ticket closed on it for lack of information.  I've added the information as a comment ([https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/61505](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/61505)) but can't find how to reopen the ticket.  Can someone tell me how to do that?

---

### Post by saultpastor on 2008-02-18
I'm having the same issue with a wre54g right now.  I have been using a Linksys at work and a Dlink at home with no issue, but I'm on vacation right now and this expander works with one laptop on Gutsy with an Atheros card using Madwifi.  The laptop that is not connecting correctly is using a Broadcom card and Ndiswrapper.  It sometimes connects but then has terrible speed issues.  Sometimes it doesn't connect at all and once it was doing good but the next time I tried it wouldn't connect at all.

Does anyone have a workaround, I'm here for a month and I need this laptop, any help would be greatly appreciated.

Thanks

---

### Post by seventhc on 2008-02-18
This might help
[https://lists.ubuntu.com/archives/launchpad-users/2007-August/001926.html](https://lists.ubuntu.com/archives/launchpad-users/2007-August/001926.html)
Also if you scroll down from the link that you gave, there is a place to file a bug for 
[LIST]
[*]             [Report another bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+filebug")             about network-manager in ubuntu[/LIST]

---

### Post by Ba66e77 on 2008-02-18
Thanks, seventhc

saultpastor, I think the only solutions are to change your wifi card or your expander.  There doesn't appear to be a "fix" for this problem.

---

### Post by saultpastor on 2008-03-02
Thanks for the feedback, for me the problem was resolved by setting up a static ip for my laptop and one on the router.  It seemed the router was having problems assigning an ip through the RE.  It still doesn't work well and is slow at times for no reason.  It also drops out often but I'm getting by and I'm on vacation so I don't need to do much with it. 

Thanks!

---

