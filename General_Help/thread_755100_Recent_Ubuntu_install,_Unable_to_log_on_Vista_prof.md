---
title: "Recent Ubuntu install, Unable to log on Vista profile"
date: 2008-04-14
forum: General Help
---

### Post by tquarles11 on 2008-04-14
I recently installed Ubuntu.  Everything was working fine and out of no where I attempted to log on to my Vista Business profile and it gave me the following error: "The User Profile Service service failed the logon.  User Profile cannot be loaded."  Has anyone received this error before or does anyone have any idea on what to do?

---

### Post by Het Irv on 2008-04-14
> Hi Guys,
It really works,
Just delete the particular profile from registary which is causing the problem.
go to registery   HKEY_LOCAL_MACHINE
SOFTWARE >>MICROSOFT>>WINDOWS NT>>CURRENT VERSION>>PROFILE LIST>> search the profile under <<S-1-5 >>
and DELETE THE PROFILE ENTRY.
 
BEFORE DELETING MAKE SURE DATA BACKUP HAS BEEN TAKEN.
 
 
Cheers,Tarun
From:[http://wforney.spaces.live.com/blog/cns!3F38E6530D38A38C!635.entry](http://wforney.spaces.live.com/blog/cns!3F38E6530D38A38C!635.entry) 

I don't know how well this will work or if it will mess with your computer any but it is a start.  You might be better off posting this in a Windows fourm just because of the nature of the problem.  I don't think it has to do with Ubuntu, but I could be wrong.  I am running a dual-boot of Ubuntu 8.04 and Vista Biz sp1 and it works fine for me.

---

