---
title: "Parental Monitoring and Control on Linux"
date: 2007-06-15
forum: General Help
---

### Post by dragonfyre13 on 2007-06-15
I'm looking for a specific type of App, and not finding it. I'm introducing and switching friends left and right to linux, and there is a specific app that some of them need that is a deal breaker. It's Parental Monitoring software. It would be nice if there was control software (though that's easy through any kind of proxy) as well, but mainly the monitoring part is what is needed. It should monitor IMs (easy through GAIM, but able to be switched off by anyone) and emails and websites visited (including the information within the website ideally).

[SIZE="5"]**Here's what I've found so far:**[/SIZE]
_Squid_ - Website access control and website (just address) monitoring.
_Gaim_ - Logging functionality, though it can easily be turned off by going to preferences menu.
_Email_ - Some kind of email server to grab all emails going through the server? I haven't gotten to this part yet, as it's lowest priority to me.
_Keylogger_ - There is one keylogger in the repositories, though it is VERY difficult, no interface, and is unreliable with USB keyboards and such.
_Screenshots_ - Plenty of screenshot programs, but I haven't found one that I can schedule recurrently (like every minute) or take pictures only when the mouse has been moved recently, or keys have been typed. Also, this would likely need to be hidden, which is possible since most allow commandline manipulation.

[SIZE="5"]**Here's my ideas that I don't know enough to see if they are possible:**[/SIZE]

Squid supports Cache, and can cache full pages locally (I believe). I'd like a way to rebuild those webpages after they are already accessed, and view exactly what the user saw on the webpage. I believe this is already available for the last time the page was visited through viewing cached data by it's ID (? This is hearsay by a squid guy at work. Never actually touched squid myself before.) This would allow viewing of webmail, and myspace messages for example. This would not cache ajax information though, which would be needed so that sites like Meebo would be monitored as well, which is where the keylogger comes in.

There are a few (2 I think) keyloggers available for linux. If I could tie these in to other monitoring software, this could be quite useful. It would show when certain things were bypassed, or something failed within the monitoring solution.

Screenshot programs are prevelent, but I don't know of one that runs silently, or takes constant screenshots every X minutes. Also, tying this into the keylogger in a way that would allow us not to take screenshots unless the mouse has moved or keys have been pressed in the past 3 minutes would be something to look into, as we don't want to take screenshots when no one is actually doing anything.

**[SIZE="5"]End Result[/SIZE]**
Once all this gets figured out, it wouldn't be hard to put all of it into a web interface. The images get stuck in a directory that is parsed by a perl or python script. This script creates a main page that is just a calandar with links to different days. Clicking on a day will bring you to a screen that contains all the Screenshots for that day, in thumbnail form, arranged in a few columns on the page. Clicking on a thumbnail will bring up a fullsized image of the screenshot, and some more info described below. Also, there would be (on the main screenshot thumbnail page) an index of all IM logs for that day, and all webpages visited as well as emails sent. These would be linked to as "Conversations", "Webpages", and "Email" linked on the top of the page. The view of webpages captured that day would be much like the interface for webpages 2 paragraphs below this.

Each of the pages for a particular screenshot contain more information than just the image. They each get tied to keylogger logs  (presented below the image)  that are between the time the screenshot was taken, and the time the next screenshot is taken. There is a next button and a previous button on the bottom to screenshots that were taken previously to, and after this screenshot, as well as links on the bottom that go to webpages visited between the time of this screenshot and the next, (an exact replica of the pages captured by squid, described below this) and IM logs that were taken that day (Gaim sorts IM logs into days).

The webpages would be presented by order of visitation, and would simply be links with a full address as thier label. The links (instead of going to the site) would go the replica of the webpage as captured by squid, so that you can view webmail, CGI pages, Login restricted pages, etc.


I'd likely make a package, and bundle all of this together for people to install easily. I can put the Squid proxy as a local transparent proxy for everything to go through, and setup everything else with specific configuration so it acts how it needs to for this purpose. If the Ubuntu community is willing to help me figure out some of these issues, I'd be happy to write the extra programs to tie it all together, and work on packaging it. This would be a major advantage to linux to have this ability, for free. Also, it would definately aide in adoption by parents worried about thier kids, as they wouldn't have to deal with the viruses and spyware from websites, and could easily monitor the kid's computer usage as well. This would be a boon for employers as well if they could monitor employee's usage also.

---

### Post by ashz on 2007-06-15
try...

[http://ubuntuforums.org/showthread.php?t=226298&page=5](http://ubuntuforums.org/showthread.php?t=226298&page=5)

[http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

these are for a program called dansguardian...

you could also instal Ubuntu Christain Edition which comes with dansguardian pre installed i believe!!

laters
ash

---

### Post by dragonfyre13 on 2007-06-15
> **ashz said:**
> try...

[http://ubuntuforums.org/showthread.php?t=226298&page=5](http://ubuntuforums.org/showthread.php?t=226298&page=5)

[http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

these are for a program called dansguardian...

you could also instal Ubuntu Christain Edition which comes with dansguardian pre installed i believe!!

laters
ash

That may work quite well for the control side, but in this post I am focusing almost entirely on monitoring. Locking down the computer doesn't achieve nearly the same thing as monitoring does, and often hinders people from doing things they legitimately want to do, and should be allowed to do.

I do appreciate the post though.

---

### Post by cookies on 2007-06-15
There is this handy little web site blocker/filter/web monitor:
[http://dansguardian.org/](http://dansguardian.org/)

---

### Post by dragonfyre13 on 2007-06-16
> **cookies said:**
> There is this handy little web site blocker/filter/web monitor:
[http://dansguardian.org/](http://dansguardian.org/)

That is the same program that is recommended above. Thank you again though for posting it.

Perhaps I'm not understanding something. I am looking at creating a **parental monitoring** solution, not a **web filtering** program. If I can use dansguardian for part of that, then great! But it looks like all it does is filter websites, albeit filtering them quite nicely. If it can record website usage (including the actual content of the site itself) then I will be more than pleased to use it, and will recommend it to people that need to monitor the web. This is still only a small peice of the puzzle. Web monitoring and filtering still doesn't give me IM, Email, keylogging, and screenshots.

I guess what I'm saying is that I appreciate input on dansguardian, but I've seen it recommended every time parents post about any kind of control or monitoring, and this is one of the reasons that I am looking for a solution to the problem. Dansguardian is recommended, but doesn't even come close to the functionality that a parent is looking for 90% of the time.

---

### Post by airtonix on 2007-06-20
drifnet : shows images as they travel through the wire. run it on a ubuntu router.

jnettop : shows traffic aggreaged totals, address accessed and ports used

etherape : graphically node display version of jnettop....basically

bandwidthd.....webbased bandwidth usage reporting tool. reports total bandwidth used per port/portocol

internode-usage-meter ( only for internode customers ) : great littlw graph showing history of usage and a basic mean daily usage to be able to have full speed all month.

i think the rest really is going to be made up of custom scripts..bash, python or php.

otherwise there is the use of guraddog as a firewall, not sure what that provides.

---

### Post by jethro10 on 2007-11-22
> **dragonfyre13 said:**
> 

Perhaps I'm not understanding something. I am looking at creating a **parental monitoring** solution, not a **web filtering** program. 

I use dansguardian in a professional environment, and although it was designed for filtering, it is dead easy to switch that off and just log all access into log files, these can be in CSV format and you can load the logs into a spreadsheet easily.

J

---

