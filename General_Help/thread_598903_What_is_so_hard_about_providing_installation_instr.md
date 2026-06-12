---
title: "What is so hard about providing installation instructions for an application"
date: 2007-10-31
forum: General Help
---

### Post by sefs on 2007-10-31
What is so hard about it in the linux world? 

Does it not make common sense to distribute even simple instructions in the gz file.

Why have a big able website talking about how fancy your product is and then provide the user with absolute no install instructions or you have them buried some where that they will never be found

I need to understand this type of thinking.  Where has this mindset come from.  I wanna know.

Songbird 0.3 I am looking at you  at the moment but there are a legion of other offenders so I guess you have strength in numbers.  Your forum sign up process does not even work.  If you are coming to the market it would be wise to come proper, free or no free.

---

### Post by -grubby on 2007-10-31
I know...it's annoying.

---

### Post by aysiu on 2007-10-31
Is this a general frustrated rant question, or is there actually a piece of software you want help installing? If it's the former, I'll move this thread to a more appropriate subforum. If it's the latter, please name the software, and people here can help you install it.

[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird) may help for now.

---

### Post by ThrobbingBrain66 on 2007-10-31
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Bookmark it...you'll thank yourself.

---

### Post by sefs on 2007-10-31
lol.  Its a bit of both but I am calm now.  But no matter where you move this thread will not help that there needs to be some right thinking when releasing any product for consumption.  And the right thinking just is not there.  At least if you have a forum make sure it is a working forum.  I could not even log into their forum because its broken.  I think they need to take a 6 months break and re-evaluate what they really want to come to people with.

Right... so I downloaded songbird 0.3 RC.  It looks like firefox so with the absence of install instructions I assume i can install it the same way.  So i uncompress the tar.gz file and copy it to my /opt directory.  and then run this command sudo chown -R root:root /opt/songbird.  But after that the program will not start.  It only runs after I do this. sudo chown -R ${USER}:${USER} /opt/songbird.  And I do not want to use songbird with this sudo chown -R ${USER}:${USER} /opt/songbird, isnt that a security risk running it where the file permissions are set to user?

Let me know if anyone knows.

---

### Post by ThrobbingBrain66 on 2007-10-31
Songbird hasn't even been officially released yet....it's only at .3

Maybe they're assuming that anyone wanting to test an alpha product knows how to install from source.  I'm not saying that it's a good line of thinking, but I suspect that may be it.

---

### Post by sloggerkhan on 2007-10-31
since the binary isn't really an install, when I've looked at songbird, I just dumped it in a folder in my /home and ran from there. It's not like I really wanted it installed, either. Just wanted to demo it and get rid of it.

---

### Post by oldos2er on 2007-10-31
I agree with the other poster; this is alpha software, so if you don't know how to install it, it's probably better that you don't.
 That said, in general most source code will include a README  or INSTALL file that explains things.

---

### Post by Dark Hornet on 2007-11-01
What did you find wrong with the Ubuntu Forum...I have never had an issue with signing up, or using it...in fact, it has been a pleasure to use.  :)

---

### Post by sefs on 2007-11-01
Dark Hornet I wasnt talking about the ubuntu forum, I was refering to the forums at [www.songbirdnest.com](www.songbirdnest.com).

---

### Post by fdv1 on 2007-11-01
Several years ago, maybe even as far back as 1998 or 1999, Eric Raymond was trying to install CUPS.

He had problems doing it. But there was NO documentation...

So he published a screed about the lack of documentation in Linux generally. Things haven't changed much because coders code, they don't always take the time to write what they do or how to use what they do. Some might figure folks could just look at the source if they wanted. It's the nature of free software sometimes.

I like Linux, but I can admit that this is one of those things like shouting "The Emperor has no clothes!" You're absolutely right, but no one wants to hear it. Windows fans must admit that, for example, setting up networking in Windows XP is a nightmare because of all of the things MS tries to do "for" you. In the same way, we Linux fans simply have to admit that there are things about this OS that make using it a challenge.

---

### Post by sefs on 2007-11-02
How to install songbird 0.3 on gutsy gibbion 7.10 (just saw on digg)

[http://www.howtoforge.com/installing_songbird_on_ubuntu_gutsy_gibbon](http://www.howtoforge.com/installing_songbird_on_ubuntu_gutsy_gibbon)

---

