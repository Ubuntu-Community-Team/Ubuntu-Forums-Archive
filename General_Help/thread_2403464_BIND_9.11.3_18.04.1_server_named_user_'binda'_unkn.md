---
title: "BIND 9.11.3 18.04.1 server named: user 'binda' unknown"
date: 2018-10-11
forum: General Help
---

### Post by mtndudebeach253 on 2018-10-11
Greetings.

Getting the weirdest named start error on a new install of BIND9 on 18.04.1 server.

ron@ubuntu-srv:/etc/bind$ sudo systemctl status bind9
&#9679; bind9.service - BIND Domain Name Server
   Loaded: loaded (/lib/systemd/system/bind9.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2018-10-11 09:46:11 MDT; 50s ago
     Docs: man:named(8)
  Process: 7555 ExecStart=/usr/sbin/named -f $OPTIONS (code=exited, status=1/FAILURE)
 Main PID: 7555 (code=exited, status=1/FAILURE)

bind version - BIND 9.11.3-1ubuntu1.2-Ubuntu (Extended Support Version) <id:a375815>

from my logs...

10/11/18 12:32 PM    systemd    Started BIND Domain Name Server.
10/11/18 12:32 PM    sudo    pam_unix(sudo:session): session closed for user root
10/11/18 12:32 PM    audit    USER_AVC pid=1948 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="ALLOWED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/systemd1" interface="org.freedesktop.systemd1.Manager" member="LookupDynamicUserByName" mask="send" name="org.freedesktop.systemd1" pid=12073 label="/usr/sbin/named" peer_pid=1 peer_label="unconfined"
 exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
**10/11/18 12:32 PM    named    named: user 'binda' unknown**
10/11/18 12:32 PM    kernel    kauditd_printk_skb: 150 callbacks suppressed
10/11/18 12:32 PM    kernel    audit: type=1107 audit(1539282724.738:505): pid=1948 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="ALLOWED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/systemd1" interface="org.freedesktop.systemd1.Manager" member="LookupDynamicUserByName" mask="send" name="org.freedesktop.systemd1" pid=12073 label="/usr/sbin/named" peer_pid=1 peer_label="unconfined"
 exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
10/11/18 12:32 PM    systemd    bind9.service: Main process exited, code=exited, status=1/FAILURE
10/11/18 12:32 PM    systemd    bind9.service: Failed with result 'exit-code'.

I don't have a user "binda" or a group call "binda".  file permissions appear to be correct. I have no idea who or what is calling "binda".   Any ideas?

Thanks!

---

### Post by SeijiSensei on 2018-10-12
What if you create a user with that name?

Maybe the server is trying to run in chrooted mode and needs a username.  I use CentOS on servers, and my DNS server runs chrooted as a bogus user called "named".

```

$ grep named /etc/passwd
named:x:25:25:Named:/var/named:/sbin/nologin
$ grep named /etc/group
named:x:25:

```

---

### Post by mtndudebeach253 on 2018-10-15
finally figured it out... there was a typo in the /etc/default/bind9 config file 

# startup options for the server
OPTIONS="-u binda -4"   obvious that should have been "bind".  Stupid mistake, but took may too long to find.    Thanks for the thoughts. -Ron

---

