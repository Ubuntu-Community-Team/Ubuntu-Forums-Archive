---
title: "file integrity checks"
date: 2008-07-10
forum: General Help
---

### Post by Xbehave on 2008-07-10
I have a 200GB data drive that im going to install as ext3 on /home, i also have a spare ~15GB drive that might not be around forever. As it might not permanently i dont want to store data on it, however i would like to use it to check the itegrity of the data (something like zfs maybe (although i personally think zfs is a bad idea due to the linking of too many independent features into a filesystem but meh) ). I was wondering if there is a tool do this or could somebody recomend a good way of doing it myself. Im treating this computer as a learning experiece so id be fine a bit of trickey setup.

I thought of setting up a database to hold a hashtable and cron jobs to check files regularly, but i don't see how this will deal with the fact that files get updated, i could throw in a file access time check, but then any file that gets updated will no longer be protected, ofc i could add some sort of file access monitor but then im not sure how effective that would be or how to do it.

---

