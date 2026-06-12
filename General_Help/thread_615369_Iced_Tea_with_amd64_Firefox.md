---
title: "Iced Tea with amd64 Firefox"
date: 2007-11-17
forum: General Help
---

### Post by sirgogo on 2007-11-17
Hello all:

I am having troubles with Iced Tea on my amd64 comp (specs in signature). It displays a gray box in place of where an applet should be. I know this is addressed in [http://ubuntuforums.org/showthread.php?t=580792](http://ubuntuforums.org/showthread.php?t=580792). The "fix-post" said to edit a file and replace the lines adding the Iced Tea repositories. I wasn't sure how to do this. Can someone provide a step-by-step on what to do?

Thanks a bunch. :KS

---

### Post by wooster on 2007-11-17
from the terminal type this 

```
sudo gedit /etc/apt/sources.list
```

then copy and paste this at the bottom of the file.

```
# iced-tea updates
deb http://people.ubuntu.com/~doko/ubuntu/ gutsy/
deb-src http://people.ubuntu.com/~doko/ubuntu/ gutsy/ 
```

save it, exit out of gedit and type this into the terminal.

```
sudo apt-get update
```

that's it you should have that repository added and updated now.

---

### Post by sirgogo on 2007-11-17
Hey:

Thanks! Okay, I did the procedure and successfully updated Iced Tea. (yay!) Unfortunately, though, the java applets are still greyed out. Does Iced Tea still not support this or whats the deal?

Thanks a lot for your help.

---

### Post by PmDematagoda on 2007-11-17
Try this:-
```

sudo update-alternatives --config java
```

then select Iced Tea, and try the Java applets again.

---

### Post by sirgogo on 2007-11-19
Hmm...
IIt seems to have updated when I did that. However, it still greys out my applets. This is very weird Oddly enough, this also happens on my other computers (Dell Inspiron 1000, Dell Inspiron 5100, Dell Dimension 2400, Ubuntu 32 bit), I'm not sure whats going on. I don't think it is the applet's fault? The applet loads fine in windows with JVM.

What should i do?

---

### Post by yostral on 2007-11-19
Have you got a web address that is not working, so we can try ?

---

### Post by sirgogo on 2007-11-19
Eeehhhhhhhhhhhhhhhhhh... Sure thing.

Heres an example of a page that I cannot view the applets for: [http://blackboard.iusd.org/courses/1/053608123456/content/_22460_1/dir_grades.zip/grades/classes.htm](http://blackboard.iusd.org/courses/1/053608123456/content/_22460_1/dir_grades.zip/grades/classes.htm)

The boxes are all greyed out for me. And I *know* it isnt a problem with the site, because I can see it on my windows computer. I'm not sure whats going on.

Thanks a bunch guys.

---

### Post by zippy028 on 2007-11-20
Some of these academic sites are written for Internet Explorer only. Are you able to access the site with Firefox in Windows? I did notice that I had similar issues with java with the 64bit Ubuntu. I switched to 32bit for other reasons so I never found a solution to the issue myself.

---

### Post by yostral on 2007-11-20
I don't know what should not work with this page. I have a grey part on the right where I can login, but I don't have any account... So I click on the preview button on the left and I can access to the site.

Should there be something else ?

I use Gutsy 64 with icedtea and firefox plugin from doko repository.

---

### Post by sirgogo on 2007-11-20
Yostral: My bad, my bad. I forgot that the link only works for a time (by session). The way to access it is:
1. [http://blackboard.iusd.org](http://blackboard.iusd.org)
2. Click User Login
3. Preview
4. Courses
5. University High School
6. Mathematics
7. Mrs. Kurdziel's Classroom " 053608123456"
8. Course Documents
9. Grades as of....

#6-10 concern the specific link I posted earlier. However, the greyed out boxes are true for all the teacher's pages.

Zippy: Yeah, a lot of sites are set-up with IE in mind. However, I use Firefox on all my other computers (including the Windows one). So I'm confident its not the fact that I'm using Firefox. I think you're right, though; that I it is the fact that I am using Firefox ***64***. Hmmm... any other ideas to try?

Thanks again.

---

### Post by yostral on 2007-11-21
Ok sirgogo.
Right, only grey boxes too. :|

---

