---
title: "Proxyserver on my ftp???"
date: 2006-10-10
forum: General Help
---

### Post by lungan on 2006-10-10
Hi, since my school blocked a lot of urls so that all the pupils can't access the pages they want i have decided to put up a proxyserver so my friends can access the pages, but im a newbe on proxy, i have an ftp i that is what i need and so on, 
The thing is just that i wanna set up an server so me and my friends can can access the internetpages throught that proxy but dont have a clue how to do it, pleace explain well what i need and so on (clients etc.).

Your homie lungan

---

### Post by Jussi Kukkonen on 2006-10-10
If you want a http (web) proxy, I don't see how ftp would be of much use...

Your server needs to be accessible from the internet (or at least from where ever you will be connecting from), the server should also have more upload bandwidth than a normal home connection otherwise it'll feel dog slow.

You need to install and setup a http proxy. There are several in the repositories (try *apt-cache search http proxy*), personally I've used tinyproxy with success in a situation like this. Install it, read the documentation (*man tinyproxy*), and configure it (edit the self-documenting  */etc/tinyproxy/tinyproxy.conf*).

---

### Post by Jussi Kukkonen on 2006-10-14
Hope you don't mind me pasting your private message here -- I assumed you wouldn't as it's not really personal...

[QUOTE=lungan]Hi there, u said u have tinuproxy and have with success used it when for example your school had blocked some homepages, but the thing is that i cant find a documantary. Can't you with yease words explain for me how i need to configure the tinyprox.conf so i have access to it from school and if i have to do someting special on the computer i whanna surf on...[/QUOTE]
I can't really tell you how to configure your machine -- that's too general... I'm sure I or someone will help if you have a specific problem.


I suggest you start with this:
1. Find out (if you don't know this already) if your server machine is accessible from the internet (or more specifically your school). Try e.g. pinging the machine...
2. Install tinyproxy on the server. Go through tinyproxy.conf, and check if there's something that looks wrong.
3. Try to use the proxy from the same (tinyproxy server) machine -- by setting your web browser proxy settings.
4. Try the same thing on the (school) client machine.

---

