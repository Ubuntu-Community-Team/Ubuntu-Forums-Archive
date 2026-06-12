---
title: "Evolution and Google Calendar"
date: 2008-03-31
forum: General Help
---

### Post by jonathanpiper on 2008-03-31
I looked in the other Evolution/GCal threads, couldn't seem to find this particular problem.

I'm running Hardy, and was really excited about the whole Evolution/GCal syncing thing.  Well, I can create the calendar in Evolution (name it, enter a username, pick a sync interval, etc), but it won't ever load.  It won't ask for a password, either.  What's even  more confusing is, every subsequent time I got to edit the details of the calendar, it deletes the username that I've entered, and it often changes the sync time back to default (30 minutes).

Basically what I'm asking is, how the heck do I get this to work, or is the feature just not ready yet?

---

### Post by cujo on 2008-04-03
I have the exact same issue.  Hopefully someone knows a solution and will share it here.  Cross your fingers.

---

### Post by ReddogOne on 2008-04-04
Just read on another thread it is known not to work. So no solution but to wait or put your coding hat on!

---

### Post by azinas on 2008-04-05
So there is** not even a clue** about whats wrong with google calendar and evolution? What if we change settings on GCal? or if its a** theme problem**? [Cause there was an issue with a theme called_ Murrina_ *(or some other name I cant remember right now)* which caused Evolution to crash whenever you tried to click the calendar tab.] I guess I'll just eat my :popcorn:

---

### Post by rfdeshon on 2008-04-14
I don't know about anyone else, but I've gotten my Google Calendar to LOAD but I can't make events and actually have them sent to my google calendar. I create the event, it shows in Evolution, never shows up in Google Calendar then when I close and start Evolution again, it is gone. It did prompt me for my password for google when I first set it up but never since. I've even deleted the calendar and created it again and it didn't prompt, just loaded. This leads me to believe that it's not removing its settings if you delete the caledar (I also can't find where it stores them) and that it may just be reading the public calendar instead of accessing the private one.

---

### Post by the_analyzer on 2008-04-14
> **rfdeshon said:**
> I don't know about anyone else, but I've gotten my Google Calendar to LOAD but I can't make events and actually have them sent to my google calendar. I create the event, it shows in Evolution, never shows up in Google Calendar then when I close and start Evolution again, it is gone. It did prompt me for my password for google when I first set it up but never since. I've even deleted the calendar and created it again and it didn't prompt, just loaded. This leads me to believe that it's not removing its settings if you delete the caledar (I also can't find where it stores them) and that it may just be reading the public calendar instead of accessing the private one.

what Ive read from a blog is that the sync with the google calendar and evolution, is read only, so you cant add or edit events from evolution. :(

---

### Post by niceguy123 on 2008-04-17
&#8206;This seems to be the anwser. Not hard at all. 
[http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php](http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php)

> Linux users: Setting up read access for your Google Calendar from the integrated Gnome calendar (included with Evolution) can be achieved with one terminal command. In fact, it is surprisingly simple to set up a self-updating subscription to your Google Calendar. You only need to enter the following command once and your calendar will automatically update.

    Go to your Google Calendar and find out your private ICAL URL (This can be found after clicking Manage Calendars > Your Calendar Name)
    Now, open a terminal and type :
    /usr/lib/evolution-webcal/evolution-webcal YOUR_PRIVATE_ICAL_URL

That's all there is to it. The dialog shown in the screenshot will appear and you'll be able to customize how frequently you want the Gnome calendar to update. When you click the calendar in the Gnome menubar, your events will be displayed.
Google Calendar & Gnome [Cagdas's Blog]

---

### Post by AldenIsZen on 2008-04-20
This didn't work as I thought, as Simon mentions below.

---

### Post by SimonJW on 2008-04-21
I think that method only gives you read access unfortunately, whereas the new system in Evolution should theoretically give you read/write access to your Google Calendar. 

I guess until the bug is fixed, if you really need read/write access, you can use the gcal daemon mentioned a few posts ago.

---

