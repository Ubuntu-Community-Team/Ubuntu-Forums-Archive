---
title: "VSFTPD + PAM LDAP authentication -&gt; OpenLDAP"
date: 2005-06-01
forum: General Help
---

### Post by shadowcode on 2005-06-01
Hey all,

I'm running Ubuntu on my new homeserver. 
Am trying to set up VSFTPd to authenticate via PAM on LDAP.

It authenticates fine on the system's authentication.
```
# Standard Un*x authorization.
@include common-auth

# Standard Un*x authorization.
@include common-account

# Standard Un*x session setup and teardown.
@include common-session
```

However, I disabled those because I want to PAM_Ldap working, so I have this;```

auth            sufficient      /lib/security/pam_ldap.so       use_first_pass
password        sufficient      /lib/security/pam_ldap.so       try_first_pass
```

Anyway, I think that vsftpd is configured properly (since it does use PAM and authenticates ok if its configured to use PAM authentication), it's also linked against PAM.

So, there's probably a misconfiguration in /etc/ldap/slapd.conf or /etc/pam_ldap.conf. Could someone check, I'm probably doing something very stupid.

As for the passwords and security, the box hasn't been hooked up directly to the internet yet, and I'll tighten the security once I got it working.

**/etc/ldap/slapd.conf**[SIZE=2]```

#######################################################################
# Global Directives:

# Features to permit
#allow bind_v2

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema
include         /etc/ldap/schema/inetorgperson.schema

# Schema check allows for forcing entries to
# match schemas for their objectClasses's
schemacheck     on

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid

# List of arguments that were passed to the server
argsfile        /var/run/slapd.args

# Read slapd.conf(5) for possible values
loglevel        5

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap
moduleload      back_bdb

#######################################################################
# Specific Backend Directives for bdb:
# Backend specific directives apply to this backend until another
# 'backend' directive occurs
backend         bdb
checkpoint 512 30

#######################################################################
# Specific Directives for database #1, of type bdb:
# Database specific directives apply to this databasse until another
# 'database' directive occurs
database        bdb

# The base of your directory in database #1
suffix          "dc=localhost,dc=localdomain"

rootdn "cn=admin,dc=localhost,dc=localdomain"
rootpw secret

# Where the database file are physically stored for database #1
directory       "/var/lib/ldap"

# Indexing options for database #1
#index           objectClass eq

# Save the time that the entry gets modified, for database #1
#lastmod         on

# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only
access to attribute=userPassword
        by dn="cn=admin,dc=localhost,dc=localdomain" write
        by anonymous auth
        by self write
        by * none

# Ensure read access to the base for things like
# supportedSASLMechanisms.  Without this you may
# have problems with SASL not knowing what
# mechanisms are available and the like.
# Note that this is covered by the 'access to *'
# ACL below too but if you change that as people
# are wont to do you'll still need this if you
# want SASL (and possible other things) to work
# happily.
access to dn.base="" by * read

# The admin dn has full write access, everyone else
# can read everything.
access to *
        by dn="cn=admin,dc=localhost,dc=localdomain" write
        by * read

```[/SIZE]

