---
title: "Eclipse VM not valid Executible"
date: 2005-10-04
forum: General Help
---

### Post by axioss on 2005-10-04
Hi, 

I had installed eclipse previously (worked fine) and then allowed synaptic to update it which is when I started getting these errors when I launch it. 
"The custom vm you have chosen is not a valid executible"

I tired "eclipse -vm /usr/bin/java" with no luck, same error.
I have java -version is 1.5, located in /usr/bin/java

Any suggestions? Thanks in advance.

---

### Post by axioss on 2005-10-04
My quick and dirty solution to this is:
"sudo eclipse -vm /usr/lib/j2sdk1.5-sun/"
 
A quick query shows my eclipse executibel owned by root:root so and not by my user hence the "sudo".
Note also the jvm path must be wrong, since I am new to ubuntu and some levels of debuging I can not spend any more time on this till the weekend, studying for an algoritms exam. If any of you want to send me down the right path, maybe resetting the java_Home env varialbe or something else that would be appreciated. 

Thanks alot.
Oh maybe why you think IDE has been taken ownership by root would be nice, I ran the update manager as a user, and also the reinstall as a user with no sudo argument.

---

