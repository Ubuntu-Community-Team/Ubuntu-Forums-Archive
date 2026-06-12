---
title: "Uninstallation"
date: 2007-08-29
forum: General Help
---

### Post by Yizi on 2007-08-29
When i uninstall Wubi it still remains in the add & remove section how do i remove it from there?

---

### Post by ago on 2007-08-29
Hmm that should not happen unless the wubi folder was moved/removed manually.

Anyway you have to delete the wubi registry key. Should be

Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

---

### Post by Yizi on 2007-08-29
> **ago said:**
> Hmm that should not happen unless the wubi folder was moved/removed manually.

Anyway you have to delete the wubi registry key. Should be

Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
 
i went to the registry but there is no folder such as Unistall\Wubi :confused:

---

### Post by clive_pearce on 2007-08-29
Did you tick the boxes to backup/save some files when you uninstalled?

 I think it went from the add/remove list after I rebooted.

---

### Post by clive_pearce on 2007-08-29
I found it by run:regedit/ edit find wubi

---

### Post by Yizi on 2007-08-29
> **clive_pearce said:**
> Did you tick the boxes to backup/save some files when you uninstalled?

 I think it went from the add/remove list after I rebooted.

no i did not tick them because i didn't needed any backup.

---

### Post by Yizi on 2007-08-29
> **clive_pearce said:**
> I found it by run:regedit/ edit find wubi

Yes i found it and deleted the whole Wubi directory but its still in control panel :(

---

### Post by ago on 2007-08-29
The reason why you do not see  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi is because you might have uninstalled properly then (as opposed to delete the wubi folder manually)...

Old wubi version might have used a different registry key, look for ubuntu or ubuntusetup.

Or look into Software\Microsoft\Windows\CurrentVersion\Uninstall

---

### Post by Yizi on 2007-08-29
> **ago said:**
> The reason why you do not see  Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi is because you might have uninstalled properly then (as opposed to delete the wubi folder manually)...

Old wubi version might have used a different registry key, look for ubuntu or ubuntusetup.

Or look into Software\Microsoft\Windows\CurrentVersion\Uninstall

I didn't done any manual installation and i didn't delete the folder.
This was the first time i installed Wubi.

---

