---
title: "winecfg broken"
date: 2007-07-06
forum: General Help
---

### Post by xturmn8r on 2007-07-06
I was trying to follow this guide ([http://appdb.winehq.org/appview.php?iVersionId=3214&iTestingId=11157](http://appdb.winehq.org/appview.php?iVersionId=3214&iTestingId=11157)) so I popped open winecfg, and made changes.  Big mistake.  Now when I type winecfg in the terminal, it tells me this:

> err:module:import_dll Library ole32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135


How do I get winecfg back? I've tried to uninstall/reinstall wine through synaptic and using apt-get, both of which ended in me getting the error message again.  

Thanks for any ideas!

---

### Post by fazavon on 2007-07-06
I would try deleting the .wine dir in you home dir (ex /home/yourname/.wine) 

Then uninstall wine 

then reinstall 

that should work, I had that same issue once before, and I'm pretty sure thats how i got it back.

let me know how it goes...

//j

---

### Post by xturmn8r on 2007-07-06
It worked, thanks!

---

### Post by fazavon on 2007-07-06
Word

---

