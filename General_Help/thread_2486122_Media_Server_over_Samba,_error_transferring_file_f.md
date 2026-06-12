---
title: "Media Server over Samba, error transferring file from Windows 10"
date: 2023-04-20
forum: General Help
---

### Post by ecronic on 2023-04-20
Hi Guys,
I'm having issues with my setup. It's been running fine since more than a year and all of a sudden I'm unable to transfer files over LAN. It's not an issue of the file size like I've read on forums but even if the file is 2MB it still give me the below attached error. I can transfer if I'm connected over wifi network. To my knowledge this issue started ever since I renewed my ISP contract and got a replacement router. I've checked all my settings on the router and everything seems fine. There's nothing that is blocking the traffic over LAN as I can stream movies from my server to my client via Plex on the Windows PC.

So far I've tried:
1. Uninstalling Bitdefender Total Security (Client PC)
2. Disable Windows Firewall & Windows Defender
3. Network Reset (Client PC)
4. Disconnected Mapped drives and Reconnected after restart
5. Clean installed the network drivers

After each step I've restarted the laptop.

**My Server specs are:**
**HP Pro3500 G2 MT PC**
Processor: Intel(R) Core(TM) i5-3340 CPU @ 3.10GHz
Installed Physical Memory (RAM): 12.0 GB
RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06)
Qualcomm Atheros AR9287 Wireless Network Adapter (rev 01)

