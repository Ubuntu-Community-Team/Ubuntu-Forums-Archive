---
title: "ubuntu server edition and tftp problem when PUTTING files."
date: 2012-11-14
forum: General Help
---

### Post by West201 on 2012-11-14
I installed tftp as per this document:
[http://icesquare.com/wordpress/solve...ess-violation/](http://icesquare.com/wordpress/solve...ess-violation/)

I followed this to the letter 3 times and every time I put a file I get:

root@CiscoCFG:~# tftp localhost
tftp> put test
Error code 2: Access violation
tftp> root@CiscoCFG:~# tftp localhost
tftp> put test
Error code 2: Access violation

If I touch the file name chmod 777 the file then do a put it works perfectly fine.

My config is as follows:

service tftp
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = nobody
server = /usr/sbin/in.tftpd
server_args = -s /svr/tftp
disable = no
}

the directory /svr/tftp permissions are 777:
drwxrwxrwx 3 nobody nobody 4096 Nov 14 10:32 svr

This thing should have full permissions as would anyone who wanted to write or read from that directory. I see nothing in the logs im really stumped on this. If the file is already in the directory I can read it all day long, I just cant make NEW files, can not put them, but I can do get's, I can only put to an existing file with permissions @777.

When I TOUCH the file ahead of time locally on the server, chmod it to 777 I can then send the file to the tftp server but thats not a valid work around, Cisco switches and routers cant log in, touch a file then send it.:mad:

---

### Post by bab1 on 2012-11-14
> **jessejj89 said:**
> I installed tftp as per this document:
[http://icesquare.com/wordpress/solve...ess-violation/](http://icesquare.com/wordpress/solve...ess-violation/)

I followed this to the letter 3 times and every time I put a file I get:

root@CiscoCFG:~# tftp localhost
tftp> put test
Error code 2: Access violation
tftp> root@CiscoCFG:~# tftp localhost
tftp> put test
Error code 2: Access violation

If I touch the file name chmod 777 the file then do a put it works perfectly fine.

My config is as follows:

service tftp
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = nobody
server = /usr/sbin/in.tftpd
server_args = -s /svr/tftp
disable = no
}

the directory /svr/tftp permissions are 777:
drwxrwxrwx 3 nobody nobody 4096 Nov 14 10:32 svr

This thing should have full permissions as would anyone who wanted to write or read from that directory. I see nothing in the logs im really stumped on this. If the file is already in the directory I can read it all day long, I just cant make NEW files, can not put them, but I can do get's, I can only put to an existing file with permissions @777.

When I TOUCH the file ahead of time locally on the server, chmod it to 777 I can then send the file to the tftp server but thats not a valid work around, Cisco switches and routers cant log in, touch a file then send it.:mad:

See the 2nd response to that question [**_[COLOR="Blue"]here[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/664424").

---

### Post by West201 on 2012-11-15
Thanks for you help man.. 

It worked perfectly ! Cheers :)

---

### Post by SteveGodfrey on 2013-02-01
> **bab1 said:**
> See the 2nd response to that question [**_[COLOR="Blue"]here[/COLOR]_**]("https://bugs.launchpad.net/ubuntu/+source/tftp-hpa/+bug/664424").

Thanks Bab1, worked a treat :D

---

