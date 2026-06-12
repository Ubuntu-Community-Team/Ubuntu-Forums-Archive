---
title: "One user is checking e-mail four times a minute..."
date: 2022-09-01
forum: General Help
---

### Post by civilpolisen on 2022-09-01
One of our users is slowing down the speed of the server due to hysteric amount of eateries to the server!
This man is unaware of it. He's using iPhone and Outlook and also Round Cube for internet access to the mailbox.

I'm no expert in these things, that's why I post! But people around med have some more experience than me
in this field.

```
jakob@mailserver:/etc/dovecot$ dovecot -a | grep "mail_max_userip_connections"
mail_max_userip_connections = 10
jakob@mailserver:/etc/dovecot$ 

```

This is the default setting.
What do you suggest me to do!? How to move on?
Is there a way to limit the requests without also limit the service and / or the experience...?

---

### Post by TheFu on 2022-09-01
iptables has the ability to limit connections.  Use that and you should contact the user to have them slow email checking to no more than once every 5 minutes for a business account and once an hour for non-business accounts.

---

