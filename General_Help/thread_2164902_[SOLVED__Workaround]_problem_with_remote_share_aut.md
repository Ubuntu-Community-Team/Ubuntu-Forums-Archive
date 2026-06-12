---
title: "[SOLVED / Workaround] problem with remote share authentification (NTLM-related?)"
date: 2013-08-02
forum: General Help
---

### Post by julien-dal-col on 2013-08-02
Hello,

There is a CIFS (smb) share at work that I can't connect to (I can connect to other CIFS shares successfully).
This specific share doesn't support NTLMv2.
In Windows, I can't access this share neither until I modify settings to allow access to shares via NTLM when NTLMv2 is not supported.

I have no idea if all this NTLM thing even means anything in Ubuntu but I was wondering if this could be the reason why I cannot access the share in Ubuntu.

What do you guys think?
How could I troubleshoot this issue?

Thank you very much in advance for your help.
Best,
-J-

---

### Post by julien-dal-col on 2013-08-02
anyone?

---

### Post by Toz on 2013-08-02
How are you trying to mount the share? Which Ubuntu version/kernel?

The default securty mode for cifs mounts prior to kernel 3.8 was ntlm. This has changed to ntlmssp in > 3.8 kernels. A description of the security modes can be found in the "mount.cifs" man page or [http://manpages.ubuntu.com/manpages/raring/man8/mount.cifs.8.html]("http://manpages.ubuntu.com/manpages/raring/man8/mount.cifs.8.html").

You can specify which security mode to use on a command line mount to determine which one will allow the mount. Something like:
```
sudo mount -t cifs -o user=foobar,password=foobar,rw,sec=ntlm //x.x.x.x/share /mnt/mount_point
```

From the man page, valid options include:
> sec=
           Security mode. Allowed values are:

           ·   none attempt to connection as a null user (no name)

           ·   krb5 Use Kerberos version 5 authentication

           ·   krb5i Use Kerberos authentication and forcibly enable packet
               signing

           ·   ntlm Use NTLM password hashing (default)

           ·   ntlmi Use NTLM password hashing and force packet signing

           ·   ntlmv2 Use NTLMv2 password hashing

           ·   ntlmv2i Use NTLMv2 password hashing and force packet signing

           ·   ntlmssp Use NTLMv2 password hashing encapsulated in Raw NTLMSSP
               message

           ·   ntlmsspi Use NTLMv2 password hashing encapsulated in Raw
               NTLMSSP message, and force packet signing

Also, a potentially related bug report [here]("https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1113395").

---

### Post by julien-dal-col on 2013-08-05
Thank you:

I am running Ubuntu 13.04

I tried: 
sudo mount -t cifs -o user=[COLOR=#ff0000]*username*[/COLOR],password=[COLOR=#ff0000]*password*[/COLOR],rw,sec=ntlm //[COLOR=#ff0000]x.x.x.x/share[/COLOR] /mnt/[COLOR=#ff0000]mount_point

[/COLOR]I get:
mount: wrong fs type, bad option, bad superblock on //[COLOR=#ff0000]x.x.x.x/share[/COLOR],
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Should I use a different version of mount located on /sbin? (mount.fuse, mount.lowntfs-3g, mount.ntfs, mount.ntfs-3g, mountall, ???)

Best,
-J-

---

### Post by Toz on 2013-08-05
> mount: wrong fs type, bad option, bad superblock on //x.x.x.x/share,
missing codepage or helper program, or other error
(for several filesystems (e.g. nfs, cifs) you might
need a /sbin/mount.<type> helper program)
In some cases useful info is found in syslog - try
dmesg | tail or so

Is cifs-utils installed? Do you have an /sbin/mount.cifs file?

---

### Post by julien-dal-col on 2013-08-05
> **Toz said:**
> Is cifs-utils installed? Do you have an /sbin/mount.cifs file?

cifs-utils in not installed and I have no issue connecting to other cifs/smb shares (other than the one I am talking about in the 1st post).

There is no mount.cifs file in /sbin. Only mount.fuse, mountall and some shortcuts (mount.lowntfs-3g, mount.ntfs, mount.ntfs-3g)

Tx
-J-

---

### Post by Toz on 2013-08-05
> cifs-utils in not installed and I have no issue connecting to other cifs/smb shares (other than the one I am talking about in the 1st post).So how are you connecting to these shares? What program are you using?

---

### Post by julien-dal-col on 2013-08-06
> **Toz said:**
> So how are you connecting to these shares? What program are you using?

"files" (aka "Nautilus"): files->connect to server
then:
smb://[COLOR=#ff0000]*IP*[/COLOR]/[COLOR=#ff0000]*share*[/COLOR]

This work for other shares but not for the one that doesn't support NTLMv2 authentication. Again, it is the same thing in Windows until I enable support for NTLM authentication when NTLMv2 is not supported by the target. Actually, I think it is even the same thing in OSX. I know that back when 10.7 (Lion) came out, the IT guys provided a script to downgrade the authentication level in OSX or something...

I don't know if the problem is similar in Ubuntu... but my best guess is that it shouldn't be too different, right?

---

### Post by Toz on 2013-08-06
> "files" (aka "Nautilus"): files->connect to server
then:
smb://IP/share

This work for other shares but not for the one that doesn't support NTLMv2 authentication. Again, it is the same thing in Windows until I enable support for NTLM authentication when NTLMv2 is not supported by the target. Actually, I think it is even the same thing in OSX. I know that back when 10.7 (Lion) came out, the IT guys provided a script to downgrade the authentication level in OSX or something...
I believe nautilus uses gvfs to mount samba shares. Unfortunately, I can't find a way to get gvfs to change the security method.

> I don't know if the problem is similar in Ubuntu... but my best guess is that it shouldn't be too different, right? 
Can you install the **cifs-utils** package and try mounting manually as per the code in post #3? At least with this method we can change the security mode and test if we can connect.

---

### Post by julien-dal-col on 2013-08-06
> **Toz said:**
> Can you install the **cifs-utils** package and try mounting manually as per the code in post #3? At least with this method we can change the security mode and test if we can connect.

I'll do this :)
In the meantime the IT guy told me the solution to the problem is here:
[https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1113395](https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1113395)
I still have to read it and try to figure out what it means :s

---

### Post by Toz on 2013-08-06
> **julien-dal-col said:**
> I'll do this :)
In the meantime the IT guy told me the solution to the problem is here:
[https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1113395](https://bugs.launchpad.net/ubuntu/+source/cifs-utils/+bug/1113395)
I still have to read it and try to figure out what it means :s

Yes, thats exactly what I've been saying. However, to use this you need to manually mount with cifs-utils - it doesn't look like gvfs-mount (the default nautilus mount method) supports this. Or at least, I can't seem to find anything.

---

### Post by julien-dal-col on 2013-08-06
> **Toz said:**
> Yes, thats exactly what I've been saying. you know your stuff ;D thank you

 > **Toz said:**
> However, to use this you need to manually mount with cifs-utils - it doesn't look like gvfs-mount (the default nautilus mount method) supports this. Or at least, I can't seem to find anything.

Does this mean the share will have to be manually mounted each time I reboot? Or will I be able to setup shortcuts and bookmarks in Nautilus (aka "Files" in 13.04) as usual?

Tx
-J-

---

### Post by Toz on 2013-08-06
> **julien-dal-col said:**
> Does this mean the share will have to be manually mounted each time I reboot? 
Yes.
> Or will I be able to setup shortcuts and bookmarks in Nautilus (aka "Files" in 13.04) as usual?
I don't use Nautilus, so I don't exactly know the answer. However, you will still need to mount the share manually, either by running that command or adding an entry to /etc/fstab before its available for bookmarking.

---

### Post by julien-dal-col on 2013-08-07
Hi,

I read this tread (especially post#29)
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/510059](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/510059)

I then modified /etc/samba/smb.conf adding the following to the [globbal] section, (in the authentication subsection):
> client ntlm auth = yes
client ntlmv2 auth = no

Then I was able to mount my share using > Files->Connect to server in Nautilus. bookmarks and shortcuts also works, even after reboot (the share is not automatically mounted at boot)

I am too ignorant to be sure, but my best guess is that it disables ntlmv2 and enables ntlm authentication in gvfs. This shouldn't be a big deal unless one tries to connect to a share that supports only ntlmv2 (and not ntlm). I don't even know if this exists

What do you think of this solution? Is this stupid (or dangerous) for some reason?

If so, I'll go back to your previous recommendation i.e. installing cifs-utils and mounting the share manually using a command line that specify the level of authentication (sec=ntlm)

Thank you very much one more time.
Best,
-J-

For some reason it doesn't work if I don't add the second line (the one disabling ntlmv2?). My best guess is that if ntlmv2 is still enabled (default situation) gvfs will no try to authenticate via ntlm on servers that don't support ntlmv2.
It would be nice to have a way to setup something like in windows7 "use ntlmv2 if negociated" (ntlm otherwise)

---

### Post by Toz on 2013-08-07
Nice find. I did not know that making changes to /etc/samba/smb.conf would affect how nautilus mounts samba shares. There is nothing wrong with this method and it allows you to continue mapping as you did before. Thanks for sharing.

---

### Post by Morbius1 on 2013-08-07
Problem is that it's still a bug. What happens when you want to authenticate to Windows Vista ( or beyond ) that uses ntlmv2 by default.

---

### Post by julien-dal-col on 2013-08-07
> **Morbius1 said:**
> Problem is that it's still a bug. What happens when you want to authenticate to Windows Vista ( or beyond ) that uses ntlmv2 by default.

You are right. In post #14I was wondering if such a situation would exist (I mostly connect to NAS or servers that support NTLM or both NTLM & NTLMv2).

Apparently the bug is very old (46 months) and I suspect nobody cares...

I see 2 options:
 - Either the developers of gvfs should implement a function to better deal with authentication protocols
 - Or someone could make a GUI that would take care of modifying smb.conf according to one's needs.

Of course, with the second option one would still be screwed if you need to connect to both an "NTLM-only" share and an "NTLMv2-only" share at the same time, and you don't want to use mount but only gvfs in both cases...

Anyway, I am not a developper and don't understand much of all that. This is just my 2 cents...
Best,
-J-

---

