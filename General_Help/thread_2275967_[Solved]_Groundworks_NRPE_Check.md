---
title: "[Solved] Groundworks NRPE Check"
date: 2015-04-29
forum: General Help
---

### Post by aaron27 on 2015-04-29
Good afternoon,

I am having an issue with our Groundworks monitoring. We have noticed that we were not getting any notification of low disk space on our servers.


If i go into the host and select the check_disk job and run a test i get the following:

```
**/usr/local/groundwork/nagios/libexec/check_nrpe -t 60 -H NRPE_IP -c get_disk -a "server_ip" "*" "90,95"**
Error! Number: 70 Description: Permission denied
Command returned exit status 3
```

I then went into the command itself and ran a test and receive the following:

```

**/usr/local/groundwork/nagios/libexec/check_nrpe -t 60 -H NRPE_IP -c get_disk -a "Server_IP" "ARG1" "ARG2"**
Error! Arguments wrong, please verify -t parameter
Command returned exit status 3 
```

I setup this up in the middle of last year, and i remember this was one of the first tests I ran to ensure notifications were working. Nothing has changed since the install as we just leave Groundworks to do its thing. Can anyone offer any advice please?

Kind regards
Aaron

---

