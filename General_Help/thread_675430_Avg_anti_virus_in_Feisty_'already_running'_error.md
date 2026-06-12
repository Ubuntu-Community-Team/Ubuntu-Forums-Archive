---
title: "Avg anti virus in Feisty 'already running' error"
date: 2008-01-22
forum: General Help
---

### Post by phil54601 on 2008-01-22
Hello All;
   I am having trouble with feisty and the update process for avg anti-virus.  I dual boot win2000, & feisty, and swap files back & forth all the time.  When ever I try to update avg I get an error.  The error started after the update download stopped & I shut down avg & the PC.  Now when ever I try to update avg I get the error:                          "Process 'avgupdate' is already running.". 
 I have been able to update avg before without trouble.  There must to be a flag somewhere that avgupdate reads & therefore thinks it's still running.  I have system monitor running & it shows a module sleeping with the name 'avgscan'.  'avgscan' is the command line scanner.  I did a complete uninstall and reinstall, twice.  Both before reinstalling my original 'install' Deb file & before installing a newly downloaded 'install' Deb file.  The new gui avg version is 7.5.51.  The version I get from the 'avgupdate -v' option in a terminal is 7.5.50, the previous  version.  I restarted feisty, windows style after each uninstall.  The problem has persisted for 2days.   Is it possible that avgupdate or a portion of it has terminated but stayed resident, & now the update program thinks it's still running?  I have never written a TSR program so I don't understand the mechanism.  I even manually edited the avg log file to remove 2 references to incomplete updates.
Thanks in advance.
Phil54601

---

### Post by jken146 on 2008-01-24
You could try ```
killall avgupdate
``` to see if the offending process goes away.

---

