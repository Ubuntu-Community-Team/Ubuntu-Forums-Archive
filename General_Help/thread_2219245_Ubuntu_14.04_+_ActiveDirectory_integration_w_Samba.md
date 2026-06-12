---
title: "Ubuntu 14.04 + ActiveDirectory integration w/ Samba + Winbind not working"
date: 2014-04-23
forum: General Help
---

### Post by vocoder42 on 2014-04-23
I'm guessing some settings have changed, or packages need to be installed...I had ActiveDirectory authentication working perfectly in 12.04 (and before).  It no longer works for me (the way I have it set up anyway) after upgrading to 14.04.  I did a fresh install as well, just to be sure.

getent passwd returns local accounts only (same with getent group)

wbinfo -u returns domain users
wbinfo -g returns domain groups

however when i try to log into my computer using my domain account, it always tells me invalid password.  additionally if i try to su to a domain account, it tells me 'no passwd entry'

after i did a pam-auth-update and noticed there was no option for activedirectory, someone pointed me to "apt-get install libnss-winbind libpam-winbind" - this does make the ad option show up, but still can't log in.  here are my config files:

/etc/pam.d/common-account
```

account sufficient pam_winbind.so
account required pam_unix.so

```

/etc/pam.d/common-auth
```

auth sufficient pam_winbind.so
auth required pam_unix.so nullok_secure use_first_pass

```

/etc/pam.d/common-password
```

password required pam_unix.so nullok obscure min=4 max=50 md5

```

/etc/pam.d/common-session
```

session required pam_mkhomedir.so umask=0022 skel=/etc/skel

```

/etc/samba/smb.conf
```

[global]

    workgroup = MYDOMAIN
    security = ADS
    realm = MYDOMAIN.COM
    netbios name = trusty

    idmap config *:backend = tdb
    idmap config *:range = 70001-80000
    idmap config MYDOMAIN:backend = ad
    idmap config MYDOMAIN:schema_mode = rfc2307
    idmap config MYDOMAIN:range = 500-40000

    winbind nss info = rfc2307
    [test]
    path = /srv/samba/test
    read only = no

```

/etc/krb5.conf
```

[libdefaults]
    default_realm = MYDOMAIN.COM
    ticket_lifetime = 24000
    allow_weak_crypto = yes
    [realms]
    MYDOMAIN.COM = {
            kdc = my.domain.com
            admin_server = my.domain.com
            default_domain = MYDOMAIN.COM
    }


    [domain_realm]
    .mydomain.com = MYDOMAIN.COM
    mydomain.com = MYDOMAIN.COM
    [login]
    krb4_convert = true
    krb4_get_tickets = false

```

/etc/nsswitch.conf
```

passwd:         compat winbind
group:          compat winbind
shadow:         compat winbind

hosts:          files mdns4_minimal [NOTFOUND=return] dns wins
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis


```

i guess the main change between 12.04 and 14.04 is the move from samba3 to samba4, is that right?  is there a setting or something that i am missing?

edit: i noticed that after i reboot the computer and login with my local account...there is not kerberos ticket, i have to kinit to get a new one....i'm wondering if it isn't doing this on startup and that is the reason i can't login...how do i make automatically get a ticket at startup?

---

### Post by sitro on 2014-04-23
> **vocoder42 said:**
> I'm guessing some settings have changed, or packages need to be installed...I had ActiveDirectory authentication working perfectly in 12.04 (and before).  It no longer works for me (the way I have it set up anyway) after upgrading to 14.04.  I did a fresh install as well, just to be sure.
[...]
i guess the main change between 12.04 and 14.04 is the move from samba3 to samba4, is that right?  is there a setting or something that i am missing?

edit: i noticed that after i reboot the computer and login with my local account...there is not kerberos ticket, i have to kinit to get a new one....i'm wondering if it isn't doing this on startup and that is the reason i can't login...how do i make automatically get a ticket at startup?

I'm not sure to understand all the problem.
So you authenticated against an active directory of microsoft server ? 
if right, in which way ? (winbind or ldap ?) it seems that you say : windbind.
From memory when I did in past that, I believe that the personnal computer (even in ubuntu) have to be register to the AD. and each computer (server and pc) have an authenticated system. On samba there is secret file that store secret pass.Therefore you did a fresh install and lost the secret file of the ubuntu 12.04.
So you have to register the computer again on the AD. I believe that it is done by the administrator of the AD. he has to delete your old computer and register the new one (logical).
So I say that from memory, and I have had not touch this kind of system for a long time. it may that I'm wrong.

