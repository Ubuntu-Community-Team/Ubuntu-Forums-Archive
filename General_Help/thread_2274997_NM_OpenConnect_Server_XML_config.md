---
title: "NM OpenConnect Server XML config"
date: 2015-04-23
forum: General Help
---

### Post by jgoguen on 2015-04-23
Using NetworkManager to connect to a Cisco AnyConnect VPN endpoint (so I've installed openconnect, network-manager-openconnect, network-manager-openconnect-gnome, and their dependencies), the first time I connect I have to specify the endpoint. After that, NetworkManager knows what endpoints are available, even ones I didn't originally specify, and it has friendly names for them. This comes from an XML file pushed from the server, but where does NetworkManager store this file?

---

### Post by jgoguen on 2015-04-28
I found this. In */etc/NetworkManager/system-connections/* there is a file with the name you give to the VPN connection. In that file there's the *[vpn-secrets]* section, which has the *xmlconfig* attribute. This attribute is the base64-encoded XML document from the server.

---

