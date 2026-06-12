---
title: "Easy file transfer between Win 10 and Studio 21.04 - how ?"
date: 2021-10-09
forum: General Help
---

### Post by greatbridge on 2021-10-09
For other reasons I have to use Windows for some tasks. Previously, when using Mint, the most effective way for me, personally, to transfer files between Windows and Mint was to use a product called Nitroshare. Now I also have Ubuntu Studio and can use Warpinator for file transfer between the two Linux computers, but I have found that Nitroshare is not supported in Studio 21.04. Is there other software, as easy for me to use as Nitroshare, that I can use for file transfer between Studio 21.04 and Win 10?

---

### Post by ActionParsnip on 2021-10-09
If you have openssh-server running on the Ubuntu system you can connect to the SFTP service from Windows using something like Filezilla (the Windows file manager isn't very good).
The Mint system and Ubuntu system can mount SFTP as a folder and makes file management this way super easy an will appear as a part of the local file system.

---

### Post by greatbridge on 2021-10-09
Thanks for the advice - however I cannot implement it because :
1. Setting up this server asks me to make choices the implication of which I don't understand, especially the security considerations of having any sort of file sever on my network, when there are mentally unwell people, worldwide, spending  their free time looking for ignoramuses like me.
2. It is, for me personally, difficult to use. My objective in having a computer is to be productive in certain ways - but needing to be an IT technical expert is not one of them. For example. my attempt to get Filezilla to transfer between Mint and a remote Windows 10 took over a month of my effort and even then I was advised that it was not secure.
3. I do think I know enough to know that Filezilla and FTP are deprecated by many 'advisers' who know a lot more than I do (but they also deprecate Nitroshare too - so what do I know?)

---

### Post by Morbius1 on 2021-10-09
Any reason you aren't using Samba?

I downloaded Ubuntu-Studio since I've never used it before and am running it in a live session without installing.

I installed samba ( sudo apt install samba )

I edited /etc/samba/smb.conf and added a share definition of the default user's Public folder at the end of the file:
```
[Public]
path = /home/ubuntu-studio/Public
read only = No
guest ok = yes
force user = ubuntu-studio
```

Saved the file and restarted smbd:
```
sudo service smbd restart
```

Then I went to Explorer in Win10 and specified the address and share name:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289252&stc=1[/IMG]

I have access to that share and added a file - with a misspelling:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289253&stc=1[/IMG]

I can also do that in reverse since I have a Win10 share share called "shared":
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289254&stc=1[/IMG]

---

### Post by ActionParsnip on 2021-10-09
> **greatbridge said:**
> Thanks for the advice - however I cannot implement it because :
1. Setting up this server asks me to make choices the implication of which I don't understand, especially the security considerations of having any sort of file sever on my network, when there are mentally unwell people, worldwide, spending  their free time looking for ignoramuses like me.
2. It is, for me personally, difficult to use. My objective in having a computer is to be productive in certain ways - but needing to be an IT technical expert is not one of them. For example. my attempt to get Filezilla to transfer between Mint and a remote Windows 10 took over a month of my effort and even then I was advised that it was not secure.
3. I do think I know enough to know that Filezilla and FTP are deprecated by many 'advisers' who know a lot more than I do (but they also deprecate Nitroshare too - so what do I know?)

```
 
sudo apt install openssh-server

```

The transfer between the server and client will be encrypted too. You can use your Ubuntu username and password to authenticate. You can set up SSH keys as authentication and disable password logins to secure the service. Yes FTP is awful. Do not use.

Filezilla is easy to setup. Just add a new site under the file menu and you can set it as SFTP.

---

### Post by kurt18947 on 2021-10-10
I took a little different path to sharing files between computers. Most SOHO routers have the capability to mount a USB drive installed in the router's USB port. Kind of a light duty NAS.

---

### Post by HermanAB on 2021-10-10
The Windows file browser supports Anonymous FTP, so that is always the easiest way to do file transfers with other machines, since you don’t have to install anything on the Windows side of the wire.

---

### Post by TheFu on 2021-10-10
> **kurt18947 said:**
> I took a little different path to sharing files between computers. Most SOHO routers have the capability to mount a USB drive installed in the router's USB port. Kind of a light duty NAS.

Most SOHO routers file sharing is full of security issues.  Google for them in your specific brand.  Routers should do 2 things.  Route and firewall.  They should not be used for wifi, storage sharing, reverse proxies, forward proxies, VPN, or any other 1-click option they have built in.  Just because there's an option to run something, that doesn't mean it is secure and doesn't negatively impact the total security of the router.  Security should be the primary consideration with any router.

WAN routers have different mandates than a LAN router.  If it is a LAN-only router, with no public IP or connection to a modem, then things are different. Go crazy.  I've seen LAN-only routers that have DLNA servers built in.  Go for it.

Many things are possible. Whether each/any is a good idea or not is judgement.
[https://www.zdnet.com/article/backdoor-account-discovered-in-more-than-100000-zyxel-firewalls-vpn-gateways/](https://www.zdnet.com/article/backdoor-account-discovered-in-more-than-100000-zyxel-firewalls-vpn-gateways/)
[https://routersecurity.org/RouterNews.php](https://routersecurity.org/RouterNews.php)
[LIST]
[*]A TP-Link router was hacked for years
[*]Hacked MikroTik routers used in HUGE botnet
[*]An Asus router offers nothing but bugs
[*]Here we go again - lots of old and vulnerable routers
[*]Cisco Will Not Patch Critical RCE Flaw Affecting End-of-Life Business Routers
[*]Bombshell revelation about Ubiquiti
[/LIST]

IMHO. There are other opinions.  Please be careful out there with routers.  It is very hard to have a secure router at any level these days.  The main issue is unpatched or misconfigured routers.  If your router hasn't been patched in the last month, chances are it is vulnerable (and KNOWN as vulnerable) to some remote attack.

---

### Post by HermanAB on 2021-10-11
BTW, FTP is not a bad protocol, you just need to use it with care.

---

