---
title: "Sharing Services are not Installed"
date: 2007-10-04
forum: General Help
---

### Post by monolithium on 2007-10-04
Hi, I've installed ubuntu feisty and after an epic battle with ndiswrapper I'm finally online. Thing is, I am trying to share the machine via samba so I can see it on my windows network. When I try to share a folder I get the @Sharing Services are not installed@ dialogue as expected but when I click @install services@ it grinds for a bit then I get the dialogue popping up again!

I can see all other machines on the network though ubuntu, but can't share a folder, any folder! Please help it's doing my head in :(

---

### Post by por100pre1 on 2007-10-04
Weird. Try to install the services manually:

```
sudo apt-get install libevent1 libgssapi2 libnfsidmap2 librpcsecgss3 nfs-common nfs-kernel-server portmap samba
```

BTW, welcome to the forums!

---

### Post by jefflin on 2007-10-05
Hi, I have the same issue. But my installation is within VMWare Server. I have followed your instruction but the system returned with "libevent1 couldn't find package" error? :(

---

### Post by kvonb on 2007-10-05
-

---

### Post by jefflin on 2007-10-07
kvonb:

Thanks for the tip. However, after execute the command, the system said that, the samba package is not available and is replaced by smbclient and samba-common packages. I checked the system, both packages were installed and up to date. Any other idea? Thanks.

---

### Post by AudioBoy on 2007-11-03
jefflin - I'm having the same issue.  I've tried manually installing samba via the command line, but the same "sharing services are not installed" message keeps popping up whenever I try to assign sharing to a folder. Furthermore, I've confirmed via Synaptic Package Manager that "smbclient" and "samba-command are installed".

---

### Post by jeremiahj on 2007-11-04
I'm also getting this error. When trying to install from command line says samba already exists. however not located in /etc/init.d/? when trying to share folder i get in an infinite loop. help.

---

### Post by kvonb on 2007-11-07
-

---

### Post by AudioBoy on 2007-11-07
Hi kvonb,

1) I'm using Ubuntu 7.10 - the Gutsy Gibbon - released in October 2007

2) I checked all the boxes in software sources and reloaded (I was first asked for a password).

3) I went into menu->System->Administration->Users & Groups, and got a dialogue box with my name and root (I was not asked for a password, I'm guessing that I was already logged in in step 2)

4) I ran:
[COLOR="Navy"]dpkg --get-selections | grep samba[/COLOR]

And got this:
[COLOR="navy"]samba-common                              install[/COLOR]
[COLOR="navy"]dan@dan-desktop:~[/COLOR]

Although it was missing the "samba    install" line of your results, I went ahead and removed it anyway.
I got confirmation that samba was removed and so I tried again to shared a folder on my desktop by right clicking and going to "share folder" but nothing happened. Then I went to administration> shared folders and tried to open it, but nothing happened again (the ubuntu icon spins for a minute, then stops).

Any ideas?

Just to pull everything together again, I'm simply trying to access files on my Ubuntu Machine from my Windows XP machine.

Thanks in advance!

---

### Post by kvonb on 2007-11-08
-

---

### Post by AudioBoy on 2007-11-10
ok, I'm getting closer!

I was able to reinstall samba through the commands you provided and was able to connect by using the IP address (//xxx.xxx.xxx.x), but I still couldn't see the shared folder.  Kept getting a message about "network path" not found. I can see shared printers on the ubuntu machine, but nothing else.  

I tried connecting via //dan-desktop/testing
but it's as if the folder "testing" doesn't exist...when it clearly does and has been assigned sharing status on the ubuntu machine.

btw - I would have posted the code results, but I'm using a different machine for net access at the moment.

---

### Post by kvonb on 2007-11-10
-

---

### Post by AudioBoy on 2007-11-10
kvonb - You made my day!  It works!

Thanks for all your help.

---

### Post by kvonb on 2007-11-10
-

---

### Post by AudioBoy on 2007-11-12
Thanks once again

---

### Post by zorkerz on 2007-12-11
Im still having the problem mentioned in the initial post of this thread. namely that when I open system->administration->shared folders it tells me that sharing services are not installed even though they are and have been for a while. I had previously set up shared folders already that people could access. When I click to have them installed again the same message just popes up over and over.

---

### Post by Jabus on 2008-01-02
I had the exact same issues however it began working right after I allowed it to download files from all areas. This is only my second day on Ubuntu so I apologize if this feels like a newbie question. But I got this sharing working so that it works on the filesystem that is installed. However, I have a couple of partitions from windows that have some videos on them. I try to share them and it seems to go through successfully. But via windows it says I don't have enough permission to view them. I can by pass this by taking files out and putting them on my main partition and then sharing that partition to my windows, but that seems like a weak work around. Any suggestions?

---

### Post by Dithers on 2008-01-21
> **monolithium said:**
> Hi, I've installed ubuntu feisty and after an epic battle with ndiswrapper I'm finally online. Thing is, I am trying to share the machine via samba so I can see it on my windows network. When I try to share a folder I get the @Sharing Services are not installed@ dialogue as expected but when I click @install services@ it grinds for a bit then I get the dialogue popping up again!

I can see all other machines on the network though ubuntu, but can't share a folder, any folder! Please help it's doing my head in :(


I just figured out the ANSWER
 in the toolbar Go to Applications Add/Remove and click on preferences at the bottom left, and check the types of downloads you will allow "I did all of them" and then It stops grinding and starts INSTALLING

---

### Post by rom82 on 2008-04-05
> **Dithers said:**
> I just figured out the ANSWER
 in the toolbar Go to Applications Add/Remove and click on preferences at the bottom left, and check the types of downloads you will allow "I did all of them" and then It stops grinding and starts INSTALLING

**THANK YOU !**

---

### Post by rsilvers on 2008-04-09
Thanks. I just had that problem and that also fixed it for me.

---

