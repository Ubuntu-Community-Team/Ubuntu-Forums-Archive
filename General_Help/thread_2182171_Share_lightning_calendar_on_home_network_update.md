---
title: "Share lightning calendar on home network update"
date: 2013-10-20
forum: General Help
---

### Post by ShaMonkey on 2013-10-20
Hi, this is my first thread and I'm responding to another thread that was closed before it was solved. The other thread was titled
**[Share lightning calendar on home network]("http://ubuntuforums.org/showthread.php?t=1840564")**

As you can see from the title member, Benchrest, asked if it was possible to share a lightning calendar on your home network. I'm trying to do this as well. I have ubuntu and use thunderbird with the lightning add-on for my calendar and tasks. I would like this calendar to be a family one and share it over our network here at home. You would think in our connected world this would be easy but not so much. There are mountains of info on connecting to google calendar. The entire enternet apparently only wants to connect to google calendar. Well I don't, and I'm trying to find out is it possible to share a lighting calendar over a home netork? 

at the bottom of the other thread Rattle1 posted:                                   

 **Re: Share lightning calendar on home network**
        If I go to from Thunderbird if I go EDIT / CALENDAR PROPERTIES I   see Calendar name HOME and Location moz-storage-calendar://                      [INDENT]      
 Hi,  I was looking for same issue and found that for Location you must enter  "file:///[COLOR=Blue]server-name\folder-name\file-name[/COLOR].ics".  For me it worked, although I'm  running Windows on both systems. I will  try this with my Linux system home, see if it works, but I don't think  there will be any issues.                 
[/INDENT]
            
                         
 He almost had it. In lightning, when you create a new calendar you can choose "On My Computer" or "On the Network". If you go for the one on your computer you don't get any say on how or where it's stored. If you go for the network calendar you get to pick from a few formats and then choose a location. However every time I put a location from my local computer a drop down says "Please enter a valid location". This is where Rattle1 came in. He was using a network server. If you want to create the file on your own machine for location you have to type (without the quotes)
"file://location/calendar name.ics"
 for example file:///home/folder name/shared calendar.ics

you must start with file:/// and you have to give you calendar a name and it will be created. I even used folder and file names with spaces and had no problem at all. It will create the file where you say.
-Question, 
1. of the format options (ICS, calDAV, WCAP) wich is the best to go with? Will windows recognize any of them?
2. if I store this on a shared drive, how does everyone else in the family use it?

Thanks guys
ShaMonkey

---