**pam_ldap.conf:**```
###DEBCONF###
# the configuration of this file will be done by debconf as long as the
# first line of the file says '###DEBCONF###'
#
# you should use dpkg-reconfigure to configure this file
#
# @(#)$Id: ldap.conf,v 1.28 2003/05/29 13:01:04 lukeh Exp $
#
# This is the configuration file for the LDAP nameservice
# switch library and the LDAP PAM module.
#
# PADL Software
# http://www.padl.com
#

# Your LDAP server. Must be resolvable without using LDAP.
# Multiple hosts may be specified, each separated by a 
# space. How long nss_ldap takes to failover depends on
# whether your LDAP client library supports configurable
# network or connect timeouts (see bind_timelimit).
host 127.0.0.1

# The distinguished name of the search base.
base dc=localhost,dc=localdomain

# Another way to specify your LDAP server is to provide an
# uri with the server name. This allows to use
# Unix Domain Sockets to connect to a local LDAP Server.
#uri ldap://127.0.0.1/
#uri ldaps://127.0.0.1/   
#uri ldapi://%2fvar%2frun%2fldapi_sock/
# Note: %2f encodes the '/' used as directory separator

# The LDAP version to use (defaults to 3
# if supported by client library)
ldap_version 3

# The distinguished name to bind to the server with.
# Optional: default is to bind anonymously.
binddn cn=admin,dc=localhost,dc=localdomain

# The credentials to bind with. 
# Optional: default is no credential.
bindpw secret

# The distinguished name to bind to the server with
# if the effective user ID is root. Password is
# stored in /etc/ldap.secret (mode 600)
rootbinddn cn=admin,dc=localhost,dc=localdomain
rootbindpw secret

# The port.
# Optional: default is 389.
#port 389

# The search scope.
#scope sub
#scope one
#scope base

# Search timelimit
#timelimit 30

# Bind timelimit
#bind_timelimit 30

# Idle timelimit; client will close connections
# (nss_ldap only) if the server has not been contacted
# for the number of seconds specified below.
#idle_timelimit 3600

# Filter to AND with uid=%s
#pam_filter objectclass=account

# The user ID attribute (defaults to uid)
#pam_login_attribute uid

# Search the root DSE for the password policy (works
# with Netscape Directory Server)
#pam_lookup_policy yes

# Check the 'host' attribute for access control
# Default is no; if set to yes, and user has no
# value for the host attribute, and pam_ldap is
# configured for account management (authorization)
# then the user will not be allowed to login.
#pam_check_host_attr yes

# Check the 'authorizedService' attribute for access
# control
# Default is no; if set to yes, and the user has no
# value for the authorizedService attribute, and
# pam_ldap is configured for account management
# (authorization) then the user will not be allowed
# to login.
#pam_check_service_attr yes

# Group to enforce membership of
#pam_groupdn cn=PAM,ou=Groups,dc=padl,dc=com

# Group member attribute
#pam_member_attribute uniquemember

# Specify a minium or maximum UID number allowed
#pam_min_uid 0
#pam_max_uid 0

# Template login attribute, default template user
# (can be overriden by value of former attribute
# in user's entry)
#pam_login_attribute userPrincipalName
#pam_template_login_attribute uid
#pam_template_login nobody

# HEADS UP: the pam_crypt, pam_nds_passwd,
# and pam_ad_passwd options are no
# longer supported.

# Do not hash the password at all; presume
# the directory server will do it, if
# necessary. This is the default.
pam_password crypt

# Hash password locally; required for University of
# Michigan LDAP server, and works with Netscape
# Directory Server if you're using the UNIX-Crypt
# hash mechanism and not using the NT Synchronization
# service. 
#pam_password crypt

# Remove old password first, then update in
# cleartext. Necessary for use with Novell
# Directory Services (NDS)
#pam_password nds

# Update Active Directory password, by
# creating Unicode password and updating
# unicodePwd attribute.
#pam_password ad

# Use the OpenLDAP password change
# extended operation to update the password.
#pam_password exop

# Redirect users to a URL or somesuch on password
# changes.
#pam_password_prohibit_message Please visit http://internal to change your password.

# RFC2307bis naming contexts
# Syntax:
# nss_base_XXX		base?scope?filter
# where scope is {base,one,sub}
# and filter is a filter to be &'d with the
# default filter.
# You can omit the suffix eg:
# nss_base_passwd	ou=People,
# to append the default base DN but this
# may incur a small performance impact.
#nss_base_passwd	ou=People,dc=padl,dc=com?one
#nss_base_shadow	ou=People,dc=padl,dc=com?one
#nss_base_group		ou=Group,dc=padl,dc=com?one
#nss_base_hosts		ou=Hosts,dc=padl,dc=com?one
#nss_base_services	ou=Services,dc=padl,dc=com?one
#nss_base_networks	ou=Networks,dc=padl,dc=com?one
#nss_base_protocols	ou=Protocols,dc=padl,dc=com?one
#nss_base_rpc		ou=Rpc,dc=padl,dc=com?one
#nss_base_ethers	ou=Ethers,dc=padl,dc=com?one
#nss_base_netmasks	ou=Networks,dc=padl,dc=com?ne
#nss_base_bootparams	ou=Ethers,dc=padl,dc=com?one
#nss_base_aliases	ou=Aliases,dc=padl,dc=com?one
#nss_base_netgroup	ou=Netgroup,dc=padl,dc=com?one

# attribute/objectclass mapping
# Syntax:
#nss_map_attribute	rfc2307attribute	mapped_attribute
#nss_map_objectclass	rfc2307objectclass	mapped_objectclass

# configure --enable-nds is no longer supported.
# For NDS now do:
#nss_map_attribute uniqueMember member

# configure --enable-mssfu-schema is no longer supported.
# For MSSFU now do:
#nss_map_objectclass posixAccount User
#nss_map_attribute uid msSFUName
#nss_map_attribute uniqueMember posixMember
#nss_map_attribute userPassword msSFUPassword
#nss_map_attribute homeDirectory msSFUHomeDirectory
#nss_map_objectclass posixGroup Group
#pam_login_attribute msSFUName
#pam_filter objectclass=User
#pam_password ad

# configure --enable-authpassword is no longer supported
# For authPassword support, now do:
#nss_map_attribute userPassword authPassword
#pam_password nds

# For IBM SecureWay support, do:
#nss_map_objectclass posixAccount aixAccount
#nss_map_attribute uid userName
#nss_map_attribute gidNumber gid
#nss_map_attribute uidNumber uid
#nss_map_attribute userPassword passwordChar
#nss_map_objectclass posixGroup aixAccessGroup
#nss_map_attribute cn groupName
#nss_map_attribute uniqueMember member
#pam_login_attribute userName
#pam_filter objectclass=aixAccount
#pam_password clear

# Netscape SDK LDAPS
#ssl on

# Netscape SDK SSL options
#sslpath /etc/ssl/certs/cert7.db

# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
#ssl start_tls
#ssl on

# OpenLDAP SSL options
# Require and verify server certificate (yes/no)
# Default is "no"
#tls_checkpeer yes

# CA certificates for server certificate verification
# At least one of these are required if tls_checkpeer is "yes"
#tls_cacertfile /etc/ssl/ca.cert
#tls_cacertdir /etc/ssl/certs

# Seed the PRNG if /dev/urandom is not provided
#tls_randfile /var/run/egd-pool

# SSL cipher suite
# See man ciphers for syntax
#tls_ciphers TLSv1

# Client certificate and key
# Use these, if your server requires client authentication.
#tls_cert
#tls_key
```

