---
title: "Active Directory Authentications"
date: 2008-04-15
forum: General Help
---

### Post by maunir on 2008-04-15
I have been testing Ubuntu on my laptop for the past couple of months and the only task that is missing is authenticating against Active Directory.  I read a lot of stuff on the net for this but wanted to avoid the situation to login in as a local user then log in with the AD credentials.  I want to avoid that situation as we need to deploy this in our env. and users are not going to like logging in twice.  I want the login process just as windows where user enters his/her login name and the AD password and that’s it.  I know there has to be stuff out there but I’m having a hard time finding it.  Does anyone have any idea how to do this or am I missing something?  Any help would be appreciated.

ps: I have also tested Likewise open and it’s still the same.  

Thanks
Maunir Shah

---

### Post by pointone on 2008-04-16
I went through whole song and dance a while ago. Let me see if I can still remember...

I ended up cobbling everything together from a number of sources, but [this post (1)]("http://blog.scottlowe.org/2007/01/15/linux-ad-integration-version-4/") and [this post (2)]("http://adminspotting.net/articles/windows/linux-and-active-directory.html") were very, very useful.

I also used [pam_mount]("http://pam-mount.sourceforge.net/") to handle mounting of existing shares on the network. If this doesn't apply to you, just forget it!

Also keep in mind that Samba + Winbind can accomplish the authentication part a lot more easily, but there's some issue with preserving file permissions. If you're not mounting shares, [this]("http://www.enterprisenetworkingplanet.com/netos/article.php/3502441") might be the better way to go.

#1: Install krb5-user and configure /etc/krb5.conf to point to your server. You can test Kerberos authentication with "kinit <username>". You'll probably also want to install and configure ntp (Kerberos requires minimal clock skew between client/server).

#2: Install libnss-ldap and configure /etc/libnss-ldap.conf to use a special "scout" account for searching the directory. (The second link I posted should be helpful for this.) You'll want to uncomment the "RFC 2307 (AD)" mappings in this file for Windows Server 2003; not sure about other versions.

#3: Edit /etc/nsswitch.conf and change passwd, group, and shadow to look in "files ldap". You can test the nsswitch changes with "getent passwd <username>".

#4: Install libpam-krb5, and libpam-mount, smbfs, if mounting shares. This is the PAM stack I used:

common-auth
```
auth      sufficient     pam_unix.so nullok_secure
auth      requisite      pam_krb5.so use_first_pass ignore_root
auth      optional       pam_mount.so use_first_pass
```

common-account
```
account   sufficient     pam_unix.so
account   requisite      pam_krb5.so ignore_root
```

common-session
```
session   requisite      pam_unix.so
session   sufficient     pam_localuser.so
session   optional       pam_mount.so
```

common-password
```
password  sufficient     pam_unix.so nullok obscure min=4 max=8 md5
password  requisite      pam_krb5.so ignore_root
```

Of course, /etc/security/pam_mount.conf.xml needs to be configured for this to work.

That's essentially all there was to it (condensed, of course). You'll need to setup your users in Active Directory with the appropriate UNIX attributes, too. 

I know I've been very vague, but it's been about six months since I touched any of this. Hopefully I've been somewhat helpful. Let me know if I can clarify anything.

---

### Post by maunir on 2008-04-18
I'm missing pam_console.so file.  Do you know where or what package contains that file.

---

### Post by bolivartech on 2008-04-28
What line did you use in the pam_mount.conf.xml file? I have an 8.04 install with Likewise-Open working but cannot seem to get pam_mount working. I'll check my stack against yours, but I think everything is there. I am authenticating against 2003AD, and user directories are shared as \\server\username. In a normal .conf file it's volume * server &$ \home\DOMAIN\&\MountPoint uid=&,- - . That has worked in the past for me, but only on a Red Hat system.

---

### Post by nullimage on 2008-05-08
> **bolivartech said:**
> I have an 8.04 install with Likewise-Open working but cannot seem to get pam_mount working. 
I'm having the same problem with Likewise-open and pam_mount. 

I've gotten to the point where i'm asked twice for the password, once for the normal login and after for pam_mount (which shouldn't happen since the pam_mount module is placed before the likewise module in the common-auth and common-session files). But after typing the password (twice) it logs in but doesn't mount the share.

Any suggestions?!

I've managed to get pam_mount working in the past with winbind but the configuration file format, for pam_mount, has changed and Likewise behaves somewhat differently from winbind.

---

### Post by bciworker on 2008-05-13
> **nullimage said:**
> I'm having the same problem with Likewise-open and pam_mount. 

I've gotten to the point where i'm asked twice for the password, once for the normal login and after for pam_mount (which shouldn't happen since the pam_mount module is placed before the likewise module in the common-auth and common-session files). But after typing the password (twice) it logs in but doesn't mount the share.

I also get asked for my p/w twice. I wonder why this is, since the pam_mount.so called in the "session section" is followed by a try_first_pass and in the "auth section" likewise should have put the password onto the stack. Maybe it's because it's not in the session stack (does it really matter which component got the password in the first place?).

Anyway, I could successfully mount a share by hardcoding the mountpoint into the volume tag in pam_mount.conf.xml. :
<volume options="uid=%(USER),gid=root,dir_mode=0700,nosuid,nodev" user="*" mountpoint="/home/DOMAIN/USER/foo" path="DFS" server="cutler" fstype="cifs" />
Since %(USER) returns a string Domain\user, using it for the mountpoint results in a mountpoint of type /home/DOMAIN/Domain\user/foo (notice the backslash)
Any ideas how to determine the username without the Domain\ string before it? Because then I could the volumes in the home folder created by likewise-open.

---

### Post by nullimage on 2008-05-13
> **bciworker said:**
> 
Any ideas how to determine the username without the Domain\ string before it? Because then I could the volumes in the home folder created by likewise-open.
Try putting this in the likewise configuration file (can't remember the name right now):
```
winbind use default domain = yes
```
I used that parameter to avoid always typing DOMAIN\username when logging in, now I just type the username directly.

---

