---
title: "FSTAB chokes after change to static IP"
date: 2008-01-17
forum: General Help
---

### Post by pfurrie on 2008-01-17
I have an Feisty (7.04) running in a MS Virtual PC machine (I don't think it important, but include for completeness).  I've setup a command in FSTAB to create a mount of an external Windows server share... here is the line in the FSTAB file:

[FONT="Courier New"]//weshsrv-eng/wiki /var/lib/mediawiki1.7/upload smbfs username=gooduser,password=goodpassword,uid=www-data,gid=www-data,user,rw,umask=000 0 0[/FONT]

This is a LAMP install, and everything was working fine, except my virtual machine was running DHCP, and I had need to have it statically addressed.  The mount auto-connected everytime, no problems.

But then (there had to be a 'but'), I did the change to a static IP.  No problem, just change the IP in the INTERFACES file, and be done.  But wait!  Now everytime the virtual machine would start, it would hang when trying to mount that external share.  Sending a "ctrl-alt-del" would get it out of the stupor, but the mount will have failed anyhow.  If I remarked the mount line from FSTAB, startup would be normal (no hangs) but also no mount.  Not good.

Finally, after much looking around online, I tried adding the "NOAUTO" to the FSTAB command for that mount.  The reboot of the system when through without hanging, and I could force the mount to happen by manually doing it at the command line (so I know it can and should work)... but I'd like to make this work automatically.

Any suggestions?

Thanks

---

### Post by mathisdermaler on 2008-01-17
When switching from DHCP to a static IP, did you lose your DNS?  If your VM doesn't know how to reach the DNS server it will not be able to mount the share.

After you boot up the VM up with the static IP, try this command at a shell:
```
host weshsrv-eng
```

If this doesn't return anything, you need to configure DNS on your VM.

---

### Post by pfurrie on 2008-01-18
Thanks for the reply.  Actually, I had tested connectivity by pinging one of the network servers by name, and had no problem.

When I try "host weshsrv-eng"... Ubuntu replies:

[FONT="Courier New"]-bash: host: command not found[/FONT]

So I figure there is no "host" command.  If I then try "ping weshsrv-eng" it resolves to the proper IP address and returns a bunch of pings, as it should.

DNS appears to be functional, so that wouldn't seem to be the source of the problem.  Any other ideas?

---

