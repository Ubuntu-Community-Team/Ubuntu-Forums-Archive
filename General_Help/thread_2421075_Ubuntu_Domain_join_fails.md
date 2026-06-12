---
title: "Ubuntu Domain join fails"
date: 2019-06-16
forum: General Help
---

### Post by pavmails on 2019-06-16
Hi All,

I have tried to add ubuntu 16 desktop to domain using samba. It fails saying Insuffiecient access.
But wbinfo works fine.
# wbinfo -t
checking the trust secret for domain DOMAIN via RPC calls succeeded

#wbinfo -a user
Enter user's password:
plaintext password authentication succeeded
Enter puser's password:
challenge/response password authentication failed
wbcAuthenticateUserEx(DOMAIN/user): error code was NT_STATUS_WRONG_PASSWORD (0xc000006a)
error message was: Wrong Password
Could not authenticate user user with challenge/response

# net ads testjoin
Join is OK  -- >  #But join was not successful



#wbinfo -i user
user:*:50000:50004::/home/DOMAIN/user:/bin/bash

Also wbinfo -g also gives output.

my smb.conf :
[global]
realm = DOMAIN.COM
#netbios name = ubuntu
security = ADS
#dns forwarder = 192.168.1.1
idmap config * : backend = tdb
idmap config *:range = 50000-1000000
template homedir = /home/%D/%U
template shell = /bin/bash
winbind use default domain = true
winbind offline logon = false
winbind nss info = rfc2307
winbind enum users = yes
winbind enum groups = yes
vfs objects = acl_xattr
map acl inherit = Yes
store dos attributes = Yes
workgroup = DOMAIN




krb5.conf :

[libdefaults]
        default_realm = DOMAIN.COM


# The following krb5.conf variables are only for MIT Kerberos.
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true


# The following encryption type specification will be used by MIT Kerberos
# if uncommented.  In general, the defaults in the MIT Kerberos code are
# correct and overriding these specifications only serves to disable new
# encryption types as they are added, creating interoperability problems.
#
# Thie only time when you might need to uncomment these lines and change
# the enctypes is if you have local software that will break on ticket
# caches containing ticket encryption types it doesn't know about (such as
# old versions of Sun Java).


#       default_tgs_enctypes = des3-hmac-sha1
#       default_tkt_enctypes = des3-hmac-sha1
#       permitted_enctypes = des3-hmac-sha1


# The following libdefaults parameters are only for Heimdal Kerberos.
        v4_instance_resolve = false
        v4_name_convert = {
                host = {
                        rcmd = host
                        ftp = ftp
                }
                plain = {
                        something = something-else
                }
        }
        fcc-mit-ticketflags = true
        default_keytab_name = /etc/krb5.keytab


[realms]


 ATHENA.MIT.EDU = {
                kdc = kerberos.mit.edu:88
                kdc = kerberos-1.mit.edu:88
                kdc = kerberos-2.mit.edu:88
                admin_server = kerberos.mit.edu
                default_domain = mit.edu
 }
        MEDIA-LAB.MIT.EDU = {
                kdc = kerberos.media.mit.edu
                admin_server = kerberos.media.mit.edu
        }
        ZONE.MIT.EDU = {
                kdc = casio.mit.edu
                kdc = seiko.mit.edu
                admin_server = casio.mit.edu
        }
        MOOF.MIT.EDU = {
                kdc = three-headed-dogcow.mit.edu:88
                kdc = three-headed-dogcow-1.mit.edu:88
                admin_server = three-headed-dogcow.mit.edu
        }
        CSAIL.MIT.EDU = {
                kdc = kerberos-1.csail.mit.edu
                kdc = kerberos-2.csail.mit.edu
                admin_server = kerberos.csail.mit.edu
                default_domain = csail.mit.edu
                krb524_server = krb524.csail.mit.edu
        }
        IHTFP.ORG = {
                kdc = kerberos.ihtfp.org
                admin_server = kerberos.ihtfp.org
        }
        GNU.ORG = {
                kdc = kerberos.gnu.org
                kdc = kerberos-2.gnu.org
                kdc = kerberos-3.gnu.org
                admin_server = kerberos.gnu.org
        }
        1TS.ORG = {
                kdc = kerberos.1ts.org
                admin_server = kerberos.1ts.org
        }
        GRATUITOUS.ORG = {
                kdc = kerberos.gratuitous.org
                admin_server = kerberos.gratuitous.org
        }
        DOOMCOM.ORG = {
                kdc = kerberos.doomcom.org
                admin_server = kerberos.doomcom.org
        }
        ANDREW.CMU.EDU = {
                kdc = kerberos.andrew.cmu.edu
                kdc = kerberos2.andrew.cmu.edu
                kdc = kerberos3.andrew.cmu.edu
                admin_server = kerberos.andrew.cmu.edu
                default_domain = andrew.cmu.edu
        }
        CS.CMU.EDU = {
                kdc = kerberos.cs.cmu.edu
                kdc = kerberos-2.srv.cs.cmu.edu
                admin_server = kerberos.cs.cmu.edu
        }
        DEMENTIA.ORG = {
                kdc = kerberos.dementix.org
                kdc = kerberos2.dementix.org
                admin_server = kerberos.dementix.org
        }
        stanford.edu = {
                kdc = krb5auth1.stanford.edu
                kdc = krb5auth2.stanford.edu
                kdc = krb5auth3.stanford.edu
                master_kdc = krb5auth1.stanford.edu
                admin_server = krb5-admin.stanford.edu
                default_domain = stanford.edu
        }
        UTORONTO.CA = {
                kdc = kerberos1.utoronto.ca
                kdc = kerberos2.utoronto.ca
                kdc = kerberos3.utoronto.ca
                admin_server = kerberos1.utoronto.ca
                default_domain = utoronto.ca
        }


[domain_realm]
        .mit.edu = ATHENA.MIT.EDU
        mit.edu = ATHENA.MIT.EDU
        .media.mit.edu = MEDIA-LAB.MIT.EDU
        media.mit.edu = MEDIA-LAB.MIT.EDU
        .csail.mit.edu = CSAIL.MIT.EDU
        csail.mit.edu = CSAIL.MIT.EDU
        .whoi.edu = ATHENA.MIT.EDU
        whoi.edu = ATHENA.MIT.EDU
        .stanford.edu = stanford.edu
        .slac.stanford.edu = SLAC.STANFORD.EDU
        .toronto.edu = UTORONTO.CA
        .utoronto.ca = UTORONTO.CA


[login]
        krb4_convert = true
        krb4_get_tickets = false






Please let me know why domain join fails ,but how wbinfo provides domain related info.

Regards
Pav

---

