---
title: "systemd problem"
date: 2019-12-07
forum: General Help
---

### Post by jgw on 2019-12-07
I got a notification that I should update my PIA VPN.  So, I downloaded it and then told it to update itself.  It then went to the terminal and started the update.  The first thing it did is ask me for my password.  I tried to enter it but I couldn't.  This happens when there is another quiery asking me to enter something.  In this case I can't find it so I can't enter it and also cannot update PIA.  I have no idea what to do to fix this.  I have checked everything I could to find what its waiting for but couldn't find anything. the notification, before the request for my password was: "Detected a previous systemd install - assuming systemd". 

I also thought I would run synaptic just to see what would happen.  I brought it up and entered my password with no problem at all so I went back and tried, again, to enter my password in the terminal to start the pia update.  Same problem.  The terminal simply ignored my (this) keyboard.  I then ran the terminal again and tried to enter something (without the update stuff) and that was just dandy.  So, for some reason I am locked out of even trying to update pia.  I now suspect that its a problem with the pia updater and will send them a little message but, just in case I will let this be in case anybody has any thoughts on this one. 

Thank you...................

---

### Post by TheFu on 2019-12-09
If the root issue is getting PIA working, then I can help.

PIA uses openvpn.  You can download and install the normal, packaged, openvpn, version.
Next you need to get from PIA the .ovpn client files. I have both the not-so-great-for-security 128-bit versions and the AES-256 versions.  I placed those into /etc/openvpn/AES-256/. 
I also use the crl.rsa.4096.pem CA files, for better security.  PIA has a guide on that.  After all, if we don't really care about security, then we'd just use the PIA proxies, right?  If you care enough to use the full VPN, then best to use the most encryption bits available, right?

The /etc/openvpn/ directory is locked down so only root can access it. You see why shortly.

```
# more Romania.ovpn 
client
dev tun
proto udp
remote ro.privateinternetaccess.com 1197
resolv-retry infinite
nobind
persist-key
persist-tun
cipher aes-256-cbc
auth sha256
tls-client
remote-cert-tls server
**auth-user-pass /etc/openvpn/login.cf**
comp-lzo
verb 1
reneg-sec 0
crl-verify crl.rsa.4096.pem
ca ca.rsa.4096.crt
disable-occ
```
is the client aes-256 config file that I use when I want to use an exit node ... in, er,  Romania.
See the login.cf file? That's something I did to make it so I didn't get hassled for VPN passwords.  It is 2 lines.
No userid= or password= stuff, just 2 lines:
```
{userid}
{password}
```
The openvpn manpage has more details, but it can be confusing. There are security considerations in doing it this way.  Don't want anyone on the system to see that file, so make it root:root and 600 permissions.

Basically, all these client-side files are the same, except the _remote_ line which says which DNS and port to use.

So we have openvpn and a client config file.   In a directory in my PATH, ~/bin/ , I have a number of scripts:
```
$ ls -F pia-*
pia-fix-files    pia-hong_kong.sh*  pia-japan.sh*      pia-stop.sh*         pia-turkey.sh*      pia-vancouver.sh*
pia-france.sh*   pia-india.sh*      pia-london.sh*     pia-Switzerland.sh*  pia-us-fl.sh*
pia-germany.sh*  pia-info           pia-singapore.sh*  pia-toronto.sh*      pia-us-midwest.sh*

$ more pia-london.sh 
/usr/sbin/openvpn  /etc/openvpn/AES-256/UK_London.ovpn &
```

Simple.  OpenVPN has to be run as root, so the command line is:
```
sudo pia-london.sh 
```

That's it.  No GUI. No trusting PIA with anything more than config files. You are using an openvpn binary from a trusted, Canonical/Debian source.

Want to stop the VPN?
```
$ more pia-stop.sh 
/usr/bin/sudo /usr/bin/killall /usr/sbin/openvpn

```
Simple.  The routes will be put back to what they were pre-VPN.

---

### Post by jgw on 2019-12-15
I contacted PIA and they told me to remove, and reinstall, pia so I went to their link and did that.  It fixed the problem.  

given the solution my problem was a known problem 

Thank you for the response - I will mark this one as solved

---

### Post by TheFu on 2019-12-15
When was the last time you got the PIA package and installed it?  Last year?

When openvpn gets updated next week, you get to do the same thing again, unless you miss that announcement.  By using the openvpn packages from Canonical repos, I'm assured that patches are part of the weekly update/upgrade process on the OS.

There is almost always a reason for doing things a specific way. Doing it the hard way isn't always without reasons.

---

