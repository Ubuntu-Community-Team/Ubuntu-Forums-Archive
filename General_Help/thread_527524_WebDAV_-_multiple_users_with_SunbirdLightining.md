---
title: "WebDAV - multiple users with Sunbird/Lightining?"
date: 2007-08-16
forum: General Help
---

### Post by tegwilym on 2007-08-16
Ok, I'm pulling my hair out here.  I finally got the Mozilla Sunbird and Lightning calendar applications working.  I also got it saving the .ics file on an internal web server here in our company.  I want to keep the shared calendars internally if at all possible, so I've put together a webdav server.  I got it running so now my own .ics file is up there and updates just fine and quickly when I change things in the calendar.

So, I have a single user on a server now, but what good is a calendar if you can't share it?

I figure I can used the htpasswd command to add users to the server easy enough, and put a user in the dav_fs.conf file.  So how do I have 30 users on this thing?  Do I need 30 folders with different users and .ics files, or can I leave them all in the same folder?  Do I put 30 users in the dav_fs.conf file??  I'm stuck and not sure where to go next.
Just trying to avoid spending big $$ on Microsoft:confused: - which we refuse to do anyway!

Ideas, comments, suggestions or even better a good HowTo?
Thanks,
:confused:

Tom

---

### Post by sikkim_20 on 2007-12-17
Hi Tom,

I am having the exact problem u are having. Can u please let me know if u have found a way to add multiple users in sunbird/lightning.I have added users the same way u have but there are a lot of users in my company and i am sure there should is  an easier way to create users.
cheers
Raj

---

### Post by tegwilym on 2007-12-17
I never quite figured out a fix for this. Although, some of our employees have been using it with Google, but  want to keep all the company stuff internal if possible.

So....we just got a server running OS X Leopard which has the iCal service built in.  Yay!  
But...I'm coming across problems just getting the service to start up. <*sigh*>

I'll just say that calendar problems really suck - and I'm NOT going back to Exchange/Outlook.  I'd rather poke myself in the eye than do that!  :)

Tom

---

### Post by sikkim_20 on 2007-12-17
Thanks champ for the quick reply..

Might do the same here..

cheers
raj

---

### Post by SeanHodges on 2007-12-17
I've recently had some experience with this where I work.

We used to have 3 .ics files (global, development, and support) published on an Apache Web server with WebDAV enabled. All of the employees had Lightning configured to point to all 3 of these ics files, and we entrusted WebDAV to handle the write transactions safely. 

We even had SSL installed on Apache, and used SSL [http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html](http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html) to authenticate the users (this was only for authenticating with the server, we still needed each user to append their name to each entry).

This configuration worked, but it had problems. Firstly as I mentioned already, we didn't know who made an entry, unless they appended their name to it. This could have been worked-around by having an ics file per user, every new user would need to publish a new calendar before they could start using it, but it would have fixed the main problem.

Secondly, the system was quite unstable. It was not really the fault of the iCal format, or of Lightning or anything else, it was simply that the configuration did not scale well for multiple users. What happened was each user's Thunderbird/Lightning application would read the published ics files into memory: When one user added an entry (wrote to the ics), the other users who still had Lightning running had an out-of-date cache. This meant that from then on, new entries would get lost, and Lightning would freak out because the server-side data had changed without it knowing.

We came across 2 possible solutions at the time. I had recently found some server-side software called webcalendar ([http://www.k5n.us/webcalendar.php](http://www.k5n.us/webcalendar.php)), which apparently handles a multi-user calendar system in a database, and imports/exports ics files to and from Lightning in a safer manner than the one I described above. I believe it would do what you want.

Unfortunately, I can't tell you for sure that it is a solution, as we went for "option 2". We had recently switched to Google Apps for our email, which provides a calendar system as well, so we migrated to that instead.

Either way, I feel using ICS/WebDAV directly might be more hassle than it's worth for you - unless you manage to work around the problems we had at the time.

---

### Post by sikkim_20 on 2007-12-17
hey  thanks for that . will give it a go and will get back to u if i come across any problem.
cheers

---

### Post by ntalamai on 2008-05-22
Probably you will have solved your problem by now. In any case, I thought this might help you:
nano /etc/apache2/mods-enabled/dav_fs.conf
Change "Require user someUser"
to    "Require valid-user"

Now all users stored in /var/www/davhome/.DAVlogin will have access. 

I suppose you have followed the HOW-TO in [http://ubuntuforums.org/showthread.php?t=119228](http://ubuntuforums.org/showthread.php?t=119228) and all your users are stored in a file like this:
htpasswd -cm /var/www/davhome/.DAVlogin firstUser
htpasswd -m /var/www/davhome/.DAVlogin newUser1
htpasswd -m /var/www/davhome/.DAVlogin newUser2
etc.

---

