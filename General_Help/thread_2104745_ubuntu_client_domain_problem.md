---
title: "ubuntu client domain problem"
date: 2013-01-14
forum: General Help
---

### Post by e303868 on 2013-01-14
Hi everyone
I configured ubuntu server 12.04 as a primary domain controller and I changed the smb.conf file as following:-

[global]
workgroup = Mydomain 
                                        
security = user

domain logons = yes                                                             domain master = yes                                                       local master = yes                                                       preferred master = yes                                                         
os level = 64 

logon path = \\%N\%U\profile

logon drive = H:                                                                 
logon home = \\%N\%U
logon script = logon.cmd

add machine script = /usr/sbin/useradd -g machines -c "%u machine accoun t" -d /var/lib/samba -s /bin/false %u 


comment = Home Directories 
browseable = no
writeable = yes 
read only = no
create mask = 0700 
directory mask = 0700
valid users = %S
username map = /etc/samba/smbusers 

[netlogon]                                                                       comment = Network Logon Service                                               path = /home/samba/netlogon  
guest ok = yes 
read only = yes 
share modes = no

[profiles]       
comment = Users profiles 
path = /srv/samba/profiles                                                                    guest ok = no 
browseable = no
create mask = 0600 
directory mask = 0700

[printers]   
  comment = All Printers
  browseable = no 
  path = /var/spool/samba 
  printable = yes  
------------------------------------------
and I added root user to samba using the following command:-
smbpasswd -a root
and it is ok
=================================
I successfully joined windows client to ubuntu 12.04 server domain everything is ok on windows client.
And I configured ubuntu 11.10 client to join the the domain using the following command:-

#net rpc join -W mydomain -U root
Enter root's password:
Joined domain MYDOMAIN.

I logged out and logged in with root user (the user which I used to join)  
but I could not login.
I tried the following:-
username:-  root
password:- 123456
and also tried:-
username:- mydomain\root
password:- 123456

it gives me the same error (invalid passwrod please try again)
despite that I am sure the password is ok because I used the same username (root) to join the domain and it is ok.

bye

---

