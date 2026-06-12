---
title: "VMWare and Windows Genuine Advantage"
date: 2006-11-26
forum: General Help
---

### Post by Paul41 on 2006-11-26
I have installed Windows XP Home Edition in VMWare and the install went fine. The problem I am having is that when I try to get updates from the Windows site it tells me I don't have a valid copy. When I try to authenticate Windows it tells me my license code is wrong. This is a legal copy of Windows. I have read that this is a problem running Windows in VMWare. Is there any way to solve this problem?

---

### Post by drphilngood on 2006-11-26
I don´t know if this is what you´re looking for but you can DL updates from [here]("http://www.softwarepatch.com/windows/") and install them yourself.  I´ve not used windows in a while so U@YOR.

---

### Post by telovoyagarcar on 2006-11-26
just get the cracked version... works much better

Or search for WGA remover.. there are patches for that.

---

### Post by Paul41 on 2006-11-27
Thanks for the replies. I will look into these.

---

### Post by AndyCooll on 2006-11-27
> **telovoyagarcar said:**
> just get the cracked version... works much better

Or search for WGA remover.. there are patches for that.

I wouldn't advocate the first viewpoint for legality reasons, but the second one might work.

I didn't have the same problem, however I ended up having to ring M$ up and getting them to validate my copy.

:cool:

---

### Post by ser1alsn1per on 2006-11-27
theres a program called ms blinder which does something to ur pc to make it be able to get updates and remover the anoying pop ups

---

### Post by munkyeetr on 2006-11-27
I've heard this works, though haven't used it myself...

   1. Lauch Windows Task Manager.
   2. End wgatray.exe process in Task Manager.
   3. Restart Windows XP in Safe Mode.
   4. Delete WgaTray.exe from c:\Windows\System32.
   5. Delete WgaTray.exe from c:\Windows\System32\dllcache.
   6. Lauch RegEdit.
   7. Browse to the following location:
      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\
      Windows NT\CurrentVersion\Winlogon\Notify
   8. Delete the folder &#8216;WgaLogon&#8217; and all its contents
   9. Reboot Windows XP.

Note: With this method, you may be prompted to install WGA Notifications again which can still be unselected. After you unselect it check the box that says not to ask you about this update again.

Good luck!

---

### Post by Fnordle on 2006-11-27
It always says invalid code if its been activated too many times (how dare you re-install software you paid for, scum! :)), or if it was an OEM version and your not using a recovery disk.  It doesn't actually mean the code is invalid.

Just click the telephone button and speak the the indian chappy (or lass).  I wouldn't advise doing anything invasive as it could bork something further down the line.  And make sure the VM settings are final or you may have to do it again.

---

