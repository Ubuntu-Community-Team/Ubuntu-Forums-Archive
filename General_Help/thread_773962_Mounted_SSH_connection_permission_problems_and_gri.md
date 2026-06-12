---
title: "Mounted SSH connection permission problems and gripes"
date: 2008-04-29
forum: General Help
---

### Post by shiznatix on 2008-04-29
I use the "connect to server" option in Nautilus all the time. This new release though has this strange problem with permissions though. Through the terminal I can connect to a server and do everything just fine but for some reason, using the exact same user (I have tripple checked) I can't create files in folders that the user I am logged in with owns.

I have tried logged in as root though the "connect to server" and all is just fine but if I am logged in as the user who actually owns the folders the "create folder" and whatnot is grayed out. The fix to this is have a terminal open with the same user and just use touch or mkdir and I am on my way but it is still annoying.

Also, it seams to be buggier than before. I have always had Nautilus crashes because of these (which sucks that it didn't get fixed) but it seams that ssh in general has slowed down. Just doing ssh to a networked computer takes like 15 seconds to give me a password prompt. This never happened until the upgrade.

Last, every time I open one of the connections in the "connect to server" bookmarks it throws another "sftp to SOME_IP" for each connection I have going there. Ugly, really just not needed because I will have like 3 windows open for the same connection and it doesn't tell you what user each one is so what good does that do me?

So really, whats up with this situation and how can I at least fix my problems with the permissions?

---

### Post by shiznatix on 2008-04-30
*bump*

Can anyone help me with any of the problems that I described?

---

### Post by niekko on 2008-10-07
> I have tried logged in as root though the "connect to server" and all is just fine but if I am logged in as the user who actually owns the folders the "create folder" and whatnot is grayed out. The fix to this is have a terminal open with the same user and just use touch or mkdir and I am on my way but it is still annoying.

Same problem here. Did you or anybody ever find a solution for this?

---

### Post by KeyserSoze93 on 2008-10-07
I have had the problem w/ nautilus (No write access to files my user group owns, and have not worked out a fix.

If you want an alternative method (which is nearly as quick), you could try installing sshfs and then mounting the server with that (with nautilus, it uses gnome-vfs).

Run the following commands (as yourself, to ensure you get full access to the mounted dir:

```
sudo apt-get install sshfs

mkdir ServerSSH

sshfs user@server:/home/user ServerSSH
```

and it should be mounted.

To unmount:

> fusermount -u ServerSSH

---

### Post by cariboo on 2008-10-07
Another solution would be to use sftp.

Open Nautilus and in the location bar type:

```
sftp://user@server
```

You will be prompted for a password. You can then navigate to your home directory on the sever and create and remove directories just as if it were located on the computer you are using.

Jim

---

### Post by niekko on 2008-10-07
Isn't this exactly what's happening when using Connect to Server and selecting SSH?

---

