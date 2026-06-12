---
title: "NX - Got lost, need help"
date: 2007-02-24
forum: General Help
---

### Post by Ionix on 2007-02-24
I was following this thread for the initial NX setup from NoMachine.
Post #2 of the thread. [http://www.ubuntuforums.org/showthread.php?t=204976&highlight=freenx](http://www.ubuntuforums.org/showthread.php?t=204976&highlight=freenx)

```

root@KYNET02:/usr/NX/bin# sudo /usr/NX/bin/nxserver --useradd kaiyang
NX> 900 Setting password for user: kaiyang.
NX> 102 Password: 
NX> 102 Confirm password: 
NX> 110 Password for user: kaiyang added to the NX password DB.
NX> 900 Adding public key for user: kaiyang to the authorized keys file.
NX> 910 WARNING: The SSH key to be used for user authentication could
NX> 910 WARNING: not be added to the private authorized keys file of user.
NX> 910 WARNING: Please note that, with these settings, the user won't be
NX> 910 WARNING: able to successfully run any sessions.
NX> 910 WARNING: Run the following command to get some hints on the possible
NX> 910 WARNING: reasons of the problem:
NX> 910 WARNING:
NX> 910 WARNING: nxserver --usercheck kaiyang
NX> 910 WARNING:
NX> 999 Bye.
root@KYNET02:/usr/NX/bin# sudo /usr/NX/bin/nxserver --usercheck kaiyang
NX> 900 Verifying public key authentication for NX user: kaiyang.
NX> 900 Adding public key for user: kaiyang to the authorized keys file.
NX> 596 ERROR: NXNODE Ver. 2.1.0-15  (Error id e32C8E1)
NX> 596 ERROR: Sat Feb 24 22:22:28 2007 running as user: 'kaiyang' (uid: 1000) on ''
NX> 596 ERROR: in node ssh keys manager: add server ssh public keys to user
NX> 596 ERROR: Cannot create file: /home/kaiyang/.ssh/authorized_keys2: Permission denied.
NX> 900 ERROR: Failed to add public key.
NX> 999 Bye.


```

I had set ENABLE_USER_DB and ENABLE_PASSWD_DB to ON and now what I was trying to get is to have all users that want to log onto the server use a same authorisation key with their own user name and password.

but got lost.. and now I don't know what i should do.

---

