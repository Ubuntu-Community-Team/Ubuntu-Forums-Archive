---
title: "Proxy settings"
date: 2004-11-09
forum: General Help
---

### Post by Franz on 2004-11-09
Hi! I' m sorry to have questions again, but I am really new to the Linux world.
  :D 
I am connected to a LAN, so I need  to set a proxy server to use apt-get or similar. I would like to avoid to set the proxy server every time I start Linux so I added these lines to /etc/profile and /home/<user>/.bash_profile

export http_proxy="http://192.168.54.1:80"
export ftp_proxy="http://192.168.54.1:80"

but however I have to give the above commands manually using the terminal, if I want the things working. what can I do to automatically configure the proxy server at the start up?
Thanks!!

---

### Post by Enygma on 2004-11-09
Add those lines to .bashrc and that should do the trick

There's an Environment Variable HOWTO here 
[http://www.ubuntuforums.org/showthread.php?t=1586](http://www.ubuntuforums.org/showthread.php?t=1586)

---

