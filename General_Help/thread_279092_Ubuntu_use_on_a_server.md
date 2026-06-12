---
title: "Ubuntu use on a server"
date: 2006-10-17
forum: General Help
---

### Post by idowindows on 2006-10-17
This may or may not be the proper forum to post this...

I work for a school district and we have a number of servers basically well..gathering dust.

I wonder what gain can we have as a school district if I was to grab one of these servers and install Ubuntu on it.  Can our network PCs (windows-networked) be of any use to a Ubuntu-run server?  What apps can Ubuntu offer of use to a school district?

I ask this for I am BARELY getting my feet wet with Linux and basically, know nothing about it.

---

### Post by woorzel on 2006-10-17
well this is a very very generic question ... what kind of services do these servers have to provide to start with?

---

### Post by Iowan on 2006-10-17
I mighta stuck the thread in **Servers**, but I doubt anyone minds it being here...
Some ideas: One server could be set up as a Domain controller (unless you already have one). Other servers can act as remote storage - students (faculty too, for that matter) can store files on a Samba server and retrieve them from whatever PC they're logged onto.  A LAMP server can either provide a Web-workshop - or just a local information portal.  
I still haven't gotten much past playing with the OS - so I'm not well-informed about what other apps are available that might interest a school system.
As **woorzel** asked - what would you LIKE them to do?

---

### Post by IYY on 2006-10-17
> I wonder what gain can we have as a school district if I was to grab one of these servers and install Ubuntu on it. 


Well, see the list of cool apps below. I think that many students (though not all, of course) will benifit from learning a somewhat different approach to computers. They could learn to program, and do other cool things in the terminal.

> Can our network PCs (windows-networked) be of any use to a Ubuntu-run server?

Depends on the way they are currently networked. If it's a standard Windows network, like the type people install in their homes, you will be able to use it pretty much in the same way as you do in Windows using **Samba**. Even if the networking is not compatible, your Windows machines will be able to access FTP and SSH on the Ubuntu machine.

> What apps can Ubuntu offer of use to a school district?

If the machine in question is indeed to function as a server (as opposed to a workstation), you obviously do not intend on running any graphical applications. So, the cool non-graphical things you will be able to do with an Ubuntu server include:

[LIST]
[*] As I said above, give your students FTP accounts with limited storate. They can store their assignments on it and access them from home.

[*] Also stated above -- and SSH server. This will allow your students to remotely log in to the Ubuntu server and do various stuff in the terminal.  This will teach them Linux in general, but they can also do things like:

[*] Create beautifully formatted assignments using LaTeX.

[*] Publish their own websites (if you install an Apache server on your Ubuntu machine).

[*] Learn programming in one of the many languages that have Linux compilers: C, C++, Python, the shells, Perl, Lisp, and many many others.

[*] Use Imagemagick to edit images in batch (for example, resize 1000 images to 800x600)
[/LIST]

> I ask this for I am BARELY getting my feet wet with Linux and basically, know nothing about it.


I would of course suggest to first install Ubuntu on a machine at home and learn how to use it. And I don't mean the graphical stuff, because remember that that is not what you do with a server.

---

### Post by bsussman on 2006-10-17
I suggest you study the edubuntu project - it is intended for server/thin client situations.  It is optimized in terms of applications and management tools for the classroom.

If the other systems will remain windows boxes, there is a limited amount of benefit.

To advise, I would want to know what your hopes and aspirations are and what your limitations (necessary current packages, skills, etc) are.

(ed)ubuntu is not right for every situation.  Could be that an ipcop firewall in front of windows/ubuntu local machines would be best for you.

Like I said - what do you want to do is computing?

---

### Post by idowindows on 2006-10-18
Thanks to all for all your insight.

Although I am not discouraged, I wonder if upper management (IT) would frown on a linux-based server.

Needless to say, our entire operation is Windows-based. Somehow, I do foresee resistance to my project.

Someone mentioned Samba to have the Linux box work with Windows platform, is this a free application?

Thanks...

---

### Post by merkur2k on 2006-10-18
yes, samba is free. it allows a linux machine to communicate with windows machines as if it were one of them. ie it will show up in windows machines network neighborhood.
If the IT department there are a bunch of MS flunkies (and most are, especially in schools), expect ALOT of resistance from them. They have been exposed to alot of FUD from other MS flunkies, and generally tend to believe that linux is some sort of "hackers" OS that is only ever used to do harm to others.

---

### Post by doobit on 2006-10-18
> **idowindows said:**
> Thanks to all for all your insight.

Although I am not discouraged, I wonder if upper management (IT) would frown on a linux-based server.

Needless to say, our entire operation is Windows-based. Somehow, I do foresee resistance to my project.

Someone mentioned Samba to have the Linux box work with Windows platform, is this a free application?

Thanks...

Many companies use Linux based servers even though they have all Windows workstations. The LAMP solutions will give you a nice, secure gateway to the web and file access for your LAN.

---

