---
title: "Problem with SMTP config."
date: 2006-12-07
forum: General Help
---

### Post by garvan on 2006-12-07
Howdy,
I have a problem when trying to forward messages that contain attachments or significant amount of content.  Significant means about 1k of data or more.  I've beat my head against my monitor enough such I've resorted to begging for help on this board! ](*,) :-D 
Here is what I know:
1. installed Thunderbird and Evolution and both exhibit the same problem.
2. setup accounts with two email servers Gmail & Bluebottle. Same problem with both servers
3. verified the SMTP accounts are connecting cuz I can send original emails all day long
4. POP works just fine.  I can receive attachments including .jpg
5. I can't find log files from Evolution or Thunderbird - I don't think I'm looking in the right spot.
6. Evolution error dialog appears after a timeout on the send -  Dialog text: 
"Error while performing operation.
 DATA command failed: Connection timed out"

I'm guessing I have a permission problem or ??? on the desktop. I say that as opposed to email client setup, router setup, or ISP.  
Looking for clues please help.
g.

---

### Post by dcstar on 2006-12-08
> **garvan said:**
> Howdy,
I have a problem when trying to forward messages that contain attachments or significant amount of content.  Significant means about 1k of data or more.  I've beat my head against my monitor enough such I've resorted to begging for help on this board! ](*,) :-D 
Here is what I know:
1. installed Thunderbird and Evolution and both exhibit the same problem.
2. setup accounts with two email servers Gmail & Bluebottle. Same problem with both servers
3. verified the SMTP accounts are connecting cuz I can send original emails all day long
4. POP works just fine.  I can receive attachments including .jpg
5. I can't find log files from Evolution or Thunderbird - I don't think I'm looking in the right spot.
6. Evolution error dialog appears after a timeout on the send -  Dialog text: 
"Error while performing operation.
 DATA command failed: Connection timed out"

I'm guessing I have a permission problem or ??? on the desktop. I say that as opposed to email client setup, router setup, or ISP.  
Looking for clues please help.
g.

You can try setting up your own SMTP server (the **postfix** package) and see what happens when you send via that.

---

