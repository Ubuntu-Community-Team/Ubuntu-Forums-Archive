---
title: "Evolution &amp; iCal"
date: 2008-03-13
forum: General Help
---

### Post by rodgewilco on 2008-03-13
Hi folkz,

for two days I am trying to combine Evolution and iCal. The very basics work fine. I am able to create a local calendar and publish this calendar as iCal. So far so good. But this is not, what I would like to have. I would like to provide a iCal-Calendar in the internet for my friends and me to work with. So the calendar has to be able to handle multiple users. It should be possible to post new entries as well as edit existing ones. So the people need to have edit-rights. Can anyone tell me how to set up a calendar like this? I realy would like. Maybe i should create the iCal on a free webspace? Thanks for your help in advance

greetz
rodgerwilco

---

### Post by priegog on 2008-03-13
Yeah, well, I'm not too knowledgable on these matters, but a webcalendar seems to be the best way to go. I'll tell you how I achieved the exact thing you described as needing:
I setup a google acoount and use google calendar with it. Then I have a friend with another google account and through there I share my calendar with that friend, making sure to give him full edit rights. 
Then, as a client app on my computer I use thunderbird with the "lightning" and "google calendar provider" extensions(there's probably a way to do it in evolution but I didn't find it at the time and I don't care since thunderbird does exactly what I need) to acces the calendar(using the "private address" for my google calendar and my google login info). My friend uses sunbird with the google calendar provider extension (same difference) to the same effect, using MY calendar's private URL (but HIS login info).
On the upside of this is I can access my calendar anywhere even if I'm not near my PC (even from my mobile phone!) and all the changes are synce'd. Pretty awesome overall.

---

### Post by en______ri on 2008-03-14
Hi Rodgewilko,

I'm really interested to the "very basics" in combining Evolution and iCal.

[INDENT]I'm looking for a way to share/combine the ics-files of iCal on a iMac with Evolution on a Ubuntu notebook. The two computers are locally connected to the same network. In few words: **Evolution should access and eventually modify the iCal-calenders**.
[/INDENT]
Could you please tell me how you did it?

Thank you in advance,
Enri.

---

### Post by rodgewilco on 2008-03-16
As far as I got to know now, it is impossible to modify published calendars. Web-Calendars will be mounted read-only. The workaround I will use now is to edit the ics-file directly using PHP. It's the only way I found. Hopefully there is a better way editing these ics-files using evolution, but I haven't found it yet. The idea of using google calendar is nice, but I would prefer a solution without google, as not everyone of the future user has an google account.

greetz

---

