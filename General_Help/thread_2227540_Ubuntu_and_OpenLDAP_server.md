---
title: "Ubuntu and OpenLDAP server"
date: 2014-06-02
forum: General Help
---

### Post by project722 on 2014-06-02
I am having multiple issues trying to get OpenLDAP-Server installed. Here is my environment:

Ubuntu 14.04 LTS - (not "server edition") running in VirtualBox on a Win 7 Prox86 machine. 

Installed OpenLDAP server with this command - "sudo apt-get install slapd ldap-utils"

Everything went smooth - no issues. 

Hosts file entry looks like this- "127.0.0.1   ldap.example.com   ldap"

I am following the guide here - [https://help.ubuntu.com/14.04/serverguide/openldap-server.html](https://help.ubuntu.com/14.04/serverguide/openldap-server.html)

I can run this - "sudo ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=config dn" to get the output listed in the guide without issue. 

However this next step:

"ldapsearch -x -LLL -H [ldap:///](ldap:///) -b dc=ldap,dc=example,dc=com dn" returns this:

"ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

I notice that when I run "netstat -plane | grep ":389" I do not see the ldap server (127.0.0.1) listening on 389. I get this:

tcp 0 0     0.0.0.0:389  1062/slapd

This may be part of the problem but I do not see how or where to force the slapd process to listen on 127.0.0.1 over port 389. I do not have anything in /etc/ldap/sasl2 and I replaced my Ldap.conf file with a sample file I found on the internet. ( I removed it earlier as a TS step) Any help is greatly appreciated.

---

### Post by project722 on 2014-06-02
This thread can be closed - it was a formatting error using ldapuri

---

