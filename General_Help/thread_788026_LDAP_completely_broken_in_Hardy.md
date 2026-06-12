---
title: "LDAP completely broken in Hardy"
date: 2008-05-09
forum: General Help
---

### Post by sleepkreep on 2008-05-09
Hello all.  I'm trying to get Hardy to auth against our ldap server.  We have approximately 25 feisty machines authing against the LDAP system successfully currently.  The LDAP server is an Active Directory 2003 server with Services For Unix 3.5 installed.  Before anyone suggests this, likewise does not work.  I have tried for two weeks to get it to work, it just won't.  It complains about many ports being closed that are in fact open.  Such as the NTP and Kerberose ports.  It doesn't matter anyway since I need the UNIX attributes that Services For Unix provides.  

***UPDATE***
I now have a working config for ldap.conf.  For some reason hardy wouldn't let me work over port 636 without a root cert from my AD server.  I don't need one since I wrote my own chfn and chsh commands.  I'm also using kerberose for authentication and password changes.  

**Steps taken:**  
     install packages: ldap-auth-client ldap-utils
     set up /etc/ldap.conf
     symlink /etc/ldap/ldap.conf to /etc/ldap.conf
     Run auth-config:  #auth-client-config -a -p lac_ldap


Config files:
**/etc/ldap.conf  *WORKING CONFIG***
```

# @(#)$Id: ldap.conf,v 1.38 2006/05/15 08:13:31 lukeh Exp $
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
host moe.cs.mtsu.edu larry.cs.mtsu.edu

# The distinguished name of the search base.
base ou=Users,ou=CS Department,dc=cs,dc=mtsu,dc=edu

# Another way to specify your LDAP server is to provide an
#uri ldapi:///moe.cs.mtsu.edu
# Unix Domain Sockets to connect to a local LDAP Server.
uri ldap://161.45.167.223
#uri ldaps://127.0.0.1/   
#uri ldapi://%2fvar%2frun%2fldapi_sock/
# Note: %2f encodes the '/' used as directory separator

# The LDAP version to use (defaults to 3
# if supported by client library)
ldap_version 3

# The distinguished name to bind to the server with.
# Optional: default is to bind anonymously.
binddn CN=***EDITED***,CN=Users,DC=cs,DC=mtsu,DC=edu

# The credentials to bind with. 
# Optional: default is no credential.
bindpw ***EDITED***

# The distinguished name to bind to the server with
# if the effective user ID is root. Password is
# stored in /etc/ldap.secret (mode 600)
#rootbinddn "CN=Some Admin,CN=Users,DC=cs,DC=mtsu,DC=edu"

# The port.
# Optional: default is 389.
port 389

# The search scope.
scope sub
#scope one
#scope base

# Search timelimit
#timelimit 30

# Bind/connect timelimit
bind_timelimit 30

# Reconnect policy: hard (default) will retry connecting to
# the software with exponential backoff, soft will fail
# immediately.
bind_policy soft

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
pam_member_attribute msSFU30PosixMemberOf

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
#
# Do not hash the password at all; presume
# the directory server will do it, if
# necessary. This is the default.
#pam_password md5

# Hash password locally; required for University of
# Michigan LDAP server, and works with Netscape
# Directory Server if you're using the UNIX-Crypt
# hash mechanism and not using the NT Synchronization
# service. 
#pam_password crypt

# Remove old password first, then update in
# cleartext. Necessary for use with Novell
# Directory Services (NDS)
#pam_password clear_remove_old
#pam_password nds

# RACF is an alias for the above. For use with
# IBM RACF
#pam_password racf

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
nss_base_passwd		ou=Users,ou=CS Department,dc=cs,dc=mtsu,dc=edu?sub
nss_base_shadow		ou=Users,ou=CS Department,dc=cs,dc=mtsu,dc=edu?sub 
nss_base_group          ou=Groups,ou=CS Department,dc=cs,dc=mtsu,dc=edu?sub 
#nss_base_hosts		ou=CS Department,dc=cs,dc=mtsu,dc=edu?sub
#nss_base_services	ou=Services,dc=padl,dc=com?one
#nss_base_networks	ou=Networks,dc=padl,dc=com?one
#nss_base_protocols	ou=Protocols,dc=padl,dc=com?one
#nss_base_rpc		ou=Rpc,dc=padl,dc=com?one
#nss_base_ethers	ou=Ethers,dc=padl,dc=com?one
#nss_base_netmasks	ou=Networks,dc=padl,dc=com?ne
#nss_base_bootparams	ou=Ethers,dc=padl,dc=com?one
#nss_base_aliases	ou=Aliases,dc=padl,dc=com?one
#nss_base_netgroup	ou=Row 2,ou=CS Lab 351,ou=Labs,ou=CS Department,dc=cs,dc=mtsu,dc=edu?sub

# attribute/objectclass mapping
# Syntax:
#nss_map_attribute	rfc2307attribute	mapped_attribute
#nss_map_objectclass	rfc2307objectclass	mapped_objectclass

# configure --enable-nds is no longer supported.
# NDS mappings
#nss_map_attribute uniqueMember member

# Services for UNIX 3.5 mappings
#nss_map_objectclass posixAccount User
#nss_map_objectclass shadowAccount User
#nss_map_attribute uid msSFU30Name
#nss_map_attribute uniqueMember msSFU30PosixMember
#nss_map_attribute userPassword msSFU30Password
#nss_map_attribute homeDirectory msSFU30HomeDirectory
#nss_map_attribute homeDirectory msSFUHomeDirectory
#nss_map_objectclass posixGroup Group
#nss_map_attribute  mail   userPrincipalName
#nss_map_attribute  gecos displayName
#pam_login_attribute sAMAccountName
#pam_filter objectclass=User
#pam_password md5
#ssl no
#
nss_map_objectclass posixAccount User
nss_map_attribute uid msSFU30Name
nss_map_attribute uidNumber msSFU30UidNumber
nss_map_attribute gidNumber msSFU30GidNumber
nss_map_attribute uniqueMember member
nss_map_attribute userPassword msSFU30Password
nss_map_attribute homeDirectory msSFU30HomeDirectory
nss_map_attribute loginShell msSFU30LoginShell
nss_map_objectclass posixGroup Group
nss_map_attribute gecos displayName
nss_map_attribute mail userPrincipalName
pam_login_attribute msSFU30Name 
pam_password crypt

# configure --enable-mssfu-schema is no longer supported.
# Services for UNIX 2.0 mappings
#nss_map_objectclass posixAccount User
#nss_map_objectclass shadowAccount user
#nss_map_attribute uid msSFUName
#nss_map_attribute uniqueMember posixMember
#nss_map_attribute userPassword msSFUPassword
#nss_map_attribute homeDirectory msSFUHomeDirectory
#nss_map_attribute shadowLastChange pwdLastSet
#nss_map_objectclass posixGroup Group
#nss_map_attribute cn msSFUName
#pam_login_attribute msSFUName
#pam_filter objectclass=User
#pam_password ad

# RFC 2307 (AD) mappings
#nss_map_objectclass posixAccount user
#nss_map_objectclass shadowAccount user
#nss_map_attribute uid sAMAccountName
#nss_map_attribute homeDirectory unixHomeDirectory
#nss_map_attribute shadowLastChange pwdLastSet
#nss_map_objectclass posixGroup group
#nss_map_attribute uniqueMember member
#pam_login_attribute sAMAccountName
#pam_filter objectclass=User
#pam_password ad

# configure --enable-authpassword is no longer supported
# AuthPassword mappings
#nss_map_attribute userPassword authPassword

# AIX SecureWay mappings
#nss_map_objectclass posixAccount aixAccount
#nss_base_passwd ou=aixaccount,?one
#nss_map_attribute uid userName
#nss_map_attribute gidNumber gid
#nss_map_attribute uidNumber uid
#nss_map_attribute userPassword passwordChar
#nss_map_objectclass posixGroup aixAccessGroup
#nss_base_group ou=aixgroup,?one
#nss_map_attribute cn groupName
#nss_map_attribute uniqueMember member
#pam_login_attribute userName
#pam_filter objectclass=aixAccount
#pam_password clear

# Netscape SDK LDAPS
#ssl on

# Netscape SDK SSL options
#sslpath /etc/ssl/certs

# OpenLDAP SSL mechanism
# start_tls mechanism uses the normal LDAP port, LDAPS typically 636
#ssl start_tls
#ssl off

# OpenLDAP SSL options
# Require and verify server certificate (yes/no)
# Default is to use libldap's default behavior, which can be configured in
# /etc/openldap/ldap.conf using the TLS_REQCERT setting.  The default for
# OpenLDAP 2.0 and earlier is "no", for 2.1 and later is "yes".
tls_checkpeer no

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

# Disable SASL security layers. This is needed for AD.
sasl_secprops maxssf=0

# Override the default Kerberos ticket cache location.
#krb5_ccname FILE:/etc/.ldapcache

# SASL mechanism for PAM authentication - use is experimental
# at present and does not support password policy control
#pam_sasl_mech DIGEST-MD5
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,daemon,dhcp,distccd,games,gdm,gnats,haldaemon,hplip,identd,irc,klog,libuuid,list,lp,mail,man,messagebus,news,ntp,nx,polkituser,postfix,proxy,pulse,root,rwhod,sshd,statd,stunnel4,sync,sys,syslog,uml-net,uucp,vde2-net,www-data


```
[B]
/etc/nsswitch[/B]
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd: files ldap
group: files ldap
shadow: files ldap

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