**My laptop specs are:**
**Alienware 14 R2**
Processor:    Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz, 2401 Mhz, 4 Core(s), 8 Logical Processor(s)
Installed Physical Memory (RAM): 16.0 GB
Killer E2200 Gigabit Ethernet Controller
Killer Wireless-N 1202 Network Adapter
Thanks[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAaMAAAAwCAYAAAC8EBWtAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAABBWSURBVHhe7Z1PT9vKFsBPUWPRJiBooopI5SKll qu Ap9C1ggpC6zZ8UCdVGxZdktugvUBSv2LCshFrDhK7C6am8j8VopqAoFkYRGDlLfOeOxM3Zsjx07cfJ6fpIF9mTG58zMOfPPHj968eLFL2AYhmGYDJmSfxmGYRgmMx795xf86h4swOX7x9aV6g0sb fg8nUBTOsK8gCl8yuYhzn3dfztn3tteHRWgs b09a1lRYsHd CUcPffujCHxjupb3zAupH8mTYSBlVHoEBNxvPoXGBJysdKO/fQb5iafWolof623loYVjh8BssrIrLfVCe1eEHLK09deeJ0P8e2pT X 57033Ng1nMa5lXPrIRsfIngX6C0HCr3OcqIsjBqS yrHPyuoqoEyc/s9UP4y7vAdQX8VyEAhi732Hp5axSX8Pjh8rvCe9i3Gs1b6OQtPwEAfap1kXl91Svy6DYbFD8SOXfhWslf2MhdQ/0H0IWlOHwB8ytWlJ18bd1/K0405WvTD/Ivxka 7781HSVTZ/9CkLk0 VfUvlEGUSpH5OBGBkZW00oiNMAUOF8BQuicg zK/KaRBRQ5acT33hzD1Az5BmF5 Fq8QX8qxwja4gkj7Bi/1e5/ dF2zixII8bAB e9cLePoHpdy3UCqC12YtzdWZVAPucKoL5/hncwC2Udx8oMQQr3/4twMEzx/hV/T9vzIK51YAl5/fp5M g unDH0PjNV1fgNtaT3/HcC4KcCnjOcfGHHQx9s3flsFmq58OfXyd/Gp4/QNA8fg7lDw2oiOxfkH2eTEN7ZoJ Te9 kZpzqCDa50oDjXQvjXlnwI6/1E4pEZyVubPArQrDcXeohHk33T2TejsN1y aPk3uHxJ6/94MUWZ3TprQzGkgKmCGGezcH3mrdhEDtqnXRm/A8UtOrdCxp6VByy0PDSPlMqBBtzYVHuHYWBl 5DvVaZqE Yr2DsOMlZM /rAAONlcF6nik6/xPp7IeO4BXPH3RMfGknlT1l/82ge6gcA8 868kpCIsoXbJ P4e4U69taB9ORVMnxU5ryHAm372ET5j o4bQ6Npa 0t5UfTRE8W Rwbx322/G8qVuv9kiRkbNv cAAjPwAWbXTNGTap34Z3Tn41MrPlX0sydwJ6 PPRc4ugGsCOc3UKpSwQ4AOSCsTOXDGyjjkLu1M CUxTDQ6ZeG/g40JdHA8i NbuSbVP5U9bcwP UAKumkFU2 cPs00TbNCo1VLYxXXQC00V4d1dv3sAn0H8LZ5qCjdmz ybn0iUK4f0tA1vINof5mifUAA7ambbiFYlWcuRFDeNmTOsJK7DNVZ8W/h/I2OmN1 I/8wpCFr9/gT3ksf40/jZGUX5Vb EOV4dDuuU5DfaOEBdqFub0r8ZtlLFi/IXMYrc0StFbbekeMeVncMsH80uvJpJE/g uXjv6EsfvDWnNw1iEsstVPhz7 KOpvIv109km2WWvDjLDtXsPjEMW h02I/0iFMP8WBx/7TYWB5UvPfscB TSdNbwsbPfPNYohfA1be3H2GLp9c9AExc BYVdqBXXOVcxpOvPho6NvTl51mFgR6q fy7AFuEHDLTvOICqUL9gL9amkqjNbPr4D46DkmjNOI38S6ZeG/tUbWNrKYTr90wOZ6ke9VOu/YDT6j6L Jik/vX1aU3WFdYyjNjySaPY9bIL9RyhRylcQ7N906Ow3HQaXLxX7HRN6j3YfzYjF OK6PJcYL02l52Y9GeK75nE0j4Y6RlNUA4GV4iSf3jQLojozcmTuJ3FGjU6/QfTvYI 2Czcb41D2ScsvefmLabAaTZ8Mg375otinPXVY KurNDwWke172Pj5DzEN1YVpdaTmo0MkAvybjlD7HQP53CSvv1nSa4xQEepB5VfVx0ytBbrbDaswxLGDyq72nn6ZaFZaohdhOJXpAUrrqP/QnMmI0emXWH9rncg47T09OFJ08ss59ZmqdK44MqBpKmcEm3L5GzhCLG B8yRhYrTyRbRPOf1W3G6DeWovthPjbt/T0DwzxQMhlnNF/VUddOXrws /JUUjXywGkC/l ps1SmOEPaj3s1i0CuLJG88CHVVsUQHkuQbvnDsd6qORmXJRgOuTn1Det2W7wn5Q/7rHMBlq/uj00 qPlfvcuk495tzWlfidI1 16bquHsvn1pRDpvqJOfU5gG0p33ED8rUS1O1plgjlr5NfDS9vA1x73ulJhE6 yPZpOU2jYkD7o KotfE15S/oz5/emldyWpsLOGK4c0ZurvLTla HPv WAuHyRcm/HrHli1B/JwneDohhGIbJHNfIiGEYhmGygBsjhmEYJnO4MWIYhmEyJ35jRBv5ycVpeppj6evkvmTFMAzDjAc8MmIYhmEyhxsjhmEYJnO4MWIYhmEyZ4reGl8SL0x9E5tAlu23mR06UBYvblnhpVfyssL0bi NJXojWF5nGIZhmChMFfe64suVtBXI58Vn0FzvuB5IKBw2oFAriY0c6eNSsOZ9R7gN8y fQJ22EtkoDfTxK4ZhGOb3ZgrAhPwre3 jx9DaLCibFXo HnUxLXaXddMfnsU3URiGYZjJZYr2djLX7qB8LKfp1FGN38ej tCFMwzDMEw4U7TZHn0P43LxBVzu5KCgfo/db4v0PnThDMMwDBPOVHk3bErNs0X6Skdske6mP3ywLdQZhmGY35Wpa/gJZftJuG3o 0ia2CK90hBbpNOXDuHUu2aUh5svMg25hXv6X0JkGIZh/p/hT0gwDMMwmcMvvTIMwzCZw40RwzAMkzlOY2Tsfk/vc9AMwzAME4PRj4z4ExQMw2SF6n9cPEChSu9VTjiB unIXv/JmaZb6Yx9ZTGqYyzjBOQfw2QG2kdxr/n72scY6D8hjVEHyscNKGeVWdTb0I3gcJRX3stARqxE6ka2S7sdGaASlH8PUJJx7UOrpxfl/nQsHfb3ylyb8Z7fQCnOS9Ie/fz2PTTCNuqNIF8w0fInkX6hRLk//ubwuwzzyx9duIZhl68HWi5YxjIcORcFuFx0v9YyCJnJn5SU9E/CBDRGZJANMM7ymWZUOCjj/j20D7zvYA0bui/mzemCs9Ftew0bnaoMFujzr3tgxbfSiFMh5f3lRrr/Li5Au3IrGgQbsRa5DXC9IdN/ wTgXdQGAdN/9wDNtzIubdS7deXST6S/1ku/fvIAs064Xr4ohOVPMv2iEXb/wuEVzMPT3kbGnvzRhYcz7PL1gr3zLRNaJ9PyfNIYd/kfwBBbvEXH2rPUA6YxDBI3RiP5BMVpCS43sZIPxAMapNUz9Etf9GTUOVaxjoVyUiGI/zHeXht QRsWZBreno x wPytVlofJIXRgX2WvOVPFw7Lxk/FhvVFrY9ziBR/oXxALkKgInGZ 248RjuTtU7k3EC3LxFB2rvX0ib6W4WIu7QgfrQxr1K3OYZ5vcru45J4//QS988KkDjyPpfL19SkuqXFHsjY3k/vPf1gQGFdbt 6sJ1DLt8PVR/QqE2B9d2 UlbLKP9WqM6yx5pdNgbfYXbN8kY7n8wXMb1nRVAG7NHllb6IQ2tr/yYpmfkWFAdvCb95P6V9MP8ok7D1x9Q3v9hySRDQ/Wn2Z7j/mtLx8qWcdr8j07Cxggr49A/QYEO6f3gPQ3qGZZhVunZudM33z Heu1WXsOCOb4Fc c5NMi4xNAV4 3k4RHk4UqkgXpsqvKQQebg2nVtnNDnXw57y05ljzWNIxsHLHOrAuKoZM0E84tsHCNttBsDNNyZVSyzT2r6eeiC2plRjVkjX0QC8ydt/QKIc3/zUw6gInu/unAtoyxfHIVtt7Fj0d Qdf9 DpcHaMtbXbhG 6uftSH/xsoHnX3r/c 05XsWS74zAoU3PwFOngm7F lD0Mg6SP42FNelf8P49Vobyu968cPTT8O/EphfL2dRBszH18/xdzOKriH6Y8eijfLOqDMRb 7BOHvi/FaX/3FwNUZ2pY9yUCtqMc6foPDcnxyzT/qtzRKYqPvSORbsWQnqTs9aD1UG2HFPnYwMWVmKTuFbBgGVbsT8w/x4bVV0Oi53noKB RB9GsfaLqoNd2K7qD /XontoOoB20HRKNSqO3LkGREnHm1HdYAG7SofNLRXPWP3Oos48vUTL38G1S YqPfHcsfesfNqRl/568KDGUX5CqpNmAdlVOFgNXaiEa3lPI5eZ99R/E84rffzONK29cX0TzC X2MeKL8BbUW lie Pv2k/pVQZUAuotd/GgmrI233NGQ0/xoVpzGiEYJd6aMcNHctWtVx/gSFuL8JcygbGYk49vx6Dtb0hVGxMjYyOIQuV7AC/oP3EfeS4P jAQv/LeW/7DmfN629A/uMNho0xVWPOY1TOr C3Jdez 76y11Az9GuY/490DDsukk9vy7q6n4fjqYpFWNwGXM8 XTo8mdQ/aISfH/UGxstZ0/IvvLXhQcxmvIV9wkYFYWis 9I/kdDtYWd1ID0HcLk19w/NP00/GsyzPez0Fq9szoXfdOQmvyPSfIHGMb5ExTi/r3pNfv4/NpTaWhudCsHNwcA8/shc8I mHAv5mHFgQVBa0vl/WZKPeMIiPy39ZrHPmwXnQ3pPQLkmlXT6Sljz 3jUzBXsdLSaaTyj4F35CzSD0EnX1LS1i8uPvc3XinlrwvXMarypVEF3SfGjIRA3D/EvhPL10GbvgXzQ 8BEpqy72NQ aOkn9i/JsX6cgNNixbWPV9k0OV/TJI1RuTEx/oTFHR/bBywJ2fLaGBPhGTuYa8T4XAZe3a0ftTX8/uHepI hX40L ZgnUOuLdWxURBrTiPA2G05C6JCtzhP83jLTzTKfvExj7D3Rg9uuMpaVMY2zDi9NaywNKfs9LxpxEkNvLJoG2fU2CefrD OM7XKt j8BnuoaDBuZxwmn02Aftr8Saifjgj3t xLdqAwf9zTKLpwm4zKVyKc3IG6jhEVnX3b stwX/ j4ufYDbwqG OA IPLT4Sk7y3/PuLqp8O/YaOpRWOtKabk2h/tjgmhy/94JGuMsNUe/ico0FBE hiGhkFPtPk 9RIA3b/uzHl/g/I6QPNjzxjFAqCyTkTrR61Vz PRpOcZOMPRcXqPwMS8mtm38/8e2jveNZWQ/MORRlMpv Xje2yUvfElFTq8jsaaRgA5TUhrCuW1HNTf9npGNHVzeQpQtPMO7wEHs3AXpbGmfP/Uk8 pH8rDImJN46WypgFzSrhePgc//SLkTyL9dES4v7AvHJ079uVZU9OFO2RRvgQ63OKq kRoPHT2LfQP9T82qCuOPPJSD2sqmBpbvLYnddv/CR1v/ETya9JPxb9GxU9/ydETaFXaUKg97StXXf7HgT8hwUSEKudgDmMy H/XT0c2 hcOv0Hxy8LEfgNt0uUfJ7gxYhgmG3BUsXRMj2tn9DRqUiZd/jGDGyOGYRgmc7gxYpjflK9fv8n//FlcfCH/Y5jhk/zR7pHx8JvvOp2B/jQNEeNhEYZhmEGZnMaIHkvlLd5/48aYCQU7DmXa90yeMsykMTmN0cXgW5yLZ9/lW859bzFPCgn0H3uqET7RwYRi/NUFo0LviUxg3WYYAPgfvDGAH50NPBQAAAAASUVORK5CYII=[/IMG]
Ecronic

---

### Post by TheFu on 2023-04-20
If you have issues with samba, perhaps posting the smb.conf file would be helpful?  Use the **testparm -s** to show it as the samba parser sees it.

We also need the EXACT versions of the server AND each client machine, since different clients support different smb protocol levels.  The higher the smb version supported, the better the security and performance will be.  Really old clients were deprecated in the default settings a few yrs ago to prevent terrible non-secure default setups.

In general, CIFS is a poor protocol to use for media streaming.  The kodi forums are pretty clear on this.  If you can, use NFS instead, assuming DLNA or some other streaming protocol cannot be used.

---

### Post by ecronic on 2023-04-21
> **TheFu said:**
> If you have issues with samba, perhaps posting the smb.conf file would be helpful?  Use the **testparm -s** to show it as the samba parser sees it.

We also need the EXACT versions of the server AND each client machine, since different clients support different smb protocol levels.  The higher the smb version supported, the better the security and performance will be.  Really old clients were deprecated in the default settings a few yrs ago to prevent terrible non-secure default setups.

In general, CIFS is a poor protocol to use for media streaming.  The kodi forums are pretty clear on this.  If you can, use NFS instead, assuming DLNA or some other streaming protocol cannot be used.

Thanks for replying.

**The output of my smb.conf file:**

```
# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb




[Movies]
    comment = All Movies
    path = /media/nasdrive2/movies
    read only = No




[TVShows]
    comment = All Shows
    path = /media/nasdrive2/tvshows
    read only = No
    valid users = @qbittorrent-nox
    write list = @qbittorrent-nox




[Torrent]
    comment = Torrents
    path = /media/nasdrive/torrent
    read only = No
    valid users = @qbittorrent-nox
    write list = @qbittorrent-nox




[Personal]
    comment = Personal
    path = /media/nasdrive/personal
    read only = No
    valid users = @qbittorrent-nox
    write list = @qbittorrent-nox




[r18data]
    comment = R18data
    path = /media/nasdrive/r18data
    read only = No
    valid users = @qbittorrent-nox
    write list = @qbittorrent-nox




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers



```

**Details of my server version:**
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:         22.04
Codename:     jammy

As for clients I only have 2 clients connecting to the server.

1. Nvidia Shield TV with Plex Client for streaming the media.
2. Alienware Laptop for copying the files to the media drives.

Details of the Windows 10 version on the Alienware Laptop attached.

Thanks
Ecronic

---

### Post by MAFoElffen on 2023-04-22
> 
The Network error 0x8007003B commonly occurs when you copy a file larger than 100 MB over a VPN connection

The size is actually anything over 5MB...

You Googled this error, so you know this is a "Windows specific" error, right? And if you did deeper, even though most of the answers say it has to do with VPN's, Anti-virus software, Firewalls... which those kinds of things could possibly affect that, most rules those out and still had that error. 

When members of Microsoft TechNet researched and looked into it: It really has to do with the versions of the SMB protocol versions being used.
RE: [https://social.technet.microsoft.com/Forums/windows/en-US/1208ca4a-47aa-451c-8aa7-04599527484c/windows-81-network-share-0x8007003b-error-copying-files?forum=w8itpronetworking](https://social.technet.microsoft.com/Forums/windows/en-US/1208ca4a-47aa-451c-8aa7-04599527484c/windows-81-network-share-0x8007003b-error-copying-files?forum=w8itpronetworking)

Please check and post the SMB protocol version level for your server and each client.

For a Windows Machine, using PowerShell:
```

Get-SmbConnection

```
For each Linux machine, in a terminal
```

sudo smbstatus

```
For each Mac OSX machine:
```

smbutil statshares  -a

```
Windows, along the way, disabled any support for SMB version 1. If you look in '/proc/mounts' does not contain a 'vers=' flag in the mount connection details, then assume that it is SMB1.

For Samba, to adjust for that, (you do not have this in yours posted above) in /etc/smb.conf, in the Global section, add these two lines:
```

[GLOBAL]
client min protocol = SMB2
client max protocol = SMB3

```
Then restart your Samba services:
```

sudo systemctl restart smb
sudo systemctl restart nmd

```
There are some other new changes for the newer versions of Samba that concern permissions... but that is outside of this error.

---

### Post by ecronic on 2023-04-22
Thanks for your input.

I'm reading through the post link you tagged in your reply. But haven't implemented the changes on my Windows 10 client mentioned.

 I have included the smb protocol version from both the server and the client machine I use.

> [COLOR=#000000]For a Windows Machine, using PowerShell:
Get-SmbConnection[/COLOR] **- This is the only Client I connect for transferring the files to the Ubuntu Server**

```
ServerName   ShareName UserName             Credential           Dialect NumOpens
----------   --------- --------             ----------           ------- --------
192.168.11.2 movies    ECRONIC-AW14\Ecronic ECRONIC-AW14\Ecronic 3.1.1   1       
192.168.11.2 personal  ECRONIC-AW14\Ecronic ECRONIC-AW14\Ecronic 3.1.1   1       
192.168.11.2 torrent   ECRONIC-AW14\Ecronic ECRONIC-AW14\Ecronic 3.1.1   1       
192.168.11.2 tvshows   ECRONIC-AW14\Ecronic ECRONIC-AW14\Ecronic 3.1.1   1       

```

> [COLOR=#000000]For each Linux machine, in a terminal[/COLOR]
 [B]- This is my Ubuntu Server's output

[/B]```
Samba version 4.15.13-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
102616  nasuserdev   nasuserdev   192.168.11.3 (ipv4:192.168.11.3:51407)    SMB3_11           -                    partial(AES-128-CMAC)

```

I have applied the below changes you mentioned and restarted the samba server as well. But still giving me the same error. As mentioned below my '/proc/mounts' didn't contain 'vers=' flag. So I updated my smb.conf file to have the min & max protocol.

> [COLOR=#000000]Windows, along the way, disabled any support for SMB version 1. If you look in '/proc/mounts' does not contain a 'vers=' flag in the mount connection details, then assume that it is SMB1.[/COLOR]

[COLOR=#000000]For Samba, to adjust for that, (you do not have this in yours posted above) in /etc/smb.conf, in the Global section, add these two lines:[/COLOR]
[COLOR=#000000]Code:
[GLOBAL]
client min protocol = SMB2
client max protocol = SMB3[/COLOR]
[COLOR=#000000]Then restart your Samba services:[/COLOR]
[COLOR=#000000]Code:
sudo systemctl restart smb
sudo systemctl restart nmd[/COLOR]


---

### Post by ecronic on 2023-04-26
> **MAFoElffen said:**
> The size is actually anything over 5MB...

You Googled this error, so you know this is a "Windows specific" error, right? And if you did deeper, even though most of the answers say it has to do with VPN's, Anti-virus software, Firewalls... which those kinds of things could possibly affect that, most rules those out and still had that error. 

When members of Microsoft TechNet researched and looked into it: It really has to do with the versions of the SMB protocol versions being used.
RE: [https://social.technet.microsoft.com/Forums/windows/en-US/1208ca4a-47aa-451c-8aa7-04599527484c/windows-81-network-share-0x8007003b-error-copying-files?forum=w8itpronetworking](https://social.technet.microsoft.com/Forums/windows/en-US/1208ca4a-47aa-451c-8aa7-04599527484c/windows-81-network-share-0x8007003b-error-copying-files?forum=w8itpronetworking)

Please check and post the SMB protocol version level for your server and each client.

For a Windows Machine, using PowerShell:
```

Get-SmbConnection

```
For each Linux machine, in a terminal
```

sudo smbstatus

```
For each Mac OSX machine:
```

smbutil statshares  -a

```
Windows, along the way, disabled any support for SMB version 1. If you look in '/proc/mounts' does not contain a 'vers=' flag in the mount connection details, then assume that it is SMB1.

For Samba, to adjust for that, (you do not have this in yours posted above) in /etc/smb.conf, in the Global section, add these two lines:
```

[GLOBAL]
client min protocol = SMB2
client max protocol = SMB3

```
Then restart your Samba services:
```

sudo systemctl restart smb
sudo systemctl restart nmd

```
There are some other new changes for the newer versions of Samba that concern permissions... but that is outside of this error.

Hi, any info my post above?

---

### Post by SeijiSensei on 2023-04-27
If your client machines can handle the DLNA protocol, minidlna is a quick and simple solution to media sharing. Doesn't need samba or anything else. 

[https://www.bananatronics.org/installation-and-configuration-of-minidlna-readymedia/](https://www.bananatronics.org/installation-and-configuration-of-minidlna-readymedia/)

Plex is another option, though I've never used it.

If the clients are Linux machines, or they run a version of Windows with the NFS client package, then NFS is by far the easiest and best solution for file sharing. The NFS client comes with the "Pro" versions of Windows.

---

### Post by ecronic on 2023-04-27
> **SeijiSensei said:**
> If your client machines can handle the DLNA protocol, minidlna is a quick and simple solution to media sharing. Doesn't need samba or anything else. 

[https://www.bananatronics.org/installation-and-configuration-of-minidlna-readymedia/](https://www.bananatronics.org/installation-and-configuration-of-minidlna-readymedia/)

Plex is another option, though I've never used it.

If the clients are Linux machines, or they run a version of Windows with the NFS client package, then NFS is by far the easiest and best solution for file sharing. The NFS client comes with the "Pro" versions of Windows.

Hi, thanks for your input.

Plex is actually the option I would like to use. Reason for this is because Plex allows my media to be shared across internet with just an account. No need of extra configurations on the server side, just adding the account I want to share the media with. I've not used minidlna but I don't think it offers such an option.

Clients - for only transfer of media is a single windows 10 laptop that I use only for transferring the media once it has downloaded to the laptop.

This is why I need to fix this issue.

Thanks
Ecronic

---

### Post by SeijiSensei on 2023-04-27
WinSCP is another possibility if all you want to do is transfer files.

[https://winscp.net/eng/index.php](https://winscp.net/eng/index.php) 

You'd need to run openssh-server on the server box. [https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/](https://www.cyberciti.biz/faq/ubuntu-linux-install-openssh-server/)

---

### Post by ajgreeny on 2023-04-27
I used to use Plex, now use Emby but would really prefer to be able to use Jellyfin, a fork of Emby created when Emby moved from Open Source to Closed Source.

Jellyfin works extremely well but regrettably does not (yet) have a client app for my LG Smart TV which is my main use of a media-server.
It will just about work using the web browser on the TV but is simply too much trouble so at present Emby is the best server for me.

I do also use minidlna mentioned above but there are several media file-types that do not play using that meaning I have to change them to alternatives; that unfortunately is just too much hassle so I only generally use it for audio, not video.

---

### Post by ecronic on 2023-04-29
I checked out Jellyfin installation and working on Youtube. It's a good solution for media sharing. I will definitely have a look into it. Though my issue isn't with the Media Server.

---

### Post by ecronic on 2023-04-29
Hi Everyone,

Thank you very much for you time and replies. Ultimately I'm not sure what solved the issue.

I did the following steps and possibly one of them have helped:
1. Update Network drivers manually
2. Update Windows 10 Client & Ubuntu Server
3. Reset Router settings
4. Network Reset on Windows Client
5. Switch LAN cables between Ubuntu Server & Windows Client - recommend on one of the Windows Forums

My network is back to normal, I can transfer files again from Client to Server again without any issues.

Thanks
Ecronic

---

### Post by ajgreeny on 2023-04-30
**Great news!**

Please now mark the thread as **SOLVED** from the Thread Tools menu at the top of the thread.
It's a great help to other users searching g the forum.

---

