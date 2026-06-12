---
title: "SSH - Sending files with scp"
date: 2007-02-02
forum: General Help
---

### Post by DuckFish on 2007-02-02
I only have access to a certain server through SSH.
Let's call my computer [color=green][font=courier new]me@local[/font][/color] and the remote one [color=red][font=courier new]me@remote-server.com[/font][/color].

To connect to [font=courier new][color=red]me@remote-server.com[/color][/font], I use:
[font=courier new][color=green]me@local[/color][color=blue]:~$ ssh[/color] [color=red]me@remote-server.com[/color][/font]

Then, my prompt changes to this:
[font=courier new][color=red]me@remote-server.com[/color][color=blue]:~$[/color][/font]

However, I want to send a local file, [font=courier new][color=blue]a.file[/color][/font], and none of these commands work:
[font=courier new][color=red]me@remote-server.com[/color][color=blue]:~$ scp a.file remote.file[/color]
[color=red]me@remote-server.com[/color][color=blue]:~$ scp local:a.file remote-server.com:remote.file[/color]
[color=red]me@remote-server.com[/color][color=blue]:~$ scp[/color] [color=green]me@local[/color][color=blue]:a.file[/color] [color=red]me@remote-server.com[/color][color=blue]:remote.file[/color][/font]

Thus, I must do (and enter my password) this each time I wish to send a file:
[font=courier new][color=green]me@local[/color][color=blue]:~$ scp a.file[/color] [color=red]me@remote-server.com[/color][color=blue]:remote.file[/color][/font]

Is there an easier way to send files? Say, while logged in to the remote server, maybe something like
[font=courier new][color=red]me@remote-server.com[/color][color=blue]:~$ sendfile localfile remotefile[/color][/font]
?
Thanks :)

---

### Post by WW on 2007-02-03
Edit: Nevermind, my original post would not help.

Re-edit: Actually, my original post might still be of use...  Do you have sshd running on local?  I think it is necessary to have sshd running on local in order to complete a transfer that is initiated at remote.  However, I think you will still be asked for your password.

To install sshd on local:
```
$ sudo apt-get install openssh-server
```

---

### Post by WW on 2007-02-03
I haven't tried it, but the description in Synaptic makes it sound like **zssh** might work for you.

---

### Post by kebes on 2007-02-03
There are lots of options.

You can use the commandline "**sftp**" to do what you want. You log in with sftp and then navigate to where you want to put a file and then use commands like "put" to upload a file. If you've ever used a commandline ftp-program, this will be very similar.

You could also write a script to send a bunch of files using rsync (which can easily tunnel via ssh by using the "ssh" option).

Or, if you have full access rights on the remote server, you could setup a secure key-pair between the two computers, which allows you to ssh into the remote server without entering a password. (This could be considered a security risk depending on the setup...)

I would guess that sftp is the easiest way. Give it a try.

---

### Post by DuckFish on 2007-02-03
Thanks, I'll try sftp when I can, and if it doesn't work, I'll take a look at zssh.

---

### Post by SeanTater on 2007-02-03
Not that it's very simple, but if nothing else helps, this should: it's a bit of a hack though..

```
cat /the/file | ssh user@host "cat > /the/remote/file"
```

I used it because I needed to securely transfer a stream that I did not have enough disk space to save.

---

### Post by schilcha on 2007-02-03
Have a look at sshfs. It establishes an ssh-connection to the remote server and mounts a directory from there to your local filesystem.
```

sshfs schilcha@burns: ~/netfs/burns/

```
...mounts my home-dir on the machine burns to the mount-point ~/netfs/burns. By copying files to/from that local directory I transfer files to/from the remote host via ssh.

To umount, use:
```

fusermount -u ~/netfs/burns

```

btw, there's a package called sshfs in the universe repos.

Good Luck!

---

### Post by DuckFish on 2007-02-07
Sorry it's been a few days!
WW: I tried zssh - the concept seems great to me - but sz (used to send local files) didn't work properly. Apparently, zmodem or some other has to be installed on both machines.

kebes: sftp is nice(r than scp), but not as convenient as rsync. (<3 rsync)

SeanTater: Interesting, but would become too complicated (I think, with a bunch of &&s) compared to rsync.

schilcha: It gave me an error message - said fusermount is disabled or something.

So, I think I'll use rsync in conjunction with a [very small] script. I found out that scp (rcp) is like rsync, but rsync is a sort of updated version - man rsync yields "rsync &#8212; faster, flexible replacement for rcp".
[quote=man rsync]rsync is a program that behaves in much the same way that rcp does, but
has many more options and uses  the  rsync  remote-update  protocol  to
greatly  speed  up  file  transfers  when the destination file is being
updated.[/quote]
Thanks, everyone! :)

- On a slightly different note...vBulletin isn't updating the title in the topics list or the page title, only the post title.

---

### Post by Bossieman on 2007-02-08
**scp -r /pathtofolder/ name@host:/targethetfolder/**

i use the above command when I want to transfer a folder to a folder on the remotecomputer, works great.

---

### Post by banato on 2007-11-30
> **DuckFish said:**
> 
schilcha: It gave me an error message - said fusermount is disabled or something.


I got sshfs to work. I also got it to work without sudo, wich is preferrable if you want to browse your remote files without typing your sudo password all the time. 

First I had to add myself to the fuse user group and change the group to /dev/fuse (for a reason I don't know):

```

sudo adduser user fuse

sudo chgrp fuse /dev/fuse
```

And I then I logged my self in again:

```

su - user
```

And voila! Sshftp worked fine. No more scp for me thank you. :)

---

### Post by Whiffle on 2007-11-30
Or, type sftp://nameofserver into the address line on nautilus or konqueror...

---

