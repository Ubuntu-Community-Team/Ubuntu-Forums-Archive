---
title: "CVS and Git"
date: 2013-09-09
forum: General Help
---

### Post by Ashiq_Irphan on 2013-09-09
I`m a student preparing myself for the degree project, Which I plan to do on C using Eclipse CDT Helios on an Ubuntu 12.04 machine.

So what I exactly want to ask is **How should I keep track of versions of my code ? **

I did a little reading on eclipse`s website and found that eclipse supports CVS by default but I don`t have a CVS server at my university that I can access.

So It means I have to store all my files on the local machine. 

I also read about Git, but it seems to be more of distributed system. Is there any system that stores versions of my code on the local machine and can integrate with eclipse ? 

Expecting great new ideas:D

---

### Post by Ashiq_Irphan on 2013-09-10
All I need is to keep a complete backup of all the changes I make to my code.

Please help me with this.

---

### Post by steeldriver on 2013-09-10
Subversion (svn) would be another option - I believe there is a subversion plugin for Eclipse, however it's not really necessary to have your version control integrated into your IDE. If the code will become part of your degree thesis then you should talk to your supervisor / professor about what to use.

---

### Post by Ashiq_Irphan on 2013-09-10
Yes, the codes are going to be part of my degree.
My professor has allowed me to choose whatever method I like.

I read about the SVN too. Can you pls guide me where I can find installation and configuration instructions for SVN...

---

### Post by steeldriver on 2013-09-10
If subversion is not installed you will need an administrator to do that for you - however once it's installed, you can create personal repositories in your own home area without special permissions.

There is online documentation here --> [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

There is also a good Windows client --> [http://tortoisesvn.net/](http://tortoisesvn.net/)

---

