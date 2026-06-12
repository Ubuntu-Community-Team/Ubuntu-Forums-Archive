---
title: "SSH - How to switch to sudo user within a script"
date: 2015-03-24
forum: General Help
---

### Post by suaro on 2015-03-24
Hi Everyone,

I'm relatively new to Ubuntu (and Linux in general). Hopefully this question is posted in the correct place.

Given the following:

_Servers:_

   - 15 servers (server1, server2, server3, etc...)

_Workstation (client)_

   - 1 client workstation.

   - **user1** - User account has sudo privileges and is able to authenticate and connect to each server using-> ssh server(n).  Once connected user1 can issue a 'sudo su' to do administrative things on the  remote machine if needed.

   - **root - **User account is NOT setup (keywise) to ssh from workstation to servers.  Its a requirement that this stays this way.

My questions is how can user1 automate tasks to the remote servers and have those tasks run under the sudo (root) account?  

For example, the following command executes the 'uptime' command on the remote machine under the user1 security context.

         pdsh -R ssh -w ^machines.list "uptime"

How can I execute this statement but have the 'uptime' command run  under root account ?  In other words if I just ssh over to that machine, then issue a sudo su , then issue uptime,  that works.  Just trying to find out how I could automate this 'sudo su' operation within the list of remote commands to execute.  I've tried inserting 'sudo su' above, but this blows chunks. 

If its not possible, what changes could be made that doesn't break the security requirement that under root account, ssh'ing to remote machines is not allowed.
Thank you

---

### Post by SeijiSensei on 2015-03-24
Why can't you add your public key to the server's /root/.ssh/authorized_keys file?  That's no less secure than you logging in and running "sudo su".  Does whoever set the policy realize that?

My personal key is authorized on the servers I manage so I can run "ssh root@server". 

Otherwise the only solution I can think of is some kludgy affair where you as a normal user run an application on the server that lets you put commands in a queue that is periodically scanned by the root user and executed.   The root part would need to run out of cron and be configured to send you the results.

---

### Post by ian-weisser on 2015-03-24
One kludgy answer is to edit /etc/sudoers

Another kludgy answer is to write a root dbus (or socket) listener that would execute a limited set of non-arbitrary actions.
A non-root dbus (or socket) client can call the trigger and collect the output.
This is exactly how, for example, your desktop Network-Manager-applet (which runs as a user) controls the real behind-the-scenes Network Manager (which runs as root).

I'm confused why 'uptime' would need to be run as root...
Or is that just an example?

---

### Post by Lars Noodén on 2015-03-24
> **suaro said:**
> For example, the following command executes the 'uptime' command on the remote machine under the user1 security context.

         pdsh -R ssh -w ^machines.list "uptime"

How can I execute this statement but have the 'uptime' command run  under root account ?

You can configure that in /etc/[sudoers]() an whitelist each program, with parameters, for a given group.  So in the case of [uptime](http://manpages.ubuntu.com/manpages/trusty/en/man1/uptime.1.html) you could do it like this for users in the group "remote"

```

%remote   ALL=(ALL:ALL) NOPASSWD: /usr/bin/uptime ""

```

That will let users in the group "remote" run "uptime" as root without a password but only without options.  

         pdsh -R ssh -w ^machines.list "sudo uptime"

You can also use regular expressions in /etc/sudoers and thus keep "PermitRootLogin" set to "no"

---

### Post by suaro on 2015-03-24
uptime was just an example. thx

Thanks everyone for the replies.

---

