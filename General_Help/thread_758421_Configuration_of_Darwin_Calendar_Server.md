---
title: "Configuration of Darwin Calendar Server"
date: 2008-04-18
forum: General Help
---

### Post by ninotob on 2008-04-18
I recently installed Darwin Calendar Server ("DCS") at my office and I am so pleased with it.  We run a mixture of Mac laptops, Ubuntu desktops, and a Suse server.

Installing DCS is covered elsewhere on the web, so I won't get into that here.  What I didn't find much info on, was how to configure the thing once its running.  I'm sure Leopard server (which starts at $500) has a lovely GUI interface for the iCal server -- cheapskates like me (and maybe you) who want to run it on a linux box are left with a handful of text files to do the configuration.

This config info is not Ubuntu specific -- should work on any installation of DCS -- but I have an account here and Google cerainly indexes these forums quickly.  Anyway, let's get started.

First off you must have DCS installed corectly and be able to run the server.  You can install it anywhere you want, but lets just say that for testing purposes you've installed it in your home directory in a folder called "calendar".  Also, for the purposes of this example, let's pretend your username is "joe".

The server startup script ("run") will reside in:
/home/joe/calendar/CalendarServer

The configuration files will reside in:
/home/joe/calendar/CalendarServer/conf

The files in conf that you will need to modify are:
* accounts.xml
* caldavd-dev.plist
Optionally, if you want to name your caldavd-*.plist file something different than the default name, you will need to edit the "run" script at /home/joe/calendar/CalendarServer/run

If you decide you want a custom plist file name, start with modifying the "run" script so that the plist plainly references your calendars.  Go to line 161 of the run script, and replace "caldavd-dev.plist" with whatever you want the file to be called, for example:  caldavd-home_cals.plist

IF YOU DO THIS, make sure that the file exists in conf.  Start by copying caldavd-test.plist to your prefered file name.  

IF YOU DON'T modify "run", copy caldavd-test.plist to caldavd-dev.plist in the conf directory and use the caldavd-dev.plist file to edit below.

Either way, let's jump into the plist file.  There isn't much to edit here, leaving most everything at default worked fine for me.  Around line 73 however, you will find the "document root" path.  The default path is quite "twisted" (ha ha): twistedcaldav/test/data/.  I made a new folder in the CalendarServer directory called "home_cals" and edited the document root string to be "home_cals/" (and at work: office_cals).   Not necessary but the default folder seems sort of obscure to me and a year from now when I've forgotten this, I'd like to be able to find the folders easily. 

Next up, set up users and groups.  I hadn't worked with a shared calendar server before, so it took me a while to get the notion through my head that if I want a calendar that multiple people can edit, it needs to be a group calendar.  

Let's setup users first, and then a couple shared calendars.  Let's assume there are three people in your household: Joe, Jane, Jeffy

Open up "accounts.xml" and basically just fill in the blanks (after a little copying and pasting).  You well get 3 user sets that look like:

```
<user>
  <uid>Joe</uid>
  <password>JoesPass</password>
  <name>Joe Doe</uid>
  <cuaddr>mailto:joe@somewhere.com</cuaddr>
</user>
... repeat for Jane and Jeffy
```

Now setup some groups:
```
<group>
  <uid>Grownups</uid>
  <password>AdultPass</password>
  <name>Big People Calendar</name>
  <members>
     <member type="users">Joe</member>
     <member type="users">Jane</member>
   </members>
</group>

```
You could repeat this with another calender named "Everyone" and include Jeffy in the members group.

There you have it.  Users and accounts all setup for a home calendar system with two group calendars, one for Mom and Dad only, and one for Mom Dad & Kid (assuming you set up Jane and Jeffy as users and an "Everyone" group including all three users as members).  

Now, point your webbrowser at the server, either localhost:8008 (or 8443 for ssl), enter a username and password, then click "principals", "groups", and then the group name of the calendar you want to use.  What you will see is not a beautiful shared calendar, but a page of links to the calendar.  You can use these links directly in Apple's iCal (Leopard version) to hook up with your calendar (e.g. "http://localhost:8003/principals/groups/GROUP_NAME").  

HOWEVER, if you are going to use **Mozilla Sunbird**, these links will cause you no end of grief.  Instead, follow the instructions rigorously at [the DCS site]("http://trac.calendarserver.org/projects/calendarserver/wiki/Sunbird"), except instead of a user calendar, you will enter a group calendar:
```
http://localhost:8008/calendars/groups/GROUP_NAME/calendar
``` 
Every user listed as a member in the group section of the accounts.xml file will be able to access the calendar with their own username and password.

Note: substitute "GROUP_NAME" with whatever you named the group, e.g., in above example "Grownups".  

Also Note:  If you are not on localhost, substitute the name or IP of the computer on your network hosting the calendar server.  Feel free to replace 8008 with 8443 if you feel the need to encrypt.

---

