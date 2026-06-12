---
title: "Is there any Open Text Socks Client alternative for Ubuntu?"
date: 2016-12-10
forum: General Help
---

### Post by ispoon on 2016-12-10
Is there a windows program alternative: Open Text Socks Client for ubuntu? 

I google but can't find any alternative so asking here if anyone know of such software for Ubuntu

Thanks in advance

---

### Post by HermanAB on 2016-12-10
Well, one way to get loads of UNIX stuff including multiple socks clients is to install Cygwin.

---

### Post by ispoon on 2016-12-10
I think you misunderstand my question. I am looking for opentext socks client for Ubuntu. The software only available in Windows. and I am looking for Ubuntu version or alternative version.

---

### Post by HermanAB on 2016-12-10
OK, as far as I can figure, OpenText is a Windows version of SSH.  

[http://connectivity.opentext.com/products/security-products.aspx](http://connectivity.opentext.com/products/security-products.aspx)

So, just use 'ssh' on Ubuntu.

---

### Post by ispoon on 2016-12-10
Its not SSH... unless I can use the following config file in ssh

In windows I feed a config file to it so can I use Remote Desktop to get in the servers from remote site

[HumSocks - General]
ProfileVersion=2
[HumSocks - Servers]
LoadBalancing=1
[HumSocks - Rules]
Action=1
[HumSocks - CRC]
Version=2
[HumSocks - Servers - Server 1]
Enable=0
IPAddress=xxx.xxx.xxx.xxx
Port=1080
Type=0
RemoteDNS=1
AuthenticationType=0
KerberosProtectionLevel=0
KerberosUseLoggedInCredentials=1
[HumSocks - Servers - Server 2]
Enable=0
IPAddress=xxx.xxx.xxx.xxx
Port=1080
Type=0
RemoteDNS=1
AuthenticationType=1
KerberosProtectionLevel=0
KerberosUseLoggedInCredentials=1
[HumSocks - Servers - Server 2 - User]
Name=name
Password=ABC
[HumSocks - Servers - Server 3]
Enable=0
IPAddress=xxx.xxx.xxx.xxx
Port=1080
Type=0
RemoteDNS=1
AuthenticationType=1
KerberosProtectionLevel=0
KerberosUseLoggedInCredentials=1
[HumSocks - Servers - Server 3 - User]
Name=name
Password=ABC
[HumSocks - Servers - Server 4]
Enable=0
IPAddress=xxx.xxx.xxx.xxx
Port=1080
Type=0
RemoteDNS=1
AuthenticationType=1
KerberosProtectionLevel=0
KerberosUseLoggedInCredentials=1


[HumSocks - Rules - Rule 1]
Enable=1
Type=1
Action=0
Name=xxx.xxx.xxx.xxx/24
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 2]
Enable=1
Type=1
Action=0
Name=xxx.xxx.xxx.xxx/24
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 3]
Enable=1
Type=1
Action=0
Name=xxx.xxx.xxx.xxx/32
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 4]
Enable=1
Type=0
Action=0
Name=C:\Program Files (x86)\Remote Desktop Connection Manager\RDCMan.exe
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 5]
Enable=1
Type=1
Action=0
Name=xxx.xxx.xxx.xxx/24
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 6]
Enable=1
Type=0
Action=0
Name=mstsc
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 7]
Enable=1
Type=0
Action=0
Name=mmc
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 8]
Enable=1
Type=0
Action=0
Name=xxx.xxx.xxx.xxx/24
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 9]
Enable=1
Type=1
Action=0
Name=xxx.xxx.xxx.xxx/24
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 10]
Enable=1
Type=1
Action=0
Name=xxx.xxx.xxx.xxx/24
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 11]
Enable=1
Type=1
Action=0
Name=xxx.xxx.xxx.xxx/24
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 12]
Enable=1
Type=0
Action=0
Name=C:\Users\ADMIN\Downloads\RDO\RemoteDesktops.exe
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 13]
Enable=1
Type=0
Action=0
Name=C:\Program Files (x86)\Remote Desktop Organizer\RDO.exe
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 14]
Enable=1
Type=0
Action=0
Name=C:\Users\ADMIN\Downloads\Devolutions.RemoteDesktopManagerFree.Bin.2.0.6.0\RemoteDesktopManagerFree.exe
StartPort=0
EndPort=0
[HumSocks - Rules - Rule 15]
Enable=1
Type=0
Action=0
Name=C:\Users\ADMIN\Downloads\mRemoteNG-Portable-1.72\mRemoteNG.exe
StartPort=0
EndPort=0

---