**SLAPD Log:**```

Jun  1 23:50:58 localhost slapd[14488]: connection_get(10) 
Jun  1 23:50:58 localhost slapd[14488]: connection_get(10): got connid=26 
Jun  1 23:50:58 localhost slapd[14488]: connection_read(10): checking for input on id=26 
Jun  1 23:50:58 localhost slapd[14488]: ber_get_next on fd 10 failed errno=11 (Resource temporarily unavailable) 
Jun  1 23:50:58 localhost slapd[14488]: do_bind 
Jun  1 23:50:58 localhost slapd[14488]: >>> dnPrettyNormal: <cn=admin,dc=localhost,dc=localdomain> 
Jun  1 23:50:58 localhost slapd[14488]: <<< dnPrettyNormal: <cn=admin,dc=localhost,dc=localdomain>, <cn=admin,dc=localhost,dc=localdomain> 
Jun  1 23:50:58 localhost slapd[14488]: do_bind: version=3 dn="cn=admin,dc=localhost,dc=localdomain" method=128 
Jun  1 23:50:58 localhost slapd[14488]: ==> bdb_bind: dn: cn=admin,dc=localhost,dc=localdomain 
Jun  1 23:50:58 localhost slapd[14488]: bdb_dn2entry_rw("cn=admin,dc=localhost,dc=localdomain") 
Jun  1 23:50:58 localhost slapd[14488]: => bdb_dn2id_matched( "cn=admin,dc=localhost,dc=localdomain" ) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_dn2id("dc=localhost,dc=localdomain"): 4 (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 4 ) "dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 4 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: do_bind: v3 bind: "cn=admin,dc=localhost,dc=localdomain" to "cn=admin,dc=localhost,dc=localdomain" 
Jun  1 23:50:58 localhost slapd[14488]: send_ldap_result: conn=26 op=0 p=3 
Jun  1 23:50:58 localhost slapd[14488]: send_ldap_result: err=0 matched="" text="" 
Jun  1 23:50:58 localhost slapd[14488]: send_ldap_response: msgid=1 tag=97 err=0 
Jun  1 23:50:58 localhost slapd[14488]: connection_get(10) 
Jun  1 23:50:58 localhost slapd[14488]: connection_get(10): got connid=26 
Jun  1 23:50:58 localhost slapd[14488]: connection_read(10): checking for input on id=26 
Jun  1 23:50:58 localhost slapd[14488]: ber_get_next on fd 10 failed errno=11 (Resource temporarily unavailable) 
Jun  1 23:50:58 localhost slapd[14488]: do_search 
Jun  1 23:50:58 localhost slapd[14488]: >>> dnPrettyNormal: <dc=localhost,dc=localdomain> 
Jun  1 23:50:58 localhost slapd[14488]: <<< dnPrettyNormal: <dc=localhost,dc=localdomain>, <dc=localhost,dc=localdomain> 
Jun  1 23:50:58 localhost slapd[14488]: SRCH "dc=localhost,dc=localdomain" 2 0
Jun  1 23:50:58 localhost slapd[14488]:     1 0 0 
Jun  1 23:50:58 localhost slapd[14488]:     filter: (uid=test) 
Jun  1 23:50:58 localhost slapd[14488]:     attrs:
Jun  1 23:50:58 localhost slapd[14488]:  
Jun  1 23:50:58 localhost slapd[14488]: => bdb_back_search 
Jun  1 23:50:58 localhost slapd[14488]: bdb_dn2entry_rw("dc=localhost,dc=localdomain") 
Jun  1 23:50:58 localhost slapd[14488]: => bdb_dn2id_matched( "dc=localhost,dc=localdomain" ) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_dn2id("dc=localhost,dc=localdomain"): 4 (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 4 ) "dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: search_candidates: base="dc=localhost,dc=localdomain" (0x00000004) scope=2 
Jun  1 23:50:58 localhost slapd[14488]: => bdb_dn2idl( "dc=localhost,dc=localdomain" ) 
Jun  1 23:50:58 localhost slapd[14488]: => bdb_equality_candidates (objectClass) 
Jun  1 23:50:58 localhost slapd[14488]: <= bdb_equality_candidates: (objectClass) index_param failed (18) 
Jun  1 23:50:58 localhost slapd[14488]: => bdb_equality_candidates (uid) 
Jun  1 23:50:58 localhost slapd[14488]: <= bdb_equality_candidates: (uid) index_param failed (18) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search_candidates: id=-1 first=1 last=11 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 4 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 1 ) "dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search: 1 does not match filter 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 1 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 2 ) "cn=admin,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search: 2 does not match filter 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 2 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 4 ) "dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search: 4 does not match filter 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 4 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 5 ) "ou=people,dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search: 5 does not match filter 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 5 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 6 ) "ou=groups,dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search: 6 does not match filter 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 6 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 7 ) "ou=machines,dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search: 7 does not match filter 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 7 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 8 ) "ou=domains,dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search: 8 does not match filter 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 8 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 10 ) "uid=pbnw,ou=people,dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: bdb_search: 10 does not match filter 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 10 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 11 ) "uid=test,dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:58 localhost slapd[14488]: => send_search_entry: dn="uid=test,dc=localhost,dc=localdomain" 
Jun  1 23:50:58 localhost slapd[14488]: <= send_search_entry 
Jun  1 23:50:58 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 11 ): returned (0) 
Jun  1 23:50:58 localhost slapd[14488]: send_search_result: err=0 matched="" text="" 
Jun  1 23:50:58 localhost slapd[14488]: send_ldap_response: msgid=2 tag=101 err=0 
Jun  1 23:50:58 localhost slapd[14488]: connection_get(10) 
Jun  1 23:50:58 localhost slapd[14488]: connection_get(10): got connid=26 
Jun  1 23:50:58 localhost slapd[14488]: connection_read(10): checking for input on id=26 
Jun  1 23:50:58 localhost slapd[14488]: ber_get_next on fd 10 failed errno=11 (Resource temporarily unavailable) 
Jun  1 23:50:58 localhost slapd[14488]: do_bind 
Jun  1 23:50:58 localhost slapd[14488]: >>> dnPrettyNormal: <cn=admin,dc=localhost,dc=localdomain> 
Jun  1 23:50:58 localhost slapd[14488]: <<< dnPrettyNormal: <cn=admin,dc=localhost,dc=localdomain>, <cn=admin,dc=localhost,dc=localdomain> 
Jun  1 23:50:59 localhost slapd[14488]: do_bind: version=3 dn="cn=admin,dc=localhost,dc=localdomain" method=128 
Jun  1 23:50:59 localhost slapd[14488]: ==> bdb_bind: dn: cn=admin,dc=localhost,dc=localdomain 
Jun  1 23:50:59 localhost slapd[14488]: bdb_dn2entry_rw("cn=admin,dc=localhost,dc=localdomain") 
Jun  1 23:50:59 localhost slapd[14488]: => bdb_dn2id_matched( "cn=admin,dc=localhost,dc=localdomain" ) 
Jun  1 23:50:59 localhost slapd[14488]: ====> bdb_cache_find_entry_dn2id("dc=localhost,dc=localdomain"): 4 (1 tries) 
Jun  1 23:50:59 localhost slapd[14488]: ====> bdb_cache_find_entry_id( 4 ) "dc=localhost,dc=localdomain" (found) (1 tries) 
Jun  1 23:50:59 localhost slapd[14488]: ====> bdb_cache_return_entry_r( 4 ): returned (0) 
Jun  1 23:50:59 localhost slapd[14488]: do_bind: v3 bind: "cn=admin,dc=localhost,dc=localdomain" to "cn=admin,dc=localhost,dc=localdomain" 
Jun  1 23:50:59 localhost slapd[14488]: send_ldap_result: conn=26 op=2 p=3 
Jun  1 23:50:59 localhost slapd[14488]: send_ldap_result: err=0 matched="" text="" 
Jun  1 23:50:59 localhost slapd[14488]: send_ldap_response: msgid=3 tag=97 err=0 
Jun  1 23:50:59 localhost slapd[14488]: connection_get(10) 
Jun  1 23:50:59 localhost slapd[14488]: connection_get(10): got connid=26 
Jun  1 23:50:59 localhost slapd[14488]: connection_read(10): checking for input on id=26 
Jun  1 23:50:59 localhost slapd[14488]: ber_get_next on fd 10 failed errno=0 (Success) 
Jun  1 23:50:59 localhost slapd[14488]: connection_read(10): input error=-2 id=26, closing. 
Jun  1 23:50:59 localhost slapd[14488]: connection_closing: readying conn=26 sd=10 for close 
Jun  1 23:50:59 localhost slapd[14488]: connection_close: deferring conn=26 sd=10 
Jun  1 23:50:59 localhost slapd[14488]: do_unbind 
Jun  1 23:50:59 localhost slapd[14488]: connection_resched: attempting closing conn=26 sd=10 
Jun  1 23:50:59 localhost slapd[14488]: connection_close: conn=26 sd=10 
```

