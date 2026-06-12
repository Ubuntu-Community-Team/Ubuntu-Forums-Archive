---
title: "Connecting to server that has two factor Authentication?"
date: 2019-07-10
forum: General Help
---

### Post by derek-u on 2019-07-10
I would like to know if there is anyway or any plans for nautilus to support connecting to servers with complex auth procedures.  For example, I have a requirement for a private key with a passphrase, and an additional 2FA prompt/response in order to access a remote system, and would like to be able to connect to such a server  over sftp using Nautilus.  It doesn't seem to be possible at the moment.  And my secondary fallback plan of using some other sftp client, like Filezilla, didn't produce any clients that seem to be working well for this use case either.

I do have a work around that might be useful for some people.  It is possible to use sshfs (for example like these instructions: [https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh](https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh) ) to mount the remote file system from the command line (even with multiple/complex authentication requirements), and then use it from Nautilus. 

My workaround looks like the following.  

All of the following is done as root, as need to mount file systems with root privileges:

1. Install sshfs
```
$ apt-get install sshfs
```
2. I have the required public/private key in my /root/.ssh/ directory, named for example thehostkey and thehostkey.pub
```
$ ls -alh /root/.ssh
total 24K
drwx------ 2 root root 4.0K Jul 10 16:30 .
drwx------ 6 root root 4.0K Jul 10 16:29 ..
-rw------- 1 root root  444 Jul 10 16:30 thehostkey
-rw-r--r-- 1 root root   91 Jul 10 16:30 thehostkey.pub
-rw-r--r-- 1 root root  483 Jul 10 16:30 config
-rw-r--r-- 1 root root  888 Jul 10 16:31 known_hosts
```
The host I am trying to access is named for example thehost.com.  I need to access it on a nonstandard ssh port. To make things a little easier, I have the following in the /root/.ssh/config file, defining the port number, user name and key file to use for authentication for that host:

```
$ cat /root/.ssh/config

Host thehost.com
         User myusername
         Port 2022
         IdentityFile ~/.ssh/thehostkey
         IdentitiesOnly yes[EMAIL="configroot@heap:~/.ssh"]
[/EMAIL][EMAIL="configroot@heap:~/.ssh"]
[/EMAIL]
```

3. Mount the filesystem so regular users can access it on my filesystem over ssh.

```
$ mkdir /mnt/thehost  # ensure the directory mount point exists before you try and mount using sshfs

$ sshfs -o allow_other thehost.com:/home/myusername /mnt/thehost
```

You will then have to perform any authentication from the command line that you usually would.  My key is passphrase protected, so I first need to enter the passphrase if it is not already in my keychain.  Then the server requires 2FA, so I need to enter the generated code.  If authentication succeeds then your remote filesystem should now be mounted at /mnt/thehost, and it should be read/writeable by other users, so you should be able to navigate to it in a graphical file browser like Nautilus and access the files form there.

I would still like to do this in Nautilus as this is a bit heavyweight of a solution.  But I am using this workaround of using sshfs mounts for now for my complex authentication use cases on Linux/Ubuntu.

---

### Post by TheFu on 2019-07-11
There isn't just 1 type of 2FA.  There are many - TOTP, HOTP, U2F, FIDOv2, Oauth2 just to name a few, so a specific solution for the exact type of 2FA being used is needed.  My U2F devices support most of those, but I haven't enabled 2FA for my ssh to server needs.  

I don't use GUI tools very often, but even only using ssh-agent, some of my computing devices won't work with my 2FA USB keys. I'm stuck until my tablet, phones and all computers have a consistent, probably USB-c port that works with a 2FA device.  NFC didn't work correctly most of the time.  I'd never trust bluetooth for anything were security is needed.  I have used the 1-time pad solution when travelling.  Walking around with (100) 1-time entries for 2FA isn't exactly fun, but paper in a wallet doesn't get looked at when crossing borders, IME.

I would have thought that if you accessed the remote system with ssh first, then that would unlock all the keys, so nautilus would "just work" and no 2FA prompt would be needed.  But IDK.

---

### Post by derek-u on 2019-07-13
Well yes of course the key agent remembers the key passphrase, so that does not need to be entered again.  And I believe that they key agent information is available to nautilus as well.  However, the verification code for my TOTP/HOTP 2FA will always need to be entered whenever a new connection is made, whether from a command line or connecting from something like Nautilus.  It appears that Nautilus can handle a regular password prompt authentication if needed.  However the need to prompt for and enter a 2FA authentication code does not appear to be generally handled yet by Nautilus nor by other SFTP clients like Filezilla, as far as I can tell.

---

