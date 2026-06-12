---
title: "Root acc messed up, and the new acc does not have all applications/addons running"
date: 2007-08-07
forum: General Help
---

### Post by frankzzsword on 2007-08-07
Hello,

I am new to this forum, joined today itself. Well I've been using ubuntu for 1 month and the journey has been awesome. One thing I would like to state that after installing lot of crap and testing. I kinda blew my root account, so instead of fixing that up I thought of making a new one, which I sucessfully did and gave all the admin rights to that one. After logging to that new root user, I found out that half of the addons/softwares I installed in root such as Gsteamer, Compiz Fusion, Emerald, Flash and Mplayer for Mozilla Firefox does NOT work.

Basically the root account is messed up because it cannot start any administrative service, it hangs. Like whenever you go to System > Administration and try opening anything out there, a window opens which asks for password and then states Starting Administration Service. There my ubuntu Hangs, and because of that I am unable to do any updates.

So 1. First of all I would like to know why doesnt any application work in my new root account
and  2. Why does my ubuntu hang when I try opening any Administrative serivce.

Thankyou

---

### Post by oldos2er on 2007-08-07
I'm a n00b too, but I'll try to answer your questions until someone more knowledgable comes along.
 Linux keeps each user's files and system settings separate, so that's why you don't have all the programs available to your new account that you previously installed. This goes back to linux's inheritance from Unix of being a multi-user OS. It Really comes down to safety and security.
 Btw, you shouldn't install end-user apps like Firefox and Flash as root. I suggest you create a new user for yourself (once System-->Admin is fixed). Ubuntu should've done this for you be default on install.

 You may be able to run 'aptitude -f' to fix your admin problem,but i'm not certain.

---

