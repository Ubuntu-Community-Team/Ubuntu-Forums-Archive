---
title: "Nord VPN not connecting in 22.04"
date: 2022-04-28
forum: General Help
---

### Post by smarmy on 2022-04-28
Haven't seen much out there regarding this yet.  I assume that there isn't support for Nord VPN yet for 22.04.  I've tried uninstalling and reinstalling the application to no avail.  Currently, I receive the following error when attempting to connect to any VPN via the terminal:

```
Whoops! Connection failed. Please try again. If the problem persists, contact our customer support.
```

I followed instructions featured at the following URL:

[https://support.nordvpn.com/Connectivity/Linux/1322207652/Troubleshooting-connectivity-Linux.htm](https://support.nordvpn.com/Connectivity/Linux/1322207652/Troubleshooting-connectivity-Linux.htm)

The only thing I've yet to try is attempting a manual connection and disabling IPV6.  Currently I am banking on nord rolling out an update in a little while to patch this, but wanted to make sure whether or not I'm doing something stupid, and/or if anyone else is experiencing a similar issue.  I'm a relative Linux noob and, while I've used Ubuntu off and on since 2004, I've only really used it consistently since 2021, so bear with me, lol.

Thanks in advance!

---

### Post by #&amp;thj^% on 2022-04-28
I'm a tester.
First of all, this is a well-known error/bug, meaning that it should be fixed in the next version of NordVPN that will be released for Linux systems. But, until then you can fix it all by running the following command.
```

sudo ln -s /usr/bin/resolvectl /usr/bin/systemd-resolve
```

You have to type in the root user password when you run the command above, and after you have done so, you can once again use the different commands and connect to any of the NordVPN servers, also in Ubuntu 22.04.

---

### Post by smarmy on 2022-04-28
> **1fallen said:**
> I'm a tester.
First of all, this is a well-known error/bug, meaning that it should be fixed in the next version of NordVPN that will be released for Linux systems. But, until then you can fix it all by running the following command.
```

sudo ln -s /usr/bin/resolvectl /usr/bin/systemd-resolve
```

You have to type in the root user password when you run the command above, and after you have done so, you can once again use the different commands and connect to any of the NordVPN servers, also in Ubuntu 22.04.

Success!  Thanks for the quick response!

---

### Post by #&amp;thj^% on 2022-04-28
Enjoy.:)
One more note, if anyone is having a link to activate in a browser use:
```
nordvpn login --legacy

```

---

