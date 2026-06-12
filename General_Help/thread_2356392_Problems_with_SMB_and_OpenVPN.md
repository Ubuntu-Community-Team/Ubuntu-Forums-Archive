---
title: "Problems with SMB and OpenVPN"
date: 2017-03-22
forum: General Help
---

### Post by mark120 on 2017-03-22
Hi,

I have successfully setup a VPN tunnel between my windows 10 pc and my dedicated Ubuntu server.
I have setup samba and a shared folder on my remote server.
I cant seem to connect openvpn to samba and is why I am unable to view my remote shared folder on my windows pc.
I have read this openvpn manual explaining how to connect the two and tried to follow it, but still it won't work.
Extracted from the openvpn manual:

[COLOR=#003366][FONT=Arial][COLOR=#ff0000]For this example, we will assume that:[/COLOR][/FONT][/COLOR]

[LIST]
[*][COLOR=#ff0000]the server-side LAN uses a subnet of **10.66.0.0/24**,[/COLOR]
[*][COLOR=#ff0000]the VPN IP address pool uses **10.8.0.0/24** (as cited in the **server** directive in the OpenVPN server configuration file),[/COLOR]
[*][COLOR=#ff0000]the Samba server has an IP address of **10.66.0.4**, and[/COLOR]
[*][COLOR=#ff0000]the Samba server has already been configured and is reachable from the local LAN.[/COLOR]
[/LIST]
[COLOR=#003366][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#003366][FONT=Arial][COLOR=#ff0000]If you are running the Samba and OpenVPN servers on the same machine, you may want to edit the **interfaces** directive in the **smb.conf** file to also listen on the TUN interface subnet of **10.8.0.0/24**:[/COLOR][/FONT][/COLOR]
[INDENT][COLOR=#ff0000]**interfaces  = 10.66.0.0/24 10.8.0.0/24**[/COLOR][/INDENT][INDENT][B]

From the openvpn client log it says:
[/B]Set TAP-Windows TUN subnet mode network/local/netmask = 10.8.0.0/10.8.0.2/255.255.255.0 [SUCCEEDED]

So I added to smb.conf

[COLOR=#FF0000][B]interfaces  = 10.66.0.0/24 10.8.0.0/24

[/B][/COLOR][COLOR=#000000][B]Openvpn client is saying my assigned ip address is 10.8.0.2

But I am totally lost, if anyone can help me I would really appreciate it.[/B][/COLOR][COLOR=#FF0000][/COLOR][/INDENT]

---

### Post by TheFu on 2017-03-25
Would you consider a different alternative?  Using CIFS over a WAN is problematic, IME.

---

