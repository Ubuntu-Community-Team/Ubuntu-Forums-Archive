---
title: "Windows network browsing"
date: 2005-10-28
forum: General Help
---

### Post by lean on 2005-10-28
I noticed that Windows Network browsing (samba), didn't work during the beta stage of Breezy.
But it still doesn't work in the final version! At least not for me. It comes up with a password dialog (Authentication Required), whenever I try to browse the Windows network (living at a dorm, lot of Windows computers connected in a non-organised manner).

Could I have set some preferences somewhere in my user files that could have given me this problem?
Could I have installed a package that breaks Windows Networking surfing?

Anybody else got this problem (searching didn't seem to show anything)

---

### Post by KingBahamut on 2005-10-28
Terminal level 

can you 

smbclient -L <hostname>

and get the share names availabe on the  machines youre trying to weight against on the network? 

assuming all of this as stated that you have samba samba-common and smbfs installed on your system.

---

### Post by rmjokers on 2005-10-28
I get the same behavior when I use Places->Network Servers.  I get asked for a password multiple times.  I keep clicking "cancel" and then it brings me to the browser window.  I can then click on Windows Network and I get nothing.  When it pops up the password window, it appears to be asking for a password to the domain master server.  If I remove my user name and click ok, it correctly lists all of the shares available.  However, it doesnt remember the setting (using no username or password) to browse the shares.  It keeps popping up this obnoxious password window.

I have a similar problem on my home machine.  I have an anonymous share that I cannot access because nautilus insists upon using a username and password every time.  It even locks up, freezing the entire desktop sometimes.  See

[http://ubuntuforums.org/showthread.php?t=71125]("http://ubuntuforums.org/showthread.php?t=71125")

for details.

If this feature is in such a sorry state at the moment, it should be turned off IMHO.  I suppose I should have filed a bug report weeks ago, but I assumed others had noticed it and that it would be a high priority thing to fix before the Breezy release.

---

### Post by lean on 2005-10-28
[QUOTE=rmjokers]  I suppose I should have filed a bug report weeks ago, but I assumed others had noticed it and that it would be a high priority thing to fix before the Breezy release.[/QUOTE]

He, my thought exactly... Incridebly it didn't get fixed. Anyone canonical care to explain if this is a 'must work' feature of Dapper?

---

### Post by mbeach on 2005-11-16
I have the exact same problem (I think).  I'm not trying to share files from my Ubuntu machine, I just want to browse the available workgroups and computers.

Running
```
smbclient -L host
```
prompts for a password, which I deal with by hitting the enter key.  I get a table of Sharename, Type and Comment for the computers in my workgroup, followed by a list of Workgroup, Master.  The only error I see is after the Header row of the Sharename, type, comment table, is:
```
Error returning browse list: NT_STATUS_ACCESS_DENIED
```
followed by
```
Anonymous login successful
```

I can manually mount a share using 
```

sudo mkdir /media/sharename
sudo mount //192.168.0.1/linux /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777

```

I've tried installing winbind, samba (previously only had samba-common) but still cannot browse the Windows network (made up of WinNT, WinXP, Win2000, Win2003 machines).

It isn't a show stopper because I can manually connect (or use fstab if I wanted to) but it would be extremely *fun* to be able to browse with Nautilus.

mb.

---

### Post by speedman on 2005-11-16
If you can connect to SMB shares by using "smbclient //ip_address_OR_hostname/share -U username%password", but you can't browse SMB shares with nautilus the following hack should solve your problem.

Edit /etc/gnome-vfs-2.0/modules/smb-module.conf and change this line:

smb: [daemon] libsmb

to read:

smb:    libsmb.so

HTH


Regards,

SM

---

### Post by prammy on 2005-12-06
[QUOTE=speedman]If you can connect to SMB shares by using "smbclient //ip_address_OR_hostname/share -U username%password", but you can't browse SMB shares with nautilus the following hack should solve your problem.

Edit /etc/gnome-vfs-2.0/modules/smb-module.conf and change this line:

smb: [daemon] libsmb

to read:

smb:    libsmb.so

HTH


Regards,

SM[/QUOTE]

Thanks a lot!!!! This helped me fix it :)

- Pramz

---

### Post by squibbon on 2005-12-06
good one. i guess this is the answer for my prayers.

---

### Post by scarter on 2005-12-22
There's a workaround that seems to avoid the "authentication required" dialog which pops up on some - but not all - of the Windows XP computers in the network:  In Ubuntu, click on Places | Network Servers.  I see all of the computers in the network, and can access them from this instance of Nautilis without trying to guess what username and password is being requested.  Any other way to access them from a file browser window seems to result in that darned endless loop.

_Five days later:_   Forget it.  This doesn't work all the time either.  The search for the elusive password is back.  Darn.

---

