---
title: "Samba fails to connect to Windows 7 or 8.1 Pro systems"
date: 2015-12-14
forum: General Help
---

### Post by cjsmall on 2015-12-14
This is an Xubuntu 15.10 system (dymaxion) running Samba 4.1.17 with a LAN containing the following machines:

  * belvedere:    Sun Solaris 10 with Samba 3.6.5
  * ionic:           Windows-XP
  * usonian:       Windows 7
  * gable:          Windows 8.1 Pro in a QUEM/KVM 

SMB connections work between all machines in all directions with the exception that the Ubuntu system cannot connect to the Windows 7 and the Windows 8.1 systems as well as being unable to connect to itself.  Here are results running smbclient on dymaxion:

```
[Solaris/Samba connection OK]
30-> smbclient //belvedere/jeff
Enter jeff's password: 
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.5]
smb: \> exit

[Windows-XP connection OK]
31-> smbclient //ionic/Documents
Enter jeff's password:
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> exit

[Windows 7 **** FAILS]
32-> smbclient //usonian/Users
Enter jeff's password:
session setup failed: NT_STATUS_INVALID_PARAMETER

[Windows 8.1 ****FAILS]
33-> smbclient //gable/Users
Enter jeff's password:
session setup failed: NT_STATUS_INVALID_PARAMETER

[Self-connection **** FAILS]
34-> smbclient //dymaxion/jeff
Enter jeff's password:
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 4.1.17-Ubuntu]
tree connect failed: NT_STATUS_ACCESS_DENIED
```

When I attempt to attach to the failing Windows systems using the Nemo file manager, there is a timeout delay and then the following password prompt appears:

[ATTACH=CONFIG]266148[/ATTACH]

Entering a password and attempting to connect simply causes this dialog to keep reappearing.

The **NT_STATUS_INVALID_PARAMETER** error problem has been repeatedly reported and most solutions seem to relate to a password encryption mismatch where the **smb.conf** file had **encrypt passwords = no**.  That is not the case here.  Below I am attaching two files running smbclient with debug mode set to 10.  The first shows a successful connection to the Windows-XP system.  The second is an unsuccessful attempt to connect to the Windows 8.1 system.  These files display the relevant **smb.conf** parameters.  I have investigated both, as well as the log files and cannot see where the problem lies.  Also, the remote shares from the Windows machines can be manually mounted using **mount.cifs** without problem.

[ATTACH]266149[/ATTACH]      [ATTACH]266150[/ATTACH]

As noted at the start, all other system can connect to the Ubuntu shares and **testparm**  is clean.  Obviously there is a configuration problem with the  Ubuntu/Samba system.  Any suggestions where to look next would be  greatly appreciated.

---

### Post by Morbius1 on 2015-12-14
This wasn't a very elegant analysis but I can reproduce the exact same error message connecting to a Win10 machine:
> morbius@vxub1510:~$ smbclient //vwin10.local/Users -U smbuser
Enter smbuser's password: 
-----
cli_session_setup: NT1 session setup failed: NT_STATUS_INVALID_PARAMETER
session setup failed: NT_STATUS_INVALID_PARAMETER

I achieved that by replacing the default values for some of the client parameters which are these:
> client schannel = Auto
client signing = default
client use spnego = Yes
With the one's you are using:
> doing parameter [COLOR=#0000cd]client schannel = no[/COLOR]
doing parameter [COLOR=#0000cd]client signing = no[/COLOR]
doing parameter [COLOR=#0000cd]client use spnego = no[/COLOR]
You might want to check your smb.conf file and see if you are overriding the defaults.

---

### Post by cjsmall on 2015-12-14
**Solved**

Morbius1: That did it!  Quite a while ago I set up this Ubuntu box and configured samba.  At this point I do not know how these entries got changed from their defaults.  I had not set them in my smb.conf on the Solaris system, so I assume I must have picked up these altered setting from some article I read back then.  After setting them back to the defaults as you suggested, things started working immediately.

For others reading this, the solution was to properly accept the default in **smb.conf** by either not defining these parameters, or setting them to:

```
[B]client schannel   = auto
client signing    = auto
client use spnego = yes[/B]
```

A very big thanks for helping me to resolve this.

---

