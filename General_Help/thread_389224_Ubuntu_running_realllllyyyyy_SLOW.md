---
title: "Ubuntu running realllllyyyyy SLOW"
date: 2007-03-20
forum: General Help
---

### Post by stchman on 2007-03-20
Hello all.  Here is the problem:

I have Edgy installed on three different machines

1.  Laptop with wireless
2.  Desktop
3.  Desktop

They are all running really slow.  The boot up time is very quick (under 1 min) so I am not looking for boot speed up.  So the login screen appears pretty quick.

I logon on to any of the three machines and it take sometimes 1.5 minutes to login.  The splash screen stays there for a while.

Opening applications and surfing the web is horribly slow.  It does not matter what applications I open it takes forever (terminal, Home folder, anything) sometimes 30 secs.  It gets better.

Here is the kicker, if I disable the network on any of the three machines (Administration--->Network) the machines then become very fast again.  I can logoff and then log back on.  Restart and then logo back on.  Once logged on applications open very quickly.

Surfing the web is also very slow.  The pages take forever to load and I am on a 5Mb connection.  I thought that the network (cable modem, router) was bad but on one of the machine I duall boot (XP/Ubuntu) and the XP side does not suffer from any type of slowdown.  BTW I disabled ipv6.  I have googled until I am blue in the face and to no avail.  Since the identical thing is happening on three separate machines I am ruling out hardware failures.

This all happened about a week ago after Ubuntu told me I needed to update.

Has anyone else had something similar happen to them?

Thanks.

---

### Post by stchman on 2007-03-20
I have been doing some reading and could it be the:

/etc/resolv.conf

or the 

/etc/nsswitch.conf

Thanks.

---

### Post by stchman on 2007-03-21
I figured it out with some reading the hosts and hostname files were incorrect.

They each only needed one line

hosts
127.0.0.1 localhost bob-laptop

hostname
bob-laptop

That was the problem.  The internet is still a little slow.

---

