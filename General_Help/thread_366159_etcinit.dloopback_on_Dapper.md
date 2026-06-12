---
title: "/etc/init.d/loopback on Dapper"
date: 2007-02-20
forum: General Help
---

### Post by unixpaul on 2007-02-20
Hello,
I am used to the standard networking scripts bringing up the 127.0.0.1 loopback address
on boot up. However I have installed Dapper, and some daemons like MySQL fail to start
becuase 127.0.0.1 has not been brought up. I need to login and do 
/etc/init.d/loopback start

to get it to come up. So I am wondering why is this seperate to normal networking,
and why it's not set to start automatically?  In /etc/rc2.d/  there is no link to the loopback
rc script. Yet when I do  update-rc.d loopback defaults it tells me it is already linked in.
Which it is not.

Is this normal behaviour on Dapper? 
Paul

---

