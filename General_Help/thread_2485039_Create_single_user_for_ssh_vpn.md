---
title: "Create single user for ssh vpn"
date: 2023-03-18
forum: General Help
---

### Post by samiojtm on 2023-03-18
Hello, I use the following command to create an SSH VPN username on my server

 adduser username --shell=/bin/false

 This is very good, it doesn't allow access, but I have a problem, my users give their passwords to others, and it causes several people to log in with just one username and password, and it causes the bandwidth of the server to run out. There is a method that at this time, only one  Can someone log in with this username and password?

---

### Post by MAFoElffen on 2023-03-18
Yes you can...

The file you want to edit on your ssh server is "/etc/security/limits.conf"

RE: Man limits.conf ([https://manpages.ubuntu.com/manpages/jammy/man5/limits.conf.5.html](https://manpages.ubuntu.com/manpages/jammy/man5/limits.conf.5.html))

the format in that file is 
```

#<domain>        <type>  <item>  <value>

```
You can put individual usernames under the domain column, type hard, use maxsyslogins (max number of logins on the system), then put 1 as the value. Like this
```

fred.flintstone     hard    maxsyslogins    1

```
You can also use groups and wildcards... Like these:
```

@oncall_staff      hard    maxsyslogins    1
*                  hard    maxsyslogins    1

```
With the later locking down the whole system saying that everyone/all users can only login to the system with one login per user.

The file itself has explanations and examples.

Note that this restriction applies for the normal users only. The root user can still able to login via SSH any number of times.

---

### Post by mIk3_08 on 2023-03-19
[QUOTE=MAFoElffen;14135334]Yes you can...

The file you want to edit on your ssh server is "/etc/security/limits.conf"
RE: Man limits.conf ([https://manpages.ubuntu.com/manpages/jammy/man5/limits.conf.5.html](https://manpages.ubuntu.com/manpages/jammy/man5/limits.conf.5.html))

```

#<domain>        <type>  <item>  <value>

```

```

fred.flintstone     hard    maxsyslogins    1

```
You can also use groups and wildcards... Like these:
```

@oncall_staff      hard    maxsyslogins    1
*                  hard    maxsyslogins    1

```
/QUOTE]
Thanks MAFoElffen. This helps a lot specially with the given link. proven and tested. Regards and cheers.

---

