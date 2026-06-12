---
title: "snap &amp; gimp"
date: 2018-07-26
forum: General Help
---

### Post by jgw on 2018-07-26
I decided to install gimp using snap.  The installation was dandy.  I could not, however, access the drive/folder where my photos were stored as I didn't have permission.  Then I did a search that said to log into snap with my ubuntu name and password.  I did that.  Changed nothing, still didn't have permission.  

So, how do I fix this and access my machine when in gimp?

Thank you...................

---

### Post by howefield on 2018-07-26
Try the following terminal command..

```
sudo snap connect gimp:removable-media
```

---

### Post by jgw on 2018-07-26
Thank you for the reply.....

I saw that one and then went to the documentation that said that command was for removable media and not for system drives so I didn't do it.  I considered replacing the removable-media with the folder location but feared blowing something up and there were no directions for that so I demurred.  I am not even sure its a snap problem.  I have currently removed the program from snap and am currently reinstalling using ppa.  Then, at least, I will know if its a gimp problem or a snap problem.

In passing I just reinstalled, using ppa, and was gifted with 2.28 instead of the latest and greatest 2.10  so, back to the drawing board.
I removed teh 2.28 and then installed using ubuntu software and now have 2.10

OK, I tried to open it with gimp, installed with ubuntu software.  Got the same reaction so its a Gimp problem and not a snap problem.  I then went to the photo itself and told it to open with gimp and got:
Opening '/mnt/sdb1/Photo/Myanmar 2015/DSCN4967.JPG' 
failed: Could not open '/mnt/sdb1/Photo/Myanmar 2015/DSCN4967.JPG' for reading: No such file or directory

I then went to the photo and copied it to pictures in my home directory and IT WORKED.  So, obviously, the new gimp has a setting someplace that needs attention.

This is getting better and better!

Thanks again!

---

### Post by monkeybrain20122 on 2018-07-26
> **jgw said:**
> Thank you for the reply.....

Iblem or a snap problem.

In passing I just reinstalled, using ppa, and was gifted with 2.28 instead of the latest and greatest 2.10  so, back to the drawing board.
I removed teh 2.28 and then installed using ubuntu software and now have 2.10




The one in Ubuntu software is the snap.

Which Ubuntu version is yours? It seems that you may be using the wrong ppa. If you are on 18.04 you can get the latest gimp (2.10.2) from the [gimp-edge ]("https://launchpad.net/~otto-kesselgulasch/+archive/ubuntu/gimp-edge")ppa.

Edited: if you are on 16.04 then your options are either snap which has problems accessing external media or compile gimp yourself, it is not too hard but you need to install some dependencies not available in 16.04.

---

### Post by jgw on 2018-07-26
Thank you for the reply.  I am using 16.04 on this machine.  I assume that their download for compiling includes most of the files as well as the make file but I think I will just wait.  There should be some way to simply add a folder/location as it has some already there but I can't find anything like that.  I really appreciate your reply as I have done virtually everything that I could and this is a gimp problem.  I guess what you are telling me is that ubuntu software installs 2.10 but its a flawed offering as I have installed every way I could think of and still am failing.  I can wait.

Thanks again!  (I can now get on with my life <G>)

---

### Post by monkeybrain20122 on 2018-07-26
I compiled gimp2.10.2 and its dependencies in a local folder. It is a bit of work the first time, but upgrading is very easy once you set it up. If interested I can post instructions.

---

### Post by jgw on 2018-07-27
Thanks, I think I will just wait.  I am currently using 2.8.22 and its working just fine.   I put 18.04 on one of my machines and dealing with that is enough for now.  In theory 18 is supposed to be ready by the end of this month (not likely) so, I will just wait and then just upgrade everything.

Thanks again.   I will mark this one as solved.  The answer was that if one is using 16.04 either compile or wait.

---

