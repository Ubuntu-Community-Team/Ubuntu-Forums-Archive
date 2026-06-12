---
title: "What is correct config to use user-pass for openvpn on ubuntu 21.04?"
date: 2021-11-24
forum: General Help
---

### Post by fairbird on 2021-11-24
[COLOR=#232629][FONT=-apple-system]I have this config

[/FONT][/COLOR]
```

proto tcp
remote server1.freevpn.me 80
connect-retry-max 3
connect-retry 3
resolv-retry 15
dev tun
client
proto tcp
remote server1.freevpn.me 80
connect-retry-max 3
connect-retry 3
resolv-retry 15
dev tun
/etc/openvpn/pass.txt
persist-key
persist-tun
nobind
verb 2
key-direction 1
```

[COLOR=#232629][FONT=-apple-system]And I have sent (pass.txt) file to /etc/openvpn .. Then I have given this command to run openvpn ..

```
[FONT=var(--ff-mono)]sudo openvpn --config /etc/openvpn/openvpn.ovpn[/FONT]
```[/FONT][/COLOR][FONT=-apple-system]

But I have got this error
[/FONT][FONT=-apple-system]
[/FONT]```
[FONT=-apple-system]Options error: Unrecognized option or missing or extra parameter(s) in /etc/openvpn/openvpn.ovpn:15: /etc/openvpn/pass.txt (2.5.1)
[/FONT][COLOR=#232629][FONT=Verdana][FONT=-apple-system]Use --help for more information.[/FONT][/FONT][/COLOR]
```[FONT=-apple-system]
[/FONT]
[COLOR=#232629][FONT=-apple-system][FONT=inherit]So How to solve the issue ?![/FONT]
[/FONT][/COLOR]

---

### Post by TheFu on 2021-11-24
I don't have 21.xx ... btw, support for 21.04 ends next month, so move the 21.10 ASAP.
However, according to the openvpn ovpn manpage, the line you want is:

```
auth-user-pass /etc/openvpn/login.cf
```
Be 100% certain that only root can access that file.

The manpage section:
```
       --auth-user-pass [up]
              Authenticate with server using username/password.  up is a file  contain&#8208;
              ing  username/password on 2 lines. If the password line is missing, Open&#8208;
              VPN will prompt for one.

              If up is omitted, username/password will be prompted from the console.

              The server configuration must specify an  --auth-user-pass-verify  script
              to verify the username/password provided by the client.

```
Check the manpage on your system to see if that has changed.

---

### Post by fairbird on 2021-11-24
Thank you .. That help me ... SOLVED

---

