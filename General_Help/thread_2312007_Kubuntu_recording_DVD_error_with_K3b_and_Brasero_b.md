---
title: "Kubuntu recording DVD error with K3b and Brasero but no problem in Unity"
date: 2016-02-01
forum: General Help
---

### Post by feveal on 2016-02-01
He had been working in Ubuntu 14.04 with Unity but a few days ago I installed Kubuntu KDE desktop. In principle I never had problems with recording in Unity with K3b. In wanting to burn a DVD in the KDE environment with K3b, I have not succeeded. I've broken 10 DVDs, changing various options and installing add-ons, but without success. I retested entering the Unity environment and the DVD was recorded perfectly.
In Kubuntu, it starts recording, it loads the buffer, and immediately stop the recording and producing an error leaving the DVD unusable. File names are recorded and watched the DVD on the track, is seen to have recorded about two mm. 10 DVD alike. I also tested with Brasero and the same problem.
I tested at different speeds, to remove and install K3b, everything.
The only thing that worked was closing session, enter the Unity environment and burn the DVD without problems.
I understand this is a bug in Kubuntu.
Anyone know how to fix it?

---

### Post by feveal on 2016-02-01
This is the error.
Only records 58 Mb
 Final error: mkisofs

[https://onedrive.live.com/embed?cid=EBFAA195CAC687DC&resid=EBFAA195CAC687DC!1015&authkey=AExJ6fLUEEyK1Wo](https://onedrive.live.com/embed?cid=EBFAA195CAC687DC&resid=EBFAA195CAC687DC!1015&authkey=AExJ6fLUEEyK1Wo)

[IMG]https://onedrive.live.com/embed?cid=EBFAA195CAC687DC&resid=EBFAA195CAC687DC!1015&authkey=AExJ6fLUEEyK1Wo[/IMG] ?

---

### Post by yoshii on 2016-02-01
I'm not sure what the issue is, but I can report that on my Ubuntu Studio Linux (with Xfce) Brasero works for me but K3B fails at 98% completed every time when trying to create a DVD.  I had to give up on K3B because I can't figure out what the error is.  It's weird because on a different system I had in the past, Brasero didn't work; it would create an entire 4.7 GB DVD even if I was just trying to burn 3 MB of data.  Something wasn't right with that.  At the time I thought it was a virus.  But I just don't know.

---

### Post by scdbackup on 2016-02-02
Hi,

if "mkisofs fallo" is the only visible reason, then the first
suspect would be the UDF feature, which obviously was enabled.
Try whether K3B lets you burn without UDF.

Another reason could be that mkisofs (actually genisoimage ?)
cannot cope with the directory structure on hard disk.

Or K3B could have omitted mkisofs option "-iso-level 3" which
enables inclusion of data files larger than 4 GiB.
Do you have such a large file in your composition ?
The messages only warn of 2 GB, which is not about mkisofs but
about very old Linux kernels (or current Solaris, or the BDSs).

If you can make K3B issue more messages about the mkisofs command
and its failure, then i might be able to read more info from it.


Brasero on Ubuntu uses by default libisofs instead of mkisofs, afaik.
Other bugs (mine actually) and other highlights.

Have a nice day :)

Thomas

---

### Post by J_Me on 2016-02-02
> Another reason could be that mkisofs (actually genisoimage ?) cannot cope with the directory structure on hard disk.  Can confirm[br]1[/br] [br]1[/br] I had similar issues as OP when burning files to dvd directly from my second hard drive, seems that I can only burn a dvd if I first move the files to my main hard drive.[br]1[/br] [br]1[/br] OP are the files on a second hard drive?

---

