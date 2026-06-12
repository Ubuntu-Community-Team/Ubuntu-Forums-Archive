---
title: "Current status of SAMBA and Windows Share?"
date: 2007-12-19
forum: General Help
---

### Post by ScottMartin on 2007-12-19
What is the current status of SAMBA and displaying a Windows Share?

I have several distros and they all are able to see the shares when you click on Windows Network.

I have modified the Workgroup in smb.conf, and yes I can access the shares if I use the IP address.

Any chance of this getting fixed or is it a nautilius issue with Ubuntu or?
( nautilus works fine in FC8 )

Would it be better to jump over to KDE and get away from gnome/nautilus in Ubuntu?

Regards,
Scott.

---

### Post by markusfarkus on 2007-12-19
What exactly is your problem?  How are you accessing these shares?  From your post it sounds like everything is working.

---

### Post by danwood76 on 2007-12-19
Its a nautilus issue, the smb/nautilus integration is very flakey and doesnt allow you to actually view shares.

The best thing to use is pyneighborhood, it works just like network neighbourhood does in windows and mounts the shares to a folder of your choice.
 regards,
Danny

---

### Post by ScottMartin on 2007-12-19
I thought I explained myself, let me try again.

In Ubuntu (Gutsy), I am unable to see the shares when I select Places/Network/Windows Share (no shares displayed). To access the shares, I must enter the IP of the share.

In Fedora, for example, when I click on Windows Share, it displays all of my share drives.

I have ready many posts in the these NG's that this is a common problem in Ubuntu using gnome and nautilius.

I was curious to know if this going to be addressed or is it just a random problem w/ some installs or? 

Accessing the drives work, manually entering IP, but the displaying the shares is the problem. I guess I could clutter my desktop with IP shortcuts, but ...

Regards,
Scott.

---

### Post by ScottMartin on 2007-12-19
I will give pyneighborhood a look. I have read several threads about this. My curiousity was why does it work in other distros if it is a gnome/nautilus issue?

Regards,
Scott.

---

### Post by danwood76 on 2007-12-19
I would check you smb.conf against the one you use in fedora and see if it uses the same settings.
I would bet that this is the problem.

I can access shares through nautilus fine but sometimes its a little buggy so I use pyneighborhood instead.

---

### Post by tehet on 2007-12-19
> **ScottMartin said:**
> Would it be better to jump over to KDE and get away from gnome/nautilus in Ubuntu?
That has definitely been my experience and is the main reason for me to use Kubuntu. SMB is nicely integrated into Konqueror and Dolphin through KIO-slaves.

---

### Post by sefs on 2007-12-19
Do you have aviha that zero conf thing installed?  and do you have bonjour installed on all your systems?  When i did this i realize that all my shares were visible everywhere, as the mdns seemed to be useful from propagating the computer names thru-out the small network where they could be pinged by the name, accessible by the name and showed up as icons in the nautilus shared folder.

---

