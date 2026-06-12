---
title: "gufw )advanced port syntax"
date: 2013-06-20
forum: General Help
---

### Post by L a r r y on 2013-06-20
Hi,
I run gUFW to enter data into my firewall, and am very restrictive on what is permitted.

Gmail is running me ragged lately with many changes of IP address, so I am entering yet another IP address and Ports 465 and 995 TCP out in the advanced tab.

Today I came across an error every time I entered the rule to allow **Out**, **TCP**, To ***the new IP*** Ports **465,995**.

I thought I've been using a comma between the port numbers, that is the way the rules already set are listed, but I just kept getting refused with an error.

At last, I eliminated ",995" and set the rule to allow out to the new IP address port 465, and set a second rule to allow for port 995.

I Googled and came up with man pages that don't address the issue, other web posts that fall short of addressing the issue, and decided to post.

I CAN specify one port by using  its number alone in the Ports box in gUFW.
I CAN specify a range of ports by specifying two numbers with a colon (:)  between them.  (Just checked)

How do I specify this IP address and Ports 465 AND 995??  I THOUGHT it was done by placing a comma.

I use Thunderbird to interface with my Gmail account.  I long ago gave up on Google's redesign of the Gmail interface on its web mail.  And everything works well.

Now maybe there's another way to set this up so by policy Thunderbird has access to pop.gmail.com port 995 regardless of this hour's IP address, and to smtp.gmail.com port 465 (I'll check my server settings to ensure the correct host names).  Can someone point me to some reading material on this idea?

---

### Post by L a r r y on 2013-06-28
Bump

---

### Post by dino99 on 2013-06-28
the actual rules seems to be : entering a single rule at once
so for your example, repeat it for each port

[http://secpanel.com/diy/how-to-deny-allow-ports-in-ufw-or-uncomplicated-firewall-ubuntu/](http://secpanel.com/diy/how-to-deny-allow-ports-in-ufw-or-uncomplicated-firewall-ubuntu/)

---

### Post by L a r r y on 2013-06-28
> **dino99 said:**
> the actual rules seems to be : entering a single rule at once
so for your example, repeat it for each port

[http://secpanel.com/diy/how-to-deny-allow-ports-in-ufw-or-uncomplicated-firewall-ubuntu/](http://secpanel.com/diy/how-to-deny-allow-ports-in-ufw-or-uncomplicated-firewall-ubuntu/)

Thanks for the link, dino99 -- gave me something to investigate.

I did successfully enter a rule in gUFW's advanced tab without specifying an IP address, to allow two ports in one entry as 465,995.  My earlier effort that spawned the posting of this thread was the same thing with IP address included, that kept throwing errors.

Is there a way to set a policy that opens a port when a program needs it  and leave the port closed otherwise?

---

### Post by L a r r y on 2013-06-29
I should add for future reference, that I was in the gUFW Advanced Tab, that I selected to allow OUT, and TCP, and entering data in the To: destination portion.  I entered string "465,995" with no IP specified.  The rule was added, with two rules, one for IPv4 and the other for IPv6, listing 465,995/tcp to anywhere out, in the list of rules.

This rule allows Thunderbird to send and receive mail no matter how many times Gmail changes IP addresses.

---

