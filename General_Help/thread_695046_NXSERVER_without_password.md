---
title: "NXSERVER without password"
date: 2008-02-12
forum: General Help
---

### Post by Spitphire on 2008-02-12
Hello,

I have an ssh server that runs off of Public/Private keys.  I dont allow access with login/password.

I would like to use RSA keys, maybe even the same ones I use for ssh to login to nxserver.. the only way i  seem to be able to login to the nxserver is if i enable password authorization in sshd_config.

Is there a way to setup nxserver for key pairs, so i can disable password authorization in my sshd_config?

---

### Post by busaGuy on 2008-04-16
I'm in the same situation.

According to nomachine ([http://www.nomachine.com/documents/admin-guide.php):](http://www.nomachine.com/documents/admin-guide.php):)

4. NX Server Authentication
NX is configured by default to allow access for any system user, as long as the user provides valid credentials for the SSH login. Please note that SSH authentication without password is not supported. NX offers an alternative authentication method, allowing the administrator to specify which user can access the system through NX. This works by implementing a separation between the system password and the NX password, so that, for example, it is possible to forbid remote access to the system by any other means except NX and use the NX tools to implement effective accounting of the system resources used by the user.
The NX administrator can control access to the NX system by configuring the server to use the authentication method better suited:

System authentication relying on SSHD + PAM authentication
NX authentication relying on NX Password DB
A further level of control, relying on the NX User DB, can be achieved by enabling only a restricted group of users to connect to the NX server. This configuration can be applied either combined with the system or NX authentication.

---

