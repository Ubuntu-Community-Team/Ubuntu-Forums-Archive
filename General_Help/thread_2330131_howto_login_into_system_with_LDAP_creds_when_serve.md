---
title: "howto login into system with LDAP creds when server with LDAP is offline"
date: 2016-07-08
forum: General Help
---

### Post by on-ilyin on 2016-07-08
[COLOR=#242729][FONT=Arial]I have Ubuntu 14.04 and LDAP as center of authentication. It works fine until LDAP server is online. Sometimes network is going to down between LDAP and other servers and LDAP is unavailable, so users can't login to server with theirs LDAP creds.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have installed nscd and during LDAP is offline command like
getent passwd $userid runs successfull. I tried several manual from internet, like:[http://ubuntuforums.org/showthread.php?t=1708785](http://ubuntuforums.org/showthread.php?t=1708785) but it doesn't work for me.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Guys, could you please share your configs with LDAP configuration which able to provide access to server with LDAP creds during LDAP is offline?[/FONT][/COLOR]

---

