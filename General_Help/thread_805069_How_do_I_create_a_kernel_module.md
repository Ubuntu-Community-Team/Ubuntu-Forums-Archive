---
title: "How do I create a kernel module?"
date: 2008-05-23
forum: General Help
---

### Post by makyramallo_22 on 2008-05-23
Hi, my name is Macarena, I'm a software engeneering student and I am desperate for some help. 

I need to create a new kernel module, something very simple, such as a module that generates a "pip" sound everytime the hour changes. But the problem is I don't even know how to start!! I would really apreciate if someone could give me some information or at least an example that I can use as a guide. 

Sorry for my terrible english.. 

Thanks!

---

### Post by ShodanjoDM on 2008-05-23
I don't think it's necessary to create a kernel module for a simple task like that. A script would suffice.

Sorry I can't help since I'm still learning the basics as well, but hopefully someone will come with an idea soon.

---

### Post by ibuclaw on 2008-05-23
Can you define the sound "pip"? (an audio example would be great)...

Although, maybe this [gnome-alarm app]("http://alarm-clock.pseudoberries.com/") is what you are looking for.

You can set an alarm for every hour. I think sounds are integrated into the app too.

[EDIT]
Installation:
```

sudo echo "deb http://ppa.launchpad.net/joh/ubuntu hardy main" >> /etc/apt/sources.list.d/launchpad.list
sudo apt-get update
sudo apt-get install alarm-clock-applet

```

Regards
Iain

---

### Post by makyramallo_22 on 2008-05-26
Thank you very much for your help, but the sound was just an example, I need to integrate a new module on the kernel, it can be a program just as simple as the "pip" sound (it doesen't really matters how it sounds), or whatever we can imagine. The thing is that I don't know how to do it...

Between(Among) the topics that must investigate they are:

1. How to initialize and to finish a module.

2. How to associate it with a device in/dev.

3. How to create an entry in/proc.

4. How to shoot a kernel thread.

5. How to take parameters 

Thank you again for all your help, and well hope you can understand my idea!

Maky.-

PD: Sorry again for my english =)

---

### Post by stix213 on 2008-07-09
I know this is an old post, but I notice no one bothered to answer your question.  

You might want to look at the book "Linux Device Drivers" for some help (I haven't read it, but I hear it is really good and is exactly what you want).  The free online version of latest 3rd edition is available here:

[http://lwn.net/Kernel/LDD3/](http://lwn.net/Kernel/LDD3/)

For a quick example of writing/linking a simple module, take a look at the helpful march 9th comment by dalonso here:

[http://ubuntuforums.org/showthread.php?t=713447](http://ubuntuforums.org/showthread.php?t=713447)

Also, grab the attachment to that comment which includes the source and builds just fine first try on my machine :)  Hope that helps you and anyone else who stumbles on this post.

---

### Post by Vivaldi Gloria on 2008-07-09
Also have a look at

The Linux Kernel Module Programming Guide

available here:

[http://tldp.org/guides.html](http://tldp.org/guides.html)

---

