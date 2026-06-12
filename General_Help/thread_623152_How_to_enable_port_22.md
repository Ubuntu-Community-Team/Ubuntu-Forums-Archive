---
title: "How to enable port 22"
date: 2007-11-25
forum: General Help
---

### Post by seattle vic on 2007-11-25
I have 2 machines on my lan, both running ubuntu.  I was trying to ssh into each from a laptop/wireless on the lan.  One worked, the other got a refused connection.  While searching the forums, I came across the command netstat to check for the ports.  One the machine that works, I get:

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 127.0.0.1:631           0.0.0.0:*             LISTEN     5424/cupsd          
tcp6       0      0 :::5900                     :::*                    LISTEN     6038/vino-server    
tcp6       0      0 :::22                         :::*                    LISTEN     5380/sshd           

For the other machine, there is no port 22 listed, only a program called master on port 25.

Can somebody direct me how to enable port 22 so sshd can listen?

Thanks in advance

---

### Post by seattle vic on 2007-11-25
Never mind.  Turns out I had not installed the sshd files, so there wasn't even any sshd_config file.  I did that and then found that I'd run lokkit some time in the past, so I figured out how to enable ssh, and now it works...

---

### Post by #Reistlehr- on 2007-11-25
Yeah just about to say that you didnt install any ssh server/client

---

