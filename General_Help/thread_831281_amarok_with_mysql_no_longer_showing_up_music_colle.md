---
title: "amarok with mysql no longer showing up music collection"
date: 2008-06-16
forum: General Help
---

### Post by exactopposite on 2008-06-16
I have one machine that mainly serves as a file server. It doesn't have a monitor or keyboard connected to it, so I log into from other machines on the lan via NX. My music collection is on this system and is shared to the rest of my lan using nfs. Amarok is configured with mysql, and the mysql database is configured so that the rest of the systems on the lan access that database. This way when I open amarok on any machine on the lan it accesses the 1 central amarok mysql database and music folder on the file server. It's been working fine like this since the week hardy came out. (i did a fresh install of hardy on all my machines at that time, and this setup had been running fine on gutsy for months before that)

Recently I added some more music to the music folder on the file server. Yesterday I noticed that the new music still wasn't showng up in amarok even after updating the collection. So i just rescanned the collection to make sure it saw the new music. After it rescanned the collection amarok doesn't show any music at all. 

Here is what I have tried so far to no avail:(all of this was done on the file server)
-Purge and reinstall amarok
-deleting the amarok setting sform my profile (in the .kde folder)
-removing the mysql database (DROP DATABASE) and creating a new one 
-purge  and reinstall mysql server 5.0 (when it was uninstalling I selected the option to remove all databases). then creating the database again

Nothing I have tried so far has bade a difference. The music is definitely in the folder and amarok does scan it, but when it finnishes scanning amarok shows mo music. It seems to be a problem with the mysql database becase when I open amarok from a client on the lan no collection shows up there either. Any ideas on what's happening here?

file server specs:
core2duo e6600
1 gig of ram
hardy 32

---

### Post by ÄssfaceJackson on 2008-06-26
I am having a different problem with a similar setup. I have central FreeBSD server that has the NFS-shared music collection and the MySQL server that I want to access from my laptop. Everything worked the first time I configured Amarok on the laptop, but when I restarted the application the collection always comes up empty (even though it's still in the database). The only way to get the collection information to come back is to switch back to sqlite, restart the application, and then switch back to MySQL. It also does not grab new files unless Amarok is running on the server.

This page might be what is needed to solve both of our problems:

[http://amarok.kde.org/wiki/Dynamic_Collection](http://amarok.kde.org/wiki/Dynamic_Collection)

I'm going to try it out when I get home tonight.

---

### Post by Ashex on 2008-06-26
Same thing happened to me today. Only difference is none of my music is hosted on the network. I have my home directory mounted on another drive. I started up amarok today and nothing shows up. There's data in the mysql database, but amarok isn't displaying it.

---

