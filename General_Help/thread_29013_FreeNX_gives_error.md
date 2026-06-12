---
title: "FreeNX gives error"
date: 2005-04-22
forum: General Help
---

### Post by maku on 2005-04-22
Hi,
i want to install the FreeNX Server on my machine, i tested it twice, one time with the debs from katonix.org/files/debian and one time with the static builds from nomachines web page. I can not log in with my other machine and when I want to start nxagent the following message appear:

```
./nxagent: relocation error: /usr/NX/lib/libXcompext.so.1: undefined symbol: _NXEnableCleanGet
```

Is this error popular? I didn't found anything with google and the forum search about this problem. Btw, the ld.so.conf looks correct:

```
root@ubuntu:/usr/NX/bin # cat /etc/ld.so.conf
/usr/X11R6/lib
/usr/NX/lib
```

And I tested several libXcompext.so's from several nxserver build and no one gives another result than that one I wrote.

**Edit:** Ok, i solved the problem myself. At this moment, i am writing over my freenx connection  :) . It works with the Debs from Katonix.org/files/debian/freenx and /nx.

Bye,
  maku

---

### Post by jshein on 2005-04-22
Here is what I did to accomplish this

I found this a while back, but I do not have the link to the original document.

Add the following to "/etc/apt/sources.list":

deb http://kanotix.com/files/debian/ ./

Install freenx

# apt-get install freenx

1. Generating the DSA private-public key pair.

You must use the "ssh-keygen" command line tool to create a private-public key pair. For example, by issuing the following command on the client machine:

# ssh-keygen -t dsa
Generating public/private dsa key pair.
Enter file in which to save the key (/Users/falfaro/.ssh/id_dsa): <ENTER>
Enter passphrase (empty for no passphrase): <ENTER>
Enter same passphrase again: <ENTER>
Your identification has been saved in /Users/falfaro/.ssh/id_dsa.
Your public key has been saved in p.pub.
The key fingerprint is:
76:f1:09:07:f3:ef:4d:0a:a9:b7:ac:48:49:93:67:fe falfaro@mac.local

The private key should NOT be protected by a passphrase, as it will be directly used by the NX client software before any authentication is performed.

2. Installing the private key into the NX client software

The next step is replacing the NX client software built-in private key with the one we have just created. NoMachine's NX client software stores the DSA private key in "/usr/NX/share/client.id_dsa.key":

# ls -l /usr/NX/share/client.id_dsa.key
-rw-r--r-- 1 root wheel 668 27 Dec 13:59 /usr/NX/share/client.id_dsa.key

Thus, we should execute the following command:

# mv /usr/NX/share/client.id_dsa.key /usr/NX/share/client.id_dsa.key.OLD
# mv /Users/falfaro/.ssh/id_sa /usr/NX/share/client.id_dsa.key
# chown root:wheel /usr/NX/share/client.id_dsa.key
# chmod 644 /usr/NX/share/client.id_dsa.key

3. Installing the public key into the NX server software

The last step is installing the public key, which corresponds to the "nx" user, into remote server. The public key will be installed as an "authorized_keys2" file inside the home directory for the "nx" user. The OpenSSH service will use this file to store the "nx" user public key the NX client software uses to authenticate against the NX server.

Depending on the distribution and FreeNX implementation, the home directory for the "nx" user will be located in different places. In Fedora Core, this is usually "/var/lib/nxserver/nxhome". In Debian, this is usually "/home/.nx".

The last step is distributing the "id_dsa.pub" file to the remote NX server machine and authorize it:

# scp /Users/falfaro/.ssh/id_dsa.pub root@NXSERVER:
# rm /Users/falfaro/.ssh/id_dsa.pub
# ssh root@NXSERVER
# mv /root/id_dsa.pub /home/.nx/.ssh/authorized_keys2
# chown nx:root /home/.nx/.ssh/authorized_keys2
# chmod 600 /home/.nx/.ssh/authorized_keys2

4. Testing public key authentication

Before using the NX client software to connect to the remote NX server, it's recommended to check whether we can connect remotely to the NX server using an SSH client using public key authentication for the "nx" user:

# ssh -i /usr/NX/share/client.id_dsa.key nx@NXSERVER
Linux NXSERVER 2.6.10 #1 Sat Dec 25 05:20:24 CET 2004 i686 GNU/Linux
...
HELLO NXSERVER - Version 1.4.0-02 OS_(GPL)
NX> 105 quit
quit
Quit
NX> 999 Bye
Connection to ubuntu closed.

If this works, we can be pretty sure the NX client will allow us to establish a remote session against the NX server.

5. Configuring FreeNX server to support resuming of suspended sessions

In file "/usr/bin/nxserver":

Replace the line that reads:

ENABLE_AUTORECONNECT="0"

