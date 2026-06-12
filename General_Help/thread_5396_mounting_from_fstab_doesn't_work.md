---
title: "mounting from fstab doesn't work"
date: 2004-11-18
forum: General Help
---

### Post by sect2k on 2004-11-18
I'm trying to  auto mount some SMB shares (from win2k)  in fstab, but it doesn't work.

Mouting from the command line works fine.

This is my fstab entry:

//192.168.0.5/Inetpub  /mnt/inetpub  smbfs  rw,users,guest,fmask=0777,dmask=0777  0  0

I get a SMB Connection Failed error when clicking on the "inetpub" icon in the Computer folder.

I also tried cifs as fs, but i get the same results, works from command line, doesn't from fstab.

Thanks for any insights,

Mitja

---

### Post by sfw5000 on 2004-11-18
what command do you use when you mount from the command line? do you include the user name and password? iirc, you need to specify user name and password when mounting samba shares.

something like...

//192.168.0.5/Inetpub /mnt/inetpub smbfs rw user,uid=<user_name>,gid=users,password="your_pw" 0 0

Somebody else probably has better syntax, as that's just from memory -- but try searching google.com/linux -- it should  be a pretty basic thing.

---

### Post by sect2k on 2004-11-18
Hi!

Thanks, but that is not the problem. Since there is no username and password for the share, including "guest" in the options does the trick. I have, just to make sure, also tried  with username & password options and the result is the same.

Anyone else any ideas?

---

### Post by p!=f on 2004-11-18
It might not be the case but I can't mount SMB shares until I put the appropriate entry in /etc/hosts file so that IP address is "translated" to a hostname. 
Sounds wierd, right? Tell me... but I get the same error message as you do.

```

[~] > cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost
192.168.0.5   hostwithsmb.homenet hostwithsmb

```

Then try to put hostname instead of IP in /etc/fstab.

Also, try to list the host shares with smbclient command
```

smbclient -L hostwithsmb

```
to see available shares. Note that you still have to keep case sensitivity. InetPub differs from inetpub share name.

---

### Post by sect2k on 2004-11-18
Doesn't help either. (the hosts thing)

I can mount shares with mount command without problems, it's only mounting from fstab that's causing them.

---

### Post by p!=f on 2004-11-18
Hmmm... Do you have your share permissions on Samba server set to per user or per share?

---

### Post by Magneto on 2004-11-18
add a username=guest comment
//192.168.0.5/Inetpub /mnt/inetpub smbfs username=guest,rw,users,guest,fmask=0777,dmask=0777 0 0

---

### Post by sect2k on 2004-11-18
Nope, doesn't help either.

I use the same options for both methods (mount, fstab) and one works and the other one doesn't. So I assume options or lack of them are not the problem.

Any alternative methods to automount SMB shares at logon?

---

### Post by Magneto on 2004-11-18
[QUOTE=sect2k]Nope, doesn't help either.

I use the same options for both methods (mount, fstab) and one works and the other one doesn't. So I assume options or lack of them are not the problem.

Any alternative methods to automount SMB shares at logon?[/QUOTE]
 you could always add a script to rc2.d or .xinitrc or in gnome  under sessions  type your mount command but i think there's an option issue- its something easy too i bet

---

