---
title: "sshd/vsftpd vs systemd vs networkmanager"
date: 2020-02-26
forum: General Help
---

### Post by dimitrisss on 2020-02-26
When I specify ListenAddress 192.168.1.7 in /etc/ssh/sshd_config, sshd fails to start. Reason being the network interface does not have the ip address assigned by the time openssh daemon starts. The ip address is assigned via dhcp and is always the same. For now my workaround is to have a cron running.

vsftpd is also affected in the same fashion

Is there a solution to this problem, as in wait for the interfaces to get an ip address before proceeding to daemon start up? I don't want to fix the ip address on the machine itself unless I have to.

Best regards,

dimitris

---

### Post by TheFu on 2020-02-26
Don't specify any IP.  Listen on any interface. To do that, just comment out all ListenAddress lines.

While you are at it, perhaps running fail2ban to prevent unlimited brute force attacks is a good idea?
[https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)
No need to have vsftpd installed.

---

### Post by dimitrisss on 2020-02-26
Thank you for the update. I actually need to restrict to which interface sshd listens - I do not want it to listen to any dynamic interface that may be brought up. I only allow certain ip addresses to connect over ssh via iptables so fail2ban will not add much. I also need vsftpd running as I am making use of it.

Best regards,

---

### Post by TheFu on 2020-02-26
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/216847](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/216847) appears to have a fix at the bottom.

In the olden days, before netplan, we had post-up options to control services for other daemons after the network was up.  These days, we get to make a systemd service file that has networking as a dependency.

---

