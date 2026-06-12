---
title: "File corruption caused by uploading archive via ftp command"
date: 2008-04-27
forum: General Help
---

### Post by mike.berggren on 2008-04-27
Hi Guys, 

I'm hoping this is a simple one.. 

I have archive files that I know are intact (open/test fine locally). 

Why I try to upload the file(s) via the ftp command to my web host... and then download them again, the files are "corrupt" (WinRAR shows them as having an invalid CRC). 

Here's my run down:

```

# ftp -n -v ftp.foowebhost.com
Connected to ftp.foowebhost.com.
220---------- Welcome to Pure-FTPd [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 00:45. Server port: 21.
220 You will be disconnected after 15 minutes of inactivity.
500 This security scheme is not implemented
500 This security scheme is not implemented
KERBEROS_V4 rejected as an authentication type
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ascii
200 TYPE is now ASCII
ftp> user foouser foopassword
331 User foouser OK. Password required
230-User foouser has group access to:  foogroup
230 OK. Current restricted directory is /
ftp> prompt
Interactive mode off.
ftp> put foo.file
local: foo.file remote: foo.file
227 Entering Passive Mode (216,227,219,38,76,214)
150 Accepted data connection
226-File successfully transferred
226 0.172 seconds (measured here), 70.10 Kbytes per second
12455 bytes sent in 0.0057 seconds (2.1e+03 Kbytes/s)
ftp> bye
221-Goodbye. You uploaded 13 and downloaded 0 kbytes.
221 Logout.

```

Yet, when I download the file (from different systems and different FTP clients, it's still corrupt. 

Questions: 

1) Any idea why this is happening? 
2) Should I be using a different command instead?
3) Is there a more reliable command for uploading via FTP?

Thanks!

-MB

---

### Post by dcstar on 2008-04-27
> **mike.berggren said:**
> Hi Guys, 

I'm hoping this is a simple one.. 

I have archive files that I know are intact (open/test fine locally). 

Why I try to upload the file(s) via the ftp command to my web host... and then download them again, the files are "corrupt" (WinRAR shows them as having an invalid CRC). 

Here's my run down:

```

........
Using binary mode to transfer files.
ftp> **ascii**
200 TYPE is now ASCII
......

```

Yet, when I download the file (from different systems and different FTP clients, it's still corrupt. 
........

Of course there will be corruption when you send binary data as ASCII.

---

