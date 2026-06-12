---
title: "Evolution plugin for Exchange not showing contacts"
date: 2017-10-01
forum: General Help
---

### Post by shaq.blogs on 2017-10-01
I recently migrated from Windows to Ubuntu (Gnome 16.04). Privacy issues have tested my patience, and Windows 10 was it!!
Was initially reluctant to try Linux being a hardcore Windows developer. But I am pleasantly surprised, this is certainly a fantastic upgrade over windows. I now feel I should have tried this a few years earlier!

In the process of setting up and exploring the feasibility, I was trying to sync my contacts & calendar from outlook.com. Did some searching around. I ran into 2 options, Evolution & Thunderbird.
Evolution has a really nice look and feel. So I installed the evolution plugin for MS Exchange using the following sudo command <sudo apt-get install evolution-ews>. I was able to add an account successfully.

Currently Calendars are in Sync. But my contacts do not show up in the Contacts Pane. This is what I see in Contacts (See image).
I explored around a bit, and I noticed that in Thunderbird it shows the contacts (using - [Ericsson/exchangecalendar]("https://github.com/Ericsson/exchangecalendar/releases")). But for it to show up in Thunderbird using that plugin, during configuration - I had to select the root of Contacts (Selecting any of the Listed Address Books wouldn't populate it).

In Evolution, Selecting the numerous AddressBooks listed from my account does not populate the default contacts list. I do not see any other options. 
What have I missed? How can I view the contacts?

[ATTACH=CONFIG]276920[/ATTACH]

---

### Post by shaq.blogs on 2017-10-08
Bump.

Anyone???

---

### Post by scottm75 on 2018-05-16
I am also trying to get an answer on this also.  Just switched from Thunderbird to Evolution after learning that Evolution with EWS will allow an exchange email connection.  After a few hick-ups email seems to work fine.  So does calendar.  I just can't get my online contacts from outlook.com to show. I instead get only people who's emails have appeared on any of my emails.  

I have tried multiple server addresses.   A few different ones work to make an establishment.  It seems like any new contact created in either Evoloution or Gnome Contacts will appear in my cloud contacts for outlook.com.  But nothing from that address list goes back to Ubuntu.

---

### Post by scottm75 on 2018-05-16
I solved this one for my self this morning.  In Evolution contacts.  A number of address books are listed.  When choosing to refresh each one.  Only the Contacts one would return an error.  It's listed in my outlook.com contacts.  Removing the address book connection from Gnome Online Accounts did nothing.  In Firefox I logged into my outlook.com account.  Set up a test address book with a test contact.  Information came through to Ubuntu.  Then deleted all of that.  I did try to change the name of Contacts in outlook.com.  Could not.  My final fix was to remove two address lists attached to my Contacts address book in outlook.com.

Everything now syncs with Ubuntu from outlook.com.  This includes, in Gnome Contacts, images of any contacts I have that for.  I've switched off add automatic contacts from emails.  Will have to go through and delete a whole lot.  Also removed a bunch of address books that Evolution adds.    

Glad I got that one solved.

---

