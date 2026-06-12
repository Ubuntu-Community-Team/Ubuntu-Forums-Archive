---
title: "firefox, openoffice 2 beta crash when print"
date: 2005-04-10
forum: General Help
---

### Post by bennettg on 2005-04-10
Hello....nOOb here. 3 months on suse linux and 3 days on ubuntu. I Love it and am so close from getting away from M$, BUT......

I can't print in firefox 1.0.2. when i goto file, print, it crashes. I tried to follow the suggestions in this thread without success. Uninstalling/reinstalling and creating new profiles did NOT work.

[http://ubuntuforums.org/showthread....t=firefox+crash](http://ubuntuforums.org/showthread....t=firefox+crash)

Interestingly, there was no discussion of openoffice. The same problem (crash) happens when trying to print in openoffice 1.9.79.2 build.

The crashing issue does not effect openoffice 1.1 (standard that came with ubuntu 5) nor mozilla 1.7.6 that I downloaded with synaptic.

HELP!!!!!!

---

### Post by dejitarob on 2005-04-10
Be sure to read those [announcements]("announcement.php?f=58"). Anways, can you print in any other applications? If not there probably is something wrong with the CUPS (Common Unix Printing Solution) service. Could you print before or was it always like this? If you could, do you remember installing or changing anything right before you had trouble? Can you open up the Printing preferences under the Gnome menu, System, Administration? Try a 'sudo /etc/init.d/cups restart' or start in the command line.

---

### Post by bennettg on 2005-04-11
i am sorry.  i did not see any announcements.  when i clicked on your link i got an error message.   can you tell me the url for the announcements?

i did not add any new programs.  the crashing happened aftering installing ubuntu.  i was curious, so i added mozilla and open office 2.   same problem existed.

---

