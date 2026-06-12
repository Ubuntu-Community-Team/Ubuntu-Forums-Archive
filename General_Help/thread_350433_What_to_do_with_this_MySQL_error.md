---
title: "What to do with this MySQL error?"
date: 2007-01-31
forum: General Help
---

### Post by Tdonohue on 2007-01-31
This seems to be an issue that others have had, but they all seem to show Mysql starting after "checking for..." , and then resolving their issue with password resets.  I got the same message immediately  following the install.  I have no idea where to go from here.  I don't know anything about if passwords were set, or what they are if they were. 


tim@tim-laptop:~$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                    [ ok ] 
 * Starting MySQL database server mysqld                                                    [ ok ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
tim@tim-laptop:~$ 


Sorry if the explanation is kind of vague...I don't really have any other info.  Installed the app...got the error...don't know what else to do from here.

Thanks in advance for any advice!!!

---

### Post by josesanders on 2007-01-31
I guess maybe I don't understand what the problem is, but I don't see any errors with what you have posted, that is normal when you restart mysql.  By default, the root user is created with no password, so you should be able to log in with the command

$ mysql -u root

If this doesn't help you, maybe you can post specifically what you are trying to do, and where you run into problems?

---

### Post by Tdonohue on 2007-01-31
Ha Ha, I'm just so dense sometimes.  Your reply caused me to re-read the "error" I was referring to.  I realized that It was telling me it was checking for corrupt tables, not telling me I  had corrupt tables,   I was copying commands from a website to install Mysql and set up a databse to use with Amarok.  Part of the problem was that I had copied the commands word for word, including unknowingly setting the root user password to "your-new-password".

I configured Amarok with the same data I set the database up with and the collection populated and I don't have any errors, so I can only assume that everything is OK. ? (I say that with cautious reservations).

Anyway, Thank you very much for your suggestion, as it ultimately pointed me in the right direction.

---

