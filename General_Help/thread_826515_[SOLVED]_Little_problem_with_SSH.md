---
title: "[SOLVED] Little problem with SSH"
date: 2008-06-12
forum: General Help
---

### Post by jelson on 2008-06-12
I have a little problem with SSH.  I want to log into a Solaris server at my school.  I can do it ok with windows, using SSH and X-Win32, but there are occasional glitches with this method.  The good thing about the windows method is that SSH for windows has a graphical file transfer system, so I can see the folders of the system I'm SSHing into and can drag and drop files from there to my desktop and vice versa, and open those files up and edit them as I please.  I want to be able to do the same in Ubuntu, and I can log in using the terminal and putting in: ssh -X [email]username@server.name.school.edu[/email], and I can run programs on that server and things, but I can't access the files that I put in there.  When I click on Places/Connect to Server, I put in that server name and do an SSH connection, but nothing happens for like 30 minutes, and then it tells me it can't access the server. What am I doing wrong?

---

### Post by molotov00 on 2008-06-12
File transfers in SSH is actually done over SFTP. Your Windows client must have hid this from you, so it looked like you were just doing 'ssh' stuff.

Just download yourself an sftp client, or use sftp from the command line just like ftp.

---

### Post by jelson on 2008-06-12
I used gFTP and that worked as good as the windows program does!  Thanks.

---

