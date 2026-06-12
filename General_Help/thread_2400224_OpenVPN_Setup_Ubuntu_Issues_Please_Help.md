---
title: "OpenVPN Setup Ubuntu Issues Please Help"
date: 2018-09-04
forum: General Help
---

### Post by ace1012 on 2018-09-04
I need help setting up direct connect VPN without an internet connection. I am a beginner and don't know much about linux. It's been a real struggle using the terminal. :? But I'm working on bettering. Here is where I'm at. 

[COLOR=#000000][FONT=&amp]sudo dpkg -R -i /home/user/nmo[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp](Reading database ... 129036 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Preparing to unpack .../nmo/liblzo2-2_2.06-1_amd64.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Unpacking liblzo2-2:amd64 (2.06-1) over (2.06-1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Preparing to unpack .../libopenconnect1_3.15-0ubuntu2_amd64.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Unpacking libopenconnect1 (3.15-0ubuntu2) over (3.15-0ubuntu2) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Preparing to unpack .../libpkcs11-helper1_1.09-1_amd64.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Unpacking libpkcs11-helper1:amd64 (1.09-1) over (1.09-1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Preparing to unpack .../network-manager-openconnect_0.9.4.0-0ubuntu1_amd64.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Unpacking network-manager-openconnect (0.9.4.0-0ubuntu1) over (0.9.4.0-0ubuntu1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Preparing to unpack .../openconnect_3.15-0ubuntu2_amd64.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Unpacking openconnect (3.15-0ubuntu2) over (3.15-0ubuntu2) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Preparing to unpack .../openvpn-as-2.5.2-Ubuntu16.amd_64.deb ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Upgrade detected (debian)...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Unpacking openvpn-as (2.5.2-Ubuntu16) over (2.5.2-Ubuntu16) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Setting up liblzo2-2:amd64 (2.06-1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**dpkg:**dependency problems prevent configuration of libopenconnect1:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] libopenconnect1 depends on libproxy1 (>= 0.4.7).[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]**dpkg:**error processing package libopenconnect1 (--install):[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Setting up libpkcs11-helper1:amd64 (1.09-1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**dpkg:**dependency problems prevent configuration of network-manager-openconnect:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] network-manager-openconnect depends on libnm-glib-vpn1 (>= 0.7.999); however:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Package libnm-glib-vpn1 is not installed.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] network-manager-openconnect depends on libnm-util2 (>= 0.7.0); however:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Package libnm-util2 is not installed.[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]**dpkg:**error processing package network-manager-openconnect (--install):[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]**dpkg:**dependency problems prevent configuration of openconnect:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] openconnect depends on libopenconnect1; however:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  Package libopenconnect1 is not configured yet.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] openconnect depends on libproxy1 (>= 0.4.7); however:[/FONT][/COLOR]

[COLOR=#000000][FONT=&amp]**dpkg:**error processing package openconnect (--install):[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] dependency problems - leaving unconfigured[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Setting up openvpn-as (2.5.2-Ubuntu16) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Automatic configuration failed, see /usr/local/openvpn_as/init.log[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]You can configure manually using the /usr/local/openvpn_as/bin/ovpn-init tool.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Processing triggers for man-db (2.8.3-2) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Processing triggers for dbus (1.12.2-1ubuntu1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Processing triggers for libc-bin (2.27-3ubuntu1) ...[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] libopenconnect1[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] network-manager-openconnect[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp] openconnect[/FONT][/COLOR]

---

### Post by The Cog on 2018-09-04
All these problems are dependency problems - the software you are trying to install depends on other packages that are not yet installed. Some of those packages don't seem to be part of the normal Ubuntu repositories so I guess you have decided to use a different source of binaries? In this case I don't know how you will find the other packages. For instance, 
> dependency problems prevent configuration of libopenconnect1:
libopenconnect1 depends on libproxy1 (>= 0.4.7).
But Ubuntu comes with libopenconnect5 instead, and that depends on libproxy1v5  not libproxy1. Making a symbolic link to libopenconnect5 called libopenconnect1 might work but might not. And so on...

I would recommend using the Ubuntu repositories whenever possible. If you don't have direct internet access, pages like this will allow you to collect files that you can use offline, and they list the dependencies too.
[https://packages.ubuntu.com/xenial/libs/libopenconnect5](https://packages.ubuntu.com/xenial/libs/libopenconnect5)
You will likely end up with quite a collection of package files.

It occurs to me, how are you going to use a VPN without internet access? But maybe I misunderstand your requirement.

---

