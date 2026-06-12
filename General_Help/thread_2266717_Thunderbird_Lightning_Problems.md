---
title: "Thunderbird Lightning Problems"
date: 2015-02-24
forum: General Help
---

### Post by bonzo2 on 2015-02-24
I'm posting here on the Ubuntu forums because I cannot find Ubuntu/Linux versions of compatible Mozilla Thunderbird (email client) and Lightning (calendar add on). Apparently, not all Thunderbird and Lightning versions are compatible and upgrades can be disabling.  

Other posts I've found online refer to Thunderbird and Lightning versions that are only available for Windows, and I'm hoping someone here would be so kind as to share with me which version of Thunderbird and Lightning he/she uses and the links to download Ubuntu/Linux versions.

Thunderbird 31.4.0 (the most recent version) is available in the Ubuntu 14.04 repository, and I've installed it. I selected Lightning 3.3.3 from the add-ons menu in Thunderbird.  Lightning installed but does not function.  

Anyone here have wisdom to share? 

Thank,
Bonzo2

---

### Post by Bucky Ball on 2015-02-24
How does it not function? Installing Thunderbird from the Ubuntu repositories and Lightning from Tools>Add-ons is the right way to go so far.

---

### Post by bonzo2 on 2015-02-25
Hi Bucky Ball, and thanks for replying.

After I installed Lightning, a calendar tab became available in Thunderbird. I added a new calendar thusly: [INDENT]On the network > 
CalDav > 
URL > 
Offline support (yes)
[/INDENT]

After naming the calendar, I got confirmation that it was created. However, the calendar name is followed by an exclamation point and despite being set to synchronize every 5 minutes, the calendar has yet to download a single event all day. Nor will it save events created in Lightning itself. The calendar is completely empty.

Thunderbird has been handling email properly all day. It's just the calendar that is non-functional.

Any clues here as to my problem? Is it the Thunderbird/Lightning incompatibility issue I've heard about?  If so, how do I fix it?

Thank you!

> **Bucky Ball said:**
> How does it not function? Installing Thunderbird from the Ubuntu repositories and Lightning from Tools>Add-ons is the right way to go so far.

---

### Post by Bucky Ball on 2015-02-25
*Thread moved to **General Help**.*

> **bonzo2 said:**
> Is it the Thunderbird/Lightning incompatibility issue I've heard about?

Doubtful. I am using both in 14.04 LTS without issue, but I'm not trying to sync it over a network, so I'd say that is where the problem is.

On the screen where you select 'Caldav', what location are you putting in on the network? Is it valid? Is the syntax correct? Is the server on? Might seem like dumb questions, but worth checking. ;)

Create another test calendar on the computer (not the network) and see if that works just to narrow it down to a problem with the network calendar.

Anything preventing you from using an iCalendar (ICS)? If not, you might want to give that a try also.

---

### Post by sgage on 2015-02-25
I've never had any problem with Thunderbird and Lightning on Trusty. I also use the Google Provider extension, so that I can read and write to gmail calendars - works great.

---

### Post by amanchesterman on 2015-02-25
I have Thunderbird 31.4.0 and Lightning 3.3.3 (same as OP) and I synchronise it with my GMail calendar across the network, using CalDav (like OP) rather than the Google Provider extension. It all works perfectly: I can add/edit an appointment in Lightning and it shows up almost at once in the GMail calendar on my Android tablet, and vice versa. The diagnostic advice given by Bucky Ball is sound, it's unlikely to be a software incompatibility.

---

### Post by bonzo2 on 2015-02-25
I also tried installing Lightning from the Ubuntu repository (Synaptic) in case using the Lightning via add-ons was the wrong approach.  Both types of install resulted in the problems I describe.

> **Bucky Ball said:**
> How does it not function? Installing Thunderbird from the Ubuntu repositories and Lightning from Tools>Add-ons is the right way to go so far.

---

### Post by sgage on 2015-02-25
You still have not said how it 'does not function'. If you click on the settings button (three horizontal lines), you should see 'Events and Tasks'. Click on 'Calendar' and you're good to go.

In my experience, simply installing the extension does not present a calendar tab - you need to select it in Events and Tasks.

I have always done the installation via the Thunderbird extension mechanism, not through the repos...

---

