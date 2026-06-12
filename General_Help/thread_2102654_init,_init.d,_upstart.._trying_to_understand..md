---
title: "init, init.d, upstart.. trying to understand."
date: 2013-01-07
forum: General Help
---

### Post by starstreams on 2013-01-07
I'm fairly new to Linux still, and I'm finding the subject of the history of how Linux managed, and now manages initialization. I've read all kinds of sources ,and I understand that the init system has moved from the older V system..to a few others and now is using *upstart*. But it's still a confusing mess in my head. 


[LIST]
[*]Is this subject something critical to learn right away?
[*]And are there any older distros I can install into a VM to experiment with the older system which used *init* and the *inittab* file?
[/LIST]
I just feel like I need to go back to the roots and learn that first, before I can understand the new *upstart*.
I know in Lubuntu, the init.d directory has a lot of links that reference config files in init. But I still don't understand how it all works because all these sources I'm reading mention files that are not there. I know inittab is long gone. I would really like to locate a "good" tutorial that starts from the beginning at the V system, and goes though the historical time line .. (while explaining things) how the system works. Everything out there I find is incomplete.

Thank you

---

### Post by bab1 on 2013-01-07
> **starstreams said:**
> I'm fairly new to Linux still, and I'm finding the subject of the history of how Linux managed, and now manages initialization. I've read all kinds of sources ,and I understand that the init system has moved from the older V system..to a few others and now is using *upstart*. But it's still a confusing mess in my head. 


[LIST]
[*]Is this subject something critical to learn right away?
[*]And are there any older distros I can install into a VM to experiment with the older system which used *init* and the *inittab* file?
[/LIST]
I just feel like I need to go back to the roots and learn that first, before I can understand the new *upstart*.
Not really needed.  Originally the OS was booted serially (one element after another).  This is not a problem with a dedicated server.  It is a problem when you think of all the variation a desktop environment brings to the table.> 
I know in Lubuntu, the init.d directory has a lot of links that reference config files in init. But I still don't understand how it all works because all these sources I'm reading mention files that are not there. I know inittab is long gone. I would really like to locate a "good" tutorial that starts from the beginning at the V system, and goes though the historical time line .. (while explaining things) how the system works. Everything out there I find is incomplete.
Thank you

The old stuff is just history.  I don't recommend learning about techniques that are not used for anything more than understanding how we got to here. 

If you are sicking with the Ubuntu then Upsart is all you need to know,  This has been a long slow process of conversion.  I believe it started in 2009 (v9.04).  The most important document I've seen is the [**_[COLOR="Blue"]Upstart Cookbook[/COLOR]_**]("http://upstart.ubuntu.com/cookbook/").

If you are interested in Debian also, I believe the developers are split between Upstart and [**_[COLOR="Blue"]systemd[/COLOR]_**]("http://wiki.debian.org/systemd").

You can check the others by googling "init system" and the distro you are interested in.

---

### Post by starstreams on 2013-01-07
Hi bab1
Yep, I ran across that upstart-ubuntu.com-cookbook this morning, it didn't make sense to me at first.  But I think [this]("http://upstart.ubuntu.com/cookbook/#what-is-upstart") might be a good starting point.
At first it seemed like the page was geared towards established developers. I notice there's a download for upstart, which I can only assume is for non Ubuntu distros that are still using the older system. 

I'll take your advise an ignore learning the older system for now and see if I can make sense of the cookbook. Thank you.

---

