---
title: "Unable to mount Mac OS Mavericks share via CIFS?"
date: 2014-03-08
forum: General Help
---

### Post by dtrumbell on 2014-03-08
Greetings,

I am trying to mount a Mac OS Mavericks share on my Ubuntu 12.04.4 server.  However, everything I've tried always returned the error:

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Here's what my /etc/fstab looks like:  (I've tried different variations on this as well)

//192.168.0.82/Media1 /media/Media1 cifs credentials=/home/[user]/.smbcredentials,iocharset=utf8,sec=ntlm 0 0

I've also followed this guide, especially around the SMB file sharing, for sharing this out on the Mavericks' side:

[http://support.apple.com/kb/HT5884](http://support.apple.com/kb/HT5884)

This problem is starting to drive me crazy.  Anyone else seen this?

Any help is greatly appreciated.

Thanks,
David

---

### Post by Morbius1 on 2014-03-08
I very rarely do this in this direction. It's the mac's accessing the Linux server in my set up.

It seems mavericks has changed a few things since they wrote their own smb. I hate to be a "try this" sort of poster but this seems to work for me:

>  //192.168.0.82/Media1 /media/Media1 cifs credentials=/home/[user]/.smbcredentials,iocharset=utf8,[COLOR=#0000cd]**sec=ntlmssp,nounix**[/COLOR] 0 0

---

### Post by dtrumbell on 2014-03-08
Thanks for the help, but I'm still getting the error.  I ran mount with verbosity turned up.  Here's the output:

$ sudo mount -a -vvv
mount: spec:  "//192.168.0.82/Media1"
mount: node:  "/media/Media1"
mount: types: "cifs"
mount: opts:  "credentials=/home/[user]/.smbcredentials,iocharset=utf8,sec=ntlmssp,nounix"
mount: external mount: argv[0] = "/sbin/mount.cifs"
mount: external mount: argv[1] = "//192.168.0.82/Media1"
mount: external mount: argv[2] = "/media/Media1"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,credentials=/home/[user]/.smbcredentials,iocharset=utf8,sec=ntlmssp,nounix"
mount.cifs kernel mount options: ip=192.168.0.82,unc=\\192.168.0.82\Media1,credentials=/home/[user]/.smbcredentials,iocharset=utf8,sec=ntlmssp,nounix,ver=1,user=[user],domain=[domain],pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

---

### Post by Morbius1 on 2014-03-08
Hm... Getting further out of my comfort zone...

I just ran the following from fstab:
```
//dmbp.local/dmbpshare /Test cifs username=[user],password=[passwd],uid=1000,sec=ntlmssp,nounix 0 0
```
And it mounted it just fine.

Maybe this is on the OSX end. 

Does the user you are using exist on the mac ?
Did you give that user access to the shared folder - System Preferences > Sharing > Shared Folders > Users ?
Did you set the sharing password for the user for that share - System Preferences > Sharing > Options > Account > check the on column for that user

---

### Post by dtrumbell on 2014-03-08
> **Morbius1 said:**
> 
Did you set the sharing password for the user for that share - System Preferences > Sharing > Options > Account > check the on column for that user


That fixed it.  Seems concerning that it's now storing my password in a less secure manner.

Anyway, thanks for all of your help here.  The next step seems to be to create a sharing specific account for shares.

---

### Post by Torsten_Lhr on 2014-05-24
> [COLOR=#000000][FONT=Ubuntu Mono]//dmbp.local/dmbpshare /Test cifs username=[user],password=[passwd],uid=1000,sec=ntlmssp,nounix 0 0[/FONT][/COLOR]

You are a lifesaver. That fixed my problem, too. Thanks a lot.

---

