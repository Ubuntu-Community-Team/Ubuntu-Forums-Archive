---
title: "Samba protected shares hostname authentication issue"
date: 2014-11-13
forum: General Help
---

### Post by hobbes1244 on 2014-11-13
I have samba running on my server and I'm having problems with protected shares.

From a Windows 7 machine, if I try to access a protected share by hostname, it will not authenticate my login. Example:
\\server\private_share  -- will ask for username/password but will not authenticate

however, if I use the hostname to access a public share, no problem. Example:
\\server\public_share -- will open public_share folder correctly.

In addition, if I access the private share by IP address it will ask for username/password and **will**  authenticate the login. Example:
\\192.168.1.20\private_share   -- will ask for username/password and will accept them and open folder.

Any ideas on why it will recognize the hostname but will only authenticate by IP address on a Windows 7 client?
Thanks.

---

### Post by bab1 on 2014-11-13
> **hobbes1244 said:**
> I have samba running on my server and I'm having problems with protected shares.

From a Windows 7 machine, if I try to access a protected share by hostname, it will not authenticate my login. Example:
\\server\private_share  -- will ask for username/password but will not authenticate

however, if I use the hostname to access a public share, no problem. Example:
\\server\public_share -- will open public_share folder correctly.

In addition, if I access the private share by IP address it will ask for username/password and **will**  authenticate the login. Example:
\\192.168.1.20\private_share   -- will ask for username/password and will accept them and open folder.

Any ideas on why it will recognize the hostname but will only authenticate by IP address on a Windows 7 client?
Thanks.

SMB/CIFS uses //NETBIOS_NAME/SHARE_NAME to locate the resource.  If you haven't set the NETBIOS NAME in the smb.conf file then the *nmbd *daemon will try and resolve the hostname to a NETBIOS NAME.  Of course the hostname needs to be properly configured for this to happen.  Have you configured the hosts file for name resolution? 

What parameters did you set for the "private share"?  Post the output of ```
cat /etc/samba/smb.conf
```

The Windows machine will pass the logged in user info to Samba.  If the user name is different from Samba to Windows then you should map the name in the smbusers file.  Is the user a Linux user (passwd) and a Samba user (smbpasswd -a)?   You can see the Samba user database with this command```
sudo pdbedit -L
```

---

