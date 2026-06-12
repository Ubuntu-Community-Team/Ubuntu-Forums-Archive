---
title: "HOWTO: use xinetd to make TCP tunnels for ANY TCP program via ssh tunnel"
date: 2008-03-17
forum: General Help
---

### Post by syadnom on 2008-03-17
thought i'd make a little howto on using xinetd to manage your ssh tunnels such as email smtp, imap.

first, you need to create unique ssh keys so that you can tie each key to a command on the remote system.  this is making the assumption that both you(the client) and the server are running linux and more specifically ubuntu of any flavor.

go to your ssh directory
> cd ~/.ssh/
create a key for the service you want to tunnel
> ssh-keygen -t rsa -f imap_myusername

now send that to the remote server into roots ssh directory(note on access to root on bottom), you need to use the .pub file here
> scp imap_myusername.pub [email]root@hostname.com:/root/.ssh[/email]/

now log in to the remote machine and setup the authorized_keys file
> ssh -l root hostname.com
cd /root/.ssh/
cat imap_myusername.pub >> authorized_keys
nano -w authorized_keys

edit the file to match your needs.  example:
#imap_syadnom
from:
> ssh-rsa AAAAB3Nz******************************************
to:
> command="nc localhost 143",no-X11-forwarding,no-agent-forwarding,no-port-forwarding ssh-rsa AAAAB3Nz******************************************


what that does is makes it so that when your ssh key is used to access the system, nc (netcat) is used to essential do a loopback telnet to port 143, which is the port you are trying to use for imap.  replace that 143 with whatever TCP port you like.  I suggest you keep the file called imap_username organized so that it suggests what it is used for

now, the server should allow passwordless connections with that key.
log off the remote server.  now you should be back on your machines

try it, note that now use don't use the .pub, just the non-suffixed file.
> ssh -i ~/.ssh/imap_username [email]root@hostname.com[/email]

you should be connected to the service you want.
now you just need to add the info for your tunnel in xinetd.conf

> nano -w /etc/xinetd.conf

add this info
> service imap
{
        socket_type     = stream
        protocol        = tcp
        wait            = no
        user            = root
        disable         = no
        server          = /usr/bin/ssh
        server_args     = -q -C -o Compressionlevel=9 -T -i /home/username/.ssh/imap_username [email]root@hostname.com[/email]
        groups          = yes
        bind            = 127.0.0.1
}


that will make a new connection to hostname.com with the username root and the key we just setup every time you connect to the port for imap on 127.0.0.1, where i have put "service imap" you could put "service 143".  I also turn on compression (-C) and put the maximum compression level (-o Compressionlevel=9) in there as it makes a big difference over the internet.  on a local network, compression typically slows everything down.

now you can use 'localhost' or '127.0.0.1' for your imap or whatever TCP connections.  I use this a lot for thunderbird and my remote email server as it is secure and much faster than a direct connection through the internet because of the compression.  just tell thunderbird that your remote IMAP server is located at localhost.

benefits:
automatic tunnel only when needed.
not prone to timeout
you done have to manually start your tunnel.
dropped connections are automatically reopened when needed.
compressible connection.
secured via ssh

dangers of giving access keys to root are a bit obvious.  the use of the "command" directive in the authorized_keys file is the solution, this is a non-escapeable shell so root access is limitedto the imap server interface.

good luck, hope everyone enjoyed this little tutorial.  this also works well for http,smtp,vnc,X11 and webmin and some ftp servers such as proftpd will allow it with some tweeking.

---

### Post by syadnom on 2008-03-17
forgot some credits here:
most of this guide is a combination of personal experience and a post here: [http://www.debian-administration.org/articles/487]("http://www.debian-administration.org/articles/487") by the debian user Utumno.  Thanks to Utumno for the info on formating in the xinetd.conf.

---

