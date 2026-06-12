---
title: "Uninstall wubi - where is iso backed up please?"
date: 2008-05-06
forum: General Help
---

### Post by candtalan on 2008-05-06
When I uninstall wubi, and I choose the option to keep the iso file - where is the iso file kept please?
tia

---

### Post by ago on 2008-05-06
c:\ubuntu-backup

---

### Post by candtalan on 2008-05-06
Thanks.
I seem to have
c:\ubuntu.old
containing only
c:\ubuntu.old\disks\swap.disk
the file swap.disk is reported as being type disk file and is about 195MB in size.

Is this the one?

I will be demonstrating wubi to others soon and so I want to know what happens.
(Wubi is going to be *so* useful for demonstrations in windowsworld!)
tia

---

### Post by ago on 2008-05-06
ubuntu.old is a pre-existing ubuntu installation and you can delete that if you want.

the relevant backup files should be in a folder called ubuntu-backup within the same drive where you installed ubuntu. If you are sure you checked the ISO backup box and cannot find any ubuntu-backup folder please provide the ubuntu logs in your user temp folder.

---

### Post by candtalan on 2008-05-06
> **ago said:**
> ... If you are sure you checked the ISO backup box and cannot find any ubuntu-backup folder please provide the ubuntu logs in your user temp folder.
thanks. I may have made a mistake, but I am installing again to do a re try to be more sure.

I am not sure where the logs can be seen -  in ubuntu before un install, in windows before or after uninstall, or where/when please?

The re install was under way before I read your comment, so is it possible that it already contains the results of the previous install and uninstall maybe? Should I clean it out before the uninstall activity maybe?

tia

---

### Post by ago on 2008-05-06
If you reinstall after uninstalling the ISO in ubuntu-backup is moved back into ubuntu/install.

Logs are in your user temp folder (%temp%)

---

### Post by candtalan on 2008-05-06
> **ago said:**
> If you reinstall after uninstalling the ISO in ubuntu-backup is moved back into ubuntu/install.

ok but following the uninstall the ubuntu-backup folder did not seem to exist, so I am repeating the install and unistall now to be more sure.

>  Logs are in your user temp folder (%temp%) Apologies I do not understand the nomenclature - if it is for windows I am very out of touch with it anyway :-)

I think I see the log you would want as
c: Documents and Settings\candt\Local Settings\Temp\Wubi-8.04-beta-rev495.log

The file is dated today (I installed yesterday and uninstalled today, and reinstalled today, so th edate would seem ok) and seems to include the install,  uninstall, and reinstall. I will run with this one because the events are apparently appended, albeit without dates. The test of uninstall is about to be done now.

---

### Post by candtalan on 2008-05-06
Result: good
Uninstall went well, and paying (more) careful attention to the checked box regarding backup of iso I realise that it is checked  by default, (to backup the iso). 

What I probably did was to read the backup option and clicked the box not noticing that my action unchecked it!

My grateful thanks for your help and time, much appreciated, and my apologies for my mistake.

---