---

### Post by sleepkreep on 2008-05-12
No one?  I need this working by then end of this week or we have to stick with Feisty for another year.

---

### Post by songshu on 2008-05-12
check my signature, i'm in pain as well.

i use OpenLDAP on the server side (debian stable), but since Gutsy the client authentication has been a moving target. i got it to work in Hardy using some gutsy guides but its not as it should be yet, nevertheless it does work as proof of concept.
It took me a chicken already to get this far and i'm seriously considering to  sacrifice another one.

---

### Post by sleepkreep on 2008-05-12
I'm afraid that doesn't really help me.  As you can see by my config, everything you have (except for using ldapi://, which I tried) in your setup, I have in mine.  

As a side note, you're project seems like total overkill.  Just use FAI.  That's what I use to deploy and maintain hundreds of Ubuntu machines on my network.  One install system manages installs and maintainance for everything from servers, Xen servers, cluster nodes, desktops, and portables (laptops).  It's a great system and will do everything you're trying to accomplish with far more flexibility.

---

### Post by songshu on 2008-05-12
have been looking at FAI, but not being sure how mature the ubuntu implementation is, i figured to go the simpler route first...till i hitted this ldap block the FAI seemd like overkill to me.

but i do not need to have this done by the end of the week so i might just go another route ;) would love to see what you have going on that part.



