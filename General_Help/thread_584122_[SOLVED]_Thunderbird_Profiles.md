---
title: "[SOLVED] Thunderbird Profiles"
date: 2007-10-20
forum: General Help
---

### Post by measekite on 2007-10-20
I now have Thunderbird 2 up and running on Feisty.

I would like Thunderbird to be able to access and share my profile in my Windows partition.  I used the Tools>Import command and the dialog box did not show how I can access my profile so I can get at my folders and my address books.  I have multiple address books.

I would also like to be able to access and combine the sunbird portion so I have a calendar

Any body have any ideas.

---

### Post by measekite on 2007-10-22
> **measekite said:**
> I now have Thunderbird 2 up and running on Feisty.

I would like Thunderbird to be able to access and share my profile in my Windows partition.  I used the Tools>Import command and the dialog box did not show how I can access my profile so I can get at my folders and my address books.  I have multiple address books.

I would also like to be able to access and combine the sunbird portion so I have a calendar

Any body have any ideas.

[COLOR=Red]**SOLUTION**[/COLOR]
It is now working.  Here is what I did.  First I found a folder that can be accessed by both Ubuntu and Windows.  I then moved the Thunderbird Profile folder from Documents and Settings\Application Data (or where ever the default is.  I then brought up Thunderbird and did Edit>Account Settings>Server Settings and changed Local Directory to the new location.  I then clicked  **advanced  **and chose the first radio button  Inbox for this servers account.

Then I booted Windows and did the same thing.  After I found my address book and exported it to an LDAP file in the same location as the profile.  I then shut down windows and booted ununtu.  I then imported the LDAP phone book.  I cut and pasted the entries into the existing address book and then deleted the imported phone book keeping the default entry with the copies addresses.  If you have other phoen books you use the same proceedure.

What I now have is two separate copies of Thunderbird 2.0 running on two different OS (not at the same time) each pointing to the same Profile.  The phone books were imported.
**[COLOR=Red]END SOLUTION[/COLOR]**




END SOLUTION

---

