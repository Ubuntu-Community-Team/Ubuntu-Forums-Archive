---
title: "Getting system emails"
date: 2015-10-22
forum: General Help
---

### Post by von Stalhein on 2015-10-22
Hi all,
I'd been without a PC for a while until I cobbled this one together a while back.

I had my previous iteration set up to send system emails when cron jobs started/failed and I think there were other default notifications as well from the machine.

Anyway, I've successfully installed Postfix and I can send and receive emails via Movemail in Thunderbird but there are no system emails coming in (been a couple of days). Telneting to Port25 works ok as well.

What config file needs editing to sort that? -  Or where should Movemail be dragging in the notifications from?  Tbird is pointing to /var/mail atm - TIA

---

### Post by btindie on 2015-10-22
Have you checked the mail for *root*? As that's where everything will be sent by default.

Try adding to /etc/aliases an alias to send the mail destined for *root *to your user account
```
root: vonStalhein
```

---

### Post by von Stalhein on 2015-10-22
> **btindie said:**
> Have you checked the mail for *root*? As that's where everything will be sent by default.

Try adding to /etc/aliases an alias to send the mail destined for *root *to your user account
```
root: vonStalhein
```

My /etc/aliases is:
```
# See man 5 aliases for format
postmaster:    root
root:    vonStalhein 
```

Thunderbird points to /var/mail
Maybe it should poll from /var/spool/mail ?

---

### Post by von Stalhein on 2015-10-26
Bump?

---

