---
title: "Login failure, kick me  back to greeter"
date: 2017-05-18
forum: General Help
---

### Post by phu004 on 2017-05-18
Hi guys,  

When I try to loggin to my ubuntu 17.04 box from greeter, it kicks me out automatically after a minute. The screen showed a blank desktop image during the whole  time.  I am able to login succsesfully from tty though.

Here is the auth.log:

```

May 19 13:34:00 fos-OptiPlex-990 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "phu004"
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_krb5(lightdm:auth): user phu004 authenticated as phu004@UOA.AUCKLAND.AC.NZ
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm:auth): (null): pam_sm_authenticate
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm:auth): pam_kwallet: Fail into creating the hash
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm:auth): (null): pam_sm_authenticate
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm:auth): pam_kwallet5: Fail into creating the hash
May 19 13:34:03 fos-OptiPlex-990 systemd-logind[881]: Removed session c11.
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm:setcred): pam_kwallet: pam_sm_setcred
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm:setcred): pam_kwallet5: pam_sm_setcred
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_unix(lightdm:session): session opened for user phu004 by (uid=0)
May 19 13:34:03 fos-OptiPlex-990 systemd-logind[881]: New session c12 of user phu004.
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm:session): pam_kwallet: pam_sm_open_session
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm:session): pam_kwallet: open_session called without kwallet_key
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm:session): pam_kwallet5: pam_sm_open_session
May 19 13:34:03 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm:session): pam_kwallet5: open_session called without kwallet5_key
May 19 13:34:17 fos-OptiPlex-990 dbus[821]: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.608" (uid=41874 pid=9238 comm="/usr/lib/x86_64-linux-gnu/indicator-sound/indicato") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.126" (uid=0 pid=2636 comm="/usr/lib/x86_64-linux-gnu/unity-greeter-session-br")
May 19 13:34:37 fos-OptiPlex-990 lightdm: pam_unix(lightdm:session): session closed for user phu004
May 19 13:34:37 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm:session): pam_kwallet: pam_sm_close_session
May 19 13:34:37 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm:session): pam_kwallet5: pam_sm_close_session
May 19 13:34:37 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm:setcred): pam_kwallet: pam_sm_setcred
May 19 13:34:37 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm:setcred): pam_kwallet5: pam_sm_setcred
May 19 13:34:38 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm-greeter:setcred): (null): pam_sm_setcred
May 19 13:34:38 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm-greeter:setcred): (null): pam_sm_setcred
May 19 13:34:38 fos-OptiPlex-990 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
May 19 13:34:38 fos-OptiPlex-990 systemd-logind[881]: New session c13 of user lightdm.
May 19 13:34:38 fos-OptiPlex-990 systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
May 19 13:34:38 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm-greeter:session): (null): pam_sm_open_session
May 19 13:34:38 fos-OptiPlex-990 lightdm: pam_kwallet(lightdm-greeter:session): pam_kwallet: open_session called without kwallet_key
May 19 13:34:38 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm-greeter:session): (null): pam_sm_open_session
May 19 13:34:38 fos-OptiPlex-990 lightdm: pam_kwallet5(lightdm-greeter:session): pam_kwallet5: open_session called without kwallet5_key
May 19 13:34:42 fos-OptiPlex-990 dbus[821]: [system] Failed to activate service 'org.bluez': timed out
May 19 13:34:44 fos-OptiPlex-990 systemd-logind[881]: Removed session c12.

```

And here is what i have in /etc/pam.d/lightdm:
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
auth    optional        pam_kwallet.so
auth    optional        pam_kwallet5.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
#session required        pam_loginuid.so
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
session optional        pam_kwallet.so auto_start
session optional        pam_kwallet5.so auto_start
session required        pam_env.so readenv=1
session required        pam_env.so readenv=1 user_readenv=1 envfile=/etc/default/locale
@include common-password
```

Can anyone help me point out what might have gone wrong?

Thanks in advance!

Pan

---

### Post by Bashing-om on 2017-05-18
phu004; Hello;

Do "you" have the authority to access your desktop :
Post back:
```

ls -al .ICEauthority .Xauthority

```

And is there a graphics's driver loaded to start that GUI :
```

sudo lshw -C display

```

see where we go from here.

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by phu004 on 2017-05-18
```

phu004@fos-OptiPlex-990:~$ ls -al .ICEauthority .Xauthority
ls: cannot access '.ICEauthority': No such file or directory
-rw------- 1 phu004 all 61 May 19 14:10 .Xauthority

```

```

root@fos-OptiPlex-990:~# lshw -C display
  *-display                 
       description: VGA compatible controller
       product: Caicos XT [Radeon HD 7470/8470 / R5 235/310 OEM]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:28 memory:d0000000-dfffffff memory:e1420000-e143ffff ioport:3000(size=256) memory:c0000-dffff

```

---

### Post by Bashing-om on 2017-05-18
phu004; Hummm ...

I do not know what to make of the absence of the .ICEauthority file. Let's make it up and then see what results .
Logged in as the user ' phu004 ' run terminal commands:
```

touch .ICEauthority
chown phu004:phu004 .ICEauthority
chmod 600 .ICEauthority

```
reboot and see if the GUI is accessible to you now .

[INDENT][INDENT]could be this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by phu004 on 2017-05-18
Thanks for the reply! I created the file .ICEauthority as the user "phu004", but it didn't seem to make any difference.  One thing I should have mentioned is that phu004 is not a local account, it sits on AD and authenticated via LDAP.  The home directory for phu004 is also not local, it is mounted on afs share.   I can log on to the GUI interface using a locally created account just fine.

From the auth.log, I can see that the the session was closed at 13:34:37. Can you tell what caused the session to be closed?

---

