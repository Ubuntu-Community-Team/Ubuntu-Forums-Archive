---
title: "About Install"
date: 2007-12-15
forum: General Help
---

### Post by Caghkan on 2007-12-15
Hi everyone! I am new user for ubuntu and I have a question. I want to install poker game and I found one. Its web address is [www.pok3d.com](www.pok3d.com) and it say below.

>     *
      Ubuntu GNU/linux gutsy
      Add the following lines to your /etc/apt/sources.list 
      deb [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./
      deb-src [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./

      If not present, 
      add deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe 
      
       Install the software and the graphics: apt-get update
      apt-get install python-poker3d poker3d-data 

      Run with /usr/games/poker3d


However, I don't understand how to install it because I am getting use to write codes!

Please help me! When I wrote this codes, root terminal didn't find them!

---

### Post by oldos2er on 2007-12-15
It might be easier for you to go to System, Administration, Software Sources, click the Third-party software tab and add the repositories from there.

---

### Post by Caghkan on 2007-12-15
Thank you!

---

### Post by Caghkan on 2007-12-15
I can't do it again! :( Please help me!

---

### Post by oldos2er on 2007-12-15
> **Caghkan said:**
> I can't do it again! :( Please help me!

 I'll try to help, but can you be more specific about what you're doing and what's going wrong?

---

### Post by Caghkan on 2007-12-15
> **oldos2er said:**
> I'll try to help, but can you be more specific about what you're doing and what's going wrong?

I opened Software Source and I couldn't do it. I don't know how to install this program because I started using ubuntu new. If someone explain me what should I and how to install it, I will do it.

---

### Post by oldos2er on 2007-12-15
Open Software Sources, click the Third-party software tab. Click the Add button, then copy and paste these lines in one at a time:

      deb [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./
      deb-src [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./

(they're the same ones as in your first post). Click 'close.' You'll be prompted to reload the sources list, go ahead and do that. Now you'll be able to install the program using Synaptic Package Manager.

---

### Post by Sef on 2007-12-15
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by Caghkan on 2007-12-16
> **Sef said:**
> Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

> **oldos2er said:**
> Open Software Sources, click the Third-party software tab. Click the Add button, then copy and paste these lines in one at a time:

      deb [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./
      deb-src [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./

(they're the same ones as in your first post). Click 'close.' You'll be prompted to reload the sources list, go ahead and do that. Now you'll be able to install the program using Synaptic Package Manager.

Thank you all, but there is an another problem. I did what you said and everything was OK except one thing. I had written those lines without ./ and system accepted it. However, then showed that message; [http://pok3d.net/gutsy/dists/deb-src/http://pok3d.net/gutsy/binary-i386/Packages.gz:](http://pok3d.net/gutsy/dists/deb-src/http://pok3d.net/gutsy/binary-i386/Packages.gz:) 404 Not Found

What can I do now? Also, I don't find anything about install these method in How to Install Anything in Ubuntu's page.

---

### Post by Sef on 2007-12-17
> Thank you all, but there is an another problem. I did what you said and everything was OK except one thing. I had written those lines without ./ and system accepted it. However, then showed that message; [http://pok3d.net/gutsy/dists/deb-src...6/Packages.gz:](http://pok3d.net/gutsy/dists/deb-src...6/Packages.gz:) 404 Not Found

Either the link is bad or the site is down.

---

