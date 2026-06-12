---
title: "ubuntu+thunderbird+VPN: unable to send emails"
date: 2017-10-22
forum: General Help
---

### Post by gonzobilbao on 2017-10-22
Hi all,

Not sure where to post this exactly, sorry if it is not the right place.

I have a VPN connection that I use quite frequently, and I've been having problems lately to send emails from my ubuntu machine, using thunderbird. Before I used to have problems only when *not* connected to the vpn (which seems very unusual, as I have seen people having a similar problem when connected to the vpn). But now I am not able to send when connected and when not connected to the vpn. I am able to download messages though.

I get the following error when sending emails:

```
Sending of the message failed.
An error occurred while sending mail: Outgoing server (SMTP) smtp-mail.outlook.com is unknown. The server may be incorrectly configured. Please verify that your Outgoing server (SMTP) settings are correct and try again.
```
I have checked the outgoing server settings (everything seems normal)
I have deleted my email accounts (outlook and openmailbox) in Thunderbird and re-added them, no success.
In my other computers I can access and send emails via thunderbird, with and without the vpn connection.


Any pointers?

Thanks!

---

### Post by DuckHook on 2017-10-23
[LIST=1]
[*]Have you tried clearing TBird's cache, cookies and history?
[*]Are you sure there's no subtle typo, or something as seemingly innocuous as an extra space in your server settings?
[/LIST]
One of my mail providers uses different server settings if one is connecting from outside its network vs from inside. Also, one must first authorize outside connections from one's customer settings web page. Perhaps check for such nuances with your mail provider.

Some mail providers (again, one of mine) don't work with some VPNs but do work with others. This may be a result of automated spam blocking algorithms since many spammers hide behind VPNs. There's no other option in such cases except to contact your mail hosting service and discuss. It will take some detective work.

---

### Post by gonzobilbao on 2017-10-28
Hi, 
thanks DuckHook for taking the time to answer my question

Here is an update on the issue:

-I installed another email client on my ubuntu partition. same problem (won´t sen emails, but downloads and folder sync is ok)

On my W10 partition, I have tried to send an email with thunderbird, with the following results:
-when not connected to my vpn: can perform all actions (send,receive, sync)
-when connected: same problem as in the ubuntu partition (and same error message)
-when connected, after flushing cache using  ipconfig /flushdns commad: everything works fine.

My outgoing server settings (SMTP) are the same in my W10 and ubuntu partitions, so that does not seem to be the problem.


I seems that my DNS cache may have something to do with it, and not thunderbird -or outlook itself (although I tried what you suggested, I am still unable to send emails). I don't know how to flush it (if indeed this is causing the problem). And in [this thread ]("https://superuser.com/questions/134762/how-to-clear-dns-cache-in-ubuntu/163296#163296")it says that ubuntu does not cache DNS at all, so not sure what to do.

Any ideas?
Cheers!

---

### Post by #&amp;thj^% on 2017-10-28
> **gonzobilbao said:**
> Hi, 
thanks DuckHook for taking the time to answer my question

Here is an update on the issue:

-I installed another email client on my ubuntu partition. same problem (won´t sen emails, but downloads and folder sync is ok)

On my W10 partition, I have tried to send an email with thunderbird, with the following results:
-when not connected to my vpn: can perform all actions (send,receive, sync)
-when connected: same problem as in the ubuntu partition (and same error message)
-when connected, after flushing cache using  ipconfig /flushdns commad: everything works fine.

My outgoing server settings (SMTP) are the same in my W10 and ubuntu partitions, so that does not seem to be the problem.


I seems that my DNS cache may have something to do with it, and not thunderbird -or outlook itself (although I tried what you suggested, I am still unable to send emails). I don't know how to flush it (if indeed this is causing the problem). And in [this thread ]("https://superuser.com/questions/134762/how-to-clear-dns-cache-in-ubuntu/163296#163296")it says that ubuntu does not cache DNS at all, so not sure what to do.

Any ideas?
Cheers!

Don't kill the messenger But here is what I'm told by mine.
> Any VPN provider like us (PIA) that does not keep logs of user activity on the
VPN must restrict SMTP (outgoing) mail traffic due to rampant SPAM
associated with anonymous VPN services. The alternative is to have many
sites and services block our VPN, which could lead to us going out of
business, OR to keep logs of user activity and hold users responsible
for the SPAM. Neither of these are preferable to us or our customers, so
we choose to restrict SMTP traffic until the proper process has been
completed. 
I would open a ticket with your VPN Provider to see if they can help...as this is not a problem with ubuntu.
Kind Regards

---

### Post by DuckHook on 2017-10-29
> **1fallen said:**
> …I would open a ticket with your VPN Provider to see if they can help...as this is not a problem with ubuntu…
Thanks for the info, 1fallen. I use PIA but did not know of this restriction. Of course, I use it on my mobile devices on which I rarely send emails. It makes sense though. Lots of spam is fronted through VPNs.

@OP
You can try bypassing this restriction by suspending your VPN when sending mail. That way, SMTP can be unimpeded for the short duration that you are sending. My VPN app allows such temporary suspension. It's easy enough to resume afterwards. A rather kludgey workaround, but it should work.

---

### Post by gonzobilbao on 2017-10-29
> **1fallen said:**
> I would open a ticket with your VPN Provider to see if they can help...as this is not a problem with ubuntu.



Hi 1fallen, thanks for your reply.


My feeling is that the problem does not come from the VPN (in my other ubuntu machines and in W10 I can send emails using thunderbird, both when connected to the vpn and when not).

The funny thing is that I could reproduce the problem with W10 while connected to my vpn... but the problem disappeared when flushing the DNS cache. Not sure if that is exactly what happens in ubuntu, as it handles cache differently.

As my SMTP settings are the same in all my thunderbird installs, it looks like there is something with my particular ubuntu configuration, but don't know exactly what.

I opened a ticket with my VPN provider (vpn.ac). So far no luck. This is starting to look like a lost battle!

Thanks in advance for your replies :)

---

