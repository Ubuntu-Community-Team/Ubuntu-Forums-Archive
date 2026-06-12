---
title: "File Sharing, Ubuntu to Ubuntu"
date: 2007-10-26
forum: General Help
---

### Post by Earthwormzim on 2007-10-26
How do you share files from an Ubuntu machine to another Ubuntu machine?  Windows shares show up automatically Places->Network...but my Ubuntu shares don't.  So, how do I get them to?

---

### Post by yostral on 2007-10-27
I use the avahi capabilities. I just install gshare to use it with files sharing.

---

### Post by drs305 on 2007-10-27
Two of the most often used programs are samba for windows sharing and ssh for linux sharing.

The ubuntu wiki has a wealth of information. Here is a link to the wiki for SSH on Feisty but you can look around for other versions as well:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server)

 The main page for gutsy is:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

If you have any problems setting it up there are lots of posts on this forum which will provide guidance for you.

---

### Post by Earthwormzim on 2007-10-27
Okay, okay...I got the dern thing to work using SSH Server and Client.  Now, when my laptop logs on, I have a folder on my desktop that automatically accesses my music on my desktop-pc.  Kind of neat.  

One thing I wonder, though is...what will happen when my laptop is not in the network?  Will I just get an error, or something?  I guess I'll find out.

---

### Post by drs305 on 2007-10-27
> **Earthwormzim said:**
> 
One thing I wonder, though is...what will happen when my laptop is not in the network?  Will I just get an error, or something?  I guess I'll find out.

I don't get any errors in similar circumstances. Congratulations on getting your network up and running.  


Response to post #6
In nautilus, at least, the SSH link just sits in the left panel. It looks the same whether it's connected or not. It only attempts to connect when I select it, and then it connects almost immediately if that computer is on. If it's off, that's when I get a "couldn't display...." message. So I never get an error unless that computer is off AND I click on the SSH link. I think that's what you are asking...

---

### Post by Earthwormzim on 2007-10-27
> **drs305 said:**
> I don't get any errors in similar circumstances. Congratulations on getting your network up and running.

You mean the fact that I'm behind a router won't affect anything?

---

