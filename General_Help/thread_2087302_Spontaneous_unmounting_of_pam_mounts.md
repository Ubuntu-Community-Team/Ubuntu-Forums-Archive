---
title: "Spontaneous unmounting of pam mounts"
date: 2012-11-23
forum: General Help
---

### Post by sionnach on 2012-11-23
We're using samba [Samba 3.4.7 and OpenLDAP auth backend] on Ubuntu 10.04.4 LTS 64 bit server for provisioning usershares and two additional generic/standard shares (share1 and share2). Developers are also using Ubuntu 10.04.4 LTS 64 bit server.

We wanted the usershare and two standard shares to mount on login for developers and opted for using pam_mount to do so. LDAP auth is already enabled for the developer machines. Following the standard guides we ended up using /etc/security/pam_mount.conf.xml configured as follows:
```

<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<pam_mount>
<debug enable="0" />
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<mntoptions deny="suid,dev" />
<mntoptions require="nosuid,nodev" />
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>
<logout wait="0" hup="0" term="0" kill="0" />
<mkmountpoint enable="1" remove="true" />

<volume options="user=%(DOMAIN_USER),workgroup=NAME_OF_WORKGROUP" fstype="cifs" server="servername" path="%(DOMAIN_USER)" mountpoint="/srv/samba/usershares/%(USER)/"></volume>
<volume options="user=%(DOMAIN_USER),workgroup=NAME_OF_WORKGROUP" fstype="cifs" server="servername" path="share1" mountpoint="/srv/samba/share1"></volume>
<volume options="user=%(DOMAIN_USER),workgroup=NAME_OF_WORKGROUP" fstype="cifs" server="servername" path="share2" mountpoint="/srv/samba/share2"></volume>

</pam_mount>
```Other edits were made to files in /etc/pam.d/ to add in "auth optional pam_mount.so".

So all three mounts worked perfectly on login. The three mounts showed up in /etc/mtab in exactly the same manner. As well 'df -h' was as expected. However after a short period of time (20 minutes - 2 hours, varying with no pattern) the two standard shares (share1 and share2) would spontaneously unmount. They were all set up the same as the usershare which remained intact and never unmounted itself. The only temporary fix we had was to log out and back in or just 'ssh localhost'. No errors were reported either in samba logs/dmesg locally or on the server. In fact, it was quite gracious unmount apart from the loss of work incurred by developers if they were editing a file (so keeping a handle on a file on the mounted drive didn't keep it open). 

After many edits to /etc/security/pam_mount.conf.xml nothing seemed to work. So then I tried moving the two standard mounts to ~/.user_pam_mount.conf.xml

with the config:
```
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
        See pam_mount.conf(5) for a description.
-->

<pam_mount>

<volume options="user=%(DOMAIN_USER),workgroup=NAME_OF_WORKGROUP" fstype="cifs" server="servername" path="share1" mountpoint="/srv/samba/share1"></volume>
<volume options="user=%(DOMAIN_USER),workgroup=NAME_OF_WORKGROUP" fstype="cifs" server="servername" path="share2" mountpoint="/srv/samba/share2"></volume>

</pam_mount>
```and changed /etc/security/pam_mount.conf.xml to:

```
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
        See pam_mount.conf(5) for a description.
-->

<pam_mount>
<debug enable="0" />
<luserconf name=".user_pam_mount.conf.xml" />
<mntoptions allow="*" />
<mntoptions require="" />
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>
<logout wait="0" hup="0" term="0" kill="0" />
<mkmountpoint enable="1" remove="true" />

<volume options="user=%(DOMAIN_USER),workgroup=NAME_OF_WORKGROUP" fstype="cifs" server="servername" path="%(DOMAIN_USER)" mountpoint="/srv/samba/usershares/%(USER)/"></volume>

</pam_mount>
```This enabled the user pam_mount configuration and moved the configuration for the two standard shares to it. Now they stay mounted after login and for as long as the user is logged in. No other system changes were made apart from the above, mainly moving the two volumes into the luserconf. This has worked for all developers.

I have no idea why this should be more robust, but I spent quite some time getting this to work and others might benefit from it. Alternatively, if someone can point out an error on my part or a better approach I'd be happy to fix it 'properly'.

Best regards,
Sionnach.

---

