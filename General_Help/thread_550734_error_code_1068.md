---
title: "error code 1068"
date: 2007-09-14
forum: General Help
---

### Post by mybrownie092201 on 2007-09-14
RAS Fails w/ Error 1068 "RIP for NWLINK Failed to Start"
View products that this article applies to.
Article ID : 165941 
Last Review : November 1, 2006 
Revision : 1.1 
This article was previously published under Q165941
SYMPTOMS
After you install Remote Access Service, you receive the following error: 
Error starting Remote Access Service on <servername>. Check the Event log on <servername> for details. Error 1068: The dependency service failed to start. 
The System Event log on <servername> contains the following errors: 
   Event Id 7000
   The RIP for Nwlink IPX service failed to start due to the following
   error: The parameter is incorrect.

   Event Id 7001
   The Remote Access Service depends on the RIP for Nwlink IPX service
   which failed to start because of the following error:
   The parameter is incorrect.
				
Back to the top

CAUSE
If you install Remote Access Service after you install a Service Pack, an older version of Nwlnkrip.sys is installed. 
Back to the top

RESOLUTION
To resolve this issue, reapply the Windows NT Service Pack. 

Back to the top


--------------------------------------------------------------------------------

APPLIES TO
• Microsoft Windows NT Workstation 4.0 Developer Edition 
• Microsoft Windows NT Server 4.0 Standard Edition 

Back to the top

Keywords:  kbnetwork kbsetup KB165941 

Back to the top
:

Is there any other way to fix this seeing as I have lost my installation software???  PLEASE HELP!!!

---

### Post by wirelessmonkey on 2007-09-14
Well, if you are actually using Win NT 4.0, you'll need to download the latest service pack (quite old) and install/reinstall it.   I THINK this is the latest [http://www.microsoft.com/downloads/details.aspx?FamilyID=e396d059-e402-46ef-b095-a74399e25737&DisplayLang=en](http://www.microsoft.com/downloads/details.aspx?FamilyID=e396d059-e402-46ef-b095-a74399e25737&DisplayLang=en)

But you may want to spend some time searching MS downloads.

---

### Post by mybrownie092201 on 2007-09-14
Ok thanks, however I am not sure if i am using Win NT, How would I find that out?  I know that I have XP operating system.

---

### Post by mybrownie092201 on 2007-09-14
Would that solve the issue of error code 711 as well which was my original issue and seems to be caused by error code 1068?

---

### Post by wirelessmonkey on 2007-09-15
Well, apparently you have Windows XP then, not Windows NT (quite old).  What exactly were you trying to do when this happened? Error code 1068 is different for XP machines, but I'm not sure on the specifics.  What were you doing to get error code 711, and can you give me any more details?

---

### Post by wirelessmonkey on 2007-09-15
Here's a quick google search answer, does it help your problem?

[http://wiki.answers.com/Q/Why_does_'Error_1068_The_Dependency_Service_or_Group_Failed_To_Start'_appear_when_starting_the_remote_access_auto_connection_manager_in_Windows_XP](http://wiki.answers.com/Q/Why_does_'Error_1068_The_Dependency_Service_or_Group_Failed_To_Start'_appear_when_starting_the_remote_access_auto_connection_manager_in_Windows_XP)

---

