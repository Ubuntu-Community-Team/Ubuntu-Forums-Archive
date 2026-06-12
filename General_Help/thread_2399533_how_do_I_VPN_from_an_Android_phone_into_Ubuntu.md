---
title: "how do I VPN from an Android phone into Ubuntu?"
date: 2018-08-26
forum: General Help
---

### Post by 777funk on 2018-08-26
I have a remote PC with Ubuntu on it and would like to access it. Is there a way to do this from an Android phone (and from another Ubuntu machine)?

I've never done anything with VPN so please excuse the simplistic question if this is one.
Thanks!

---

### Post by TheFu on 2018-08-27
ssh - use ssh-keys. There are lots of ssh clients which support this.  Don't use passwords over the internet.
sftp - this is ssh-based, but like FTP.   Lots of sftp/scp clients exist. Again, don't use passwords over the internet. It is best to block non-key access from outside IPs.
You can use ssh to setup a SOCKS proxy, which is an encrypted channel. I've never done this from Android. The ssh-tunnel would need to use ssh-keys, never passwords.

Do you see the trend?  The remote system needs  to have openssh-server installed and the router protecting it needs to have a TCP port open to the world that redirects to ssh on the machine.  I'd also recommend installing fair2ban, to block all the brute force attacks that happen.  If you don't use 22/tcp, most of those attempts won't happen. Use a very high port for ssh, perhaps 63022/tcp on the WAN and forward that to 22/tcp on your Linux machine.  That way, inside your LAN, 22/tcp is used, but from outside, you'll use 63022/tcp.

You can use openvpn of you want lots of protocols supported like CIFS, SMB, HTTP, VNC and others.  Don't use VNC without a full VPN. It isn't secure.  There are other VPN options and setting up an openvpn server is 100x harder than using ssh.  IMHO.
But _using_ openvpn from Android, once setup, is much easier.

---

