---
title: "Samba - required `net ads join` on ubuntu-20"
date: 2020-05-17
forum: General Help
---

### Post by gkman10 on 2020-05-17
Hi.

I have posted this question also on stack-exchange but wasn't able to completely solve it there- so I am trying my luck here.
[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]I have been using ubuntu 18.04 with sssd to join my servers to my active directory domain for a while now. 
This worked quite nicely, enabling me to ssh to the servers with AD users and create samba shares with AD authentication as well.
What I usually do is set all the configuration files (krb5, sssd, smb.conf) and use [FONT=courier new]realm join[/FONT] to join the server to the domain.

with Ubuntu 20 I followed my same procedure to join the server to the domain. However I encountered an error with my smb.conf file- the smbd service wouldn't start as long as I had the setting [FONT=courier new]security = ads[/FONT] enabled.
In order to make it work I had to run [FONT=courier new]net ads join[/FONT] command (this is after I already ran realm join)- only then did the smbd service agree to start with [FONT=courier new]security = ads[/FONT] setting enabled.

What has changed between Ubuntu-18 and Ubuntu-20?
Is there a problem using net ads and sssd at the same time?
Can I make samba work again with only sssd?

---

### Post by theta1 on 2021-02-02
Hey did you ever solve this? I am needing to setup and as authenticated file share and would love to know if you did. Or how you did in earlier releases.

---

