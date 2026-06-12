---
title: "Partitioning Security?"
date: 2008-02-18
forum: General Help
---

### Post by hey2222 on 2008-02-18
At school I watched one of my friends partition his server editions of Ubuntu, and he separated his folder partitions(/home,/var,/etc and others directorys). When i ask him why he said "Its like creating multiple drives in windows, and splitting up the important folders in c:/ among the drives for security purposes". I don't really know if he fed me some bull or if theres something to what he's saying, but if this is true what directorys in / should i have partitioned separately?

---

### Post by SpaceTeddy on 2008-02-18
security is (as far as i know) not the word here. Partitioning the drive will help you with a few gotchas that can happen to a machine. 
As usual, all users will have their stuff under /home, and if that is not a  different drive, user would acctually be able to swamp the system full with their data (which is not desired nor known by the user). Also, /var is for log files, which sometimes can get pretty big (especially if you did a mistake by accident) and again, it could disrupt your whole system if it full.
Lastly, ANYBODY can write ANYTHING to /tmp... well, you know where that one is going...

If you don't know exactly what you are going to do with the system, just ignore the partitoning stuff, it is not neccessary... just protects you from a few problems one could maybe walk into. 

I personally like to have /home on a different drive, since that is the only place where I put my stuff. And in case of a crash i can reinstall and have all my setting and documents safe and sound on a different partition which i just have to mount in the new install and everything will be still there and working like i set it up before 

Hope this clarifies some stuff :)

---

### Post by bodhi.zazen on 2008-02-18
You can increase security (IMO marginally) with such a partitioning scheme.

It is best to understand what an how you are doing though.

If you need a basic overview see here : [http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

And, for a more detailed explanation, 2 references from that thread :

[http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix/11208-linux-partitioning-guide.html)

[http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System](http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System)

---