**Ldapsearch output:**```
root@serverII:/etc # ldapsearch -x -D "cn=admin,dc=localhost,dc=localdomain" -w secret
# extended LDIF
#
# LDAPv3
# base <> with scope sub
# filter: (objectclass=*)
# requesting: ALL
#

# localhost.localdomain
dn: dc=localhost,dc=localdomain
objectClass: organization
objectClass: dcObject
dc: localhost
o: localhost

# people, localhost.localdomain
dn: ou=people,dc=localhost,dc=localdomain
objectClass: organizationalunit
ou: people

# groups, localhost.localdomain
dn: ou=groups,dc=localhost,dc=localdomain
objectClass: organizationalunit
ou: groups

# machines, localhost.localdomain
dn: ou=machines,dc=localhost,dc=localdomain
objectClass: organizationalunit
ou: machines

# domains, localhost.localdomain
dn: ou=domains,dc=localhost,dc=localdomain
objectClass: organizationalunit
ou: domains

# pbnw, people, localhost.localdomain
dn: uid=pbnw,ou=people,dc=localhost,dc=localdomain
uid: pbnw
cn: pbnw
sn: pbnw
loginShell: /bin/bash
uidNumber: 1
gidNumber: 1
shadowMin: -1
shadowMax: 999999
shadowWarning: 7
shadowInactive: -1
shadowExpire: -1
shadowFlag: 0
objectClass: top
objectClass: person
objectClass: posixAccount
objectClass: shadowAccount
homeDirectory: /shared
userPassword:: e0NREmOvedremOvEDHc=

# test, localhost.localdomain
dn: uid=test,dc=localhost,dc=localdomain
uid: test
cn: test
sn: test
loginShell: /bin/bash
uidNumber: 1
gidNumber: 1
homeDirectory: /shared
shadowMin: -1
shadowMax: 999999
shadowWarning: 7
shadowInactive: -1
shadowExpire: -1
shadowFlag: 0
objectClass: top
objectClass: person
objectClass: posixAccount
objectClass: shadowAccount
userPassword:: e0NREmOvedremOvEDHc=

# search result
search: 2
result: 0 Success

# numResponses: 8
# numEntries: 7

```

Now, I suspect that there's something very obviously wrong somewhere, but, I've been staring at this stuff and I just can't find what's wrong. So please, if anyone wants to take a fresh look at it, thanks in advance!

---

### Post by shadowcode on 2005-06-02
Ugh, I posted this to the wrong forum, didn't see the  Ubuntu Server Talk one.

---

### Post by shadowcode on 2005-06-02
Never mind, I found what I was doing wrong..

I failed to realize that even if you let PAM handle the authentication, the system isn't configured to use LDAP to handle users, so that's where it goes wrong.

Unless you also let the 'system' completely authenticate against LDAP, you'll still need unix users for FTP accounts. Or something. I'll give it more thought later on, now it just 'works' (phew).

---

