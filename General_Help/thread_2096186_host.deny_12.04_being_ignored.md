---
title: "host.deny 12.04 being ignored"
date: 2012-12-19
forum: General Help
---

### Post by Drenriza on 2012-12-19
Hey guys.

I'am editing host.deny with the

ALL:ALL

entry. But when i remotely ping my server, it still responds on ping's.
Why is the host.deny being ignored? Should it not deny all services from all destinations with the above entry?

Kind regards.

---

### Post by JKyleOKC on 2012-12-19
The hosts.allow and hosts.deny files operate to control file access, rather than total system access. Pings, however, work at the network connection level and never involve access to a file.

If you want to disallow ping response, the proper place to do so is in your firewall (iptables, UFW, and so on) so that the incoming packet is either dropped or rejected.

My impression is that the two hosts.* files actually only control launch of services via "inetd" or "xinetd" and have no effect at all in other situations. However I've not been able to confirm this.

---

### Post by Rexilion on 2012-12-19
> **JKyleOKC said:**
> My impression is that the two hosts.* files actually only control launch of services via "inetd" or "xinetd" and have no effect at all in other situations. However I've not been able to confirm this.

It depends on the server software you are running. NFSD, for example, is not ran by inetd. It's even driven by part of the kernel. It consults these files for permissions. For NFSv3, ip addresses where the only filtering mechanism around.

I think that inetd and xinetd do this as well by default. For each service listed in their directory they consult these files (not sure).

But there are also standalone servers that consult these files. However, the contents of these files have nothing to do with file permissions, these are handled by UNIX DAC (rwx, read write execute, owner group world).

As for the threadstarter: ICMP pings are handled by the kernel IP stack. And yes, I agree with JKyleOKC that you should block these with a firewall.

However, there is an alternative using sysctl, which disables ICMP entirely:

sudo sysctl net.ipv4.icmp_echo_ignore_all=1

Not sure what the exact implications are though.

---

### Post by Drenriza on 2012-12-20
So my impression is that the host.deny and host.allow aren't really used anymore?

What CAN you use the host.allow and host.deny for? in 12.04 and later.

---

### Post by rnerwein on 2012-12-20
> **Drenriza said:**
> So my impression is that the host.deny and host.allow aren't really used anymore?

What CAN you use the host.allow and host.deny for? in 12.04 and later.
hi
i think the ping theme is already out of sense. there was good explanations.

but by the way its --> host[COLOR=Red]s[/COLOR].allow and host[COLOR=Red]s[/COLOR].deny

i only write this because when you will use these files for other occasions and you have 
accedentally create those files using an editor.
cheers

---

### Post by rnerwein on 2012-12-20
> **Drenriza said:**
> So my impression is that the host.deny and host.allow aren't really used anymore?

What CAN you use the host.allow and host.deny for? in 12.04 and later.
hi
sorry i missed your question. as an example you can use it for nfs-server. here is mine:

rpcbind mountd nfsd statd lockd rquotad : 127.0.0.1 127.0.1.1 193.149.xx.x
cheers

---

### Post by Lars Noodén on 2012-12-20
> **Drenriza said:**
> So my impression is that the host.deny and host.allow aren't really used anymore?

What CAN you use the host.allow and host.deny for? in 12.04 and later.

You can use it to control access to specific daemons, provided those daemons have been compiled to be tcpd-aware.  That would include daemons like sshd from the package OpenSSH-Server, but exclude ones like httpd from nginx or Apache2.  Read up on tcpd or tcpwrappers for more background.  You can probably do about as much with iptables instead or do more with xinetd.

---

### Post by Drenriza on 2012-12-21
Thanks Lars.

I have read about tcp wrappers and it made good sense.

Kind regards.

---

