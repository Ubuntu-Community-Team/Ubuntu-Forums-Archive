---
title: "Problems renewing expired OpenLDAP SSL Certificate"
date: 2012-10-23
forum: General Help
---

### Post by dougsymes on 2012-10-23
We went through the steps of revoking an SSL Certificate used by our OpenLDAP server and renewing it but we are unable to start slapd.

Here are the commands we used:
> 
  openssl verify hostname_domain_com_cert.pem

We got back that the certificate was expired but "OK"

We revoked the certificate we'd been using:

> 
  openssl ca -revoke /etc/ssl/certs/hostname_domain_com_cert.pem


Revoking worked fine.  

We created the new Cert Request by passing it the key file as input:

> 
  openssl req -new -key hostname_domain_com_key.pem -out newreq.pem


We generated a new certificate using the newly created request file "newreq.pem"

> 
  openssl ca  -policy policy_anything -out newcert.pem -infiles newreq.pem


We looked at our cn=config.ldif file and found the locations for the key and cert and placed the newly dated certificate in the needed path.  

Still we are unable to start slapd with:

> 
  service slapd start


We get this message:

> 
Starting OpenLDAP: slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).

Below, you can find the command line options used by this script to
run slapd. Do not forget to specify those options if you
want to look to debugging output:
  slapd -h 'ldap:/// ldapi:/// ldaps:///' -g openldap -u openldap -F /etc/ldap/slapd.d/


Here is what we found in /var/log/syslog

> 
Oct 23 20:18:25 ldap1 slapd[2710]: @(#) $OpenLDAP: slapd 2.4.21 (Dec 19 2011 15:40:04) $#012#011buildd@allspice:/build/buildd/openldap-2.4.21/debian/build/servers/slapd
Oct 23 20:18:25 ldap1 slapd[2710]: main: TLS init def ctx failed: -1
Oct 23 20:18:25 ldap1 slapd[2710]: slapd stopped.
Oct 23 20:18:25 ldap1 slapd[2710]: connections_destroy: nothing to destroy.


We are not sure what else to try.  Any ideas?
:confused:

---

