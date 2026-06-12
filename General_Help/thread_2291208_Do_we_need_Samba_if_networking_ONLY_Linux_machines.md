---
title: "Do we need Samba if networking ONLY Linux machines?"
date: 2015-08-18
forum: General Help
---

### Post by 777funk on 2015-08-18
I always thought of Samba as a bridge from Linux to Windows. What if there are NO Windows machines? Still need Samba?

---

### Post by matt_symes on 2015-08-18
Hi

NFS is the standard network file system on Linux. There are others as well such as sshfs.

You only really need samba if any devices only have that option as a networked filing system.

Kind regards

---

### Post by Bashing-om on 2015-08-18
777funk; Hello;

As Matt advises ^ . 

If you only want to copy files between 2 linux boxes, in the same house sharing a common router AND security is not an issue. I find this the easiest way to cp files 'tween two Lubuntus that share the same router/house (Morbius1) :
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449)

[INDENT][INDENT]easier does it better
[/INDENT][/INDENT]

---

### Post by SeijiSensei on 2015-08-18
Use NFS: [https://help.ubuntu.com/14.04/serverguide/network-file-system.html](https://help.ubuntu.com/14.04/serverguide/network-file-system.html)

---

### Post by Bucky Ball on 2015-08-18
Haven't used samba for years. :)

I use Filezilla and lately Gigolo. Both in the repos. Gigolo lets you mount the other shares in a number of ways: ssh, ftp, etc.

---

### Post by Morbius1 on 2015-08-18
It turns out that samba in an all Linux network or a Linux / OSX network can be made to work far easier than one with Windows in the mix. The only requirement is that all Linux machines have avahi-deamon running and it's related port open.

Once you have samba installed and a share created it can be as simple as connecting to each other with a:
```
pcmanfm smb://hostname.local
```
Which results in something like this:
[ATTACH=CONFIG]263923[/ATTACH]
Or if you want to get fancy about this you can add an avahi samba service file which makes it so you can do something like this when "Browse Network" is selected:
[ATTACH=CONFIG]263924[/ATTACH]
[COLOR=#0000cd] The "SMB Hostname" icon appears outside of the "Windows Network" icon because the Windows related "stuff" isn't being used.[/COLOR]

Instructions on how to create the avahi service file:  

**Create a file:
```
gksu gedit /etc/avahi/services/samba.service
```
** Add this content:

```

<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">SMB %h</name> ## Display Name
<service>
<type>_smb._tcp</type>
<port>445</port>
</service>
</service-group> 

```[COLOR=#0000cd][I]
Make sure there are no spaces in front of that first line in the file.[/I][/COLOR]

**Restart avahi:
```
sudo service avahi-daemon restart 


```
That's about it.

[COLOR=#0000cd]**EDIT**: In case you have religious restrictions about using Samba the exact same technique can be used with SSH.[/COLOR]

---

### Post by kurja on 2015-08-18
It is a nuisance that smb is what is available without the user installing any other software and through nautilus - and it doesn't seem to work so great for anyone.

---

### Post by QDR06VV9 on 2015-08-18
> **Morbius1 said:**
> It turns out that samba in an all Linux network or a Linux / OSX network can be made to work far easier than one with Windows in the mix. The only requirement is that all Linux machines have avahi-deamon running and it's related port open.

Once you have samba installed and a share created it can be as simple as connecting to each other with a:
```
pcmanfm smb://hostname.local
```
Which results in something like this:
[ATTACH=CONFIG]263923[/ATTACH]
Or if you want to get fancy about this you can add an avahi samba service file which makes it so you can do something like this when "Browse Network" is selected:
[ATTACH=CONFIG]263924[/ATTACH]
[COLOR=#0000cd] The "SMB Hostname" icon appears outside of the "Windows Network" icon because the Windows related "stuff" isn't being used.[/COLOR]

Instructions on how to create the avahi service file:  

**Create a file:
```
gksu gedit /etc/avahi/services/samba.service
```
** Add this content:

```

<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">SMB %h</name> ## Display Name
<service>
<type>_smb._tcp</type>
<port>445</port>
</service>
</service-group> 

```[COLOR=#0000cd][I]
Make sure there are no spaces in front of that first line in the file.[/I][/COLOR]

**Restart avahi:
```
sudo service avahi-daemon restart 


```
That's about it.

[COLOR=#0000cd]**EDIT**: In case you have religious restrictions about using Samba the exact same technique can be used with SSH.[/COLOR]

Nice How To! 
Thank you!

---

### Post by funkytwig2 on 2015-08-18
Samba became populer years ago for linking Linux boxes as it is a lot more secure than NFS.  I am sure there are other alternatives but vanilla NFS is probably to be avoided.

---

### Post by Bucky Ball on 2015-08-18
> **funkytwig2 said:**
> Samba became populer years ago for linking Linux boxes as it is a lot more secure than NFS.

Just wondering what this is based on. The debate continues. A lot more secure? Don't think so. :-k

---

### Post by HermanAB on 2015-08-19
NFS is trivial to configure - one line in one file - vs Samba that has a 3 inch thick book.  So the choice is obvious.

Apart from NFS, you can also use FTP, WebDAV, SSH, Netcat - a veritable zoo of ad hoc network methods.  Usually, I don't bother with NFS even.  I just run sshd on each machine, put the host names in the hosts file and copy files around with scp, either from the command line, or with Konqueror or Dolphin.

---

### Post by SeijiSensei on 2015-08-19
> **Bucky Ball said:**
> Just wondering what this is based on. The debate continues. A lot more secure? Don't think so. :-k

Considering that NFS enforces the very same permissions as the rest of any *nix system, I don't think so either.

---

### Post by matt_symes on 2015-08-19
Hi

NFS on a trusted network is fine.
NFS on an untrusted network requires NFSv4 and Kerberos with auth and encryption.
NFS over the Internet is just nuts.

Anyway, that's besides the point. If you trawl through the CVE database you will see both NFS and samba have had major security issues over the years. Most software has.

On my trusted LAN, I use both. Samba shares are exported ro and NFS share exported rw.

I use NFSv4 and Kerberos with auth only and I only set that up to really play with it. I wanted any machine and user able to access my NFS shares to be authenticated, not because I have any major security concerns but because I wanted to learn how to set a a KDC and admin server. I also wanted to set up a local DNS and NTP server and this sounded like a good coherent set of tasks to play around with.

Just chewing the cud here really :)

Kind regards

---

### Post by Morbius1 on 2015-08-19
Since this has become an NFS vs Samba argument I though I'd look at the original question again - in parts:
> **777funk said:**
> I always thought of Samba as a bridge from Linux to Windows.
Samba ( their own in-house version ) is now the default file sharing mechanism in Apple's OSX replacing AFP. Together with Microsoft that constitutes 95% of the world's desktop systems. Since many Linux distros now install the samba server packages by default the number increases marginally from that. In addition Android can do it as well as iOS.
> What if there are NO Windows machines? Still need Samba?         
I guess it depends on the definition of "need". I personally believe that KDE is an over-engineered mess. Do I personally believe that the Linux ecosystem needs KDE? Absolutely not. My view is irrelevant however since KDE appears to be alive and well.

So does an all Linux network need Samba? No.

---

### Post by 777funk on 2015-08-19
Lots of good replies. I'm not familiar with NFS but I'll look into it.

---

