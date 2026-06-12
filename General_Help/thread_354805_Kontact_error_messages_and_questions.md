---
title: "Kontact error messages and questions"
date: 2007-02-06
forum: General Help
---

### Post by Village on 2007-02-06
Hi there,

After playing around with Ubuntu I've found that Kubuntu seems to work better with the wifi and I as I'm a big email, address book and calendar person Konctact is better for me. So KDE it is for a while at least.

That said I have been getting the follow error messages. I'm not sure what they are to do with. They could be because of some iCal's that I put into it from Google Calendar?  See below.


> Could not rename partial file /var/tmp/kdecache-XYZ/kcal/kresources/pGnnebtKl7.
Please check permissions.

Could not rename partial file /var/tmp/kdecache-XYZ/kcal/kresources/iRgBlR4VLj.
Please check permissions.

Could not rename partial file /var/tmp/kdecache-XYZ/kcal/kresources/kBJGXVHQSU.
Please check permissions.

XYZ is an edit, that's where my name is. These each pop up as a separate error messages.

Also just a couple of other Kontact related questions if people know the answers;

1. I have a Sony Ericsson W800i (although I might be upgrading soon) what's the best program to get it to sync between the w800i (or any mobile/cell phone) and Kontact? Contacts and Calendar would be very useful, used to do this all the time in Windows.

2. I'm going to assume that this is possible, but ask never-the-less (I'm new, sorry!). If I have an iCal on my own domain, can I use Kontact to edit the iCal entries without having to use the web browser. Currently I have a google Calendar and I know that you can't do that because Google won't let you (its their product, their choice). But I am going to be buying my own domain, and have the ability to set it up. I thought that this could be more useful as I would still have the check it anywhere in the world ability and have a program which I can hopefully sync up with my phone.

Any suggestions?

Thanks,

Village

---

### Post by utkjamie on 2007-03-20
From what I've picked up, the Kontact problem you are having is due to both Kontact and the Korganizer Reminder Daemon simultaneously trying to access the same file. Apparently the "first one there" locks the file and the other reports the error. It seems to be a fairly widespread problem (see the Google results: [http://tinyurl.com/3atgfr)]("http://tinyurl.com/3atgfr%29"), so I hope the developers will fix it soon. In the meantime, I know of no workarounds. If you come across any, please pass them on.

Like you, I'm crossing my fingers for a way to sync Kontact and Google Calendar. In the meantime, I have Kontact pulling my Google Calendar information into Kontact. I wrote a shell script that periodically uploads my Kontact calendar to an FTP site I maintain. I then have Google Calendar subscribed to that exported calendar. In this way both Google Calendar and Kontact have all of my calendar entries (and I can take advantage of adding new calendar entries to Google Calendar with my mobile phone). The downside is that Google Calendar seems to only update remote calendars once or twice a day and therefore isn't entirely up to date.

---

### Post by Village on 2007-03-21
Thanks for the information, looks like I'll just have to wait until the developers fix the problem. I'm also waiting for some kind developers to work on Sync software, its still quite new, but the sooner it gets finished the better.

Village

---

### Post by DJRumpy on 2007-10-29
FYI you can use GCALDaemon to sync your google calendar directly with contact at whatever interval you choose.

The downside is that if you define more than one calendar in Kontact, it also causes the above problem to appear ;)

It's great for a single calendar though.

---

