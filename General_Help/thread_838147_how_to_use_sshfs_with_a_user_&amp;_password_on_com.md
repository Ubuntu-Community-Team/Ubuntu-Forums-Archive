---
title: "how to use sshfs with a user &amp; password on command line?  how to add sshfs to fstab?"
date: 2008-06-23
forum: General Help
---

### Post by kraymore on 2008-06-23
I am following this how-to for using a secure encrypted remote volume

[https://wiki.ubuntu.com/SecureEncryptedRemoteVolumeHowTo](https://wiki.ubuntu.com/SecureEncryptedRemoteVolumeHowTo)

it gives an example of 

sshfs [email]your-ssh-username@your-web-host.com[/email]:remote-directory ~/.remote-secure-volume

my remote ssh host requires a username and password so i'm not sure how to tailor this example to include that all at the command line

i would also like to be able to add this sshfs to /etc/fstab if possible so i dont have to mount it manually when using it.  how to do i do that ?

one final question about this secure encrypted remote volume.  in the url listed above, it has the following two command line lines for use:

sshfs [email]your-ssh-username@your-web-host.com[/email]:remote-directory ~/.remote-secure-volume
encfs ~/.remote-secure-volume $HOME/remote-encrypted-volume

after executing those two commands do i simply use nautilus (or terminal) to save files remotely encrypting on the fly to the ~/remote-encrypted-volume ?  the reason it confuses me is i am unsure why i had to create the hidden ~/.remote-secure-volume directory and if i would ever user that directory in practice or if i should just execute both and only use ~/remote-encrypted-volume for what i wish to do (backup files securely and remotely through ssh, preferably encrypted)

thank you

---

### Post by vanadium on 2008-06-23
> i'm not sure how to tailor this example to include that all at the command line
You can pass user and password on the command line as an option. The "simple" way to do this, is including

-o username=user,password=pass

A more secure, recommended way to do this is to use a credential file. This is a plain text file, stored in a secure directory only readable by yourself. It contains nothing more than

username=yourusername
password=youpass

chmod it to 600 so that it is only readable by yourself (and root).

Suppose the file is $HOME/.credentials
then you use the file on the command line like:
($HOME stands for your home directory and can be typed as such at the command line: it will be "expanded" automatically).

```

sshfs -o credentials=$HOME/.credentials your-ssh-username@your-web-host.com:remote-directory ~/.remote-secure-volume

```


In /etc/fstab, your line will look like

```

sshfs#user@server.domain.com:/<your default dir> <mount point> fuse credentials=<path to .credentials>.credentials 0 0 

```

(you cannot use the $HOME variable, but you need to spell out the full path yourself).

I am not sure about the "encrypt" part: probably you will need to issue this command manually before the transaction, or have it placed in a script.

---

### Post by ubundom on 2008-11-26
This post looked like precisely what I needed but unfortunately I get a FUSE error:

```
ubundom@localpc:~$ /usr/bin/sshfs -o credentials=$HOME/.creds ubundom@server01:/home/ubundom ~/data/server
ubundom@server01's password:
fuse: unknown option `credentials=/home/ubundom/.creds'
ubundom@localpc:~$

```

I wasn't expecting the password to be prompted, my .creds file contains:

username=ubundom
password=mypassword

Shall I try:

```
/usr/bin/sshfs -o credentials=$HOME/.creds ubundom@server01:/home/ubundom ~/data/server < .creds
```

conFUSEd: :confused:

---

### Post by narcisgarcia on 2010-10-07
A new guide to configure better the client and the server:
[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(with special care with owners and permissions questions)

---

