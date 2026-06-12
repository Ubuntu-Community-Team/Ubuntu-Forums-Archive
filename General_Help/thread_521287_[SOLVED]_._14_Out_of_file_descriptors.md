---
title: "[SOLVED] .: 14: Out of file descriptors"
date: 2007-08-09
forum: General Help
---

### Post by kast on 2007-08-09
Ok so I seem to have two issues, whether there related I don’t know. 

                  ** 1.** The issue that has been posted all over about the 

[B]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/B]
                       
                    ** 2.** When trying to stop or start/stop ntop I get 

**.: 14: Out of file descriptors**

(stop/started nessusd with out issue) Not sure if it’s just ntop 

I included both my issues in one post only to see if there is any possibility of a relation. The first issue I tried everything that has been posted, all the apt-get –options, like clean configure –a etc... Also deleting the locked file but it comes back after running aptitude and or apt-get. I have noticed that my /var/cache/apt/archives is empty and also has a locked file in there. I have tried things like using grep to find process’s to see if there are multiple instances of Synaptic or Apt but all come back with a  

**Warning: bad ps syntax, perhaps a bogus '-'?** 

I'm assuming that it’s basically telling me it’s not finding what I’m looking for.

For my second issue I haven’t found anything to try on that one. I know this is vague I apologize I don’t post much

Is there any logs perhaps that would help me identify one if not both of my issue's? looked around didn't see much.

                                    What ever help I can get is much appreciated!







Ubuntu:Feisty

---

### Post by kast on 2007-08-09
Ok not really a Bump just letting you know I found out how to up my descriptors, first find out how many your at.

To get the current limit:
Code:
**$ulimit -n**

To increase or set file descriptor limit per user, modify,
**/etc/security/limits.conf**

And add a fixed limit.
Code:
your_username hard nofile 32768

After that I was getting some segmentation fault errors running the ntop daemon, but I chocked it up to just messing something up in the last two days trying to get it to work :) so I apt-get remove and that finale worked!  (it wasnt before!) 

Ok I can tell not many people wanted to to touch this issue with a ten foot poll : ) so if you don't mind I would like to ask, hopefully an easier question.

Does anyone know of a reason why I can do an **sudo aptitude update** and a 
**sudo aptitude upgrade** with out issue, but not 
[B]
sudo aptitude update && aptitude upgrade[/B] together ??? i get the same error

[B]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/B]


 Thanks!

---

### Post by kast on 2007-08-11
Ok so the Descriptors issue was solved by 

get the current limit:
Code:
**$ulimit -n**

To increase or set file descriptor limit per user, modify,
**/etc/security/limits.conf**

And add a fixed limit.
Code:
your_username hard nofile 32768

The problem with running  **sudo aptitude update**  then running **sudo aptitude  upgrade** working but running them together not working was solved because this is what i was originally running.

**sudo aptitude update && aptitude upgrade**

putting sudo after the && solved my issue 

**sudo aptitude update && sudo aptitude upgrade**

---

