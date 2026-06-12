---
title: "Can't connect to my SSH server by global IP address when I'm not on the servers wifi"
date: 2015-09-04
forum: General Help
---

### Post by noahdessauer on 2015-09-04
When on the same network it works fine with either the global or local IP address being used.

When trying to connect over global IP.
It trys to connect but it returns this error after a while of trying  etimedout (connection timed out).
I am forwarding port 1555 to my servers static IP.

I made sure port 1555 was open like this on the server: `sudo ufw allow 1555/tcp`

I am on Linux my fire wall is configured correctly with a open port 1555. I can ping the server. The IP is configured correctly I did not make a mistake there. Open ssh in the terminal does not return a error it just trys endlessly to connect. A ssh app I have returns the error. MTR works 100%

How do I fix this?

---

### Post by TheFu on 2015-09-04
[http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

And double check everything.

---

