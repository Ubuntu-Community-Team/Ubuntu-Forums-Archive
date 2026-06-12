---
title: "Gutsy problem libsasl2/libsasl2-2"
date: 2008-01-05
forum: General Help
---

### Post by mwiertz on 2008-01-05
Hi everyone,

I'm just struggling to get a certain package (part of scalix 11.2.0) installed. I managed to get almost everything it depends on installed, but I cannot get the dependency on libsasl2 fulfilled.

I found out that the package really wants to have libsasl2 installed, but Ubunt 7.10 (gutsy gibbon) just comes with libsasl2-2 as a replacement. There's no more 'fake' package called libsasl2 for compatibility as there was/is for 7.04 (feisty).

I found a post regarding this on the scalix forum ([http://www.scalix.com/forums/viewtopic.php?p=42454&sid=4a74ef9bb815a691920f0dbaac0ed429](http://www.scalix.com/forums/viewtopic.php?p=42454&sid=4a74ef9bb815a691920f0dbaac0ed429)), it says:

Go to /var/lib/dpkg, open status and replace libsasl2 in the 'scalix-server' section with libsasl2-2 and reconfigure the scalix-server package.

But actually I do not know how to reconfigure, if I try to use sudo dpkg-reconfigure scalix-server-xxx.deb, it fails.

Maybe someone can explain to me what I'm doing wrong? :confused:

On the other hand I see this as a really quick and dirty trick, but if it works somehow I would live with it, no problem.

But maybe I can create a kind of 'fake' libsasl2 package myself, maybe even based on the existing one. But then again I'm not experienced enough to get that done or where to find a tutorial for this kind of action. #-o

I would appreciate any help... 

please... [-o<

---

### Post by mwiertz on 2008-01-06
Hi,

Thanks to this thread: [http://ubuntuforums.org/showthread.php?t=501032&highlight=dummy+package](http://ubuntuforums.org/showthread.php?t=501032&highlight=dummy+package) (I found after searching on dummy package)... I manged to fix the dependency by creating a special compatibility package myself and installing it by hand (using dpkg).

Maybe someone else can use this info as well.

---

