---
title: "LDAP Does Not Trust My CA Cert"
date: 2012-12-22
forum: General Help
---

### Post by peridian on 2012-12-22
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:        12.04
Codename:       precise

I've found a lot of bug reports around the following error:

TLS: peer cert untrusted or revoked (0x82)
TLS: can't connect: (unknown error code).
ldap_err2string
ldap_sasl_bind(SIMPLE): Can't contact LDAP server (-1)

I've also found a lot of bug reports about ldap clients not picking up the TLS_CACERT option:

TLS_CACERT /etc/ldap/cacerts/cacert.pem
TLS_CERT /etc/ldap/cacerts/server.pem
TLS_KEY /etc/ldap/cacerts/server.key.pem
TLS_REQCERT demand

When I run openssl s_client -connect ldapserver:636, I get:

Verify return code: 19 (self signed certificate in certificate chain)

Whereas if I run openssl s_client -connect ldapserver:636 -CAfile /etc/ldap/cacerts/cacert.pem, I get:

Verify return code: 0 (ok)

I thought it was a question of having my CA cert installed as a trusted cert, so I installed the cert under:

/usr/local/share/ca-certificates

This allows the command curl ldapserver:636 to complete without problem:

curl: (52) Empty reply from server

But it still does not solve the problem with ldap.

Is there some core certificate store that ldap trusts that I could copy my certificate into?

Regards,
Rob.

---

### Post by luvshines on 2012-12-22
Is your LDAP server using the same CA cert which your client is ?

---

### Post by peridian on 2012-12-22
> **luvshines said:**
> Is your LDAP server using the same CA cert which your client is ?

Yes, the cacert.pem is the public certificate issued by our Signing Authority server.  The certificates used by both the LDAP server and the Ubuntu server have both been signed by the same server.

The problem is not one of certificate mismatch, the problem is to do with the fact that my Signing Authority server signed its own private certificate.  Hence the message about a self-signed certificate in the chain.

Reading the bug reports, it seems at some point (around v8 or v9) Ubuntu's cert checking has been changed to no longer trust self-signed root authorities.

Understandable for the average joe's home desktop, or public facing web servers, but our organisation has a number of internal only applications that use SSL (e.g. LDAP) and we don't care about trusted certificate issuers for those.

Most of our servers are either Wintel or Red Hat, all of which can successfully negotiate the secure connection (once they have had the Signing Authority public cert either installed in their trusted certificate stores, or pointed to by the ldap.conf).

We've been looking to add a few Ubuntu servers to the estate, but unless we can resolve this issue, we've hit a dead end.

LDAP on Ubuntu ignores the setting in ldap.conf, and I can't seem to find where to install the cacert.pem in order to get the server as a whole to treat the cert as a trusted one.

Regards,
Rob.

---

