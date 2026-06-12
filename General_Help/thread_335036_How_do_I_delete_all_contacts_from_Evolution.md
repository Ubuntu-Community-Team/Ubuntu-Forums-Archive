---
title: "How do I delete all contacts from Evolution"
date: 2007-01-09
forum: General Help
---

### Post by tc101 on 2007-01-09
I tried to import some calender data and did something wrong and it was imported into my contact list.  I need to delete the whole list.  Is there a way to do this?

Also, has anyone successfully imported calendar data into evolution?  Yahoo calendar let me export the data into a csv file, but I have not been able to import it into evolution.

---

### Post by meng on 2007-01-09
Contacts, click on one, press ctrl-A (select all) and delete!

---

### Post by tc101 on 2007-01-09
I figured out how to delete all contacts.  I just did a select all, then did a delete. I still need to get import the calendar data if that is possible.

---

### Post by Zimmer on 2007-01-09
> **tc101 said:**
> I tried to import some calender data and did something wrong and it was imported into my contact list.  I need to delete the whole list.  Is there a way to do this?

Also, has anyone successfully imported calendar data into evolution?  Yahoo calendar let me export the data into a csv file, but I have not been able to import it into evolution.

Yes, from a previous version of Evolution, it is held in /.evolution/calendar/local/system  folder as calendar.ics 

look at file>import > single file  in Evolution and see if any of the file types in the drop down list correspond to any of the options given by Yahoo export facility   eg..vck .ldif .ics  etc.

Then export from Yahoo in the relevant format.

Hope this is of help

---

### Post by tc101 on 2007-01-09
Yahoo will only let me export the calendar as a CSV file.  When I try to import that CSV file into evolution, even though I am in calendars, it imports it into the contacts, which makes a mess, I have to delete all the contacts and then reimport the contacts.

I did a google on evolution import calendar, and it seems there have been problems with this in previous versions.  Where is the best forum to ask about this?

---

### Post by Zimmer on 2007-01-10
> **tc101 said:**
> Yahoo will only let me export the calendar as a CSV file.  When I try to import that CSV file into evolution, even though I am in calendars, it imports it into the contacts, which makes a mess, I have to delete all the contacts and then reimport the contacts.

I did a google on evolution import calendar, and it seems there have been problems with this in previous versions.  Where is the best forum to ask about this?

I have found references to linking to Web Calendars from Evo,
Have you tried first linking to the Yahoo calendar   New>Calendar  then change type to  'On the web'
and fill in the required info on the subsequent form..  I have no web calendar to experiment with this, so it is more of a hint from me , rather than a rock solid solution.. 
or import directly from the Yahoo calender by pointing the importer directly to it.

You may want to backup your /.evolution/addressbook/  folder before trying import again, so you can easily replace the contacts if they get messed up again.
There is this link for Google calendars, which, if Yahoo is similar, could be of use...
[http://johnnyjacob.wordpress.com/2006/04/30/google-calendar-in-evolution/](http://johnnyjacob.wordpress.com/2006/04/30/google-calendar-in-evolution/)

Otherwise.....
    *
[http://www.scheduleworld.com/tg/calendarInterop.jsp](http://www.scheduleworld.com/tg/calendarInterop.jsp) says...
      Yahoo!
      ScheduleWorld used to be able to import/export the Yahoo! CSV format but something has changed and this no longer works. Hopefully this will be working again shortly.
      You may have some luck if you export your Yahoo! calendar data, then open it in a text editor and page wrap the entire document. On Windows you also may need to go to format, font, and use Kern. The file may then import properly.....

This sort of method would have been my final suggestion , that is , manually making the .csv file into the format of the required .ics file for Evolution.
The efficiency of this would depend on
 1) How much calendar data you had on Yahoo ( could be quicker to type in your appointments to Evo ): ) and 
2) How much editing the .csv file required to convert it to .ics

for this you would need to create a calendar in Evo and view the resulting .ics file and compare it with the data in the .cvs... to see if the simple text wrapping suggestion above is of any use...

---

### Post by tc101 on 2007-01-10
Zimmer, thanks for taking the time to research and explain all of that.  You have pointed me in the right direction.  I bet I will get it working one way or another with your suggestions.

---

### Post by tc101 on 2007-01-11
I finally got the calendar data from yahoo into evolution.  

For anyone who has to do this in the future, here are the steps I had to take.  There may be a quicker way but this worked.  

I exported the yahoo calendar as a cvs file.
I imported that into google calendar.
I made google calendar public.
In evolution I went to new/calendar and created a web calendar with the address of the google calendar.  I had to use the version with the .ics address.  Google give you three address options.  They are XML, ICAL, and HTML.  ICAL is the one you need.

After I had the google calendar linked in evolution I saved it to disk.

I then imported that calendar file saved to disk, which also ended in .ics to create an evolution calendar that is on my computer and not linked to google.

I probably could have skipped using google and just shared the yahoo calendar, but I was confused and experimenting.

---

### Post by Zimmer on 2007-01-11
Glad you have succeeded and posted your route to success, it always helps those who search the threads after.. :)

---

