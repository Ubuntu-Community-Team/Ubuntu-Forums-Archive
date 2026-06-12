---
title: "OSS Scheduling Software"
date: 2007-01-31
forum: General Help
---

### Post by unkemptwolf on 2007-01-31
Can anyone tell me if there are any stable OSS scheduling packages? Lets say I run a business, such as a small franchise restaurant. I have 20 or so employees whose availability varies, and I need software that can take this into account when scheduling them to work. If it could help me with determining the feasibility of time off for employees that would help too. It would also help if it was cross platform (Linux for home and Windows for work). Any suggestions? Thanks!

P.S. Mods, I'm sorry if this is in the wrong forum but I couldn't figure out where else to put it. Feel free to move as needed.

---

### Post by reclusivemonkey on 2007-02-01
> **unkemptwolf said:**
> Can anyone tell me if there are any stable OSS scheduling packages? Lets say I run a business, such as a small franchise restaurant. I have 20 or so employees whose availability varies, and I need software that can take this into account when scheduling them to work. If it could help me with determining the feasibility of time off for employees that would help too. It would also help if it was cross platform (Linux for home and Windows for work). Any suggestions? Thanks!

P.S. Mods, I'm sorry if this is in the wrong forum but I couldn't figure out where else to put it. Feel free to move as needed.

Sounds like a database would be the best solution here. Using MySQL or any of the free SQL alternatives along with OpenOffice should make it cross platform (if you can share it from home via the web securely, you should be able to use a browser to access it). Although if you are not familiar with databases this might be a bit tricky :-S

Do you know any DB wizards?

---

### Post by lamego on 2007-02-01
He is looking for a complete software, the database would only provide a data backend. It would not take care of the required computing for the scheduling problem.

---

### Post by glabouni on 2007-02-01
As a starting point, you can look into ["Office/Business :: Scheduling" category on freshmeat]("http://freshmeat.net/browse/130/").

IMHO what you need here is a web application. 
This would allow your employees to check their schedule from any internet connection.

---

### Post by reclusivemonkey on 2007-02-01
> **lamego said:**
> He is looking for a complete software, the database would only provide a data backend. It would not take care of the required computing for the scheduling problem.

Yeah, maybe I got carried away there. As databases are my daily bread and butter it would be a fairly simple and interesting task for me. Also, he could store all the contact information in there are well, with details of his staff ready for mail shots, etc. I would think it would be a good idea for his business to have all this data in a database.

Its not right to suggest that a database could not compute the scheduling though; its more than capable of doing that.

If I had a franchise, and wasn't capable of doing it myself, I would be paying for someone to create exactly this type of database for me.

---

