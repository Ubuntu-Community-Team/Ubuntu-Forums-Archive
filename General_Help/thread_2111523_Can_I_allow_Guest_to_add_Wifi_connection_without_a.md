---
title: "Can I allow Guest to add Wifi connection without admin privileges?"
date: 2013-02-02
forum: General Help
---

### Post by brownbat on 2013-02-02
I'd like to loan my netbook to a friend for a day or so. I'd like my friend to be able to set up a connection to any wireless network he encounters, but a password appears to be required to add a new network, and I don't really want to open the floodgates to full admin privileges.

I know that physically handing a device to someone could be said to be trusting them as much or more than handing them a password. That said, I'm still curious, is there a way to pre-approve some admin functions without giving up full rights?

(Sorry if it's out there, my searches taught me a bit about setting wifi networks manually and the history of sudo, but not exactly what I was looking for...)

Thanks!

---

### Post by steeldriver on 2013-02-02
[S]Not sure about the true 'Guest' user, but regular (non-sudo) users should be able to add connections provided they uncheck the 'available to all users' box

That should create a 'user-connection' which gets saved in the user's home config rather than a 'system-connection'[/S]

EDIT: it seems (at least on 12.04) it is not possible to do this in the  way I indicated - the 'available to all users' box is checked by default  and can't be unchecked by a non-sudo user

[https://answers.launchpad.net/ubuntu/+source/policykit/+question/203473](https://answers.launchpad.net/ubuntu/+source/policykit/+question/203473)

---

### Post by rnerwein on 2013-02-02
> **brownbat said:**
> I'd like to loan my netbook to a friend for a day or so. I'd like my friend to be able to set up a connection to any wireless network he encounters, but a password appears to be required to add a new network, and I don't really want to open the floodgates to full admin privileges.

I know that physically handing a device to someone could be said to be trusting them as much or more than handing them a password. That said, I'm still curious, is there a way to pre-approve some admin functions without giving up full rights?

(Sorry if it's out there, my searches taught me a bit about setting wifi networks manually and the history of sudo, but not exactly what I was looking for...)

Thanks!
hi
you can add in /etc/sudoers (as last line):
account_of_your_friend  ALL=NOPASSWD: command_to_set_up_a_connection

cheers

---

### Post by brownbat on 2013-02-18
As a tip, do not edit sudoers directly, you risk losing access to sudo with no easy way to get it back. Some online have recommended "visudo."

Next time I'll just make her an account and make sure I don't have any important files on there. :)

---

