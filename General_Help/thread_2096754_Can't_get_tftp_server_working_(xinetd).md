---
title: "Can't get tftp server working (xinetd)"
date: 2012-12-20
forum: General Help
---

### Post by redox000 on 2012-12-20
I am trying to get a very simple tftp server working. I followed the guides at several websites, including [http://icesquare.com/wordpress/how-to-setup-tftp-on-ubuntu/](http://icesquare.com/wordpress/how-to-setup-tftp-on-ubuntu/) and [http://mohammadthalif.wordpress.com/2010/03/05/installing-and-testing-tftpd-in-ubuntudebian/](http://mohammadthalif.wordpress.com/2010/03/05/installing-and-testing-tftpd-in-ubuntudebian/) , but I haven't been able to get a tftp server working.

The xinetd service is running (I know this because I do a ps -A | grep xinetd and see it), but I don't see tftp in netstat -na | grep LIST | grep 69. In other words, xinetd is running but I don't see the tftp server. I tried connecting to the server from my Windows tftp client but it failed, so I know for sure it's not running.

My /etc/xinetd.d/tftp config file looks like this:

```
service tftp
{
protocol = udp
port = 69
socket_type = dgram
wait = yes
user = nobody
server = /usr/sbin/in.tftpd
server_args = /tftpboot
disable = no
}
```

---

### Post by redox000 on 2012-12-21
Ok, after a couple more hours of playing around, I haven't made much progress. I tried running /usr/sbin/in.tftpd using the --foreground option, but it still closes right away. So maybe there is something wrong with my in.tftpd file? Can anyone offer any help? If not, is there a better forum I can post to?

---

