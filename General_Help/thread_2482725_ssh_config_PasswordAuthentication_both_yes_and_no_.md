---
title: "ssh config: PasswordAuthentication both yes and no present"
date: 2023-01-09
forum: General Help
---

### Post by my-name-is-koen on 2023-01-09
I use a bash script to set up new instances of an OS (normally raspbian/ubuntu). I am trying to set password authentication 'yes' for one user and 'no' for the rest. Now I see that I have failed in my new digital ocean droplet because at the beginning of the sshd_config file there was a line that includes "50-cloud-init.conf" (with "Include /etc/ssh/sshd_config.d/*.conf") and in that file there's "PasswordAuthentication yes". It sets the PasswordAuthentication to "yes" while in the main sshd_config file there is "PasswordAuthentication no".

I'm confused. Why would there be a file included with a single setting that reverses what is explicitly allowed in the main file? And what is a good way to adjust my script for it?

---

### Post by TheFu on 2023-01-09
I don't do this for specific users, rather I do it for specific subnets.
```
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24,172.22.21.0/24
      PasswordAuthentication yes

```

So if you have a "Match User" section, ensure that's at the bottom of the file.  Indentation doesn't matter, but I use it as a reminder.

The manpage on 20.04, says this:
```
     Match   Introduces a conditional block.  If all of the criteria on the
             Match line are satisfied, the keywords on the following lines
             override those set in the global section of the config file, un&#8208;
             til either another Match line or the end of the file.  If a key&#8208;
             word appears in multiple Match blocks that are satisfied, only
             the first instance of the keyword is applied.

             The arguments to Match are one or more criteria-pattern pairs or
             the single token All which matches all criteria.  The available
             criteria are User, Group, Host, LocalAddress, LocalPort, RDomain,
             and Address (with RDomain representing the rdomain(4) on which
             the connection was received).
...

```
So, put your "Match" lines at the bottom of the time ... or include them at the bottom of the file, if you prefer.

---

### Post by philhughes on 2023-01-09
Files in /etc/ssh/sshd_config.d/ override those in the main configuration file. So you can put your changes in an included file, and this means that when there is a package upgrade, you will not get asked whether you want to keep your edited file or install the package maintainers file. Files are read in lexical order, so put your own changes in a file say "99-local.conf", and these will take precedence. See man sshd_config.

---

### Post by my-name-is-koen on 2023-01-10
Good suggestions, thanks.

---

