---
title: "Evolution Exchange Calendar Sync"
date: 2007-05-11
forum: General Help
---

### Post by tebbendj on 2007-05-11
I am running Feisty and I have problems getting Evolution and Exchange to sync calendars using the evolution-connector.  Updates on my local calendar do not make it back to the Exchange server.  (Emails seem to work fine).  I have made sure that I am actually making changes to the Exchange calendar, and not just a local or some other calender.  Also, when I restart Evolution it removes the entire Exchange calender and reloads it from the OWA server, which in turns deletes any changes I made to my calendar from the Ubuntu/Evolution side.  I have searched both these forums and Google, but cannot find anyone else having this problem.

---

### Post by nampat on 2007-12-04
Hi.

I have the same problem. When I create some meeting in evolution, it wonät sync it to the exchange. When I creat meeting from my mobile phone and sync it with exchange, i can see created meeting in evolution. But somehow it won't sync from evolution to exchange.

Any ideas? It is real showstopper in my everyday work :(

---

### Post by Seadhi on 2008-02-28
I am having the same exact problem.  Is there any more information on this?

---

### Post by tlinden on 2008-04-08
We have the same problem. We are trying to replace all windows desktop with Ubuntu desktops. But for that we need Evolution to work correctly with exchange. 

We sync our appointments trough owa to our mobile devices (Using mailforexhange within symbian). At this moment appointments created in evolution are not synced to the mobile devices.

---

### Post by tlinden on 2008-04-08
Check [http://bugzilla.gnome.org/show_bug.cgi?id=403903](http://bugzilla.gnome.org/show_bug.cgi?id=403903)

---

### Post by AldenIsZen on 2008-04-20
You have to be running Hardy... [http://ubuntuforums.org/showthread.php?t=740925&highlight=evolution+google+calendar](http://ubuntuforums.org/showthread.php?t=740925&highlight=evolution+google+calendar)

 OR a direct link: 

[http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php](http://lifehacker.com/software/linux-tip/automatically-subscribe-to-your-google-calendar-297960.php)


Go to your Google Calendar and find out your private ICAL URL (This can be found after clicking Manage Calendars > Your Calendar Name)
Now, open a terminal and type :
/usr/lib/evolution-webcal/evolution-webcal YOUR_PRIVATE_ICAL_URL


 I used [http:///wwww.google.com](http:///wwww.google.com) and all.... It seems to working to some extent!

---

