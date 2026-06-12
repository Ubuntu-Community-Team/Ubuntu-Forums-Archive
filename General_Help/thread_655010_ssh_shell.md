---
title: "ssh shell"
date: 2007-12-31
forum: General Help
---

### Post by pranami on 2007-12-31
Dear Ubuntu users,

       I tried connecting to my computer (Mac OS X) at office from home using ssh on Ubuntu. To connect I issued: ssh -Y [email]myname@office.comp[/email]uter and I was able to connect successfully. To open a text file on my office computer I issued the following command: emacs filename.tx &

      But nothing happened. Hitting the return key again gave the following output:
[3]+  Stopped                 emacs filename.txt

      Using -Y flag (I tried -X instead of -Y as well) should let me open a text file from my office computer in the emacs window on my computer at home. Why is this happening?:confused: On the other hand, emacs can open the text file in the xterm window if I Issue following command: emacs filename.txt

      Please help me with this. It make work easy to be able to open multiple emacs windows.

Thanks

---

### Post by HermanAB on 2007-12-31
It may be the ampersand.  Leave it off and try again.

Cheers,

Herman

---

### Post by bindatype on 2007-12-31
You may want to check /etc/ssh/sshd_config on the remote machine to see if X11 forwarding is enabled. If it isn't then that's a show-stopper. Check /etc/ssh/ssh_config on your local machine and ssh using 
```

ssh -v -X (or -Y) yourname@yourdomain

```
and look for anything suspicious.

---

### Post by pranami on 2008-01-01
> **HermanAB said:**
> It may be the ampersand.  Leave it off and try again.

Cheers,

Herman

By not having & at the end, the file gets opened in the xterm window itself, so I can not use xterm unless I exit emacs. Thanks for thoughts.

---

### Post by pranami on 2008-01-01
> **bindatype said:**
> You may want to check /etc/ssh/sshd_config on the remote machine to see if X11 forwarding is enabled. If it isn't then that's a show-stopper. Check /etc/ssh/ssh_config on your local machine and ssh using 
```

ssh -v -X (or -Y) yourname@yourdomain

```
and look for anything suspicious.

The /etc/ssh_config file on my office computer looks like this:


[HTML]
# Site-wide defaults for various options

# Host *
#   ForwardAgent no
#   ForwardX11 no
#   RhostsAuthentication no
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication yes
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange yes
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes2
56-cbc
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
[/HTML]

     Clearly, it shows that ForwardAgent and ForwardX11 are set to no . I am not able to set them to yes because this file is apparently read only. Am I actually allowed to modify this file? If yes then how?

Thanks for your help.

---

### Post by HermanAB on 2008-01-01
$ sudo gedit /etc/ssh/ssh_config

---

### Post by pranami on 2008-01-01
> **HermanAB said:**
> $ sudo gedit /etc/ssh/ssh_config

Thanks brother. I'll try it and let you know what happens when I modify the ssh_config file. Happy New Year. :)

---

### Post by bindatype on 2008-01-01
You'll want to check /etc/ssh/sshd_config on the remote machine and /etc/ssh/ssh_config on the local machine--the two are not the same. 

Are you a sudoer on your office machine? If not then an admin will have to grant you the privilege.

---

### Post by pranami on 2008-01-04
> **bindatype said:**
> You'll want to check /etc/ssh/sshd_config on the remote machine and /etc/ssh/ssh_config on the local machine--the two are not the same. 

Are you a sudoer on your office machine? If not then an admin will have to grant you the privilege.

Hi bindatype, I m sorry for getting back so late. I got caught in work. On my office computer I edited the /etc/ssh_config file and set:

[HTML]# ForwrdAgent no
# ForwardX11 yes[/HTML]

 and on my home computer with Ubuntu 7.10 the etc/ssh/ssh_config file has:

[HTML]#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes[/HTML]

After logging in to my office computer from home using the following command:

[HTML]ssh -X (or -Y) myname@myofficecomputer[/HTML]

when I try to open a file on from my office computer using emacs it does not open in a new window, using the command:

[HTML] emacs filename &[/HTML]

on the other hand, issuing the command:

[HTML] emacs filename [/HTML]

opens the file in the xterm window. I don't know why I am not able to get xterm to open files in separate window? Please help me with that. Thanks.

---

### Post by geirha on 2008-01-04
You need to check that ssh**d**_config (on the office computer you are connecting to) has X11Forwarding enabled. Whether ForwardX11 in ssh_config is set or not doesn't matter, since the -X or -Y to ssh will override whatever the ssh_config says.

---

### Post by anaconda on 2008-01-04
> **pranami said:**
> Hi bindatype, I m sorry for getting back so late. I got caught in work. On my office computer I edited the /etc/ssh_config file and set:
[HTML]# ForwrdAgent no
# ForwardX11 yes[/HTML]


Well.. I don't really know about ssh_config, but usually the # in front of the line means that that line is commented away..  and the default value is given after the comment.

so you might want to try like this:
```
ForwardX11 yes
```
etc..

---

### Post by pranami on 2008-01-04
> **geirha said:**
> You need to check that ssh**d**_config (on the office computer you are connecting to) has X11Forwarding enabled. Whether ForwardX11 in ssh_config is set or not doesn't matter, since the -X or -Y to ssh will override whatever the ssh_config says.

Thanks for your reply. **bindatype ** also suggested that I take a look at sshd_config but for some reason  I thought it was ssh_config. I checked the sshd_config on my office computer and found:  "ForwardX11 no" . I have changed that to "ForwardX11 yes", I'll see if things work out when I get back home tonight. Thanks for your help.

---

### Post by pranami on 2008-01-04
> **anaconda said:**
> Well.. I don't really know about ssh_config, but usually the # in front of the line means that that line is commented away..  and the default value is given after the comment.

so you might want to try like this:
```
ForwardX11 yes
```
etc..

Thanks for your thought. On my office computer it seems that if there is a space between **#** and **keyword** it is treated as a comment and if there is no gap then it is treated as setting. e.g.:

Comment: [HTML]# ForwardX11 yes[/HTML]
Setting: [HTML]#ForwardX11 yes[/HTML]

---

### Post by bindatype on 2008-01-06
Are giving the command 
```

$ sudo /etc/init.d/ssh restart

```

after you make your changes? I tried to reproduce the behavior you indicated regarding the comments and spaces and I could not do it. Maybe you forgot to restart ssh?

The man page for sshd_config has this to say
> 
 Lines starting with &#8216;#&#8217; and empty lines are interpreted as comments.


---

### Post by geirha on 2008-01-06
If it's got a # in front of it, it's a comment, however the comments in the shipped ssh_config all show the default value, and ForwardX11 yes is a default value, so you only really need to uncomment them if you need to change its value.

---

