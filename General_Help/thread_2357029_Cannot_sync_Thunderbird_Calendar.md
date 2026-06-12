---
title: "Cannot sync Thunderbird Calendar"
date: 2017-03-29
forum: General Help
---

### Post by Nailhac on 2017-03-29
I use Ubuntu 16.04 with Thunderbird calendar and have installed "provider for google" add on to enable syncing to smart phones. I have a similar set-up with win 10 which works perfectly but for some reason cannot get ubuntu set-up to sync with smart phones. I would be grateful for any suggestions.

---

### Post by speartip on 2017-03-29
Just to clarify.
I don't think Thunderbird syncs with your smartphone. Do you mean that Thunderbird syncs with your Google Calendar, which is what your smartphone is doing as well?
If so, are you saying that you cannot get Thunderbird to sync with your Google Calendar?

---

### Post by Nailhac on 2017-03-29
Hi speartip
I use thunderbird calendar extension "lightning" with win 10 which syncs with my android smartphone which runs google calendar. I use the "google provider" add on for the sync.
I have installed same in ubuntu but for some reason it does not function.

---

### Post by speartip on 2017-03-30
I think you misunderstand what is happening here. Lightning isn't syncing with your smartphone. They're all just syncing with your google calendar. So when you add something in Lightning, it syncs with your google calendar, which you are then picking up with your smartphone.
Regardless. Are you saying that in Ubuntu, you cannot get lightning to sync with your Google Calendar?
If so did you add xul-ext-lightning & xul-ext-gdata-provider, from the official repos or from some other place?

---

### Post by Nailhac on 2017-03-30
I installed lightning as an add-on to Thunderbird under tools option in Thunderbird.

---

### Post by speartip on 2017-03-30
Best to uninstall that then, & use the 2 official packages in the repos as per my last post.
Lightning should sync flawlessly then.

---

### Post by Nailhac on 2017-04-06
Hi speartip
I did as you advised but still cannot get lighnting to sync. After the failed result I ran sudo apt-get remove --auto-remove xul-ext-lightning which removed everything associated with lightning and then re run the get lightning command again all to no avail. Maybe I should just use google calendar instead?

---

### Post by speartip on 2017-04-06
So when lightning was installed, and you tried to create a new calendar, did you get any error messages after you entered your Google user name and password? Also do you have 2 step verification enabled in google?

---

### Post by Nailhac on 2017-04-07
No error messages and no I do not have two step verification.

---

### Post by speartip on 2017-04-07
[SIZE=2][FONT=tahoma]In that case, I've no idea why it's not syncing.
So instead let's try the CalDAV alternative.
At this point it's probably worth deleting all your non-working Calendars. 
 In Thunderbirds Menu, follow the same procedure, "New Message" "Calendar", Obviously tick the "on the network" box, and Next.
Now instead of ticking "Google Calendar", tick "CalDAV". In the location box, you will want the following line:

                     [/FONT][/SIZE][SIZE=2][FONT=tahoma] [https://apidata.googleusercontent.com/caldav/v2/](https://apidata.googleusercontent.com/caldav/v2/)[COLOR=#FF0000]*yourgmailaddress*[/COLOR]/events

Obviously changing the red italics for your own gmail address.
You will then be asked for your gmail password, & given a final message that "your calendar has been created".
All should then be OK.[/FONT][/SIZE]

---

### Post by Nailhac on 2017-04-08
I do not understand your instructions in Thunderbird "new message" or "calendar" as no references are now made to calendar as it has been uninstalled.

---

### Post by speartip on 2017-04-08
If you don't understand, how have you tried creating and syncing your calendar previously?
I'm only asking because I feel your probably not setting it up correctly. 
It would be good if you could post back exactly what you've tried to do.
Also if you still have Lightning installed, the instructions in my previous post should be pretty easy to follow.

---

### Post by Nailhac on 2017-04-08
Hi speartip
The reason I could not access "New Message" and Calendar was I had uninstalled lightning instead of deleting calendars. I reinstalled lightning and associated google provider then deleted calendars and followed your instruction. All working OK, I appreciate your help. Thank you.

---

### Post by speartip on 2017-04-08
Good to know you're sorted. I always tend to use caldav, it seems to be more reliable.

---

