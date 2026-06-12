---
title: "SSH Download File to Local Computer"
date: 2016-01-22
forum: General Help
---

### Post by jonathan90 on 2016-01-22
Does anyone know if there's a way I can download a file from a server when I'm SSH'd into it? I know you can do it with ftp/sftp, and I'm confused on how to use scp to download. I'd like to download the file preferably to the directory on my PC I was in before I connected to the server.

---

### Post by HermanAB on 2016-01-23
You can use 'screen' to make use of multiple windows using a single SSH connection, or you can open multiple terminals on your local machine and run multiple ssh connections to the server.  Some prefer the former, I prefer the latter.

So, in you present console window use 'pwd' and 'ls' to list the file you are interested in. Open another console window (right click open new terminal window) and retype the whole file path, or use mouse highlight and middle click to copy it from the other window:
$ scp username@servername:/path/to/file .

The 'space dot' means 'here'.  So the file will be copied to the path that the terminal is in, which you can see with 'pwd'.

'Hope that helps!

---

### Post by SeijiSensei on 2016-01-23
You can use scp from either end.  On the client you can just use 
```
scp user@server:/path/to/remote/file .
```
to copy the file to the current directory.  You don't need to be connected via SSH at all.  If you have openssh-server running on your local machine as well, you can use scp in the other direction after connecting to the server with SSH:
```
scp /path/to/some/file user@machine:/path/to/location
```

I generally use multiple tabs within the terminal application for situations like this.  I use KDE's Konsole since I'm running Kubuntu, but I'm pretty sure the terminal app in vanilla Ubuntu has tabs as well.

Kubuntu also supports fish:// URLs in its file browser, Dolphin.  That uses SSH to create a connection to the server that you can browse just like you would browse local directories.  I usually upload files to my web server by having two windows open in Dolphin, one local and one pointing to the server.  Then I can just drag-and-drop files in either direction.  I don't know if a similar method exists in Nautilus.

---

### Post by jonathan90 on 2016-01-23
Okay thanks! I got it working and I'm using 2 terminal windows (one for  SSH and one for downloading). But is there anyway I can do the download  command from the SSH terminal like "get" in ftp/sftp or in the windows SSH client?

---

