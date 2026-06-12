---
title: "Empathy for VoIP"
date: 2013-03-10
forum: General Help
---

### Post by Matpen on 2013-03-10
Hi everyone!

I am currently trying to get Empathy to work on Ubuntu 12.10. Surprisingly, this turned out to be not very straightforward to me. So it would be nice if someone could provide some help.

Background:
In my case the topmost goal would be to make voice & video calls to other online contacts as well as voice calls "ubuntu to landline".
According to [this table]("https://help.gnome.org/users/empathy/stable/audio-video.html.it") the protocols that accomplish this task should be SIP and XMPP.
In my case, I already have a working (tested with phone-to-phone) SIP account with smartvoip.com and a google account which I normally use for gmail (but to my understanding it should be a XMPP account, too).

The problem:
For SIP I installed the package "telepathy-sofiasip", but even after reboot I do not see an option to create a SIP account in the "online accounts" window (press F4 in Empathy).
For XMPP I created a "Google" type account which looks to be working: I can switch to the "available" status (although I have no contacts yet) and in the google web interface I can see that I successfully provided ubuntu with access to the google account. However, I do not see an option to make calls to landline? Is this even possible, or do I need to install Google Voice?

Thank you in advance for any information!
matpen

---

### Post by Matpen on 2013-03-11
I found out [here]("http://infraadvisory.wordpress.com/2012/09/29/adding-sip-to-empathy/") that, in order to see the option for adding a SIP account, the package account-plugin-sip has to be installed (at least in Ubuntu 12.10).
Does anyone have experience with Google Talk / Google Voice / XMPP on Empathy?

Thank you in advance!

---

### Post by Matpen on 2013-03-12
One more thing I found out along the way, which might be interesting for somebody having the same problems as I am facing.
For skype integration the package "pidgin-skype" must be installed. Since (at least in Ubuntu 12.10) the account management is achieved with the system accounts, and a package "account-plugin-skype" is not available yet, the workaround is to launch "empathy-accounts" from a terminal, which gives access to empathy's own account management interface. There it will be finally possible to choose the skype account (labeled "bigbrownchunx-skype-dbus").

---

### Post by sharkey77 on 2013-04-03
Thank you soooo much for telling me about the empathy-accounts command.  I was going crazy trying to find google talk in empathy.

---

