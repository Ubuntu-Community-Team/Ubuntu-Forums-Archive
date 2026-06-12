---
title: "Questions about keepass. Minimized on startup and preselect file"
date: 2014-12-18
forum: General Help
---

### Post by petermartin2 on 2014-12-18
Questions about keepass

a) When I check "minimize on startup" in preferences it still starts maximized in the middle of the screen?

b) I've tried preselecting a keyfile using this command line
KeePass.exe "C:\My Documents\MyDatabase.kdb" -preselect:C:\pwsafe.key

but it didn't work! How can I preselect a key?

Thank you

---

### Post by Penguin360 on 2014-12-18
> **petermartin2 said:**
> Questions about keepass

a) When I check "minimize on startup" in preferences it still starts maximized in the middle of the screen?

b) I've tried preselecting a keyfile using this command line
KeePass.exe "C:\My Documents\MyDatabase.kdb" -preselect:C:\pwsafe.key

but it didn't work! How can I preselect a key?

Thank you

You cannot execute KeePass.exe in Ubuntu. .exe is a Windows thing.

---

### Post by petermartin2 on 2014-12-18
> **Penguin360 said:**
> You cannot execute KeePass.exe in Ubuntu. .exe is a Windows thing.

Ok thanks. Is there any equivalent in ubuntu? I have now added the file as a bookmark so it goes pretty quick but still it would save a lot of time in a longer perspective if the file would just open automatically

---

### Post by Penguin360 on 2014-12-18
> **petermartin2 said:**
> Ok thanks. Is there any equivalent in ubuntu? I have now added the file as a bookmark so it goes pretty quick but still it would save a lot of time in a longer perspective if the file would just open automatically

Yes, KeePassX or KeepPass2. [http://keepass.info/download.html](http://keepass.info/download.html)

---

### Post by petermartin2 on 2014-12-18
> **Penguin360 said:**
> Yes, KeePassX or KeepPass2. [http://keepass.info/download.html](http://keepass.info/download.html)

I have keepass installed on ubuntu I'm trying to find a way to have it always start up with my kdb file already mounted

---

### Post by kpatz on 2014-12-18
I have Keepass (version 2) installed in Mint MATE and it starts up with the kdb file selected already.  I just enter my passphrase and I'm in.

You can install Keepass2 with sudo apt-get install keepass2.  It needs Mono to run, as it uses .NET.  Only trouble is the minimize on open doesn't work properly.  It "minimizes" and disappears completely (no taskbar item or anything in Alt-Tab), and relaunching does nothing.  I had to edit the config file manually to turn off the minimize feature so I could use it again.

---

### Post by petermartin2 on 2014-12-25
> **kpatz said:**
> I have Keepass (version 2) installed in Mint MATE and it starts up with the kdb file selected already.  I just enter my passphrase and I'm in.

You can install Keepass2 with sudo apt-get install keepass2.  It needs Mono to run, as it uses .NET.  Only trouble is the minimize on open doesn't work properly.  It "minimizes" and disappears completely (no taskbar item or anything in Alt-Tab), and relaunching does nothing.  I had to edit the config file manually to turn off the minimize feature so I could use it again.

Ok. I tried keepass2 but it told me my file was damaged so I switched back to keepass "classic". I've solved the problem with the mounting though I think it was due to my internal hard drives not being mounted on startup and once I fixed that keepass also launched with the file mounted.

However I have not yet found a solution to have to autostart it minimized, that's not really a big problem though since I have it's locked to launcher

---