with

ENABLE_AUTORECONNECT="1"

Replace the line that reads:

session_list_user_suspended "$USER" 'Suspended' "$(getparam geometry)" "$(getparam type)" | log_tee

with

session_list_user_suspended "$USER" 'Suspended$|^status=Running$' "$(getparam geometry)" "$(getparam type)" | log_tee

This is very important as sometimes, when the NX client is disconnected from the NX server, the session is not marked as suspended.

---

### Post by Golovko on 2005-06-07
[QUOTE=jshein]Here is what I did to accomplish this

I found this a while back, but I do not have the link to the original document.

Add the following to "/etc/apt/sources.list":

deb [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./

Install freenx

# apt-get install freenx

1. Generating the DSA private-public key pair.

You must use the "ssh-keygen" command line tool to create a private-public key pair. For example, by issuing the following command on the client machine:

# ssh-keygen -t dsa
Generating public/private dsa key pair.
Enter file in which to save the key (/Users/falfaro/.ssh/id_dsa): <ENTER>
Enter passphrase (empty for no passphrase): <ENTER>
Enter same passphrase again: <ENTER>
Your identification has been saved in /Users/falfaro/.ssh/id_dsa.
Your public key has been saved in p.pub.
The key fingerprint is:
76:f1:09:07:f3:ef:4d:0a:a9:b7:ac:48:49:93:67:fe [email]falfaro@mac.loca[/email]l

The private key should NOT be protected by a passphrase, as it will be directly used by the NX client software before any authentication is performed.

2. Installing the private key into the NX client software

The next step is replacing the NX client software built-in private key with the one we have just created. NoMachine's NX client software stores the DSA private key in "/usr/NX/share/client.id_dsa.key":

# ls -l /usr/NX/share/client.id_dsa.key
-rw-r--r-- 1 root wheel 668 27 Dec 13:59 /usr/NX/share/client.id_dsa.key

Thus, we should execute the following command:

# mv /usr/NX/share/client.id_dsa.key /usr/NX/share/client.id_dsa.key.OLD
# mv /Users/falfaro/.ssh/id_sa /usr/NX/share/client.id_dsa.key
# chown root:wheel /usr/NX/share/client.id_dsa.key
# chmod 644 /usr/NX/share/client.id_dsa.key

3. Installing the public key into the NX server software

The last step is installing the public key, which corresponds to the "nx" user, into remote server. The public key will be installed as an "authorized_keys2" file inside the home directory for the "nx" user. The OpenSSH service will use this file to store the "nx" user public key the NX client software uses to authenticate against the NX server.

Depending on the distribution and FreeNX implementation, the home directory for the "nx" user will be located in different places. In Fedora Core, this is usually "/var/lib/nxserver/nxhome". In Debian, this is usually "/home/.nx".

The last step is distributing the "id_dsa.pub" file to the remote NX server machine and authorize it:

# scp /Users/falfaro/.ssh/id_dsa.pub root@NXSERVER:
# rm /Users/falfaro/.ssh/id_dsa.pub
# ssh root@NXSERVER
# mv /root/id_dsa.pub /home/.nx/.ssh/authorized_keys2
# chown nx:root /home/.nx/.ssh/authorized_keys2
# chmod 600 /home/.nx/.ssh/authorized_keys2

4. Testing public key authentication

Before using the NX client software to connect to the remote NX server, it's recommended to check whether we can connect remotely to the NX server using an SSH client using public key authentication for the "nx" user:

# ssh -i /usr/NX/share/client.id_dsa.key nx@NXSERVER
Linux NXSERVER 2.6.10 #1 Sat Dec 25 05:20:24 CET 2004 i686 GNU/Linux
...
HELLO NXSERVER - Version 1.4.0-02 OS_(GPL)
NX> 105 quit
quit
Quit
NX> 999 Bye
Connection to ubuntu closed.

If this works, we can be pretty sure the NX client will allow us to establish a remote session against the NX server.

5. Configuring FreeNX server to support resuming of suspended sessions

In file "/usr/bin/nxserver":

Replace the line that reads:

ENABLE_AUTORECONNECT="0"

with

ENABLE_AUTORECONNECT="1"

Replace the line that reads:

session_list_user_suspended "$USER" 'Suspended' "$(getparam geometry)" "$(getparam type)" | log_tee

with

session_list_user_suspended "$USER" 'Suspended$|^status=Running$' "$(getparam geometry)" "$(getparam type)" | log_tee

This is very important as sometimes, when the NX client is disconnected from the NX server, the session is not marked as suspended.[/QUOTE]
 Does part 5 above apply to the backports packages? I grepped nxserver for ENABLE_AUTORECONNECT="0" on a line by itself and no luck. I would love to have suspend/resume working.

Gol

---

