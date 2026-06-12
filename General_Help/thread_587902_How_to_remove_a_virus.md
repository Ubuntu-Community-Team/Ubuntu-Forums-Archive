---
title: "How to remove a virus?"
date: 2007-10-23
forum: General Help
---

### Post by Cet on 2007-10-23
My friend uses Windows and has a virus that blocks his PC so that it is not possible to install and run an anti virus program. My idea is to boot from Ubuntu Live-CD and remove the virus. Does anyone know how to accomplish that?

---

### Post by 1/0 on 2007-10-23
I haven't used Windows in years but good old Google told me that LinuxDefender Live! does that. Hope it helps.

---

### Post by mahousaru on 2007-10-23
> **Cet said:**
> My friend uses Windows and has a virus that blocks his PC so that it is not possible to install and run an anti virus program. My idea is to boot from Ubuntu Live-CD and remove the virus. Does anyone know how to accomplish that?

Wow nice idea, I guess this is a variant of virus scanning via samba.  The only thing is that I think the user's registry will not be scanned.

But before trying this I would recommend that you try running Mcafee's Stinger, its a single binary and might be able to dislodge it in safe mode.  But make sure you don't close the warning about safe mode, instead use Ctrl Shift Esc to bring up the task manager and run it from there.

[http://vil.nai.com/vil/stinger/](http://vil.nai.com/vil/stinger/)

Back to the topic, I would try booting up to the live disk.  Get an internet connection and then add an AV proggy like ClamAV, mount the disk as writeable and then give it a scan.  

What ever you decide to do, make sure you back up all their data first.  Also I would be a little worried that ClamAV might delete a system file that the virus has replaced making the PC unusable.....

Good luck!

---

### Post by Nunu on 2007-10-23
On windows go to task manager and see if you can find any odd looking processes running. can those process and try installing that way, if that fails look for the target files and remove them (not DLL files though) also start the machine in safe mode when doing this it should allow you to remove the files that are malicious. Also remember with Windows you need to stop the method of infection other wise it will simply reinfect itself so you might need to look at downloading critical MS updates. these will close the "Backdoor" and should enable you to install some for of av. I suggest downloading AVG free edition that is a very good av scanner.

---

