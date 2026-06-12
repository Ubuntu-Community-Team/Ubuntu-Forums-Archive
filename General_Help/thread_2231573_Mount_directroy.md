---
title: "Mount directroy"
date: 2014-06-26
forum: General Help
---

### Post by Escande_Guillaume on 2014-06-26
Hello there, 


I set up an intranet automatic connection with Active Directory. 


In internet explorer when a user goes to the intranet is automatically connected. 


There is another feature I have added is a search engine file on a windows network drive. 


I do not know if this is the right way, but I try to make sure that users who connect to the intranet can access the network and the network drive mounts automatically in the user's home directory drive. 


I tried several tutorial but I confess patoger a little? 


Here is my config so far: 


Apache: 


  <Location /user/login/sso> 


      Options-MultiViews 
     options FollowSymLinks 
            NTLMAuth on 
            AuthType NTLM 
            AuthName "Moodle NTLM Authentication" 
            NTLMAuthHelper "/ usr / bin / ntlm_auth - helper-protocol = squid-2.5-NTLMSSP" 
            NTLMBasicAuthoritative on 
            require valid-user 




Smb. conf: 




[global] 
     # No. Tld 
     workgroup = DOMBS1 
     # Active Directory System 
     security = ads 
     # With. Tld 
     realm = DOMBS1.PRI 
     # Just a member server 
     domain master = no 
     local master = no 
     preferred master = no 
     # Disable printing error log messages When CUPS is not installed. 
     printcap name = / etc / printcap 
     load printers = no 
     # Works in Both samba 3.2 and 3.6. 
     idmap backend = tdb 
     idmap uid = 10000-99999 
     idmap gid = 10000-99999 
     # No. Tld 
     idmap config DOMBS1: backend = rid 
     idmap config DOMBS1: range = 10000-9999 
     winbind enum users = no 
     winbind enum groups = no 
     # This way users log in with username INSTEAD of [email]username@example.org[/email] 
     winbind use default domain = yes 
     # Inherit groups in groups 
     winbind nested groups = yes 
     winbind refresh tickets = yes 
     winbind offline logon = true 
browseable = no 
writable = yes 
     Becomes # / home / example / username 
     template homedir = / home/DOMBS1 /% U 
     # No shell access 
     template shell = / bin / false 
     Client use spnego = yes 
     customer NTLMv2 auth = yes 
ntlm auth = no 
     encrypt passwords = yes 
     restrict anonymous = 2 
     log file = / var / log / samba / log.% m.log 
max log size = 1000 
     log level = 2 
syslog = 0 
# Logins go to `last` 
    wtmp directory = / var / log 
    utmp = yes 
    utmp directory = / var / run 


The problem is that the directory / home/DOMBS1 is never supplied. 
Any idea?

---

