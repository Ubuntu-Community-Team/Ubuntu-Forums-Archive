---
title: "Access your Bonjour printer over VPN from your iOS device"
date: 2019-02-20
forum: General Help
---

### Post by fatih3 on 2019-02-20
[FONT=arial]Hey,

I am trying to setup on my server OpenVPN with BIND9 to be able to print over my iOS Device on the way. I found a tutorial but have some problems with understanding it.
The tutorial is here: [http://theriom.com/Access-your-Bonjour-printer-over-VPN-from-your-iOS-device](http://theriom.com/Access-your-Bonjour-printer-over-VPN-from-your-iOS-device)

As some links are not working on the tutorial page i had to search for alternates which had no result.

It says:
> *[COLOR=#404040]Bonjour helps to resolve a hostname in the same way as your hosts file and dns. Which means we can [/COLOR][I]fake*[COLOR=#404040] Bonjour responces using out of the box DNS. The clever people at Apple have already figured this out and made it easy for us, they call it [/COLOR][Wide-Area Bonjour]("http://www.dns-sd.org/")[COLOR=#404040], and it was intended to make Bonjour services work across large coperate and education networks.[/COLOR][/I]

[/FONT]
[LIST=1]
[*][FONT=arial]Install your VPN Server of choice. You can use any VPN Server that allows you to push DNS server settings - which should be all of them. I used OpenVPN and installed it following this guide [https://openvpn.net/index.php/open-source/documentation/howto.html](https://openvpn.net/index.php/open-source/documentation/howto.html).[/FONT]
[*][FONT=arial]Next, I setup my own DNS Server. If you have an existing DNS server, you can skip this step. I choose to create my own .lan top level domain. This would be used as the default search domain. I used this guide [https://www.samculley.co.uk/how-to-install-configure-bind9-on-raspbian-wheezy/](https://www.samculley.co.uk/how-to-install-configure-bind9-on-raspbian-wheezy/) - replacing example.com with lan.

The URL above is not working so i set the regular way the bind9 like here [https://www.ionos.com/digitalguide/server/configuration/how-to-make-your-raspberry-pi-into-a-dns-server/](https://www.ionos.com/digitalguide/server/configuration/how-to-make-your-raspberry-pi-into-a-dns-server/)
I know it is for Raspberry Pi as it should be configurated on a Raspberry Pi too.
[/FONT]
[*][FONT=arial]I changed OpenVPN ppp config to use the new dns server. Edit /etc/openvpn/server.conf and change the following lines to point to your newly configured DNS server. 

```
[COLOR=#444444]**push**[/COLOR][COLOR=#444444] "[/COLOR][COLOR=#444444]**dhcp-option **[/COLOR][COLOR=#444444]**DNS **[/COLOR][COLOR=#444444]10[COLOR=#880000].0[/COLOR][COLOR=#880000].1[/COLOR][COLOR=#880000].200[/COLOR]"
[/COLOR][COLOR=#444444]**push**[/COLOR][COLOR=#444444] "[/COLOR][COLOR=#444444]**dhcp-option **[/COLOR][COLOR=#444444]**DOMAIN **[/COLOR][COLOR=#444444]**lan**[/COLOR][COLOR=#444444]"[/COLOR]
```

where [COLOR=#444444]10[/COLOR][COLOR=#880000].0[/COLOR][COLOR=#880000].1[/COLOR][COLOR=#880000].200[/COLOR] is the IP address of my DNS server (Ubuntu Server), and lan (the default seach domain) is my top level domain. You’ll need to restart your VPN server to use the new settings. I choose to only use the DNS server for VPN clients, but you could configure your DHCP server to use this DNS server for all client.[/FONT]
[*][FONT=arial]Add mDNS settings to you DNS hosts file.
Add a host (A Record) for you printer, for example (for me this was in /etc/bind/zones/db.lan[COLOR=#404040]):
```
printer[COLOR=#880000].lan[/COLOR][COLOR=#444444].    [/COLOR][COLOR=#444444]**IN**[/COLOR][COLOR=#444444]**A**[/COLOR][COLOR=#444444]       10[/COLOR][COLOR=#880000].0[/COLOR][COLOR=#880000].1[/COLOR][COLOR=#880000].202[/COLOR]
```

After this I installed the Wide-Area Bonjour SDK and run the code on Windows command line:

```
dns-sd -Z _ipp._tcp,_universal
```

The output which has been set correctly like in Tutorial should be like below:

```
; To direct clients to browse a different domain, substitute that domain in place of '@'lb._dns-sd._udp         IN      PTR     @


_ipp._tcp                        PTR     Brother\032MFC-L2710DW\032series._ipp._tcp
_universal._sub._ipp._tcp       PTR     Brother\032MFC-L2710DW\032series._ipp._tcp


Brother\032MFC-L2710DW\032series._ipp._tcp        SRV     0 0 631 printer.lan
Brother\032MFC-L2710DW\032series._ipp._tcp      TXT     "txtvers=1" "qtotal=1" "pdl=application/octet-stream,image/urf,image/pwg-raster" "rp=ipp/print" "note=" "ty=Brother MFC-L2710DW series" "product=(Brother MFC-L2710DW series)" "adminurl=http://BRWD46A6A54D76A.local./net/net/airprint.html" "priority=25" "usb_MFG=Brother" "usb_MDL=MFC-L2710DW series" "usb_CMD=PJL,HBP,URF" "Color=F" "Copies=T" "Duplex=T" "Fax=T" "Scan=T" "PaperCustom=T" "Binary=T" "Transparent=T" "TBCP=F" "rfo=ipp/faxout" "URF=W8,CP1,IS4-1,MT1-3-4-5-8,OB10,PQ3-4-5,RS300-600-1200,V1.4,DM1" "kind=document,envelope,label,postcard" "PaperMax=legal-A4" "TLS=1.2" "UUID=e3248000-80ce-11db-8000-3c2af43a6a91" "print_wfds=T" "mopria-certified=1.3"
```
[/COLOR][/FONT]
[/LIST]
[FONT=arial][COLOR=#404040]
I think this has to be add to [/COLOR][/FONT][COLOR=#404040][FONT=monospace]/etc/bind/zones/db.lan

[/FONT][/COLOR][FONT=arial][COLOR=#404040]My first Problem is that I can not bind DNS Name as "lan" and get this error:
[/COLOR][/FONT]```

   Loaded: loaded (/lib/systemd/system/bind9.service; enabled)
  Drop-In: /run/systemd/generator/bind9.service.d
           &#9492;&#9472;50-insserv.conf-$named.conf
   Active: failed (Result: exit-code) since Wed 2019-02-20 22:11:45 GMT; 1s ago
     Docs: man:named(8)
  Process: 29049 ExecStop=/usr/sbin/rndc stop (code=exited, status=1/FAILURE)
  Process: 29044 ExecStart=/usr/sbin/named -f -u bind (code=exited, status=1/FAILURE)
 Main PID: 29044 (code=exited, status=1/FAILURE)


Feb 20 22:11:45 debian-cups named[29044]: using 1 UDP listener per interface
Feb 20 22:11:45 debian-cups named[29044]: using up to 4096 sockets
Feb 20 22:11:45 debian-cups named[29044]: loading configuration from '/etc/bind/named.conf'
Feb 20 22:11:45 debian-cups named[29044]: /etc/bind/named.conf.local:16: zone '.lan': is not a valid name
Feb 20 22:11:45 debian-cups named[29044]: loading configuration: failure
Feb 20 22:11:45 debian-cups named[29044]: exiting (due to fatal error)
Feb 20 22:11:45 debian-cups systemd[1]: bind9.service: main process exited, code=exited, status=1/FAILURE
Feb 20 22:11:45 debian-cups rndc[29049]: rndc: connect failed: 127.0.0.1#953: connection refused
Feb 20 22:11:45 debian-cups systemd[1]: bind9.service: control process exited, code=exited status=1
Feb 20 22:11:45 debian-cups systemd[1]: Unit bind9.service entered failed state.

```[FONT=arial][COLOR=#404040]
[/COLOR][/FONT]

---

### Post by QIII on 2019-02-20
What OS are you using on your Pi?

---

### Post by fatih3 on 2019-02-21
Tests are running local on Ubuntu, on VM Debian and on Pi Raspian.

---

