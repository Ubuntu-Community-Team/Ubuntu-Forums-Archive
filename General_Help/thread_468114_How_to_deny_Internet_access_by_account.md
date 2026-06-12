---
title: "How to deny Internet access by account?"
date: 2007-06-08
forum: General Help
---

### Post by Triple Crown on 2007-06-08
I searched the forum and could not find a similar question/answer, so I am asking for assistance. Several people have asked how to limit Internet access to certain hours or days, but my question is how can I completely disable Internet access to my child's account? I was restricting permissions to a batch file that ran a script that connected to my DSL Extreme account, but then I installed a new router/firewall that has Internet access always on....apparently for all users. Is there a way I can deny Internet or network access to a single user? I am running Ubuntu 7.04 on X86 hardware with a DSL Extreme supplied modem and a Linksys WRT54GL router which is currently limited to wired networking only.

---

### Post by mbeierl on 2007-06-08
Ummm.  You could try having group execute permissions on your browsers, chat clients, etc, without world ```
sudo chmod 754 /usr/bin/firefox
```and then removing your child's account from that group...

---

### Post by stchman on 2007-06-08
> **Triple Crown said:**
> I searched the forum and could not find a similar question/answer, so I am asking for assistance. Several people have asked how to limit Internet access to certain hours or days, but my question is how can I completely disable Internet access to my child's account? I was restricting permissions to a batch file that ran a script that connected to my DSL Extreme account, but then I installed a new router/firewall that has Internet access always on....apparently for all users. Is there a way I can deny Internet or network access to a single user? I am running Ubuntu 7.04 on X86 hardware with a DSL Extreme supplied modem and a Linksys WRT54GL router which is currently limited to wired networking only.

I am going to assume you have an account set up on your PC for your child to use.  I would recommend that you give him/her her own PC.  You would then be able to tell your router that that IP address cannot access the internet.

Otherwise do what the previous poster said and restrict him/her via permissions on all web browsers and chat clients.

---

### Post by Triple Crown on 2007-06-08
Thanks for the suggestion, mbeierl. This would have the undesirable side effect of preventing access to local browser based applications. But, you've got me thinking. Is it possible to assign permissions to a device?

sudo chmod 754 /dev/lan0

---

### Post by mbeierl on 2007-06-25
Okay, I was just setting up a web filter for my kids' school, and came across this:

[http://www.linux.com/articles/113733](http://www.linux.com/articles/113733)

It got me thinking, if iptables can do filtering based on userid, why not something like the following:
```

sudo iptables -A OUTPUT -p tcp -m owner --uid-owner nonet -j DROP

```
Replace nonet with the username of your kid, of course.  This effectively drops ALL output TCP traffic for that userid.  You can restrict by protocol, port#, time of day, etc, when you want to get more sophisticated...

---

### Post by The Keeper on 2007-09-03
> **mbeierl said:**
> Okay, I was just setting up a web filter for my kids' school, and came across this:

[http://www.linux.com/articles/113733](http://www.linux.com/articles/113733)

It got me thinking, if iptables can do filtering based on userid, why not something like the following:
```

sudo iptables -A OUTPUT -p tcp -m owner --uid-owner nonet -j DROP

```
Replace nonet with the username of your kid, of course.  This effectively drops ALL output TCP traffic for that userid.  You can restrict by protocol, port#, time of day, etc, when you want to get more sophisticated...

This caught my attention and I tried it at home just a moment ago. Unfortunately when I log on to the affected account, it freezes up during login.

Are there any other clean ways to prevent a single account from accessing internet? I don't really want to go and change permissions per-application...

---

