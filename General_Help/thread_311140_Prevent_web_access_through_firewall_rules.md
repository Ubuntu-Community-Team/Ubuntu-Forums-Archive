---
title: "Prevent web access through firewall rules"
date: 2006-12-02
forum: General Help
---

### Post by dfaulkner on 2006-12-02
I was recently asked to create a restricted account that couldn't browse the web but could otherwise use the computer normally.

This was for a family member and Ubuntu fan who now wants an account on the desktop for her daughter. The goal is that the young lady can write reports, etc, but not use the web without mom's knowledge.

I realize that there are filters out there (danguardian), but mom's request was for *no access whatsoever*. So I played around a bit and discovered that it is possible:

```
# iptables -I OUTPUT -p tcp --dport 80 -m owner --uid-owner 999 -J REJECT

```where 999 = the UID of the daughter. To make sure this starts at boot, I put this (and a similar line with dport 443) into the firestarter custom rules file (/etc/firestarter/something), and now all's well.

The story would end there, except that this got me wondering: are there any mechanisms for doing this in a more general manner? For example, it would be really nice if the graphical user & group tool had a set of privileges like[LIST]
[*]browse the web
[*]get email
[*]read news
[*]access local network hosts
[*]access the following host(s) [enter a hostname/ip/range]
[*]Run/Don't run program(s)[/LIST]and so on. And of course, I want the list customizable, so I can build new privileges later.

The trouble is, most of this is network-based, and so iptables-related. Some of it is not, like "permit/forbid the user to run a program," where I'm not sure what the best way to control that sort of behavior is. There are also all sorts of problems with that, as experienced users of sudo know. 

And yes, I know this 'is backward' from the normal firewall use, but outbound lists are typically restrictive rather than permissive. I also know that allowing "browse the web" can obviate most of the others for sufficiently smart users.

All that said, what do you all think?

---

