---
title: "update manager+synaptic package manager+add/remove applications problems-hardy herron"
date: 2008-04-25
forum: General Help
---

### Post by the_jackel on 2008-04-25
i just installed ubuntu 8.04 and ive had a number of issues.

firstly when i go to add/remove applications, most of the applications listed there have the description "[the application] cannot be installed on your type of computer (i386). Either the application requires special hardware features or the vendor decided to not support your computer type." i never had any of these problems with ubuntu 7.10. 


my other problem is that in add/remove applications, it comes up with a message saying that the add/remove applications list is out of date, but when i go to reload it, it downloads 11/20 files and has errors with the rest of them so nothing ever happens. i also have the same problem in the update manager and the synaptic package manager.

any help PLEASE

---

### Post by kyleabaker on 2008-04-25
I've been running 8.04 since Alpha 1 and haven't had package-manager problems until 8.04 was released yesterday. I think some of the issues may be due to their servers. It seems the servers are overloaded or are cracking under a bit of publicity. It almost seems like a "denial-of-service" (DoS) attack.

That's unfortunate for them since it will appear that Ubuntu isn't working well, when it's their servers all along.

I've seen the first problem you mentioned before, but I'm running x64 so some programs haven't been make to work yet on x64. If you're running the 32-bit version then I'm not sure where those messages are coming from. Maybe someone else can help you further with that, or maybe it's related to the servers as well..? No telling.

---

### Post by olechrk on 2008-04-26
I have the same problem too. Just installed ubuntu 7.10 (32-bit) and get the same error message as you.

---

### Post by shr2004 on 2008-05-06
Oh dear...I found my mates here who have the same problem as mine....Have you guys found any solution yet..just let me know. The most bothering matter is whatever was I try I always get "Forbidden". I was about to post a new thred, but found this. so decided to continue here
thanks

---

### Post by shr2004 on 2008-05-06
After several try with both wired and wireless network I have found the problem in my machine. Just reminder that I could not use add/remove or Sunaptic to get any new package. 
So, I changed my the package source to another location and changed from http to ftp, simply find a ftp server that I can connect. Now its connecting to the server and can find any update I want.

---

### Post by stankopp on 2008-05-08
I just upgraded to 8.04 on-line.  When I try to open the Synaptics package manager, it does absolutely nothing except change the cursor (the little spinning busy cursor) and then return to the normal selection cursor.  When I try to check for updates, it does nothing but change the cursor and grey-out the box.  I have let it go for  a half day and nothing.  Today I was informed that I have 12 updates.  When I go to the update manager, I see the list of updates, but when I click on the install updates button, I get the busy cursor and the greyed-out box just as in check for updates. Obviously I am able to see the update site and be seen by it.

I have done the sudo get-apt thing and it did donload some packages...

Does anyone have any ideas?

---

### Post by ubuntu-freak on 2008-05-08
As someone else posted, try ftp instead of http by navigating to System > Administration > Software Sources. You can also select to use an alternative server for system updates/installations. There are further details in my [sticky](http://ubuntuforums.org/showthread.php?t=766683), including fixes in part 1 related to errors during updates/installations.
 
Nathan

---

### Post by stankopp on 2008-05-08
That would not have solved my problem.  I could not open administrative/software sources.

My problem was an "unable to solve host" problem.  I searched the fora for that problem and have resolved my issues.  The update had my local hosat as yelnats.wilnt.com.  It should have been just yelnats.  I used the gksudo edit /etc/hosts to edit the file in order to correct it to correct it.

---

