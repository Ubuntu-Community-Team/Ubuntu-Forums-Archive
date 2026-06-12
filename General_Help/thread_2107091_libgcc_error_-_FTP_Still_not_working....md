---
title: "libgcc error - FTP Still not working..."
date: 2013-01-21
forum: General Help
---

### Post by CourtArtanis on 2013-01-21
Hi,
I've searched and searched about this topic until my eyes bleed (or at least i think i have).
I still can't find a proposed solution or workaround that seems to do the trick.

First of all, the system is a VPS.
OS: Ubuntu 12.04
Dedi.Mem: 1gb
Open firewall for testing purposes.

[COLOR="Red"]The error....[/COLOR]
```

		[21/01/2013 07:16:18] 331 Please specify the password.
COMMAND:>	[21/01/2013 07:16:18] PASS *****
		[21/01/2013 07:16:18] libgcc_s.so.1 must be installed for pthread_cancel to work
		500 OOPS: priv_sock_get_result
ERROR:>   	[21/01/2013 07:16:18] WARNING! Invalid FTP reply received: 3 digit number expected at the beginning of the server reply.
ERROR:>   	[21/01/2013 07:16:18] Syntax error: command unrecognized.
STATUS:>  	[21/01/2013 07:16:19] Connection closed.

```

I've tried reinstalling libgcc_s.so.1 from several different sources and it's possible i've skimmed over other solutions being that i'm not 100% familiar with *nix servers...yet - gotta start somewhere right?

Here's the output from locate libgcc_s.so.1:
```
root@xxxxx:~# locate libgcc_s.so.1
/lib/i386-linux-gnu/libgcc_s.so.1
/lib/x86_64-linux-gnu/libgcc_s.so.1

```

As i'm using EHCP(latest) which is bundled with vsftpd(2.3.5) i'm not sure reinstalling the FTP server would be an option.

Also, 500 OOPS: priv_sock_get_result may be related? Not totally sure.....

---

### Post by cheruvim2 on 2013-09-27
I'm having this very same problem. Everything I've found so far says that it's a pam.d problem and to add 'crypt=hash' like so 
```

auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed crypt=hash

```

but that didn't work

I"m using vsftpd 2.3.5 and Ubuntu precise 64 <- might be the problem I assume that the crypt lib might only work as 32 bit???

any help would be appreciated..

Thanks

---

