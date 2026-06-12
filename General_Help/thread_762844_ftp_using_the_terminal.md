---
title: "ftp using the terminal"
date: 2008-04-22
forum: General Help
---

### Post by enchance on 2008-04-22
How do I use ftp using the terminal? I want to be able to do the usual stuff like copy and editing files, if possible.

---

### Post by oldos2er on 2008-04-22
Start by reading "man ftp"

---

### Post by RainCT on 2008-04-22
Well, just run "ftp ftp.server" (where ftp.server is the address to which you want to connect) and tell it the username and password when it asks for them; this will leave you in a console where you can upload files "put", download with "get", change the current directory on the server with "cd" (or "lcd" to change it locally), see a list of files in the current directory with "ls", etc. You can type "help" or "help command_name" for more info about the available commands.

If your host supports SFTP you can use "sftp [email]username@ftp.serv[/email]er", which is more secure.

---

### Post by markjensen on 2008-04-22
If you have ever used FTP from the commandline on a Windows box, the commands are the same.  "mget" for multiple get, and so forth.

---

