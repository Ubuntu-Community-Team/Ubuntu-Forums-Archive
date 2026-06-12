---
title: "Resume from suspend hangs; last user profile fails to load at login screen"
date: 2016-04-30
forum: General Help
---

### Post by jackbnimble67 on 2016-04-30
**Computer System:** I have Ubuntu 12.04 LTS hosted on an HP Pavilion dm4-1295dx laptop. 

This issue involves two problems that could be considered as two separate issues that have two separate resolutions. However, since the first issue most likely propagated the second, they can presented together. The issues are:  

 
[LIST=1]
[*][B]The laptop hung while in the process of resuming from the     suspend state.
[/B]
[*]**After rebooting, the last logged in user profile failed to     load at the login screen. **
[/LIST]


 **Issue #1** had occurred once before, however, it was not followed immediately by **Issue #2**.  

I've searched the forum for each issue and found some similar ones for **Issue #1**, but not **Issue #2**. I've tried the suggested resolutions for the former, but to no avail. For this reason, and since **Issue #1** may have most likely caused **Issue #2**, I'm posting them together despite the fact that there were similar posts. 

 Also, I don't know if the following is somehow related, but another anomaly occurred that is somewhat similar and may help diagnose **Issue #1**. After leaving my laptop for about 20 minutes or so, I came back to find that it had somehow rebooted. I thought perhaps it had done so as a result of a pending reboot after an update. However, it has never done that before since it has always required user interaction to initiate an update and a reboot. So, then I wondered if it was the result of a virus. However, as an intermediate-level Linux user, I wasn't exactly sure how to proceed in detecting compromises in security.  

 [FONT=Arial][SIZE=4]Issue #1 [/SIZE][/FONT] 

 The laptop had been put in *suspend mode* by closing the lid to the laptop. Upon opening the lid, the system hung in the process of resuming. Since the system was unresponsive, I shut it down with the power button, and then powered it back up again.  

 _**NOTE:**_ I did not think at the time to take note of the last few lines that were displayed on the screen, however, it may have been related to the wireless adapter.  

 [FONT=Arial][SIZE=4]Issue #2 [/SIZE][/FONT] 

 The first time I tried to log back into my account (the account that was logged into when the system went into *suspend mode*), I entered my user credentials at the login screen. The system accepted my credentials, the login screen was replaced temporarily by a flicker of a blank screen, and then the system returned back to the login screen. So, although the system accepted my account credentials, my user profile failed to load. The user credentials were never reported as invalid.  

 _**NOTE:**_ Since I was unable to login to the system with my user account, I logged in as a guest user. Once logged in, I proceeded to create a temporary administrator user account. I then logged out as guest and logged in again using as the new administrator user. I did this for two reasons:  
 
[LIST=1]
[*]To verify     if **Issue #2** is related to that specific user profile or is system     wide (affecting all user profiles). 
[*]To have a     working user profile that enabled me to do administrative tasks in     order to diagnose the issues. 
[/LIST]
 Based on what I know so far, I think that the issue might be related to a system resource that was acquired in my last login, but was unreleased since the system failed to fully resume from the suspend mode. However, I don't know enough about what goes on &#8220;under the covers&#8221; to be sure or know how to identify and resolve it.  

Any help would be appreciated. Thanks in advance!

---

