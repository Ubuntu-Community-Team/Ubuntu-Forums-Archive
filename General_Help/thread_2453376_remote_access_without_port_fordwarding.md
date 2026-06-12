---
title: "remote access without port fordwarding?"
date: 2020-11-09
forum: General Help
---

### Post by josephchrzempiec on 2020-11-09
Hello i setup a ubuntu desktop at my house which is over 700 miles away. I had remote access to it using temaviewer and anydesk as a backup. Problem is i rebooted my system and i can no longer get remote access. I still have ssh access but that is all. I need to open a port on my router but i can not get into the desktop to open a browser and portforward anything. Is there a way in ssh i can reopen teamviewer or anydesk? The problem is even if i reopen them the passwords on temaiewer has changed. I don't know what to do. Can someone please help me on this problem? Or is there any other vnc program i can install though ssh?


Joseph

---

### Post by dragonfly41 on 2020-11-09
I have no experience in this scenario so I am only musing over what I might try if in your shoes ..

Would it be feasible to install webmin on your remote desktop and gain access to webmin port management through webmin?

[https://linuxhint.com/install_and_use_webmin_ubuntu/](https://linuxhint.com/install_and_use_webmin_ubuntu/)

Extending this thought you might need ngrok to be installed also on your desktop.

[https://ngrok.com/](https://ngrok.com/)

---

### Post by HermanAB on 2020-11-09
You have SSH access - what more do you want?

You can run any GUI program using SSH, provided that you have an X server on the local machine, which can be Windows, Mac or Linux. For example:
$ssh -Y user@ipaddy “gedit filename”

To speed it up a bit use header compression and a simpler encryption -C and -c blowfish.

---

### Post by SeijiSensei on 2020-11-09
Since you can ssh to the remote, you might consider setting up a static OpenVPN tunnel between the two devices. 

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

---

### Post by TheFu on 2020-11-09
If you have ssh access, then **x2go** will work too.  The NX protocol uses ssh for both authentication and tunneling of the highly efficient NX remote desktop.  I always use the PPA to setup the remote server and local client.  Windows has a client that works well too, just be certain to install the font packages on Windows.  Also, don't use gnome as the DE. Use one of the lighter DEs (LXDE, XFCE) or openbox or fvwm.  I bet you'll never go back to trusting some 3rd party again.

---

### Post by HermanAB on 2020-11-09
SSH also does VPN.

Basically, all you got to do is read the SSH manual:
[http://www.snailbook.com/](http://www.snailbook.com/)

---

### Post by SeijiSensei on 2020-11-09
> **HermanAB said:**
> SSH also does VPN.
I always thought SSH just handled port mapping. Can you use it to construct a tunnel that carries all traffic regardless of the port/service involved?

---

### Post by HermanAB on 2020-11-10
SSH is a sysadmin Swiss Knife.  It can do anything.  Not necessarily fast, but it is secure.  

You got to read the Snailbook.  You won't be sorry.

---

### Post by TheFu on 2020-11-10
> **HermanAB said:**
> SSH is a sysadmin Swiss Knife.  It can do anything.  Not necessarily fast, but it is secure.  

You got to read the Snailbook.  You won't be sorry.

ssh really can do almost anything to connect 2 systems together.  The manpage is a work of art too.
ssh is enough for

[LIST]
[*]    secure remote access to files via sftp
[*]    secure remote filesystem access via sshfs
[*]    secure remote CLI/shell access to systems with plain ssh
[*]    secure remote desktops via x2go/freenx
[*]    secure remote file replication with rsync (ssh is the default rsync protocol)
[*]    secure port forwarding of selected ports
[*]    secure remote editing with vim/gvim and other editors
[*]    pseudo-VPN with [sshuttle]("https://github.com/sshuttle/sshuttle") <— this may be helpful.
[/LIST]

Be certain that you don't leave ssh open to the world. There are a few ways to lock that down.
[LIST]
[*]Huge Firewall blocks for 99% of the world
[*]Fail2ban / DenyHosts
[*]PortKnocking
[/LIST]

By just moving the public ssh port to a non-standard port (i.e. not 22/tcp), about 99% of all ssh attacks will stop. Use port translation in your WAN router, so that the default port can be used internally.  Then just put fail2ban on every ssh-server (for me that's every Unix-like OS) and configure for key-only authentication for all non-LAN IP connections using the "Match Address" in /etc/ssh/sshd_config

ssh is amazing.

---

### Post by HermanAB on 2020-11-10
If using sshuttle is too easy, here is the hard way to make a SSH VPN:
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

---

