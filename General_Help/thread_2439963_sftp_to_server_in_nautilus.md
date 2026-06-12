---
title: "sftp to server in nautilus?"
date: 2020-04-03
forum: General Help
---

### Post by MgFrobozz on 2020-04-03
I used to be able to browse in other servers from nautilus, but my configuration procedure no longer works. Advice?

I'm doing this:
[LIST]
[*]Fire up nautilus
[*]Click "Other Locations"
[*]For "Connect to Server", enter (eg) "sftp://myserver.com:2020", where "myserver.com" is the domain name, and "2222" is the ssh port number (intentionally _not_ port 22)
[*]Click "Connect"
[*]Nautilus used to respond with a dialog that allowed me to enter the username and password for the connection. Now it responds "Permission denied".
[/LIST]

Is there a way to convince it to pop up the authentication dialog?
If not, is there a way to store the username/password combination in ~/.config/nautilus? (I can't find any information on that file structure).

---

### Post by TheFu on 2020-04-03
is the ssh client package installed on the machine?

```
sudo apt install openssh-client
```

That is just a guess. i don't use nautilus.

Obviously, the remote systems must have the openssh-server package installed, configured.  Hopefully, you also install fail2ban for protection on those machines too.

Really, passwords are a terrible idea.  Just takes 2 commands to setup ssh-key authentication between a client and the servers. Getting prompted just once every 4 hrs to unlock the key is pretty nice AND much more secure than using passwords.

---

### Post by HermanAB on 2020-04-04
Debug it from the command line with 'ssh -vvv...' to see the error messages.  

If it doesn't work from Bash, then it won't work from Nautilus.

---

### Post by MgFrobozz on 2020-04-04
Hi, The Fu ...

Yep, ssh is installed (I use it frequently). I'm also using ssh-key authentication, with .ssh/authorized_keys at the server(s) end.

> > dpkg --list | grep openssh-client
ii  openssh-client                        1:7.6p1-4ubuntu0.3                               amd64        secure shell (SSH) client, for secure access to remote machines


---

### Post by MgFrobozz on 2020-04-04
Hi, HermanAB ...

Direct ssh and sftp (from a bash shell) works to the same machine I'm trying to access in nautilus. 

I'm fine with using bash, but a co-worker finds the bash learning curve too steep, and needs a gui method instead. It doesn't have to be nautilus, any app with a gui that could do this will be fine.

---

### Post by HermanAB on 2020-04-04
OK, if the command line works, then that eliminates all network routing problems - meaning that your problem is purely with Nautilus.  

If you launch Nautilus from a Gnome menu, then you cannot see any error messages.  Launch Nautilus from Bash and see what errors you get.

---

### Post by TheFu on 2020-04-04
Whenever I've used sftp:// in the URI for any Linux file manager, it has always worked. Don't remember doing anything special, ever, but I use caja perhaps 1-2 times a year, so I'm hardly an expert.  Caja is the Mate file manager.

Hummmm. Just tried it with caja and it worked fine.
[https://askubuntu.com/questions/349873/use-connect-to-server-to-connect-via-sftp-to-access-a-folder-in-a-remote-serve](https://askubuntu.com/questions/349873/use-connect-to-server-to-connect-via-sftp-to-access-a-folder-in-a-remote-serve)
Seems like that should "just work."  $ sftp lubuntu is working between the same machines too.  Whenever that's happened before for other programs, it was usually
* firejail confinement
* snap confinement
* remote system firewall

Used it to a system without ssh-keys setup and was prompted for credentials, then allowed in.  Tried 5 different systems. They all worked.

So, it should be working fine.  Can you tail -f /var/log/auth.log while attempting the connections?  The logs should provide some google-ible lines.

---

### Post by MgFrobozz on 2020-04-04
Thanks HermanAB and TheFu ...

I found "nemo" (a fork of nautilus?), and installed it ("sudo apt install nemo"). Alt-F2, then run "nemo" and

[LIST]
[*]From the nemo menu, Click "File/Connect to Server ..."
[*]For "Server", enter the alias name from ~/.ssh/config
[*]For "Type", select "SSH"
[*]For "Folder", select the home folder for the appropriate user on the server
[*]Leave "User Name" and "Password" empty (nemo will use the credentials from ~/.ssh/config)
[*]Click "Connect"
[/LIST]

After installing nemo, one needs to do this to hide nautilus and show nemo:

[LIST]
[*]Right-click "Applications" and select "Edit Menus"
[*]Click "Accessories"
[*]There will be two "Files" icons. Right-click on each and select "Properties"
[*]Make sure only  the icon using nemo has "Show" selected"
[*]Click "Close"
[/LIST]

(Btw, if you do this in nemo, the ssh mount will also show up in nautilus.)

---

