---
title: "Unable to connect through Filezilla"
date: 2017-03-07
forum: General Help
---

### Post by Suchetana on 2017-03-07
Dear Forum Users
I am using Ubunty 14.04. I use Filezilla to connect to a remote system for file transfer. Recently, I noticed that despite giving the correct password, etc, I am not able to connect. It is showing "Connection timed out". The same remote location is easily connecting via terminal. When I ran the detection wizard, it gave up messages indicating firewall issues. However, I have not changed a single setting on my system.
Please guide me to resolve this issue.
Thanks in advance

P.S. My colleagues ahve been able to connect to the same location via Filezilla from their systems today also.

---

### Post by dragonfly41 on 2017-03-07
I'm on 14.04 and I just had a quick look at FileZilla ..
If you go to FileZilla > Edit > Settings, in the popup window, left panel, at the bottom of menu is Debug option.
Perhaps enable Debug to get more information for troubleshooting session.

---

### Post by Suchetana on 2017-03-07
The specific error:
Error:    Connection timed out
Error:    Could not connect to server
Status:    Waiting to retry...
Status:    Connecting to 10.200.6.5:21...
Status:    Connection established, waiting for welcome message...
Response:    220 (vsFTPd 2.2.2)
Command:    USER sanjibs
Response:    331 Please specify the password.
Command:    PASS *******

---

### Post by Suchetana on 2017-03-07
It helped. Thanks!

---

### Post by Suchetana on 2017-03-07
However, the file transfer isn't happening. It is throwing up the same error

---

### Post by dragonfly41 on 2017-03-07
There is a "Failed transfers" tab at bottom of FileZilla window.
Any clues there?

---

### Post by Suchetana on 2017-03-08
It shows disconnected from server

---

