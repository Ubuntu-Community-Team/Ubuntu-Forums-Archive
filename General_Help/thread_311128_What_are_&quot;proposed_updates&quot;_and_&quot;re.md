---
title: "What are &quot;proposed updates&quot; and &quot;recommended&quot; updates?"
date: 2006-12-02
forum: General Help
---

### Post by dpm on 2006-12-02
Under the "Internet Updates" of the update-manager, I've got the option of enabling several repositories for internet updates.

I know what security updates and backports are, but I've never heard of "proposed" or "recommended" before. Could anyone tell me what's the purpose of those? Or point me to some documentation where this is explained?

BTW, pressing the help button does not help. The help is still describing the Update Manager preferences for Hoary!!!

Thanks.

---

### Post by drphilngood on 2006-12-02
[Issue 2 of the Ubuntu Weekly Newsletter explains the proposed repository.]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue2")

> Proposed Archives

A new set of package archives has been added to archive.ubuntu.com to allow proposed updates and fixes to be uploaded and tested (by those with the archive enabled) before the packages are officially released. This process will allow for the proposed updates to see wider testing helping improve the quality of the updates....

---

### Post by dpm on 2006-12-03
Thanks for the reply, that clears things up a bit

Having a look at [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) I see the following package archives for Edgy, which, if I'm correct map to the repositories I've written next to them, as referred to in update-manager:

[IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG] [edgy-backports/]("http://archive.ubuntu.com/ubuntu/dists/edgy-backports/")         -> Backports from Feisty (and/or Debian unstable?)
[IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG] [edgy-proposed/]("http://archive.ubuntu.com/ubuntu/dists/edgy-proposed/")  -> Proposed updates
[IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG] [edgy-security/]("http://archive.ubuntu.com/ubuntu/dists/edgy-security/")    -> Security updates
[IMG]http://archive.ubuntu.com/icons/folder.gif[/IMG] [edgy-updates/]("http://archive.ubuntu.com/ubuntu/dists/edgy-updates/")    -> Recommended updates?

I still do not quite understand how the proposed and recommended updates work, but after reading the link drphilngood posted, I'm guessing that both repositories must only be enabled by "power users" which want to test packages or get the latest fixes. In this way, I'm thinking that "proposed" is the testing repository before packages go to "recommended". 

Could that be right?

---

### Post by drphilngood on 2006-12-04
> **desp said:**
> Thanks for the reply, that clears things up a bit

You are most welcome.

> **desp said:**
> I still do not quite understand how the proposed and recommended updates work, but after reading the link drphilngood posted, I'm guessing that both repositories must only be enabled by "power users" which want to test packages or get the latest fixes. In this way, I'm thinking that "proposed" is the testing repository before packages go to "recommended". 

Could that be right?

That is pretty much it.  It was implemented to allow for further testing of updates on more hardware than is available to the devs alone.  If no problems are reported, ¨proposed¨ moves to ¨recommended¨ rather quickly.

---