### Post by bonzo2 on 2015-02-25
Hi sgage:

I do have the calendar tab open as you've explained. Thanks. 

Lightning simply does not function at all under CalDAV.  It will neither download appointments from the sever nor will it save events created at the desktop via Lightning. 

 The local calendar in Lightning does seem to work however. While the local calendar has no exclamation marks next to it, the CalDAV/s have exclamation marks next to them. Is there any special meaning attributed those marks (besides general failure to function)? 

Any other ideas?

Thanks,
Bonzo2
 

> **sgage said:**
> You still have not said how it 'does not function'. If you click on the settings button (three horizontal lines), you should see 'Events and Tasks'. Click on 'Calendar' and you're good to go.

In my experience, simply installing the extension does not present a calendar tab - you need to select it in Events and Tasks.

I have always done the installation via the Thunderbird extension mechanism, not through the repos...

---

### Post by bonzo2 on 2015-02-26
Bucky:

Your so-called "dumb" questions made me think. Thanks :wink:

I cut and pasted the URL for the calendars from the service provider,  so I'd imagine the URL syntax is correct. It looks like this:[https://apps.xxxxxxx.com/calendars/test%40xxxxxxx.com/Calendar](https://apps.xxxxxxx.com/calendars/test%40xxxxxxx.com/Calendar). syntactically correct?
Is there a way that I might tell  if it were not? 

What exactly do you mean by "where" am I putting the  CalDAV on the network?  I pasted the CalDAV link in the box when prompted by Lightning. Should  I be doing more?  

The server is always on. 

My local calendar DOES work. May I safely presume that the CalDAV issue is server based?   I don't think it's a connectivity issue  because I've been online  without issue all day. Is there a free calendar service besides Google's that would allow me to test a different CalDAV account?  I don't have another account that includes a calendar.

Thanks for the feedback and your time. I really want to resolve this.

Bye ):P

> **Bucky Ball said:**
> 

Doubtful. I am using both in 14.04 LTS without issue, but I'm not trying to sync it over a network, so I'd say that is where the problem is.

On the screen where you select 'Caldav', what location are you putting in on the network? Is it valid? Is the syntax correct? Is the server on? Might seem like dumb questions, but worth checking. ;)

Create another test calendar on the computer (not the network) and see if that works just to narrow it down to a problem with the network calendar.:wink:

---

### Post by Bucky Ball on 2015-02-26
[QUOTE=bonzo2]My local calendar DOES work. May I safely presume that the CalDAV issue is server based? [/QUOTE]

I would think so, yes, if local calendar works without issue. Must be something to do with either the address you're putting in or the connection to the server. Can you ping the server ok with a terminal or communicate with it any other way?

```
ping ***.***.***.***
```

Where ***.***.***.*** is the IP of your server.

---

### Post by amanchesterman on 2015-02-26
"Is there a free calendar service besides Google's that would allow me to test a different CalDAV account?"

Yes, Yahoo calendar can be synchronised with Lightning via CalDav: instructions are here [https://help.yahoo.com/kb/synching-sln4707.html](https://help.yahoo.com/kb/synching-sln4707.html)

I think you would need to sign up for a (free) Yahoo email account in order to use the calendar, but you could always close the account afterwards if you don't want it.

---

### Post by bonzo2 on 2015-02-26
Bucky ):P

My results from the ping: 56(84) bytes of data. Good, yes? 

Based on your earlier suggestion, I attempted to add the calendar as iCal.  It worked very briefly, but when I tried to edit an appointment, it threw a "modification_failed" java script error at resource://calendar/modules/calUtils.jsm - and shut itself off. It did populate the calendar with many appointments that are still visible, just not editable.

I use Open JDK 7 for java. I dont know if that's an issue or if it needs to be specifically enabled in Thunderbird/Lightning. If so, I couldn't figure out how to do that.

Goofy question: Would you happen to know where the setting is to change the password associated with my CalDAV calendar? I want to make sure I didn't accidentally enter it in wrong initially. 

Thanks for hanging with me (guiding me) as I troubleshoot ahead of hearing back from my service provider. It reinforces my satisfaction in having switched to Ubuntu ... abruptly. :-)





> **Bucky Ball said:**
> I would think so, yes, if local calendar works without issue. Must be something to do with either the address you're putting in or the connection to the server. Can you ping the server ok with a terminal or communicate with it any other way?

