---
title: "Can I Switch to a X session started by NX?"
date: 2007-12-12
forum: General Help
---

### Post by superyounan1 on 2007-12-12
I installed the free version of NX by nomachine (i just couldn't get freeNX to work), and I noticed when you close the client, you have the option of keeping the new X session alive so you can log back into it later..

So what about when I go back to the remote PC; If I still have that other session initiated by NX active, can I switch to it? Shut it down?

---

### Post by daflame on 2007-12-14
> **superyounan1 said:**
> I installed the free version of NX by nomachine (i just couldn't get freeNX to work), and I noticed when you close the client, you have the option of keeping the new X session alive so you can log back into it later..

So what about when I go back to the remote PC; If I still have that other session initiated by NX active, can I switch to it? Shut it down?

It depends on a couple of things.  You can only resume sessions started in Windows from a windows machine, and Linux from Linux.  If you go to the physical desktop, you are on a different display than the one you logged into remotely, so you have to resume the session on the local computer to continue using it.  This means that you can't run the session in Windows if you want access to it later on the local computer.

---

### Post by superyounan1 on 2007-12-15
> **daflame said:**
> It depends on a couple of things.  You can only resume sessions started in Windows from a windows machine, and Linux from Linux.  If you go to the physical desktop, you are on a different display than the one you logged into remotely, so you have to resume the session on the local computer to continue using it.  This means that you can't run the session in Windows if you want access to it later on the local computer.

Well alright, what if i run an NX session remotely on another linux PC? Can i disconnect and continue it locally? 

And if its just not possible, if remote session can only be accessed remotely, then there must be at least a way of killing those sessions locally

Seems to me there ought to be a straight-forward way of starting and stopping any X session locally and remotely, logging back into it remotely or locally, and shutting them down. Makes sense with the whole Client / Server methodology of it, and it would be more robust than Windows RDP

---

### Post by daflame on 2007-12-16
> **superyounan1 said:**
> Well alright, what if i run an NX session remotely on another linux PC? Can i disconnect and continue it locally? 

And if its just not possible, if remote session can only be accessed remotely, then there must be at least a way of killing those sessions locally

Seems to me there ought to be a straight-forward way of starting and stopping any X session locally and remotely, logging back into it remotely or locally, and shutting them down. Makes sense with the whole Client / Server methodology of it, and it would be more robust than Windows RDP

Yes, you can reconnect to them locally.  You just need to run NX Client locally and select the session you want to resume after attempting login.  If there is only one session to resume it will automatically reconnect to that session.

---

### Post by superyounan1 on 2007-12-17
oh ok, i didn't think about that. thanks for the tip

---

### Post by daflame on 2007-12-19
> **superyounan1 said:**
> oh ok, i didn't think about that. thanks for the tip

By the way, if the two connection limit bothers you, you can retry with FreeNX here:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

### Post by superyounan1 on 2007-12-19
thanks again, but I already wasted about 5 hours trying to get that dang thing working properly, I followed 8 or 9 different sets of instructions to the letter. Even if i found an easy deb file, I simply refuse to try again.

just like even if AMD came out with perfect drivers for my card tomorrow, I'm still buying an Nvidia next time around.

---

