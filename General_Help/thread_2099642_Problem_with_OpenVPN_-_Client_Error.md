---
title: "Problem with OpenVPN - Client Error"
date: 2012-12-30
forum: General Help
---

### Post by leomoon on 2012-12-30
Hello,

I checked multiple tutorials on how to setup OpenVPN on Debian/Ubuntu/RaspberyPi. All of them are more or less the same but I get the same error on the client side with all of them. The part I don't get is that even if I turn off the linux server, the client will give the same error. Shouldn't the client say connection failure or something like that?

```

Sat Dec 29 23:39:50 2012 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables
Sat Dec 29 23:39:50 2012 Re-using SSL/TLS context
Sat Dec 29 23:39:50 2012 Control Channel MTU parms [ L:1541 D:138 EF:38 EB:0 ET:0 EL:0 ]
Sat Dec 29 23:39:50 2012 Socket Buffers: R=[8192->8192] S=[8192->8192]
Sat Dec 29 23:39:51 2012 Data Channel MTU parms [ L:1541 D:1450 EF:41 EB:4 ET:0 EL:0 ]
Sat Dec 29 23:39:51 2012 Local Options hash (VER=V4): '3514370b'
Sat Dec 29 23:39:51 2012 Expected Remote Options hash (VER=V4): '239669a8'
Sat Dec 29 23:39:51 2012 UDPv4 link local: [undef]
Sat Dec 29 23:39:51 2012 UDPv4 link remote: <ip.address.removed>:1194
Sat Dec 29 23:39:51 2012 TLS: Initial packet from <ip.address.removed>:1194, sid=7c1856aa 16021aeb
Sat Dec 29 23:39:57 2012 VERIFY ERROR: depth=1, error=self signed certificate in certificate chain: /C=CA/ST=BC/L=BBY/O=LeoMoon/OU=LMDEV/CN=LMDEV_CA/name=DEV/emailAddress=admin@leomoon.com
Sat Dec 29 23:39:57 2012 TLS_ERROR: BIO read tls_read_plaintext error: error:14090086:SSL routines:SSL3_GET_SERVER_CERTIFICATE:certificate verify failed
Sat Dec 29 23:39:57 2012 TLS Error: TLS object -> incoming plaintext read error
Sat Dec 29 23:39:57 2012 TLS Error: TLS handshake failed
Sat Dec 29 23:39:57 2012 TCP/UDP: Closing socket
Sat Dec 29 23:39:57 2012 SIGUSR1[soft,tls-error] received, process restarting
Sat Dec 29 23:39:57 2012 Restart pause, 2 second(s)

```
Here is the server.conf:
```

port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem
server 10.8.0.0 255.255.255.0
#cipher none
#cipher AES-128-CBC
#cipher AES-256-CBC
cipher BF-CBC
#comp-lzo
client-to-client
persist-key
persist-tun
status openvpn-status.log
verb 3
tun-mtu 1500
tun-mtu-extra 32
mssfix 1450
push "redirect-gateway def1"
push "dhcp-option DNS 192.168.50.1"
keepalive 5 30
#crl-verify /etc/openvpn/easy-rsa/keys/crl.pem

```
And here is the client.ovpn:
```

client
dev tun0
proto udp
remote <ip.address.removed> 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ns-cert-type server
#cipher none
#cipher AES-128-CBC
#cipher AES-256-CBC
cipher BF-CBC
#comp-lzo
verb 3
ca ca.crt
cert leomoon.crt
key leomoon.key

```

Can someone please tell me what I'm doing wrong?

---

### Post by leomoon on 2012-12-30
I just found something interesting. About two weeks ago, I made this work and obviously I generated a certificate back then. Something happened and I had to redo the server configuration. I did exactly the same steps but the variables were a bit different.

Now in the client error log that I pasted above, I saw the old variables instead of the new ones:
/C=CA/ST=BC/L=BBY/O=LeoMoon/OU=LMDEV/CN=LMDEV_CA/name=DEV/emailAddress=admin@leomoon.com

I deleted all the files @:
c:\Program Files (x86)\OpenVPN\config
And pasted the new ones. How come it still remembers the old cert n how can I remove it?

---

### Post by The Cog on 2012-12-30
It's definitely a certificates issue. All I can suggest is that you delete **all** the certifictes on both client and server, and start again with the certificate making.

---

### Post by leomoon on 2012-12-30
I installed the server OS and OpenVPN from scratch and regenerated new certificates. I also used a new computer as client to test it. But somehow it still remembers the damn old certificate. I don't know how's that possible!!!

---

### Post by leomoon on 2012-12-30
I formatted the server and reinstalled the OS, OpenSSL and OpenVPN. Generated new keys for server and client. Copied the client certificates over and when I connect the client, it still shows the very old certificate variables in the log.

Am I missing something here? How can it still show the old variables?

---

