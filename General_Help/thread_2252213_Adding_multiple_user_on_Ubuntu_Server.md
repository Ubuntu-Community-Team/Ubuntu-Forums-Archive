---
title: "Adding multiple user on Ubuntu Server"
date: 2014-11-10
forum: General Help
---

### Post by Rahul_Pandey on 2014-11-10
Hello to all,

I need to create multiple user accounts ( around 200 ) on Ubuntu for school. 
One way is to do manually.
Is there any other way like script or command to complete this task.

Any help is welcome.

Thanks in advance.

---

### Post by mastablasta on 2014-11-10
this one looks nice (second one): [http://askubuntu.com/questions/410712/script-to-add-multiple-users-in-ubuntu-bulk](http://askubuntu.com/questions/410712/script-to-add-multiple-users-in-ubuntu-bulk)

and simple. not sure why it got -1

but what it does is takes the list of users creates them and assigns them a random password. I would use some calc or something to create the users list, then get the passwords and create users and then go back to calc to add those passwords to users and user emails. then use the mass mail addon in thunderbird to send out individually crafted emails. a bit lame but that's all I know :) I guess you could use mailx or similar and include that in script so users would get emails about passwords automatically after the script runs.

---

### Post by Lars Noodén on 2014-11-10
The utility [useradd](http://manpages.ubuntu.com/manpages/trusty/en/man8/useradd.8.html) works well in a script, it is not interactive.  You have to explicitly set a lot of options, but then the script will fill them in for you.

---

