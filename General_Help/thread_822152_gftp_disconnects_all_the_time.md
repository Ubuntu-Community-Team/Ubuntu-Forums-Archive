---
title: "gftp disconnects all the time"
date: 2008-06-07
forum: General Help
---

### Post by ryank76nz on 2008-06-07
I have logged in and can see the files in the Drupal site that I want to back up. 
```

I have recently connected a router and have disabled ipv6 as suggested in other threads. This is still disconnecting all the time though:
215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
CWD /html

250 OK. Current directory is /html
PASV

227 Entering Passive Mode (64,13,192,183,220,255)
RETR /html/sites/default/files/pictures/picture-6.jpg

150 Accepted data connection
Error: Cannot open local file /home/ryan/websites/Curious/sites/default/files/pictures/picture-6.jpg: No such file or directory
ABOR

226-File successfully transferred
226 0.007 seconds (measured here), 260.54 Kbytes per second
PASV

226 Since you see this ABOR must've succeeded
Cannot find an IP address in PASV response '226 Since you see this ABOR must've succeeded'
Disconnecting from site outthere.dev64.net
Error: Remote site disconnected after trying to transfer file
Could not download /html/sites/default/files/pictures/picture-8.jpg from outthere.dev64.net
Error: Remote site outthere.dev64.net disconnected. Will reconnect in 30 seconds
```

Once I log in again and everything seems fine, I try to download some files: 

```
yan/websites/Curious/sites/default
CWD /html/sites/default/files

250 OK. Current directory is /html/sites/default/files
Loading directory listing /html/sites/default/files from server (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,183,221,206)
LIST -aL

150 Accepted data connection
226-ASCII
226-Options: -a -l 
226 7 matches total
CWD /html/sites/default/files/color

250 OK. Current directory is /html/sites/default/files/color
Loading directory listing /html/sites/default/files/color from server (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,183,227,158)
LIST -aL

150 Accepted data connection
226-ASCII
226-Options: -a -l 
226 2 matches total
CWD /html/sites/default/files/images

250 OK. Current directory is /html/sites/default/files/images
Loading directory listing /html/sites/default/files/images from server (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,183,204,60)
LIST -aL

150 Accepted data connection
226-ASCII
226-Options: -a -l 
226 5 matches total
CWD /html/sites/default/files/pictures

250 OK. Current directory is /html/sites/default/files/pictures
Loading directory listing /html/sites/default/files/pictures from server (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,183,197,96)
LIST -aL

150 Accepted data connection
226-ASCII
226-Options: -a -l 
226 5 matches total
CWD /html/sites/default/files/images/temp

250 OK. Current directory is /html/sites/default/files/images/temp
Loading directory listing /html/sites/default/files/images/temp from server (LC_TIME=en_NZ.UTF-8)
PASV

227 Entering Passive Mode (64,13,192,183,216,69)
LIST -aL

150 Accepted data connection
226-ASCII
226-Options: -a -l 
226 2 matches total
CWD /html/sites/default

250 OK. Current directory is /html/sites/default
Error: Could not make directory /home/ryan/websites/Curious/sites/default/files: Permission denied
Error: Could not change mode of /home/ryan/websites/Curious/sites/default/files to 775: No such file or directory
PASV

227 Entering Passive Mode (64,13,192,183,229,184)
RETR /html/sites/default/files/.htaccess

150 Accepted data connection
Error: Cannot open local file /home/ryan/websites/Curious/sites/default/files/.htaccess: No such file or directory
ABOR

226-File successfully transferred
226 0.000 seconds (measured here), 2.40 Mbytes per second
Error: Could not make directory /home/ryan/websites/Curious/sites/default/files/color: No such file or directory
Error: Could not change mode of /home/ryan/websites/Curious/sites/default/files/color to 775: No such file or directory
PASV

226 Since you see this ABOR must've succeeded
Cannot find an IP address in PASV response '226 Since you see this ABOR must've succeeded'
Disconnecting from site outthere.dev64.net
Error: Remote site disconnected after trying to transfer file
Could not download /html/sites/default/files/homosexuality-and-the-bible.doc from outthere.dev64.net
Error: Remote site outthere.dev64.net disconnected. Will reconnect in 30 seconds
Looking up outthere.dev64.net
Trying outthere.dev64.net:21
Connected to outthere.dev64.net:21
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 73 of 800 allowed.
220-Local time is now 20:45. Server port: 21.
220-This is a private system - No anonymous login
220 You will be disconnected after 15 minutes of inactivity.
USER access@outthere.dev64.net

331 User xxxx OK. Password required
PASS xxxx
230-User xxxx has group access to:  3543    
230 OK. Current directory is /
SYST

215 UNIX Type: L8
TYPE I

200 TYPE is now 8-bit binary
CWD /html/sites/default

250 OK. Current directory is /html/sites/default
PASV

227 Entering Passive Mode (64,13,192,183,220,4)
RETR /html/sites/default/files/homosexuality-and-the-bible.doc

150-Accepted data connection
150 54.0 kbytes to download
Error: Cannot open local file /home/ryan/websites/Curious/sites/default/files/homosexuality-and-the-bible.doc: No such file or directory
ABOR

226-File successfully transferred
226 0.000 seconds (measured here), 650.54 Mbytes per second
Error: Could not make directory /home/ryan/websites/Curious/sites/default/files/images: No such file or directory
Error: Could not change mode of /home/ryan/websites/Curious/sites/default/files/images to 775: No such file or directory
Error: Could not make directory /home/ryan/websites/Curious/sites/default/files/pictures: No such file or directory
Error: Could not change mode of /home/ryan/websites/Curious/sites/default/files/pictures to 775: No such file or directory
PASV

226 Since you see this ABOR must've succeeded
Cannot find an IP address in PASV response '226 Since you see this ABOR must've succeeded'
Disconnecting from site outthere.dev64.net
Error: Remote site disconnected after trying to transfer file
Could not download /html/sites/default/files/images/Polaroid.png from outthere.dev64.net
Error: Remote site outthere.dev64.net disconnected. Will reconnect in 30 seconds
```

help!! please?

---

