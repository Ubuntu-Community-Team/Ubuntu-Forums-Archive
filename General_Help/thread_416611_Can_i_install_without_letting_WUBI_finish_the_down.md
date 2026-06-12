---
title: "Can i install without letting WUBI finish the download?"
date: 2007-04-21
forum: General Help
---

### Post by Antimethod on 2007-04-21
I have already downloaded the ubuntu-7.04-alternate-i386.iso and i wondered if there was a way to just use this iso and not wait until WUBI downloads it again in the "Install" folder.
i canceled the download and copied the iso in the Install folder, but when i restarted the installer it deleted the file and started the download again...i have a poor connection to the internet so waiting for the iso to download again is not an option :D
thanks! and sorry for my bad english..

---

### Post by danbutter on 2007-04-21
I usually just put it into C:\wubi
and it works for me just fine.

Problem is that I don't know if they support the final release yet (ubuntu-7.04-alternate-i386.iso).  You may have to wait a bit for that to work.

Last one that I knew worked was the beta, not final.

---

### Post by Antimethod on 2007-04-21
I understand...i thought it didn't work.
well i just have to wait for the new release of Wubi then..
thanks!

---

### Post by roydelmundo on 2007-04-21
After copying it into the folder, in Wubi, that the download has started in, 
Maybe you may need to rename the complete file to  ubuntu-7.04-beta-alternate-i386.iso 
as thats what the conf. file says its looking for, or edit conf file to remove -beta
Just a thought, i'm trying that later.
Roy

---

### Post by Antimethod on 2007-04-21
i tried that and it worked.
it installed ubuntu and asked me to reboot in oreder to finish the instalation.
but when it tried to boot it crashed...so it seems that we have to wait for the new release of wubi.

---

### Post by ecology2007 on 2007-04-21
Nice try but it will not work.
Kernel version of wubi-beta-alternate-v3.exe is 2.6.20-12.
Kernel version of ubuntu-7.04-alternate.iso  is 2.6.20-15.
The debian installer will not start.

---

### Post by tuxcantfly on 2007-04-22
try the new wubi-7.04-v1; it's now using the final released feisty isos

just place the file in the same folder that wubi is in it should detect it

---

### Post by ysuire on 2007-04-23
The problem is that at reboot, it's loading but no more ...

---

