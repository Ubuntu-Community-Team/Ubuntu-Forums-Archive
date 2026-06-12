---
title: "start upstart job from regular script"
date: 2013-09-27
forum: General Help
---

### Post by hg088 on 2013-09-27
I'm running ubuntu using crouton on a samsung arm chromebook.

I'm having trouble running samba cause ubuntu can't run upsatart jobs since only chrome os can do that.

The crouton developer posted a comment ([https://github.com/dnschneid/crouton/issues/120](https://github.com/dnschneid/crouton/issues/120)) saying i needed to figure which commands should be issued in order for samba to run (from the smbd.conf file in the init folder)

Here's the content of the file:

```
description "SMB/CIFS File Server"author      "Steve Langasek <steve.langasek@ubuntu.com>"


start on (local-filesystems and net-device-up)
stop on runlevel [!2345]


respawn


pre-start script
	RUN_MODE="daemons"


	[ -r /etc/default/samba ] && . /etc/default/samba


	[ "$RUN_MODE" = inetd ] && { stop; exit 0; }


	install -o root -g root -m 755 -d /var/run/samba
end script


exec smbd -F



```

So I was wondering which of these commands i need to run in order to start samba

---

