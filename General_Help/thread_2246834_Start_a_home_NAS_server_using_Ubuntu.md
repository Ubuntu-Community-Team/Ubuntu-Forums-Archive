---
title: "Start a home NAS server using Ubuntu?"
date: 2014-10-03
forum: General Help
---

### Post by bluesoviet on 2014-10-03
Is it possible to start a home NAS server using the standard Ubuntu distro? If so, how would i do it? Are there any special requirements that i need to know about first before attempting it?

---

### Post by ian-weisser on 2014-10-03
Do you mean to convert existing NAS hardware to Ubuntu?

Or to repurpose more general equipment (desktop/laptop/tower) as an Ubuntu server?

---

### Post by tgalati4 on 2014-10-03
All Ubuntu desktops can be servers.  Just install and put in some disks and turn sharing on the directories that you want to share over your local network.  What kinds of things do you want this home server to do?

---

### Post by bluesoviet on 2014-10-03
> **ian-weisser said:**
> Or to repurpose more general equipment (desktop/laptop/tower) as an Ubuntu server?  ^This.  > **tgalati4 said:**
> All Ubuntu desktops can be servers. Just install and put in some disks and turn sharing on the directories that you want to share over your local network. What kinds of things do you want this home server to do?   What disk(s) are you referring to? How do i turn on sharing? Can computers running Windows see the network drive?  I plan on using it for storing music and other important files mostly. Is there a limit to what i can store on the network drive?

---

### Post by 1clue on 2014-10-03
The short answer is "yes."

What is your intent?

Do you just want a NAS, or do you want to figure this out, or do you just want a NAS and happen to have some old equipment sitting around?

There are reasons for my questions.

[LIST=1]
[*]If you just want a NAS and want to have all the goodness of a modern NAS -- Like file sharing on all platforms, music/photos/etc for ipod/ipad/android -- then you should buy a NAS.
[*]If you want a high quality low cost NAS that handles files for any platform including music and photos for your phones and tablets, then go buy a NAS.
[*]If you want to learn how file sharing works and don't care about spending a lot of time figuring things out, then go ahead with the Ubuntu approach.
[*]If you want something specific, then continue with the Ubuntu approach or look at a NAS-oriented distro like FreeNas.
[/LIST]

I'm not trying to get in the way of somebody who wants to do their own thing, but I'm also not going to let you try this without a warning that doing it yourself is not cheaper if you value your time.

Modern NAS devices aimed at homes or small offices are extremely competitively priced.  I don't think it's possible to buy new parts to make a NAS, install software on it and configure it all for anywhere near the price of a new NAS.

Not only can Ubuntu be a NAS, but also there are NAS operating systems based on Linux and other Open Source operating systems which look a lot like what you would buy.  In fact, some of them are actually used in NAS devices which are commercially available.

---

### Post by tgalati4 on 2014-10-04
To share a folder, Right-Click on it while in file manager and select "Share Folder".  It's pretty easy.  If you need a more complicated sharing arrangement, then you have some [reading]("https://help.ubuntu.com/community/Samba") to do.

---

### Post by bluesoviet on 2014-10-07
> **tgalati4 said:**
> To share a folder, Right-Click on it while in file manager and select "Share Folder".  It's pretty easy.  If you need a more complicated sharing arrangement, then you have some [reading]("https://help.ubuntu.com/community/Samba") to do.

Yeah it didn't work. Windows 7 can't see the folder at all. Any idea why?

---

### Post by 1clue on 2014-10-08
> **bluesoviet said:**
> Yeah it didn't work. Windows 7 can't see the folder at all. Any idea why?

Because that only shares it in NFS, which is how UN*X does it.  CIFS shares are different.

---

### Post by Morbius1 on 2014-10-08
> [quote]                     Originally Posted by **tgalati4**

                 To share a folder, Right-Click on it while in  file manager and select "Share Folder".  It's pretty easy.  If you need a  more complicated sharing arrangement, then you have some [reading]("https://help.ubuntu.com/community/Samba") to do.
                            
Yeah it didn't work. Windows 7 can't see the folder at all. Any idea why?                 [/QUOTE]
Can't see the folder or can't see the Ubuntu machine?

Anyway, When you right click a folder and select "Share Folder" you create a Samba Usershare. Samba with Windows has to follow some rules ( ironically,  Samba in an all Linux / OSX environment is easier ) so we need to know how your system is set up. To do that please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

---

### Post by tgalati4 on 2014-10-08
Also, Linux SAMBA shares use the default "WORKGROUP".  So if you have changed the workgroup to "CLOWNHOUSE" in Windows, then you can't see shares from "WORKGROUP".  

What workgroup are you using in Windows?

---

