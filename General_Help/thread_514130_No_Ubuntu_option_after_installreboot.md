---
title: "No Ubuntu option after install/reboot"
date: 2007-07-31
forum: General Help
---

### Post by thebaron2 on 2007-07-31
I installed Ubuntu through Wubi and it seemed to work fine.  It said it'd be about an hour to d/l the ISO so I left the laptop alone for a bit and did some other work.

I came back and was at the reboot screen, installation had completed successfully and I have the C:\Wubi directory.

For some reason, though, when I reboot I get sent right back into Windows XP.  No boot options whatsoever.  If I restart the Wubi-7.04 install program I'm brought to the "Wubi is already installed" screen with the options to backup the downloaded files, backup the documents, and uninstall.

Any ideas, here?  This is an old Dell Latitude laptop.  If more information is necessary let me know.  Any help, ideas, or suggestions are much appreciated.

Thanks.

---

### Post by ago on 2007-07-31
Check boot.ini (might be hidden) there should be a line loading wubi.ldr. We might have edited the wrong boot.ini.

---

### Post by thebaron2 on 2007-07-31
C:\boot.ini

> 
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(o)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


I'm assuming something relating to Ubuntu should be in there (sorry, I'm relatively new to this)?

On a side note - this is a great little program.  I've been trying to get Ubuntu on this laptop for awhile now but it was too slow to install off of a burnt ISO.  This is exactly the sort of program I needed, thanks!

---

### Post by Odegard on 2007-07-31
This is my working boot.ini.

```

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noguiboot
c:\wubildr.mbr="Ubuntu"

```

---

### Post by thebaron2 on 2007-07-31
Well I have the wubildr.mbr file but it's in  C:\wubi\boot\winboot, not C:\.

Should I copy that last line as-is from Odegard's boot.ini, change it to c:\wubi\boot\winboot\wubildr.mbr, or something else entirely?

Thanks for the help!

EDIT: There's also a wubildr.exe in that folder.  No other wubildr.mbr location.

---

### Post by Odegard on 2007-07-31
I've got those two files in both locations, that is on c:\ and c:\wubi\boot\winboot and they appear to be the same. If I were you I'd copy those two files to c:\ instead of editing the boot.ini, seems to me to be a safer option.

To be more specific, copy wubildr and wubildr.mbr to c:\, not wubildr.exe

---

### Post by ago on 2007-07-31
With XP you only need wubildr. I am courious though why it skept the installation of those files. Do you have other partitions/windows setups?

---

### Post by thebaron2 on 2007-07-31
Ahh, well I think this may have isolated the problem.  I just got an Access Denied error when copying to C:.

This is a really old work computer so access may have been limited to non-admin logins.  I think I need uninstall, log in as admin, then reinstall.  I'm guessing that's why boot.ini wasn't changed either.

When I uninstall, if I check the "Backup downloaded files. (CD iso file)" box, will that prevent me from needing to re-download the whole iso?

---

### Post by ago on 2007-07-31
> **thebaron2 said:**
> Ahh, well I think this may have isolated the problem.  I just got an Access Denied error when copying to C:.

This is a really old work computer so access may have been limited to non-admin logins.  I think I need uninstall, log in as admin, then reinstall.  I'm guessing that's why boot.ini wasn't changed either.
Yes you need admin rights, but it's still strange since wubi (nsis) should check and require admin rights.

> When I uninstall, if I check the "Backup downloaded files. (CD iso file)" box, will that prevent me from needing to re-download the whole iso?
yes

---

### Post by thebaron2 on 2007-07-31
That is odd...

I'll post the results once I get admin access and reinstall.

---

### Post by thebaron2 on 2007-07-31
Seems to have worked once I logged in as admin.

I'm at the blue "Select and install software" screen right now.

Thanks for the help, folks, I'm sure I'll need more of it once I start fooling around with the OS.

---

