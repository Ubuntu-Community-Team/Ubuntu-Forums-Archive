---
title: "Can anybody please recomend a good firewall?"
date: 2007-06-07
forum: General Help
---

### Post by the lemming on 2007-06-07
I know quite a few people have told me that ubuntu does not need a firewall.  However I have read a few Linux magazines and distro reviews and they all recommend that a firewall sould still be installed with a linux distro.

With this in mind, could somebody please recommend a good firewall please?

Cheers

---

### Post by nemarasu on 2007-06-07
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall")

---

### Post by the lemming on 2007-06-07
> **nemarasu said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall")

Thank you for the link.

I have now installed the firewall but I have another consern.  Windows style firewalls ask a lot of questions about my computer activity.  However I am conserned about the simplicity of the Firestarter wizard.  It only asked a couple of questions and I'm wondering if that is all I need to do.  Can I now leave it and forget it?

cheers

---

### Post by orb9220 on 2007-06-07
First ubuntu already comes with a firewall built in called iptables and it is already configured for most user's.

Second FireStarter is not a firewall it is the Gui frontend to iptables which is already running on startup.

For me I never had to install firestarter since iptables is running and I have never run into any problems.

Other's with paranoid flavor say no you must lock down anything and everything. Which I believe iptables does lock down all incoming but not outgoing connections.

Please others correct  my view if it is distorted or biased.

---

### Post by the lemming on 2007-06-07
> **orb9220 said:**
> First ubuntu already comes with a firewall built in called iptables and it is already configured for most user's.



I'm confused now.  This week I read a review of 8 distros.  When reviewing ubuntu the reviewer commented that ubuntu did not have any open ports and it did not have a firewall installed.

With this in mind and your comments on iptables, will iptables conflict with firestarted that I have just installed onto my laptop?

---

### Post by orb9220 on 2007-06-08
Firestarter is just the Gui to iptables.  It is graphical frontend to configure iptables.

It cannot conflict with iptables because it is not (Firestarter) a firewall.

---

### Post by mifi on 2007-06-08
> **the lemming said:**
> Thank you for the link.

I have now installed the firewall but I have another consern.  Windows style firewalls ask a lot of questions about my computer activity.  However I am conserned about the simplicity of the Firestarter wizard.  It only asked a couple of questions and I'm wondering if that is all I need to do.  Can I now leave it and forget it?

cheers
Despite some others' opinions, I think you are right that you want to manage your firewall yourself.

It is true that the basic filtering is already in Ubuntu. It is called iptables and it does the actual firewalling, so to speak.
Iptables knows what to do based on rules that have to be configured. Ubuntu comes with a standerd set of rules but they can be changed using the appropiate commands.

Firestarter is a nice graphical interface to IPtables, that makes it easier to change the rules that iptables is using. You do not need to use the iptables commands but you can use firestarter instead.

The firewall will not use pop-up screens, like you are used to under windows, if an event occurs. Instead the events will be reported in the events tab in firestarter. As a result, when an application seems to hang (because it cannot establish a connection) you will not be alerted by a popup, but you will have to check the events tab in firestarter instead and then fix your policy accordingly by hand.

Using firestarter you have to set policies, depending on what you want to protect.

This is all very nice. Firestarter + iptables is comparable to personal firewalls on windows, which are usually packet filters.

There are a couple of firewalls for Linux systems to go beyond that and are intended for use on dedicated firewall servers with proxies and all. These are more geared towards company networks. I seem to remember that suse has one installed by default, but it has been a while. This is what the reviewers pointed out. Sure, these firewalls are better, but they are also overkill for normal users that use their systems as workstations at home. And they require knowledge to be configured correctly.

hope this helped.
good luck
mifi

---

### Post by laidback on 2007-06-08
> **the lemming said:**
> I'm confused now.  This week I read a review of 8 distros.  When reviewing ubuntu the reviewer commented that ubuntu did not have any open ports and it did not have a firewall installed.


I guess you are referring to the LXF article in the July issue. I too am confused as I have believed that Ubuntu is protected by default with iptables. However, it may be that the article was pointing out that there is no manipulation GUI for a firewall by default, i.e. Firestarter needs to be installed from the mirror....gosh what an effort that is...I think not. My feeling is that the article is a little misleading and some additional comment is needed on this particular issue. I feel a letter coming on. But heh Ubuntu comes out on top, should we expect anything else?

---

### Post by mifi on 2007-06-08
> **laidback said:**
> I guess you are referring to the LXF article in the July issue. I too am confused as I have believed that Ubuntu is protected by default with iptables. However, it may be that the article was pointing out that there is no manipulation GUI for a firewall by default, i.e. Firestarter needs to be installed from the mirror....gosh what an effort that is...I think not. My feeling is that the article is a little misleading and some additional comment is needed on this particular issue. I feel a letter coming on. But heh Ubuntu comes out on top, should we expect anything else?
One can differ on what actually comprises a firewall. There are those that do not consider an ip filter a firewall. For them, a firewall is a thing that has proxies. I believe the definition of terms leads to the confusion.
Forget the nitpicking. Use firestarter on Ubuntu and you'll be fine.

Remember: whatever the firewall, you will have to think about your policies anyway. Any firewall is only as safe as the policies it implements.

mifi

---

### Post by laidback on 2007-06-08
> **mifi said:**
> One can differ on what actually comprises a firewall. There are those that do not consider an ip filter a firewall. For them, a firewall is a thing that has proxies. I believe the definition of terms leads to the confusion.
Forget the nitpicking. Use firestarter on Ubuntu and you'll be fine.

Remember: whatever the firewall, you will have to think about your policies anyway. Any firewall is only as safe as the policies it implements.

mifi

mifi,
Thanks for this explanation. The misty clears.

---

### Post by bapoumba on 2007-06-08
Please check the [Firestarter doc]("http://www.fs-security.com/docs/introduction.php"). It is very well written.
There is a [FAQ]("http://www.fs-security.com/docs/faq.php")  where you can find links to test your firewall if you wish.
Look at: Q: How can I test if the firewall is working for sure?

---

