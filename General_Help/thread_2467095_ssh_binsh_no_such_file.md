---
title: "ssh /bin/sh no such file"
date: 2021-09-15
forum: General Help
---

### Post by Cadryc on 2021-09-15
I have a server with Ubuntu 20.04 and sftp set up with a user specifically created for the sftp, but I do not remember the exact comand i used. It works fine, but now I got a second server, Raspberry Pi on a remote location, and to backup some stuff I would like to rsync from the raspberry to the ubuntu server. The raspberry will be always on while the ubuntu server may be powered off sometimes (a later project may be to get my edgerouter to wol the ubuntu server on incomming connections)

I began with trying to get autoligin to work. First I could not ssh into the ubuntu server, but I manually copied a pulic key to .ssh and commented out Forcecommand internal-sftp in sshd_config and now it seems it begins to log in on ssh but immediately runs into */bin/sh: No such file or directory*

I guess some stuff is missing for my sftp user in order to use ssh. Please help so I don't have to begin from scratch...

---

### Post by TheFu on 2021-09-15
On the remote system, the userid password entry points to a login shell that either doesn't exist or isn't approved as a login shell.  The admin of that other system should change it - /etc/shells has the list of valid login shell programs on any system. That file isn't always the same.

/bin/sh: No such file or directory
That error tells us something clear.  In the login session via ssh, the /bin/sh program doesn't exist.  If I were allowing someone else access to my raspberry pi, I wouldn't allow an ssh connection when all they requested was sftp.  Further, I'd setup a chroot environment, so no other programs were available to the userid.  ssh has this chroot capability built-in these days, so it isn't hard to modify the /etc/ssh/sshd_config file to configure for that access.

It is also possible that the other admin setup the userid to be sftp-only user.  I'd have to look up exactly how to accomplish that. There are how-to guides that google will find.  [https://www.digitalocean.com/community/questions/trying-to-setup-a-sftp-user-with-limited-access](https://www.digitalocean.com/community/questions/trying-to-setup-a-sftp-user-with-limited-access) seems reasonable.  Step 8 is the stuff I'd check first.

---

### Post by Cadryc on 2021-09-16
My sshd_config looks like that, with chroot. Both the ubuntu server and the pi are mine, but since they will be communicating over open web, so to speak, I want to keep it safe. Hence the sftp (not on port 22).

But since rsync can't sync to an sftp I ran into this problem. But now I found a script using lftp, but can't get that to work either

```
#!/bin/bash
HOST='mysftp.duckdns.org:22222'
USER='sftpuser'
PASS='sftpuserpass'
TARGETFOLDER='/Backup/Stuff/'
SOURCEFOLDER='/mnt/externaldrive/Backup/Stuff/'

lftp -f "
open $HOST
user $USER $PASS
lcd $SOURCEFOLDER
mirror --reverse --delete --verbose $SOURCEFOLDER $TARGETFOLDER
bye
"
```

First I had problem with the password, it seemed to interpret a portion of the password as a command, I guess there was a character the script tripped on. So I changed the password on my server sftp to something simpler (what special character should be avoided?), but when I run the script still a password prompt appears, and if I type in the password it still wont work.

Maybe this thread should be moved to the server section?

---

### Post by TheFu on 2021-09-16
ssh/rsync won't work with the chroot, unless you setup much more.  I'd just disable the chroot for now, install fail2ban and STOP USING PASSWORDS FOR SSH AUTHENTICATION!  Set up ssh-keys.  You can block 99.9999% of the internet from access to port 22222 in the sshd_config as well. This is well traveled stuff. [https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](https://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) tries to explain. 

Using passwords is a total security failure. Always use keys or certs, after then 1st connection ... to send the key over.  I only allow ssh/sftp/scp/rsync/x2go with passwords on the same LAN. All other connections must use ssh-key based authentication, period.

I've never needed/heard of lftp or the 'mirror' command. Sorry.

---

### Post by Cadryc on 2021-09-16
So I'm into setting up public keys. The commands ran fine. But... connecting to the sftp from nautilus, using the mysftp.duckdns.org, on my daily computer works perfectly now, gets logged to the directory specified with chroot. But when doing the same from my server, which actually just is running the ordinary ubuntu 20.04, same as my daily computer, I still get a password prompt. I type in the username for the sftp user, leaves the password blank, and get logged in to the system root... and I can view files as if I was at the pi. So very different behavior even thou I do the exact same thing from two computers.

---

### Post by TheFu on 2021-09-16
Each ssh client needs to create their own keys and send those over using ssh-copy-id (or manually, if you are careful to not screw up the files or permissions).
I don't really use GUIs. Can't help with nautilus or caja or thunar or whatever else might be used. Sorry.  Those things just get in the way.  Realistically, I barely use sftp - prefer rsync and scp which are much easier to use from a shell.

But I do know that when ssh-keys are working, all 50+ ssh-based clients see those and "just work".

My blog has an ssh-troubleshooting article with steps, but it is more about when someone didn't change the defaults on the client or server.  When things are remove and you cannot easily visit to fix mistakes, resetting all to "factory standard" for sshd could turn our badly.  I suppose opening 3 ssh connections first (precaution) and just renaming /etc/ssh/ , then doing an **sudo apt install --reinstall ssh** should work. I've not tried it.  Don't leave any time between the deletion of the directory.  Heck, maybe try doing the --reinstall first to see that the sshd_config and ssh_config files are reset to the install versions would be best. Only if that doesn't work, then rename  /etc/ssh/  and try the --reinstall.

---

### Post by Cadryc on 2021-09-16
I made keys from both clients, exactly the same commands. Maybe I'Il try a reinstall of ssh on the rasberry pi. Thanks for your pointers, at least I getting somewhere now (atleast until the next road bump..)

I didn't know about scp until recently when I looked into sync over sftp. Maybe I will try that, if I get stuck. I try my best at the terminal but gui is still my habitat.

---

### Post by TheFu on 2021-09-16
rsync defaults to using ssh tunnels and has for 15+ yrs. That is the best answer here.
scp is going to be deprecated - I don't know what that means.

scp ~= rcp
sftp ~= FTP

Those commands were created as drop-in replacements for the old, non-secure, no encryption, tools we used in the early 1990s. the commands are all the same.  The great thing about scp and rsync is that your prompt is probably exactly the part of the command you need to copy/paste for either the source or target for either of those commands.

And don't forget that sshfs can be handy too. It is slow, but there is place it fills when the program is installed and configured on a different machine than where the data is located.

---

