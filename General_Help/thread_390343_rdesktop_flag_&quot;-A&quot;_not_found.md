---
title: "rdesktop flag &quot;-A&quot; not found"
date: 2007-03-21
forum: General Help
---

### Post by srunni on 2007-03-21
Hi,

I've been trying to get Seamless Virtualization to work on my Kubuntu 6.06 install, with VMware Server and Windows XP Pro SP2. However, when I run the command ```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" localhost:3389 -u administrator -p password
``` in Konsole, I get ```
rdesktop: invalid option -- A
``` Does anyone know why I'm getting this?

Thanks in advance for the help!!!!!

---

### Post by scxtt on 2007-03-21
there is no "-A" option for rdesktop, according to **man rdesktop** ... what is that flag supposed to do?

---

### Post by statictonic on 2007-03-21
What version of rdesktop do you have?


from rdesktop man page

       -A     Enable  SeamlessRDP. In this mode, rdesktop creates a X11 window
              for each window on the server side. This mode requires the Seam&#8208;
              lessRDP   server   side   component,  which  is  available  from
              [http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/).  When using this option, you
              should specify a startup shell which launches the desired appli&#8208;
              cation through SeamlessRDP.

              Example: rdesktop -A -s ’seamlessrdpshell notepad’.

---

### Post by scxtt on 2007-03-21
on edgy:
```
[font=courier]:> aptitude show rdesktop
Password:
Package: rdesktop
State: installed
Automatically installed: no
**Version: 1.4.1-1.1**
Priority: optional
Section: x11
Maintainer: Tomas Fasth <tomfa@debian.org>
Uncompressed Size: 397k
Depends: libc6 (>= 2.3.4-1), libssl0.9.8 (>= 0.9.8a-1), libx11-6
Description: RDP client for Windows NT/2000 Terminal Server
 rdesktop is an open source client for Windows NT/2000 Terminal Server, capable of natively speaking its Remote Desktop
 Protocol (RDP) in order to present the user's NT/2000 desktop. Unlike Citrix ICA, no server extensions are required.[/font]
```

---

### Post by srunni on 2007-03-21
I have version 1.4.1 of rdesktop. Do I need to get a newer version for SeamlessRDP?

---

### Post by statictonic on 2007-03-21
> **scxtt said:**
> on edgy:
```
[font=courier]:> aptitude show rdesktop
Password:
Package: rdesktop
State: installed
Automatically installed: no
Version: 1.4.1-1.1
Priority: optional
Section: x11
Maintainer: Tomas Fasth <tomfa@debian.org>
Uncompressed Size: 397k
Depends: libc6 (>= 2.3.4-1), libssl0.9.8 (>= 0.9.8a-1), libx11-6
Description: RDP client for Windows NT/2000 Terminal Server
 rdesktop is an open source client for Windows NT/2000 Terminal Server, capable of natively speaking its Remote Desktop
 Protocol (RDP) in order to present the user's NT/2000 desktop. Unlike Citrix ICA, no server extensions are required.[/font]
```

I think it was added in version 1.5 I believe, if the original poster could please reply as well, because that could very well be the problem you are having.

---

### Post by srunni on 2007-03-21
Well, it's working for sxctt, and he has 1.4.1 as well.

---

### Post by statictonic on 2007-03-21
> **srunni said:**
> I have version 1.4.1 of rdesktop. Do I need to get a newer version for SeamlessRDP?

1.5 should work.

[http://www.rdesktop.org/](http://www.rdesktop.org/)

Available on there, you could also try apt-get install rdesktop or apt-get update to see if that'll update it, but I'm not sure it will.

---

### Post by scxtt on 2007-03-21
it doesn't work for me, i'm not using any "seamless desktop" ... i was just pointing out that rdesktop1.4.1-1.1 does NOT have a -A option, which is why you're getting the error you opened the thread w/ :)

---

### Post by statictonic on 2007-03-21
> **srunni said:**
> Well, it's working for sxctt, and he has 1.4.1 as well.

Well I assume your trying to get seamlessrdp working, he mentioned that he did not have -A listed as an option in the man pages on 1.41, that is the option that enables seamless RDP, at least on 1.5, I don't have a install of 1.41 to check with right now.

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

Is that what your trying to do right now?  I got that setup already with version 1.5 of rdesktop, if you need any further help with it just ask

---

### Post by srunni on 2007-03-21
I guess I misinterpreted that. I thought he said he DID have it in his man pages. Anyway, I tried out version 1.5, and I'm at least not getting that error, but I am getting an error with the Windows application not showing up like it should. It just gives me the XP desktop without the explorer.exe shell. Any ideas?
EDIT: Never mind, I got it. I was just locking the XP Administrator account, instead of logging out of it. When I did, the SeamlessRDP program worked just fine. Thanks again for all the help!

---

### Post by statictonic on 2007-03-21
> **srunni said:**
> I guess I misinterpreted that. I thought he said he DID have it in his man pages. Anyway, I tried out version 1.5, and I'm at least not getting that error, but I am getting an error with the Windows application not showing up like it should. It just gives me the XP desktop without the explorer.exe shell. Any ideas?
EDIT: Never mind, I got it. I was just locking the XP Administrator account, instead of logging out of it. When I did, the SeamlessRDP program worked just fine. Thanks again for all the help!

I'm actually putting something together so that you can install apps off of your linux partition as well as run multiple apps from desktop shortcuts with this setup.  I'll post it up when I'm done.

---

