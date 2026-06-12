---
title: "SFTP Access"
date: 2012-10-26
forum: General Help
---

### Post by GeneralBroach on 2012-10-26
I have setup and have currently working Ubuntu 12.0.4 Server with only OpenSSH running.  This servers sole function is to provide SFTP access for our Customers.  While they are able to login with Filezilla/SCP, delete, upload, and download files my local users are unable to access the same files unless they  use the Customers Username/password combination.  I have tried accessing the SFTP connection with the initial users the server sets up and I can see all files just fine, I am unable to perform any actions on those files.  The way I have it chrooted is as follows

[I]chown root:root /sftp
chown root:root /sftp/<username>
chown <username>:<sftpgroup> /sftp/<username>/files[/I]

I want to establish a user that can access **all **files in each users chrooted directories and perform maintenance as needed, **BUT **I do not want that user to have full Admin rights to the system, only from /sftp and down.

I followed this guide for initial setup of my chrooted SFTP.
[http://www.thegeekstuff.com/2012/03/chroot-sftp-setup/]("http://www.thegeekstuff.com/2012/03/chroot-sftp-setup/")

Any help or further direction is greatly appreciated.

---

### Post by LewisTM on 2012-10-26
Hi and welcome to the Forums,

What you seek can be accomplished with Access Control Lists (ACL).

Create a new user that will be your sftp admin. We'll call him sftpadmin.

Grant this user read, write and execute (for dirs) permissions to all files and directories in /sftp
```
sudo setfacl -R -m sftpadmin:rwX /sftp
```
Set any newly created file to have those permissions by default
```
sudo setfacl -R -d -m sftpadmin:rwX /sftp
```
That's it! Good luck!

P.S. Note that files copied or moved from elsewhere on the server to the sftp tree (not uploaded/created on the spot) will not inherit those ACL. You may have to refresh the file tree from time to time.

---

### Post by GeneralBroach on 2012-11-01
> **LewisTM said:**
> Hi and welcome to the Forums,

What you seek can be accomplished with Access Control Lists (ACL).

Create a new user that will be your sftp admin. We'll call him sftpadmin.

Grant this user read, write and execute (for dirs) permissions to all files and directories in /sftp
```
sudo setfacl -R -m sftpadmin:rwX /sftp
```
Set any newly created file to have those permissions by default
```
sudo setfacl -R -d -m sftpadmin:rwX /sftp
```
That's it! Good luck!

P.S. Note that files copied or moved from elsewhere on the server to the sftp tree (not uploaded/created on the spot) will not inherit those ACL. You may have to refresh the file tree from time to time.

Well I tried as you suggested and I was able to create a user that could access any of the chrooted jail directories I have the users tied to.  However, once I take action like delete or add a new file to their directories they can no longer SFTP in.  Their connection is no longer allowed even though my global user can still interact freely.  Any thoughts?

---

### Post by LewisTM on 2012-11-01
It's possible that changing certain ACLs did not please the OpenSSH server. It now finds some permissions too "permissive" and denies access. This is true for standard Linux permissions, I didn't think it would apply to ACLs.

What you need to do is reset the permissions to OpenSSH standards
```
$ chmod 700 ~/.ssh
$ chmod 600 ~/.ssh/id_?sa* ~/.ssh/authorized_keys  ~/.ssh/known_hosts
```
Then remove the ACLs from those files and directories
```
setfacl --remove-all -R ~/.ssh
```
See if that helps.

---

### Post by GeneralBroach on 2012-11-01
> **LewisTM said:**
> It's possible that changing certain ACLs did not please the OpenSSH server. It now finds some permissions too "permissive" and denies access. This is true for standard Linux permissions, I didn't think it would apply to ACLs.

What you need to do is reset the permissions to OpenSSH standards
```
$ chmod 700 ~/.ssh
$ chmod 600 ~/.ssh/id_?sa* ~/.ssh/authorized_keys  ~/.ssh/known_hosts
```
Then remove the ACLs from those files and directories
```
setfacl --remove-all -R ~/.ssh
```
See if that helps.

Both commands worked except for the following.  no id_?sa* or authorized_keys.  The chmod 700 ~/.ssh took fine as well as the known_hosts and setfacl command.  But still no luck accessing with the other users.  I did these commands using sudo under the default user account made by Ubuntu at setup for its files.  Do I need to run those commands against the users created for SFTP @ their home directory chroot jails?

> 
Response:	fzSftp started
Command:	open "********@files.generalbroach.com" 22
Command:	Pass: **********
Error:	Network error: Software caused connection abort
Error:	Could not connect to server
Status:	Waiting to retry...
Status:	Connecting to files.generalbroach.com...
Response:	fzSftp started
Command:	open "********@files.generalbroach.com" 22
Command:	Pass: **********
Error:	Network error: Software caused connection abort
Error:	Could not connect to server


---

### Post by LewisTM on 2012-11-01
You need to run these commands as superuser or as the owner of the files, for every user. If you haven't setup the ssh server to work with keys then it's normal not to find any.
IMO removing the ACLs in each user's ~/.ssh directory should do the trick. Since you don't use keys you could even delete the directories, they should be re-created on login. Make a backup just to be safe.

---

### Post by LewisTM on 2012-11-01
There is something I'm not too clear about.
Are users chrooted into their home directories (containing .ssh) or are they in some other directory (/sftp)?
Basically I need to know if you did modify the ACL in .ssh to begin with. If not, something else is amiss...

---

### Post by GeneralBroach on 2012-11-01
I would direct you to this link which I followed in setting this chroot jail system up.  

[http://www.thegeekstuff.com/2012/03/chroot-sftp-setup/](http://www.thegeekstuff.com/2012/03/chroot-sftp-setup/)

But I believe the answer is yes.. these are redirected home directories off of an already chown root:root established directory called /sftp from which all SFTP users homes are chown root:root enslaved.  I believe that link explains my setup better though.

---

### Post by Lars Noodén on 2012-11-01
An excerpt from sshd_config (sanitized or otherwise) would clear things up even more.

---

### Post by GeneralBroach on 2012-11-01
> **Lars Noodén said:**
> An excerpt from sshd_config (sanitized or otherwise) would clear things up even more.


```

# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding no
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem 	sftp	internal-sftp

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

Match Group sftpusers
	ChrootDirectory /sftp/%u
	ForceCommand internal-sftp

```

---

### Post by Lars Noodén on 2012-11-01
> **GeneralBroach said:**
> 
I want to establish a user that can access **all **files in each users chrooted directories and perform maintenance as needed, **BUT **I do not want that user to have full Admin rights to the system, only from /sftp and down.


Ok but whatever the solution, to meet the chroot requirements of the ssh server, /sftp/%u has to be owned by root and not writable by anyone else.  The subdirectories are free from that restriction.

---

### Post by LewisTM on 2012-11-01
> **Lars Noodén said:**
> Ok but whatever the solution, to meet the chroot requirements of the ssh server, /sftp/%u has to be owned by root and not writable by anyone else.  The subdirectories are free from that restriction.
Indeed, my bad. That means GeneralBroach should execute 
```
sudo setfacl --remove-all /sftp /sftp/<user1> /sftp/<user2> etc...
```
Funny though that inappropriate permissions for select files or directories only prevent key-based authentication on my system, not passwords. But it's not a chroot jail setup.

---

### Post by Lars Noodén on 2012-11-01
> **LewisTM said:**
> But it's not a chroot jail setup.

That's the only case where root ownership is required.  Without chroot, the directories can be set to anything.  I haven't thought it through enough to understand why ownership of chroot jails need to be special.

---

### Post by GeneralBroach on 2012-11-01
**Thank you** gentlemen,

That does appear to be running as intended now 

:popcorn: on the house!!

---

