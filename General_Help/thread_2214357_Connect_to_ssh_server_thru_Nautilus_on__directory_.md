---
title: "Connect to ssh server thru Nautilus on / directory and not user home"
date: 2014-03-31
forum: General Help
---

### Post by mobidoy2 on 2014-03-31
I am connecting to a server thru ssh in Nautilus with : 

ssh://user@server.

when it connects, it gets me in the home folder (which is sudoer) and I cannot navigate up the tree to go in say /etc or /usr folders.

I would like to be able to open files on it with softwares like Pype ! 

Thanx

---

### Post by TheFu on 2014-04-01
Welcome to the forums.

Not certain that I understand the issue. My beard is grey, so I don't always understand.

Nautilus is a file manager - it works with sftp, not ssh.

If you need to edit files that are owned by any other userid, then you'll need to connect with that userid or a userid in the same group, if the files allow group write.

I don't know of any GUI that does scp, rcp, sftp AND allows dynamic sudo. It just isn't done that way.

If you use a terminal, you can ssh into a remote system, then you can use sudo as needed (assuming this works for the command and userid is in the sudoers file via name or group).

Sorry - never heard of pype, so can't help with that at all. It isn't on my systems, so can't check the manpage quickly.

---

### Post by steeldriver on 2014-04-01
@TheFu, at least in 12.04 the 'Connect to server...' popup in Nautilus refers to sftp as 'SSH' - perhaps that's the source of the confusion

It sounds to me like the particular server that the OP is connecting to is using a chroot setup to 'jail' sftp users to their home directories - otherwise AFAIK there's nothing to stop browsing upwards via Nautilus (and the default is to open the remote filesystem at the / directory anyway)

---

### Post by mobidoy2 on 2014-04-01
the problem is more with nautilus finaly, as it has no navigation bar at the top, when you connect to the server, it goes to user home folder without anyway to browse back to parent folder.

Using an application ex:pype, I can browse back up to root directory and go anywhere.

Is there a way to get the navigation bar back or to have a way to get .. folder ?

---

### Post by steeldriver on 2014-04-01
You can use **Ctrl-L** to display the location input area or use **Alt-Up** to navigate up directly

---

