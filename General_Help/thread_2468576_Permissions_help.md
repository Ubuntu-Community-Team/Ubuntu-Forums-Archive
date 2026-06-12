---
title: "Permissions help"
date: 2021-11-03
forum: General Help
---

### Post by uros-likar on 2021-11-03
I have a general idea how permissions, users and user groups are working but still I have problems with it. 

I installed Apache, php and mariaDB for developing needs and all went fine but...

I downloaded zip file of CMS which I extracted it and copied to www folder. When I tried to install it I got an error that PHP can't write on disk. I figure out that PHP / apache uses user www-data. I changed ownership of CMS folder to that user and then I could start the install process.

However... after installation I couldn't edit files created by CMS. I googled a little and then If I'm not mistaken I added my user to www-data group to solve that. Then I created one file and tried to open with CMS without success. I'm not 100% sure if I wrote the the proper procedure I went through becaus I tested various things.

Please correct me if I'm wrong. 
- When my user "uros" was created on Ubuntu installation also user group named "uros" is created.
- Same is with www-data which represent a user "www-data" which is part of the group "www-data"

My goal is that inside www folder I and www-data can write and read (and probably execute too?), what I need to do to achieve this? 
Should I put my  "uros" user to "www-data" group or "www-data" user to "uros" group? ... or both ?

After users and groups I set then probably I'll need to chmod "www" folder to 755 or something similar?

If anyone knows a good tutorial regarding this please send me the link to it.

---

### Post by TheFu on 2021-11-03
There's a little more to it.  [Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp)

With most CMS programs, it is pretty important to have the program and library areas read-only, even for the www-data user+group to prevent it from being hacked.  Just the data upload needs to be read-write and only for the exact userid that needs it. The DBMS it uses needs to be locked down to only allow connections from the correct userid running on the correct client system. Do not allow any other IPs to connect to the DBMS.  Management, if needed at all, should happen through the CMS or using an ssh-tunnel into the system where the DBMS runs, so the connection appears to come from 'localhost' ... that's any IP in the 127.0.0.0/8 subnet.

If you search "ubuntu permissions", you'll find the tutorial for that.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has a chapter just on permissions.  This comes after the userid and groupid stuff. Those are important to understand as well. It appears you have 80+% of the ideas correct with permissions and just didn't need to understand the setgid parts.

Tutorials usually don't go into all the techniques. That is up to us to acquire that knowledge, usually through mentoring and sometimes by trying new techniques because we have the understanding for how these things are implemented.  

I think you are on the right path.  Naming the specific CMS used would get people with specific knowledge about that program to comment - probably best to change the thread title with that infor, if you can.

---

### Post by uros-likar on 2021-11-04
Thanx for all the info. I have only problems with ownership and not with actual permissions. I know how to set folders properly on CMS to make it secure and production sites are on dedicated servers which are maintained by professionals. 

Security is not an issue because my localhost will never be exposed online and I need it only for testing and developing purposes. Anyway, it's not a secret, cms I use is Modx and occasionally Laravel framework.

---

### Post by TheFu on 2021-11-04
Security has to be considered on all platforms, including dev to prevent issues in test, preprod, prod and DR systems. The sooner that security is applied, the more likely everything else will be smooth.

Are you using the setgid bit and changing the group as the first link above shows?

---

### Post by uros-likar on 2021-11-05
I added my user to www-data group and chmod entire www folder to 2755 and seems to work.

---

### Post by TheFu on 2021-11-05
> **uros-likar said:**
> I added my user to www-data group and chmod entire www folder to 2755 and seems to work.

You probably shouldn't do that.  Just do it for the directories, not the files and be cautious about which directories got touched, since some may need "other" to have NO access at all for security.  This will break at deploy time to other dev environments and prod.
Would have been better to use **chmod g+s** on the directories only. That would add the setgid bit, but not alter others. Much safer.

---