---

### Post by vocoder42 on 2014-04-24
yeah the computer is joined to the domain.  using the configuration files i posted above, the steps are:

net ads join -U accountname

it joins the domain.  I double checked the DNS server (running on the same machine as the active directory server) and the computer shows up.

after this, wbinfo -u and wbinfo -g return domain users + groups.

ntpdate mydomain.com to make sure the time is in sync

kinit [email]account@MYDOMAIN.COM[/email] to get a ticket

klist confirms that ticket has been created

su domainuser returns "user not in passwd"

su domainuser on a 12.04 computer i have joined to the domain allows me to become that user.

if i reboot the computer, open a shell and type klist, it shows no ticket.  if i reboot the 12.04 computer that is working and type klist, it shows a ticket.  therefore i think that is at least partially my problem, but i'm not sure what is causing it. although you would think that after performing all the steps above, i could at least become the domain user (without reboot)

and yes, this is joining a microsoft active directory server.

---

### Post by sitro on 2014-04-24
ok. I think there are many jobs to touch all the files that are in this system.
maybe you can be helped by 2 packages that integrate a machine in an Active Directory environment: 

- likewise [https://help.ubuntu.com/10.04/serverguide/likewise-open.html](https://help.ubuntu.com/10.04/serverguide/likewise-open.html) .
or
- sadms  [https://help.ubuntu.com/community/ActiveDirectoryWinbind-SADMS](https://help.ubuntu.com/community/ActiveDirectoryWinbind-SADMS)

---

### Post by sitro on 2014-04-24
[COLOR=#333333][FONT=Ubuntu]I read there :
1/ The name service cache daemon (nscd) can interfere with winbind, as winbind maintains its own cache. [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Remove it.[/FONT][/COLOR]
2/ compare to your configuration file . your nssswitch seems not correct.
[COLOR=#333333][FONT=inherit] -check that nsswitch is correct. Shadow should not reference winbind. Shadow passwords will be retrieved through the pam implementation of winbind.
[/FONT][/COLOR]file: /etc/nsswitch.conf
[LIST]
[*=left]passwd:         compat winbind
group:          compat winbind
shadow:         compat
[/LIST]

---

### Post by mad_pheonix on 2014-04-24
I was having the exact same problems.  I was able to solve my issues by installing libnss-winbind and libpam-winbind, then restarting the winbind service.  I note that they are not dependencies of the winbind package, maybe that is what has changed between 12.04 and 14.04?

---

### Post by vocoder42 on 2014-04-25
yeah, I installed both of those packages and its still not working for me.  It's extremely frustrating as I'm not really sure how to troubleshoot it..and this method worked perfectly in 12.04 (and earlier versions)

---

### Post by lingpanda on 2014-04-25
This link may or may not be of some assistance. [https://wiki.samba.org/index.php/Winbind](https://wiki.samba.org/index.php/Winbind)

---

### Post by vocoder42 on 2014-04-25
yeah i've looked at that....so i sshd into my machine to look at auth.log when i try to login with a domain account...and this shows up in the log:
```

        Apr 25 11:59:21 mycomputer lightdm: PAM adding faulty module: pam_kwallet.so
        Apr 25 11:59:28 mycomputer lightdm: pam_unix(lightdm:auth): check pass; user unknown
        Apr 25 11:59:28 mycomputer lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=
        Apr 25 11:59:28 mycomputer lightdm: pam_winbind(lightdm:auth): getting password (0x00000388)
        Apr 25 11:59:28 mycomputer lightdm: pam_winbind(lightdm:auth): pam_get_item returned a password
        Apr 25 11:59:30 mycomputer lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
        Apr 25 11:59:30 mycomputer lightdm: PAM adding faulty module: pam_kwallet.so

```
it makes sense that pam_unix is failing because its not a local account...but i'm not sure what to make of the winbind mesage.  and the pam_kwallet thing is weird...i believe its a bug, seems to happen on local account successful logins as well, so not sure it is related to this or not.

edit: I had forgotten I had changed my pam files to default....changing them back to what I had (and what is suggested in the samba.org link) here is the auth.log
```

    Apr 25 13:08:09 mycomputer lightdm: pam_winbind(lightdm:auth): getting password (0x00000000)
    Apr 25 13:08:15 mycomputer lightdm: pam_winbind(lightdm:auth): user 'domanuser' granted access
    Apr 25 13:08:15 mycomputer lightdm: pam_unix(lightdm:account): could not identify user (from getpwnam(domainuser))
    Apr 25 13:08:15 mycomputer lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared 
object file: No such file or directory


```

so its strange...it seems to authenticate...but still tell me invalid password

---

### Post by WoodenWalker on 2014-04-25
> **vocoder42 said:**
> 

su domainuser returns "user not in passwd"



I haven't really used Trusty that much.... But have you checked the passwd file for said user? It seems to be returning that the user you're looking for has not been added to that file. Try editing it? Sorry if that isn't very useful, but it's all I can think of at the moment.

---

### Post by vocoder42 on 2014-04-25
well, the thing is...it shouldn't be checking the passwd file...it should be using active directory (winbind i guess) for authentication - the user won't be in the passwd file, as that is for local users.

---

### Post by jamesisin on 2014-04-25
I have only used likewise-open (now called pbis-open and no longer in the repositories but available as a .deb).  I have these notes on adding a machine which may or may not be of use (or perhaps spark something):

[http://jamesisin.com/a_high-tech_blech/index.php/2011/12/attach-ubuntu-to-windows-domain-via-active-directory-sudo/](http://jamesisin.com/a_high-tech_blech/index.php/2011/12/attach-ubuntu-to-windows-domain-via-active-directory-sudo/)

---

### Post by sitro on 2014-04-26
> **vocoder42 said:**
> 
however when i try to log into my computer using my domain account, it always tells me invalid password.  additionally if i try to su to a domain account, it tells me 'no passwd entry'


/etc/pam.d/common-password
```

password required pam_unix.so nullok obscure min=4 max=50 md5

```



I'm not an expert, but the file /etc/pam.d/common-password should it not be :
```

[COLOR=#000000]password   sufficient pam_winbind.so  [/COLOR]use_authtok[COLOR=#000000]
[/COLOR][COLOR=#000000]password   required   pam_unix.so nullok obscure min=4 max=50 md5[/COLOR][COLOR=#000000]
[/COLOR]
```

---

### Post by sitro on 2014-04-26
there is a document that describes the possible architectures for linux-active directory (not a help for your issue but fine to see the general goal)
[http://technet.microsoft.com/en-us/magazine/2008.12.linux.aspx#id0060057](http://technet.microsoft.com/en-us/magazine/2008.12.linux.aspx#id0060057)

---

### Post by sitro on 2014-04-26
> **vocoder42 said:**
> 
```

        Apr 25 11:59:21 mycomputer lightdm: PAM adding faulty module: pam_kwallet.so
        Apr 25 11:59:28 mycomputer lightdm: pam_unix(lightdm:auth): check pass; user unknown
        Apr 25 11:59:28 mycomputer lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=
        Apr 25 11:59:28 mycomputer lightdm: pam_winbind(lightdm:auth): getting password (0x00000388)
        Apr 25 11:59:28 mycomputer lightdm: pam_winbind(lightdm:auth): pam_get_item returned a password
        Apr 25 11:59:30 mycomputer lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
        Apr 25 11:59:30 mycomputer lightdm: PAM adding faulty module: pam_kwallet.so

```
it makes sense that pam_unix is failing because its not a local account...but i'm not sure what to make of the winbind mesage.  and the pam_kwallet thing is weird...i believe its a bug, seems to happen on local account successful logins as well, so not sure it is related to this or not.

Don't be worry with the error message of the pam_kwallet. it's the KDE wallet single sign on for kubuntu.
I don't know why they integrate in the file /etc/pam.d/lightdm . 
there is a reference bug :  [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1309535](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1309535)

---

### Post by vocoder42 on 2014-05-05
I could never get the samba/winbind integration to work.  I believe it's something that has changed in Samba 4 that isn't working right (or a setting i'm missing) with our Active Directory server.  Haven't been able to figure out what it is though.

I installed powerbroker open and after messing around with it for a bit, finally got it working....except I am unable to SSH into my machine using my domain details.  Basically, it appears that Powerbroker Open uses a variable called "Template" to set the domain users shell (and you can change this using config LoginShellTemplate) - well when I try to SSH into the machine, in auth.log I see this: "User domainuser not allowed because shell Template does not exist"

So i'm wondering if there is some way to tell SSH to use a specific shell instead of the Template variable or something along those lines.  Anyone have experience with this?  I would try asking over on the powerbroker forums, but they appear mostly inactive and you have to wait for someone to approve your account before you can post (have been waiting for a week so far)

---

### Post by lingpanda on 2014-05-05
> **vocoder42 said:**
> I could never get the samba/winbind integration to work.  I believe it's something that has changed in Samba 4 that isn't working right (or a setting i'm missing) with our Active Directory server.  Haven't been able to figure out what it is though.

I installed powerbroker open and after messing around with it for a bit, finally got it working....except I am unable to SSH into my machine using my domain details.  Basically, it appears that Powerbroker Open uses a variable called "Template" to set the domain users shell (and you can change this using config LoginShellTemplate) - well when I try to SSH into the machine, in auth.log I see this: "User domainuser not allowed because shell Template does not exist"

So i'm wondering if there is some way to tell SSH to use a specific shell instead of the Template variable or something along those lines.  Anyone have experience with this?  I would try asking over on the powerbroker forums, but they appear mostly inactive and you have to wait for someone to approve your account before you can post (have been waiting for a week so far)

I'm unable to paste in a format that is readable. 

Sorry for the format. See below from Admin guide.

Set the Home Directory and Shell for Domain Users
When you install PowerBroker Identity Services on a Linux, Unix, or Mac
computer but not on Active Directory, you cannot associate a PowerBroker
cell with an organizational unit, and thus you have no way to define a home
directory or shell in Active Directory for users who log on the computer
with their domain credentials. To set the home directory and shell for a
Linux, Unix, or Mac computer that is using PBIS Open or PBIS Enterprise
without cell, edit the value entry in registry.
If you use PBIS Enterprise to set the shell and home directory both in
Active Directory and in the registry, the settings in Active Directory take
precedence.
After you change the home directory or shell in the registry, you must clear
the PBIS authentication cache, log off, and then log on before your changes
will take effect.
In the lsass branch, there are two keys that contain value entries for the
home directory and shell. One is for the local provider, the other is for the
Active Directory provider. Locations:
[HKEY_THIS_
MACHINE\Services\lsass\Parameters\Providers\ActiveDirectory]
[HKEY_THIS_MACHINE\Services\lsass\Parameters\Providers\Local]
PBIS Open Installation and Administration Guide
BeyondTrust® May 8, 2012 226
The following value entries for the home directory and shell, shown with
their default settings, appear under both the Active Directory and Local
provider keys:
"LoginShellTemplate"="/bin/sh"
"HomeDirTemplate"="%H/local/%D/%U"
"HomeDirPrefix"="/home"
"CreateHomeDir"=dword:00000001
Set the Shell
Under the key for a provider, modify the value of the following entry to set
the shell that you want:
LoginShellTemplate
Example with default value:
"LoginShellTemplate"="/bin/sh"
Note: /bin/bash might not be available on all systems.
Set the Home Directory
You can modify the HomeDirTemplate value entry to set the home
directory that you want by using these variables:
Variable Description
%U The default user name. It is required.
%D The default domain name. It is optional.
%H The default home directory. It is optional. If used, it must be set
as an absolute path. This value, if used, is typically the first
variable in the sequence.
%L The hostname of the computer. It is optional.
Here is an example with all four variables set: %H/%L/%D/%U
Example with default value:
"HomeDirTemplate"="%H/local/%D/%U"
In the example above, the HomeDirTemplate is using the %H variable for the
HomeDirPrefix to set the user's home directory. In the example, the
HomeDirPrefix is not preceded by a slash because the slash is included in
the default HomeDirPrefix to ensure that the path is absolute. By default,
the %H variable automatically changes to be compatible with the operating
system to generate a home directory path. On Solaris, for example, the %H
variable maps to /export/home. On Mac OS X it maps to /Users; on
Linux, it maps to /home.
PBIS Open Installation and Administration Guide
BeyondTrust® May 8, 2012 227
Optionally, you can set the HomeDirPrefix by changing the prefix to the
path that you want. However, the HomeDirPrefix must be an absolute
path&#8212;so you must precede it with a slash. Example with default value:
"HomeDirPrefix"="/home"
You must use the default user name variable (%U). You may specify the
default domain name by using the domain name variable (%D), but it is not
required.
All the users who log on the computer by using their Active Directory
domain credentials will have the shell and home directory that you set under
the Providers\ActiveDirectory key. All the users who log on the
computer by using their local PBIS provider credentials will have the shell
and home directory that you set under the Providers\Local key.
Important: On Solaris, you cannot create a local home directory in /home,
because /home is used by autofs, Sun's automatic mounting service. The
standard on Solaris is to create local home directories in /export/home.
On Mac OS X, to mount a remote home directory, you must first create the
directory on the remote server as well as the folders for music, movies, and
so forth. See Use the createhomedir Command to Create Home Directories
and other information on Apple's website.
Turn Off Home Directories
By default, a user's home directory is created upon logon. To turn off the
creation of home directories, change value of the following entry to 0, for
false:
CreateHomeDir
Example with default setting of 1, which creates a home directory:
"CreateHomeDir"=dword:00000001
See Also
Fix the Shell and Home Directory Paths

---

### Post by vocoder42 on 2014-05-05
Thanks, however I am not sure this helps me.  I do have the LoginTemplate set and it works when I log into the machine locally.  The only issue is if I try to remotely SSH into this machine using my domain account - it tells me it can't set the shell called Template, which prevents me from logging in.  Instead of trying to set the shell to Template, it obviously should be trying to set the shell to whatever is defined in LoginShellTemplate (/bin/bash) but it looks like instead of trying to set the shell to /bin/bash, its trying to set it to Template, which of course is a non-existent shell.  I even tried adding "Template" to /etc/shells, but that didn't work

---

### Post by jamesisin on 2014-05-05
Have you tried adding the shell specifically to your user's bashrc file?

---

### Post by vocoder42 on 2014-05-06
well I'm a complete idiot.  Apparently when typing the command './config LoginShellTemplate /bin/bash' I instead typed './config LoginShell Template /bin/bash' which set the shell to Template, which of course doesn't exist.  Found this out when I went back and typed ./config --show LoginShellTemplate and didn't see /bin/bash.  thanks for all the help!

---

### Post by NetVicious on 2014-05-29
I have the same problem..

I'm looking to fix it but I didn't. I downgraded the samba + winbind packages to precise, deleted tdb databases and it doesn't works (i did lot of tries changing things on smb.conf so I should broke something it was ok for samba 3.6 of precise).

Tip others with the same problem:
- Change the log level of samba in smb.conf with "log level = 3"
- Check samba logs with tail -f /var/log/samba/*

I tried too using sssd but it didn't fixed it.

On Samba v4 the getent passwd showed AD users, but getent group didn't show any AD information.
Not in v3.6 samba both works but samba shares are not woking yet.

---

### Post by edubidu on 2014-06-26
Hi,
I have a similar problem. I can connect into AD but gdm bugs.
My treat is here, but nobody replys...
[http://ubuntuforums.org/showthread.php?t=2230602&p=13054355#post13054355](http://ubuntuforums.org/showthread.php?t=2230602&p=13054355#post13054355)

---

### Post by Romu on 2014-06-26
Hi,
Found this thread from my friend Google, ...not my friend actually!

I run a setup with Ubuntu 14.04 + PBIS. My goal is to setup a nas for my colleagues, all on Windows. I've an issue to install the samba interop components on 14.04. I run:

> sudo /opt/pbis/bin/samba-interop-install --install

And the result is:

> Found smbd version 4.1.6-Ubuntu
Unsupported smbd version 4.1.6-Ubuntu
Error: ERROR_PRODUCT_VERSION


Is there any fix or workaround somewhere? Thanks.

---

### Post by edubidu on 2014-07-01
> **edubidu said:**
> Hi,
I have a similar problem. I can connect into AD but gdm bugs.
My treat is here, but nobody replys...
[http://ubuntuforums.org/showthread.php?t=2230602&p=13054355#post13054355](http://ubuntuforums.org/showthread.php?t=2230602&p=13054355#post13054355)

SOLVED: [http://ubuntuforums.org/showthread.php?t=2230602](http://ubuntuforums.org/showthread.php?t=2230602)

---

