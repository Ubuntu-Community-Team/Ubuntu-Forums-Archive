---
title: "FTP port problem"
date: 2020-04-12
forum: General Help
---

### Post by abody511 on 2020-04-12
My problem is when I disable the firewall I can access the FTP, but if I enable it I can connect to the FTP but I can't discover the Folders & Files.
 I have tried to add Rules in FTP 
-I have added port (20) and (21) as TCP

[IMG]https://i.imgur.com/UZi1mIP.jpg[/IMG]


In FTP Software log :

[IMG]https://i.imgur.com/tr0vDa8.jpg[/IMG]

---

### Post by TheFu on 2020-04-12
Plain FTP uses multiple ports.  The 2nd port changes wth each connection.  Firewalls don't like that.
Really, plain FTP should have died around 2002 when telnet died.  

Today, sftp should be used.  Any interest in using that?  Or rsync or scp?

---

### Post by abody511 on 2020-04-12
> **TheFu said:**
> Plain FTP uses multiple ports.  The 2nd port changes wth each connection.  Firewalls don't like that.
Really, plain FTP should have died around 2002 when telnet died.  

Today, sftp should be used.  Any interest in using that?  Or rsync or scp?

Can u PM me ?

---

### Post by coffeecat on 2020-04-12
Support, not chat. *Thread moved to **General Help***

> **abody511 said:**
> Can u PM me ?

Please do not ask forum members for support via pm. From the forum [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules"):

> **Private Messaging:** Asking support questions via private messages is strongly discouraged. It is unlikely that users will respond to these requests and it defeats the secondary intent of the forums to be a resource for people seeking assistance using internet searches and forum searches. 

---

### Post by abody511 on 2020-04-12
I apologize about that , what is the best FTP for Ubuntu

---

### Post by HermanAB on 2020-04-13
OpenSSH is the best SFTP for Linux.  Your default install already has it.  Read 'The Snail Book' - it is online and free.

---

### Post by The Cog on 2020-04-13
This one? [https://mothernatured.com/product/the-snail-book/](https://mothernatured.com/product/the-snail-book/) (top hit on a DDG search)

---

### Post by HermanAB on 2020-04-13
That one is nice for gardening, but this one is better for networking:
[http://www.snailbook.com](http://www.snailbook.com)
:)

---

### Post by TheFu on 2020-04-13
> **The Cog said:**
> This one? [https://mothernatured.com/product/the-snail-book/](https://mothernatured.com/product/the-snail-book/) (top hit on a DDG search)

I missed that too.  Whoooooosh!

Unix people use ssh for any system to system connection as the default, then only switch to something else for a specific purpose.  There must be at least 50 different, common, uses for ssh connections.  Yet, Windows people haven't usually heard about any.  If you have 2 Unix systems (which is basically, any computers not running Windows), then some ssh method is probably the quickest, easiest, method to have those systems communicate, transfer data, run remote commands, create a tunnel for network traffic, or do a quick remote file system mount .... all under the end-users control.  No admin need get involved once sshd is allowed.

[LIST]
[*]    secure remote CLI/shell access to systems with plain ssh
[*]    secure remote access to files via sftp or scp or rsync
[*]    secure remote filesystem access via sshfs
[*]    secure remote desktops via x2go/freenx
[*]    secure remote file replication with rsync (ssh is the default rsync protocol)
[*]    secure remote file backups with any of 50 different backup tools rsync, rdiff-backup, lots more)
[*]    secure port forwarding of selected ports
[*]    secure remote editing with vim/gvim and other editors
[*]    pseudo-VPN with sshuttle <— this may be helpful.
[/LIST]
[https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh](https://blog.jdpfu.com/2014/09/23/you-don-t-know-ssh-about-ssh)

I use ssh tunnels as a poor mans VPN/SOCKS proxy when on unknown networks. All the traffic goes through my home-office connection before going out to internet servers.

Plus, all of these leverage the ~/.ssh/config file, so we don't need to remember userids, non-standard ports, IP addresses.  

```
host brians
  user thefu
  hostname brians.com
  port 23428

host china
  user ccp-user999
  hostname 223.223.182.190
  port 63428

```
I'd use **ssh brians** and my userid, hostname and non-standard port gets filled in.
or  **sftp brians**
or [B]rsync -azv  /etc/hosts brians:/tmp/
[/B]or **sshfs brians:bin /tmp/brians-bin**
or .... any of the other commands.

No more trying to remember if the odd port needs a -p or -P option again.  All ssh-based tools honor the per-user config file.

---

