---
title: "Unable To Copy User's Xauthorization File"
date: 2017-01-31
forum: General Help
---

### Post by G_M_Slater on 2017-01-31
Running Ubuntu/Ubuntu Studio 16.04. I have an external USB drive that is full, so I need to delete files from it. Whenever I attempt to access it as root so I may do so, I get an error message stating Unable To Copy The User's Xauthorization File. This same error occurs whenever I attempt to launch any applications requiring root access. Also, I am unable to launch most applications on my system. When I attempt to, I get the spinning circle icon for a few seconds, then nothing happens. I would normally try to uninstall/re-install the applications in question but I can not open Synaptic as that it requires root access and gives me the same Can Not Copy The User's Xauthority File error. This file exists, but I do not know if it is corrupt. What is my next step in restoring everything? I am frantic!!

---

### Post by Bucky Ball on 2017-01-31
If you need to access it as root to delete files from it as you can't do so as a regular user, you have the permissions wrong on the external drive.

Is the only way you can access this drive as root? Can you copy/paste files to the drive as a normal user using a file manager? Which filesystem is the external partition using (NTFS? FAT? EXT?)?

---

### Post by Impavidus on 2017-01-31
Can you run command line tools as root? That should allow you to delete files from the external drive and doesn't need .Xauthority. How do you run applications as root? Because it's easy to mix up .Xauthority by using sudo the wrong way.

What are the permissions and ownership of .Xauthority?

```
ls -l .Xauthority
```

---

### Post by G_M_Slater on 2017-01-31
> **Impavidus said:**
> Can you run command line tools as root? That should allow you to delete files from the external drive and doesn't need .Xauthority. How do you run applications as root? Because it's easy to mix up .Xauthority by using sudo the wrong way.

What are the permissions and ownership of .Xauthority?

```
ls -l .Xauthority
```

When I run the -l .Xauthority I get the following result: -rw------- 1 gslater gslater 60 Jan 30 23:41 Xauthority
The owner of the Xauthority file is listed as ME, and the permissions are Read and Write.

When I referenced running applications as root I should have been more clear. What I need to do is run Lucky Backup (super user). When I attempt to launch it via its regular shortcut icon in the start menu I get the error: Unable to Copy User's Xauthorization File.

The other bizarre issue I am running into is that when I attempt to launch other applications like Audacity, nothing happens. I attempted to reinstall via Synaptic, but I get the following message: E:/var/cache/apt/archives/audacity_2.0.6-2build1-i386.deb: cannot copy extracted data for './usr/bin/audacity' to '/usr/bin/audacity.dpkg-new':failed to write (No space left on drive). This can't be true as that I have plenty of drive space available. Ugh!

---

### Post by G_M_Slater on 2017-01-31
As a follow up, I was able to get access to my external drive, and am able to delete/write files to it now, so I have a full backup. I also determined that the main file system partition was almost full, so I uninstalled some unneeded applications and was then able to re-install Audacity. Unfortunately, when I attempt to launch it nothing happens. This is also occurring with a few other applications, like my VPN manager (PIA). Also, I am still getting the Unable To Copy User's Xauthorization File message when attempting to do anything as super user. Not sure where to go from here, but I definitely need to get Audacity working as that I have a couple of unfinished time sensitive projects I need to edit in it. Does anyone have any ideas?

---

### Post by steeldriver on 2017-01-31
How exactly are/were you "attempting to access" as root or "do anything as super user"? 

If you used 'sudo nautilus' or "sudo someapp" that could explain some things. It's possible that some application configuration files in your home directory have become owned by 'root' and now applications fail to start as your regular user because they can't overwrite them.

---

### Post by Bucky Ball on 2017-01-31
> **G_M_Slater said:**
> Not sure where to go from here, but I definitely need to get Audacity working as that I have a couple of unfinished time sensitive projects I need to edit in it. Does anyone have any ideas?

Yes. This issue belongs in another thread in another area as it has nothing to do with this thread or support area and you reduce your chances of support by posting about it here, deep on a thread about something else. 

Post a new thread with a descriptive title in 'Multimedia Software' about anything that's to do with your Audacity issue. There is a chance the Audacity issue is linked with your xauthority issue so you'd be best fixing that first. You will need to fix the xauthority issue before much is going to work as it should I would think. Everything else may just fix itself when you do.

Good luck with it. ;)

---

### Post by Impavidus on 2017-02-01
> **G_M_Slater said:**
> When I run the -l .Xauthority I get the following result: -rw------- 1 gslater gslater 60 Jan 30 23:41 Xauthority
The owner of the Xauthority file is listed as ME, and the permissions are Read and Write.That's fine. Those permissions often get mixed up by users running sudo nautilus or something like that, but permissions and ownership are correct here.> E:/var/cache/apt/archives/audacity_2.0.6-2build1-i386.deb: cannot copy extracted data for './usr/bin/audacity' to '/usr/bin/audacity.dpkg-new':failed to write (No space left on drive). This can't be true as that I have plenty of drive space available. Ugh!That's not so fine. You get no error like "No space left on drive" when there's plenty of space left. Maybe the space that's left is not where you think it is. Run```
df
df -i
```to get some more diagnostics.

---

### Post by G_M_Slater on 2017-02-01
Issue resolved. I deleted a LOT of old linux-image versions. That freed  up space in my root partition and now all works normally.

---

