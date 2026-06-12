---
title: "CD Burning"
date: 2004-12-01
forum: General Help
---

### Post by Infatuated_iPod on 2004-12-01
What is a good CD burning Application? I am looking for an all around kind of app, like WMP, but i cant seem to find anything, what do you recommend?

---

### Post by Infatuated_iPod on 2004-12-01
I got k3b, but when i start up this message pops up.. 

> 
cdrecord does not run with root privileges
It is highly recommended to configure cdrecord to run with root privileges. Only then cdrecord runs with high priority which increases the overall stability of the burning process. Apart from that it allows changing the size of the used burning buffer. A lot of user problems could be solved this way. This is also true when using SuSE's resmgr.
Solution: Use K3bSetup to solve this problem.
cdrdao does not run with root privileges
It is highly recommended to configure cdrdao to run with root privileges to increase the overall stability of the burning process.
Solution: Use K3bSetup to solve this problem.

What do i do?

---

### Post by zenwhen on 2004-12-01
[http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-05.2946111988](http://www.ubuntulinux.org/support/documentation/howto/helpcenterhowto.2004-10-05.2946111988)

That should get you there.

---

### Post by Infatuated_iPod on 2004-12-01
> 
K3b did not find a suitable writer. You will only be able to create an image.



what does that mean?

---

### Post by zenwhen on 2004-12-01
For some reason it didnt find your writer.

---

### Post by Infatuated_iPod on 2004-12-01
..:-\ Any suggestions?

---

### Post by b10m on 2004-12-03
I had the same error, too.
I added the cd-writer by myself... for example adding /dev/hdc (I have the writer as primary over second ide line).

---

### Post by dishkuvek on 2004-12-09
[QUOTE=Infatuated_iPod]..:-\ Any suggestions?[/QUOTE]
 I really think that you would benifit from using a distro that is not as GUI oriented.  I know that GUI = Easy, but it makes it really hard to learn anything about working your way around a unix enviroment.

I'm not saying abandon Ubuntu, just dual boot with something else.

---

### Post by jeremy on 2004-12-09
[QUOTE=Infatuated_iPod]..:-\ Any suggestions?[/QUOTE]
If your k3b version is earlier than 0.11.17 you will have to run it as root, you could download and compile the latest version that corrects this.

---

### Post by Infatuated_iPod on 2004-12-09
[QUOTE=dishkuvek]I really think that you would benifit from using a distro that is not as GUI oriented.  I know that GUI = Easy, but it makes it really hard to learn anything about working your way around a unix enviroment.

I'm not saying abandon Ubuntu, just dual boot with something else.[/QUOTE]

Okay, what do you suggest i use along with ubuntu? And is it possible to have XP, ubuntu, and someting else on the same hard drive? I have a 5 gig partition that i made by accident. It you could triple boot, that would be great.

---

