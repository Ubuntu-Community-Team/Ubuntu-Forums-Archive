---
title: "X2Go Error"
date: 2014-08-26
forum: General Help
---

### Post by ynnusd on 2014-08-26
When starting the X2Go client on osx 10.9.4 I click and start the new session to my biolinux server running ubuntu 14.04.1 LTS after logging in I get two pop up errors. "SSH daemon failed to open the application's public host key." and "Connection failed Can not open file - " The session then continues to run just fine. 

Here is the log from the client. The server log just shows a successful connection.
```
NXPROXY - Version 3.5.0

Copyright (C) 2001, 2010 NoMachine.
See http://www.nomachine.com/ for more information.


Info: Proxy running in client mode with pid '54345'.
Session: Starting session at 'Tue Aug 26 10:23:49 2014'.
Info: Connecting to remote host 'localhost:31001'.
Info: Connection to remote proxy 'localhost:31001' established.
Info: Connection with remote proxy completed.
Warning: Unrecognized session type 'unix-kde-depth_32'. Assuming agent session.
Warning: Failed to read data from the X auth command.
Warning: Generated a fake cookie for X authentication.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: Using cache file '/Users/me/.x2go/cache-unix-kde-depth_32/S-F99877802B7F869806E65AA67E9040BC'.
Info: Forwarding X11 connections to display '/tmp/launch-9HfzQ9/org.macosforge.xquartz:0'.
Session: Session started at 'Tue Aug 26 10:23:51 2014'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.


Warning: Generated a fake cookie for X authentication.
Info: Using ADSL link parameters 512/24/1/0.
Info: Using cache parameters 4/4096KB/8192KB/8192KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde-depth_32'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 4/4.
Info: Using cache file '/Users/me/.x2go/cache-unix-kde-depth_32/S-8BEE9E45F10A1F115106FBFD5E9C13D7'.
Info: Forwarding X11 connections to display '/tmp/launch-9HfzQ9/org.macosforge.xquartz:0'.
Session: Session started at 'Tue Aug 26 09:34:54 2014'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
```

---

### Post by TheFu on 2014-08-26
Did you use ssh-copy-id to push the public ssh key from OSX to the linux userid?

---

### Post by ynnusd on 2014-08-27
No, is this something that I should try?

---

### Post by Phani_Vadrevu on 2014-10-16
Did you resolve this? I get the same error when using x2goclient on OSX trying to connect to x2goserver on Ubuntu 14.04. Please let me know if you resolved this issue.

---

### Post by stevew-purdue on 2014-11-26
I had this same problem and found that it was caused by missing SSH key files on the Mac client.  To force the Mac to generate these keys, I enabled SSH (System Preferences -> Sharing -> Remote Login) and then logged in over SSH from another computer.  Once I did that, the missing SSH key files were created and I was able to use X2Go without this annoying error message.

Hope that helps!

Steve

---

### Post by SimFre on 2015-05-23
I just ran what stevew-purdue suggested and it solved the problem. Thank you!

---

