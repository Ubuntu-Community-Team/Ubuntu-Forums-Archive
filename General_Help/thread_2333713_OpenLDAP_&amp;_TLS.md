---
title: "OpenLDAP &amp; TLS"
date: 2016-08-12
forum: General Help
---

### Post by treaves on 2016-08-12
I'm having great trouble getting this to work.  I am following the directions [here]("https://help.ubuntu.com/lts/serverguide/openldap-server.html#openldap-tls"). When I run the command ```
[COLOR=#333333][FONT=monospace]ldapmodify -Y EXTERNAL -H ldapi:/// -f /etc/ssl/certinfo.ldif[/FONT][/COLOR]
``` I get this output.
```
SASL/EXTERNAL authentication startedSASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
modifying entry "cn=config"
ldap_modify: Other (e.g., implementation specific) error (80)



```

I've searched for two days now, and can not get past this.  I see this error in the search results, but, they all have an additional error line that provides additional information.  I see nothing in sysmsg, and when I run slaps in debug mode, nothing seems out-of-the-ordinary.

I have also tried [this]("https://help.ubuntu.com/community/OpenLDAPServer#Encryption") older document, where you just put the cert files directly into slaps.conf.  When I restart slaps, and try to connect using TLS, I just get [I]unsupported extended operation. 
[/I]
I'd greatly appreciate any help.

---

### Post by treaves on 2016-08-12
Well, I all of a sudden made progress.  While tailing the syslog file I saw an apparmor error preventing slaps from reading the cert files, even though the permissions on the cert files should have allowed it.  This seems to be a common issue, although some people report that they were able to get around it by setting file permissions.  I was not.  I tried to add a recursive read rule to /etc/apparmor.d/local/usr.sbin.slapd but that still showed the read error (probably because I do not understand apparmor).  I added each cert file, and it can now read them.  So the ldapmodify command succeeds.

Now the issue I am working on is getting Apache Directory Server to work.  I can create the connection, test the auth (which works), and retrieve the base dn.  But, once I complete the connection and actually try to connect, it hangs.

---

### Post by treaves on 2016-08-12
I'm running Ubuntu 16.04.1.  The issue I now have is:
```
140668035487384:error:140790E5:SSL routines:ssl23_write:ssl handshake failure:s23_lib.c:177
```

In [searching]("http://serverfault.com/questions/389197/ssl-routinesssl23-writessl-handshake-failure"), this seems to be a [bug in Ubuntu's OpenSSL]("https://bugs.launchpad.net/ubuntu/+source/openssl/+bug/965371").  But, I thought that was fixed by 1.0.2.  I guess not?

---