```
ping ***.***.***.***
```

Where ***.***.***.*** is the IP of your server.

---

### Post by bonzo2 on 2015-02-26
):PHi amanchesterman:

Yahoo is a great idea for a calendar. 

Thanks much!

> **amanchesterman said:**
> "Is there a free calendar service besides Google's that would allow me to test a different CalDAV account?"

Yes, Yahoo calendar can be synchronised with Lightning via CalDav: instructions are here [https://help.yahoo.com/kb/synching-sln4707.html](https://help.yahoo.com/kb/synching-sln4707.html)

I think you would need to sign up for a (free) Yahoo email account in order to use the calendar, but you could always close the account afterwards if you don't want it.

---

### Post by Bucky Ball on 2015-02-26
No worries, but I'm shooting in the dark really as I don't use Lightning with a network, only locally. ;)

---

### Post by speartip on 2015-02-26
i know i'm jumping in a bit late here. But if I were you I wouldn't use lightning from the addons in Thunderbird.
In the repos you want the package xul-ext-lightning, which should pull in xul-ext-gdata-provider & xul-ext-calendar-timezones.
If not you can install them manually.
Lightning should then work fine using CalDav & Google or any other account.

---

### Post by bonzo2 on 2015-02-26
Hi speartip:

Thanks for jumping in here. I have already removed the Lightning version obtained through add-ons in Thunderbird and added xul-ext-lightning through Synaptic (which then appears in extensions as Lightning 3.3.4).  My CalDAV calendar did not work with either version of Thunderbird, but I settled on the repository version just to be safe. At least now I know I have the most compatible version of Lightning. 

Please feel free to jump in again. I'm still sorting this out.


> **speartip said:**
> i know i'm jumping in a bit late here. But if I were you I wouldn't use lightning from the addons in Thunderbird.
In the repos you want the package xul-ext-lightning, which should pull in xul-ext-gdata-provider & xul-ext-calendar-timezones.
If not you can install them manually.
Lightning should then work fine using CalDav & Google or any other account.

---

### Post by Bucky Ball on 2015-02-26
Others have the regular repo version working fine with what you're doing. My feeling is that it isn't that, but something locally, perhaps on the server side. Puzzled as to what.

---

### Post by bonzo2 on 2015-02-26
Bucky et al,

I will report back when this gets sorted out.  My next step is to install another CalDAV calendar. 

bonzo2

> **Bucky Ball said:**
> Others have the regular repo version working fine with what you're doing. My feeling is that it isn't that, but something locally, perhaps on the server side. Puzzled as to what.

---

### Post by speartip on 2015-02-27
Just a quick question.
Are you using Google as your service provider or someone else?
The reason I ask is that I have had Lightning & Google working flawlessly since I can remember, so if you're using Google I may be able to help.

---

### Post by sgage on 2015-02-27
If you want read/write access to a Google calendar, use the Google Provider for Lightning available through Extensions. It has been reworked to use the newest Google API's for its calendar. It has worked flawlessly for me for months now. I've never used CalDav or the like.

---

### Post by bonzo2 on 2015-02-27
sgage,

Thanks for the Google calendar info. I don't have a Google calendar, although I wish my calendar worked as smoothly as your Google calendar does.  

I have not been able to set up a CalDAV account yet because none of my email accounts includes a calendar and it would seem that those services that do provide CalDAV calendars require a cell phone number.  I'm hesitant to give out my number for a throwaway account, so I'm still working on how to test Lightning with CalDAV.  Hmmmm.

;-0
Bonzo2


> **sgage said:**
> If you want read/write access to a Google calendar, use the Google Provider for Lightning available through Extensions. It has been reworked to use the newest Google API's for its calendar. It has worked flawlessly for me for months now. I've never used CalDav or the like.

---

### Post by bonzo2 on 2015-03-15
Hello:

I apologize for abandoning this thread.  I thought I posted a follow up.  It turns out that my calDav and carDav links were both bad.  I am back to enjoying Thunderbird & Lightning, both sourced from the Ubuntu repository.  I'm also having great luck with the SoGo connector. Thanks so very much for everyone's assistance in helping me solve this. 

Bonzo2

---

