---
title: "Trouble importing .ovpn file with Network Manager (GUI and CLI), and OpenVPN directly"
date: 2018-04-04
forum: General Help
---

### Post by geesh-so on 2018-04-04
The following **.ovpn** file with parts of identifying information obfuscated with "blah". I've been trying to connect using Ubuntu 16.04.

```

    client
    dev tun
    proto udp
    remote blah.blah.com
    port 52424
    resolv-retry infinite
    nobind
    persist-key
    persist-tun
    remote-cert-tls server
    tls-version-min 1.2
    verify-x509-name server_blahblahblah name
    cipher AES-256-CBC
    auth SHA256
    compress lz4
    verb 3
    <ca>
    -----BEGIN CERTIFICATE-----
    blahblahblah
    -----END CERTIFICATE-----
    </ca>
    <cert>
    -----BEGIN CERTIFICATE-----
    blahblahblah
    -----END CERTIFICATE-----
    </cert>
    <key>
    -----BEGIN RSA PRIVATE KEY-----
    blahblahblah
    -----END RSA PRIVATE KEY-----
    </key>
    <tls-crypt>
    -----BEGIN OpenVPN Static key V1-----
    blahblahblah
    -----END OpenVPN Static key V1-----
    </tls-crypt>

```

When I try to import this with **sudo nmcli connection import type openvpn file blah.ovpn** I get the following.

    ```
Error: failed to import 'blah.ovpn': configuration error: unsupported blob/xml element (line 92).
```

Line 92 is where you see **<tls-crypt>**.


When I try **sudo openvpn --config blah.ovpn** I get the following.


    ```
Options error: Unrecognized option or missing parameter(s) in blah.ovpn:15: compress (2.3.10)
```


Line 15 is **compress lz4**. When I comment this out and try again, I get the following.


    ```
Options error: Unrecognized option or missing parameter(s) in blah.ovpn:20: tls-crypt (2.3.10)
```


Line 20 is just in two lines after **-----BEGIN CERTIFICATE-----** in the **<ca>** tag, which seems odd.


I've looked online and while I've seen *similar* errors I've not seen anyone having these exact problems that I have.


I created the **.ovpn** file on my Raspberry PI using **pivpn**. The generated files work smoothly on both my Windows machine, and my Android device, just not Ubuntu.


Any ideas?

---

### Post by hpka on 2018-04-29
In the exact same circumstances, also using a PiVPN generated ovpn

---

