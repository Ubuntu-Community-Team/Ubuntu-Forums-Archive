---
title: "Thunderbird EHLO / HELO string"
date: 2014-03-03
forum: General Help
---

### Post by Newbunto on 2014-03-03
Is there any way to control by preferences what Thunderbird sends for the EHLO / HELO string?

The current behaviour seems to be to send "[a.b.c.d]" where a.b.c.d is my private IP address. (I am, like most people, behind NAT.)

I see from discussion on the net that I am not the only one to raise this issue but I haven't found a solution.

There are numerous possible objections to the current behaviour. (All the following discussion assumes that the SMTP server that is being used is somewhere on the internet i.e. not on my private network. For example, it might be my ISP's SMTP server.)

1. It is a security and privacy failing that a private IP address is revealed.

2. The private IP address is at best meaningless to the SMTP server.

3. Some SMTP servers will complain that the claimed IP address does not match the client's actual IP address (which will have been NATted).

Since an SMTP client doesn't exactly know whether the SMTP is on my private network, and whether NAT will occur, and since it is difficult for the SMTP client to determine the WAN IP address, the only sensible option here would seem to be that the user can override the string to be sent.

Ideally that would be on a per-SMTP server or per-account basis (since Thunderbird may have multiple accounts configured and those accounts may be using different SMTP servers and hence the desired EHLO string may be different). However I think I can get by with a single EHLO string for all SMTP servers and all accounts.

A partial workaround is to run the SMTP session through a local TCP relay. Then Thunderbird sends [127.0.0.1], which is equally bogus to the SMTP server, but at least does not raise security or privacy issues.

Another possible workaround (not tested) is to send all mail through an SMTP server that *is* on the private network and arrange for that server when relaying the email on as an SMTP client to

a) do better

b) censor (drop or alter) the original Received header

but that is a fairly heavyweight solution.

Thunderbird version is 24.3.0 but I think this has probably been an issue "forever" if it can't currently be done.

---

### Post by Newbunto on 2014-03-24
No takers?

---

