---
title: "Using konqueror with SOCKS (ssh -D) proxy"
date: 2007-12-30
forum: General Help
---

### Post by WebDrake on 2007-12-30
Hello all,

I'm trying to set up Konqueror to work via a SOCKS proxy created through an ssh tunnel.

That is, if I first ssh into the remote server,

ssh -D 1234 [email]user@remotehost.com[/email]

... I want to set up Konqueror to use localhost as a proxy server on port 1234 (analogous to what one can do in Firefox with FoxyProxy).

I've edited the Konqueror/KDE proxy settings to use the option to "Manually specify the proxy settings" and have entered localhost (or rather, [http://localhost](http://localhost) or [http://127.0.0.1](http://127.0.0.1) -- I've tried both) as the server, and 1234 as the port.  But when I then try to access the web I get an error: "connection to host is broken".

Can anyone advise?  Alternatively, can anyone recommend an FTP client that can use this kind of proxy?

Many thanks,

    -- Joe

---

### Post by bernied on 2007-12-30
This works for me with firefox, but I haven't been able to make it work with Konqueror. Probably not much help, but try firefox, at least you'll know whether it's network or application that's not working.

---

### Post by WebDrake on 2008-01-02
It does work with Firefox. :-)

The reason for wanting it to work with Konqueror is that I want to use it not just with Konqueror's browsing capacities but also its FTP/file manager abilities.  I need to go via the proxy to *upload* to a website I need to update while away from the office.

It doesn't *have* to be Konqueror.  If I could get FTP access via the proxy using another piece of software, that would be fine.  It's just the obvious choice because it's what I normally use for FTP.

---

### Post by bernied on 2008-01-02
This is not so hard. Try this in the address line in konqueror:
```
fish://user@server:22/home/user
```
Swap 'user' for your username on the remote machine, 'server' for the name of the server, or it's IP address, and '/home/user' for whatever directory you want to find yourself in. This is an ssh connection to your remote filesystem. If fish: does not work, try scp: which is another ssh protocol.

If it works, add it as a bookmark. You can also add it as a Remote Place in the System Menu.

You can also use sshfs to add remote directories, so that they are mounted on your filesystem at startup, but that is a little more complicated. Google sshfs, or install it and read the man pages.

---

### Post by WebDrake on 2008-01-03
> **bernied said:**
> This is not so hard. Try this in the address line in konqueror:
```
fish://user@server:22/home/user
```
Swap 'user' for your username on the remote machine, 'server' for the name of the server, or it's IP address, and '/home/user' for whatever directory you want to find yourself in. This is an ssh connection to your remote filesystem. If fish: does not work, try scp: which is another ssh protocol.
Unfortunately it is not so simple.  The server to which I have ssh access, and the server to which I want to make an FTP connection, are not the same machines.  I *cannot* use ssh to access the latter, indeed I cannot make *any* connection to it from any machine outside the university domain (which is why I have to set up a proxy).

So, the problem is basically: how do I get my FTP software (usually I would use Konqueror but I'm open to other suggestions) to recognise the proxy settings I've created?

I don't know if I could create the FTP connection as a virtual folder on the machine to which I have ssh access and then proceed via fish:// as you suggest, but if not, we're back to the original problem of getting Konqueror to recognise the proxy created by ssh -D.

---

### Post by bernied on 2008-01-04
Ahhh, I see. Sorry I didn't understand properly.
Well, I still don't know how to do this with SOCKS in Konqueror. 

Another idea - tunnel the specific port for ftp using ssh, then connect through the tunnel. So, for ssh, you would do:
```
ssh -L 10021:ftp.server.ip.address:21 sshserver
```
then in konqueror, try:
```
ftp://localhost:10021
```
You don't have to use port 10021 on the local side, but (I think) it does have to be a number bigger than 1024. I think 21 is the standard port for ftp - check this if it doesn't work.

---

### Post by Contess on 2008-01-29
Hi, I have the exact same problem.

Not sure if this is true, but someone told me that Filezilla 2.2.23 did have this function. Looking for it now. Let me know if you find out. 

Cheers

---

### Post by Contess on 2008-01-29
Well, I have found an older version on sourceforg.org:

[http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=15149](http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=15149)

Downloaded :
FileZilla_2_2_32_dbg.zip
FileZilla_2_2_32.md5

..and I am stuck now. :confused: How can I install this thing ?

---

### Post by Contess on 2008-01-29
apparently, all versions before 3.0 are windows, so we'd have to run it through Wine.

Any opinions ??

---

### Post by Contess on 2008-01-29
Hello again,

Installed FireZilla 2.2.32 into wine. Installation worked but I didn't have the chance to actually try it out yet..
Will let you know.

Cheers

---

### Post by Contess on 2008-01-31
RESOLVED

1.
Installed FireZilla 2.2.32 into wine

2.
Configured FireZIlla to use a Proxy at 127.0.0.1  port 8888

3.
sudo ssh -D 8888  username_at_proxyserver@proxy_server_IP


Works Great

---

