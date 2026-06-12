---
title: "regedit wont work"
date: 2007-02-13
forum: General Help
---

### Post by Moffett on 2007-02-13
when i type regedit in the terminal ```
 jon@jon:~$ regedit
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x136
  Serial number of failed request:  13
  Current serial number in output stream:  15
jon@jon:~$ 
``` pops up. What should I do to fix it?

---

### Post by llamakc on 2007-02-13
What are you trying to run "regedit" for? I don't see this program in the repositories.

Oh snap, it is installed on my system. It's for wine. Sounds like your Wine install is mucked up. Where and how did you install it, what version(s) are you currently using?

PS: it worked just fine for me.

---

### Post by madcow72 on 2007-02-13
Right.  regedit is a Windows program.  Ubuntu doesn't have a registry like Windows, thus no reason to edit it.  If you're trying to edit your registry for Wine, like llamakc says, that's a different matter that I don't know much about...

---

### Post by Soulxlight on 2007-02-13
Wow...that is something I completely never tried. I didn't even know wine installed regedit for it, since all I really do with wine is run Photoshop, I've never played with it much....

---

### Post by llamakc on 2007-02-13
I know: I gave it a try and it started me up. Almost made me spit out my beer! I'll have nightmares now.

---

### Post by Moffett on 2007-02-13
ok i tried to uninstall wine to reinstall it and hope that it could fix it. not sure how to uninstall it i tried to open synaptic package manager and i now get the following error message 

E: Type 'repository' is not known on line 41 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

i changed some settings in the regedit as described in the world of warcraft install post and i think that is what caused the problem. I want to open regedit to undo the change i made but now i cant. I am totally new to Linux and i don't yet know how to work stuff so i just copy and past and follow all the directions im given.

---

### Post by Soulxlight on 2007-02-13
Go into .wine > drive_c > windows or whatever it is on your system , and try to open it manually...

---

### Post by Moffett on 2007-02-13
try to open what? im not sure what im looking for to fix.

---

### Post by Soulxlight on 2007-02-13
go into your home directory, and then into your username, hit ctrl H to show hidden files and directories. Then go to .wine > drive_c > windows, and click on regedit.exe. See if that will open it since it won't open in terminal...

---

### Post by llamakc on 2007-02-13
> **Moffett said:**
> ok i tried to uninstall wine to reinstall it and hope that it could fix it. not sure how to uninstall it i tried to open synaptic package manager and i now get the following error message 

E: Type 'repository' is not known on line 41 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

i changed some settings in the regedit as described in the world of warcraft install post and i think that is what caused the problem. I want to open regedit to undo the change i made but now i cant. I am totally new to Linux and i don't yet know how to work stuff so i just copy and past and follow all the directions im given.


Your sources.list error is not related to using regedit, it's because you have an error at line 41. Let us see the contents our your /etc/apt/sources.list file (to fix the Synaptic/apt-get problem).

---

