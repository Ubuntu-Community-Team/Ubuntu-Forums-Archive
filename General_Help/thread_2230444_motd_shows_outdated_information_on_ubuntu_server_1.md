---
title: "motd shows outdated information on ubuntu server 14.04 LTS"
date: 2014-06-19
forum: General Help
---

### Post by Netson IO on 2014-06-19
Before reporting a bug I just wanted to make sure I am not doing something wrong here.

After performing a fresh installation of Ubuntu Server 14.04 LTS I notice that the MOTD message which is shown when I login via SSH is outdated: it shows the information which was generated during my LAST login. So when I last logged in last week and then login again today, the information presented to me is from last week's login. I am specifically referring to the system info as below (this login message was shown to me today, on the 19th of June):

```

Welcome to Ubuntu 14.04 LTS (GNU/Linux 3.13.0-29-generic x86_64)

  System information as of Thu Jun 16 12:24:09 CEST 2014

  System load:  0.02               Processes:           105
  Usage of /:   18.0% of 14.40GB   Users logged in:     0
  Memory usage: 53%                IP address for eth0: xxx.xxx.xxx.xxx
  Swap usage:   2%
```

When I logout and in again, I am shown the information from my login session a few minutes ago.

Here's my sshd_config:

```

ChallengeResponseAuthentication no
HostbasedAuthentication no
IgnoreRhosts yes
PasswordAuthentication no
PermitEmptyPasswords no
PermitRootLogin no
PrintLastLog yes
Protocol 2
PubkeyAuthentication yes
RSAAuthentication yes
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes
X11Forwarding no
```

Is something wrong with my configuration or is this a bug? Any help would be very much appreciated!

---

### Post by tgalati4 on 2014-06-19
motd used to be a simple framework;  now it has gotten quite complicated.

> tgalati4@Mint14-Extensa ~ $ apropos motd
motd (5)             - message of the day
motd.tail (5)        - Template for building the system message of the day
pam_motd (8)         - Display the motd file
update-motd (5)      - dynamic MOTD generation

```
man update-motd
```  is where I would start.

---

### Post by Netson IO on 2014-06-19
I know, it took me a while to figure out I needed to enable PAM (UsePAM) in my SSHD config in order to show the Motd at all, regardless of the ShowMotd=yes/no config. But now it does show outdated info; any clues on howto fix this?

If I type the command from your post, here's the output:
```
root@x:/home/netson# apropos motd
motd (5)             - message of the day
pam_motd (8)         - Display the motd file
update-motd (5)      - dynamic MOTD generation
```

---

### Post by rlangner on 2014-07-06
I have the same problem - takes 2 logins to get up to date info from MOTD.  Any ideas on how to fix? Ubuntu 14.04 LTS

---

### Post by tgalati4 on 2014-07-06
I'm running Linux Mint MATE 14 which is based on 12.10.  So obviously the motd framework has changed again.  I would file a bug against 14.04.  I'm sure there are others with the same problem.  I presume that local logins are OK, that the motd is updated correctly?  So it is only ssh logins that display outdated information?  Is it possible that you have different versions of ssh between machines?  It might be a bug between older and new ssh daemons interacting with motd.

```
apt-cache policy openssh-client
apt-cache policy openssh-server
```

---

### Post by SAH62 on 2014-07-09
Here's something to try that worked for me. Edit the file /etc/pam.d/sshd; it's owned by the root user so you'll need to be logged in as root or able to sudo. Look for this line:

```

session    optional     pam_motd.so  motd=/run/motd.dynamic noupdate

```

Remove "noupdate":

```

session    optional     pam_motd.so  motd=/run/motd.dynamic

```

Save the file. After making this change I've noticed that I now get current system information when I login via ssh.

---

### Post by tgalati4 on 2014-07-09
And I remember that this was disabled for a reason.  If you have a busy, headless server in a remote location, ssh would time out because of heavy load trying to assemble the motd.  So that would effectively lock you out of a server, just as you needed to log in and figure out why it is so slow.

For a normally-functioning server, motd is trivial.  But when you are having issues, having a login-process that interferes with logging in is not so nice.

---

### Post by SAH62 on 2014-07-09
> **tgalati4 said:**
> And I remember that this was disabled for a reason.  If you have a busy, headless server in a remote location, ssh would time out because of heavy load trying to assemble the motd.  So that would effectively lock you out of a server, just as you needed to log in and figure out why it is so slow.

For a normally-functioning server, motd is trivial.  But when you are having issues, having a login-process that interferes with logging in is not so nice.

There's some code in /etc/update-motd.d/50-landscape-sysinfo to address that risk:

```

#!/bin/sh
cores=$(grep -c ^processor /proc/cpuinfo 2>/dev/null)
[ "$cores" -eq "0" ] && cores=1
threshold="${cores:-1}.0"
if [ $(echo "`cut -f1 -d ' ' /proc/loadavg` < $threshold" | bc) -eq 1 ]; then
    echo
    echo -n "  System information as of "
    /bin/date
    echo
    /usr/bin/landscape-sysinfo
else
    echo
    echo " System information disabled due to load higher than $threshold"
fi

```

---

### Post by SAH62 on 2014-07-09
Oh, and FWIW the same edit should be made to /etc/pam.d/login. I found the same use of "noupdate"in there, too.

---

