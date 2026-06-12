---
title: "Unable to create files without using Sudo?"
date: 2006-11-25
forum: General Help
---

### Post by alien21010 on 2006-11-25
I was wondering if anyone knew why my main user is unable to create files using VIM and Azureus in particular without using sudo?  I can save files in OpenOffice, normally... So what could be causing this?  Is this something that Ubuntu does by default for security reasons, or did I mess up a setting somehow?  Any help would be greatly appreciated.

---

### Post by aysiu on 2006-11-25
What folder do VIM and Azureus try to create files in?

---

### Post by alien21010 on 2006-11-25
Ah well they are trying to create the files in folders that I have created within my home directory, so for example: /home/username/programming or something to that nature.  

I just did some more testing and found that the user can create files in VIM and Azureus as long as they are in the home directory, but cannot do so with any files outside the home directory... This might be the cause, but why would it do this for folders within the home directory?

---

### Post by aysiu on 2006-11-25
Are you able to create files within /home/*username*/programming through the file manager?

---

### Post by AdamTheCamper on 2006-11-25
Try to check the permissions in your home folder.And user who owns it. Maybe it is not you but root.

---

### Post by alien21010 on 2006-11-25
Well I figured it out... The problem was that I was using mistakingly using sudo mkdir to make the folders and as such lacked sufficient priviledges to actually do anything in the folders without using sudo.  Such a simple mistake... 

I never would have thought though to use the file manager...  That was a dead give away though, when all my folders were locked.

Thanks for your help.

---

