---
title: "samba config file"
date: 2014-10-06
forum: General Help
---

### Post by Westley on 2014-10-06
Hi,

I've got a server I've been running for quite some time now. It is running Ubuntu 12.04.3. It is an at-home file server, that I was using for just some minor file sharing. I had a NAS drive that was doing the bulk of the file sharing. The NAS drive started failing, so I've moved everything over to my Ubuntu server.

The problem I'm having is that one of my original SAMBA shares is still accessible, but I can't find it in my smb.conf file. The reason I'm looking for it is because I'm having some issues with the new share I created since my NAS drive failed and I wanted to compare settings.

I'm running everything "stock". No compiling things myself, so I figured my smb.conf file should be in /etc/samba. When I look in that folder, I have an smb.conf file, but it has no mention of the "missing" share.

I tried stopping/starting smbd and nmbd hoping that the log file would list the location of the config file, but no luck on that.

When I run testparm on /etc/samba/smb.conf, these are the shares it lists:
Processing section "[Video]"
Processing section "[windrive250gb]"
Processing section "[iTunes]"
Processing section "[downloads]"

What is missing is a share called "da-parish". The share is visible from windows and when I do a smbclient -L.

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        pei             Disk
        Video           Disk
        windrive250gb   Disk
        iTunes          Disk
        downloads       Disk
        IPC$            IPC       IPC Service (replica server (Samba, Ubuntu))
        da-parish   Disk



Anyone have any clues?

Thanks,
Westley

---

### Post by bab1 on 2014-10-07
> **Westley said:**
> Hi,

I've got a server I've been running for quite some time now. It is running Ubuntu 12.04.3. It is an at-home file server, that I was using for just some minor file sharing. I had a NAS drive that was doing the bulk of the file sharing. The NAS drive started failing, so I've moved everything over to my Ubuntu server.

The problem I'm having is that one of my original SAMBA shares is still accessible, but I can't find it in my smb.conf file. The reason I'm looking for it is because I'm having some issues with the new share I created since my NAS drive failed and I wanted to compare settings.

I'm running everything "stock". No compiling things myself, so I figured my smb.conf file should be in /etc/samba. When I look in that folder, I have an smb.conf file, but it has no mention of the "missing" share.

I tried stopping/starting smbd and nmbd hoping that the log file would list the location of the config file, but no luck on that.

When I run testparm on /etc/samba/smb.conf, these are the shares it lists:
Processing section "[Video]"
Processing section "[windrive250gb]"
Processing section "[iTunes]"
Processing section "[downloads]"

What is missing is a share called "da-parish". The share is visible from windows and when I do a smbclient -L.

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        pei             Disk
        Video           Disk
        windrive250gb   Disk
        iTunes          Disk
        downloads       Disk
        IPC$            IPC       IPC Service (replica server (Samba, Ubuntu))
        da-parish   Disk



Anyone have any clues?

Thanks,
Westley

Look in /var/lib/samba/usershares.  If you find it there then you created the share via a GUI interface (right click etc.).  Most likely this share is a directory in your home directory.

---

### Post by Westley on 2014-10-07
Hi bab1,

Yep. Had a file in /var/lib/samba/usershares called da-parish.

Contents:
#VERSION 2
path=/media/WinDrive250GB/da-parish
comment=
usershare_acl=S-1-1-0:F
guest_ok=n

I must have created this share when I first built the machine and had a monitor attached to it.

That mystery is solved!

Even better, I figured out why ultimate problem wasn't a samba problem but an ownership problem. Changed the ownership on everything in my Downloads folder and all is working as should be.

Thanks for your help!
Westley

---

