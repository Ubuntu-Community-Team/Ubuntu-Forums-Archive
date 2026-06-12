---
title: "Postfix - Redirect mail based on From Address and/or Sender IP"
date: 2018-06-24
forum: General Help
---

### Post by khandu on 2018-06-24
Hey Guys

Playing with postfix. I can see that we can do a redirect of mail to a particular SMTP Relay depending on from address

```

main.cf
sender_dependent_relayhost_maps = hash:/etc/postfix/relay_maps

relay_maps
@domain1.com    [amazonaws.com]:587
@domain2.com        [google.com]:25

```

(Ignore the smtp relay addresses above - they don't exist, I have modified them for illustration purpose)

But can you also do this routing If the mail is coming from an IP address then send it to particular relay?

Something like

```

relay_maps
@domain1.com    [amazonaws.com]:587
10.10.10.10    [amazonaws.com]:587

@domain2.com        [google.com]:25
20.20.20.20              [google.com]:25

```

NOTE: I don't want to use **mynetwork **and block the SMTP server based on an incoming IP..That already exists. I just want to redirect to another SMTP relay IF 

[LIST]
[*]A mail from address domain is @domain1.com
[*]Sender IP is 10.10.10.10
[/LIST]

Send both to amazonaws.com

A combination of both is the best solution to robustness.. or preferred is that if IP address based routing working

Need urgent help

Thanks

---

### Post by SeijiSensei on 2018-06-25
[http://www.postfix.org/postconf.5.html#sender_dependent_relayhost_maps](http://www.postfix.org/postconf.5.html#sender_dependent_relayhost_maps)

---