the culprit would be the lac_ldap in this one i think, what do you have over there? 
lac_ldap is the standard one for OpenLDAP as far as i understood, i used a slightly modified version...for AD you should need a different config if i get it right after reading the dev mailing list

---

### Post by sleepkreep on 2008-05-12
Yeah, overkill was an inappropriate word to describe what you are trying to do.  I can say that the Ubuntu implementation for FAI is pretty solid with Hardy.  It's just a matter of figuring out which packages to install.  Since Ubuntu is pretty much made up of meta packages, that's fairly simple.  I need FAR fewer hacks with Hardy than I did with Feisty or Dapper.  Anyway, if you're just trying to deploy one type of system on just a few machines, your way will work fairly well.  But FAI allows you to install (and maintain) many different kinds of installs over the network, no media necessary.  You do have to have a network card capable of PXE boot, but what card doesn't do that no-a-days?  

I did finally get my LDAP setup working, but not the way I want.  I don't want to go through setting up keys for the clients just so the directory admin user can bind against it.  I just use kerberose authentication to auth  and change passwords.  Unfortunately that requires I get Windows to sync against our NTP server which seems to be a real pain.  I'll post a working setup in a bit when I finish my work.

---

### Post by songshu on 2008-05-12
i need to do about 70 desktops but they will be all the same. and if changes are needed they would all have to change, so i figured i could handle that with some meta packages.

the flexibility of FAI for the most part comes from the NFS root as far as i understood. this would also ask for some adjustment since i do most my server taksks with Vserver and that does not work so well with NFS.

and i would have to put in some more study in to the whole thing before i would feel really comfortable with it.

nevertheless if you know some good info on Hardy specifics i would like to know, the most i could find was mainly based on Hoary.

---

