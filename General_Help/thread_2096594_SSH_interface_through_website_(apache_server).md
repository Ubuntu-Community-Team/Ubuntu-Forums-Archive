---
title: "SSH interface through website (apache server)"
date: 2012-12-20
forum: General Help
---

### Post by lg8 on 2012-12-20
Hello,
I'm sorry if I'm at the wrong place.
 
i'm running ubuntu on my server in the NL .
i would like to connect it by ssh from my work though it is not possible by the normal way.
 
i only have a web browser as a tool to access the internet.
 
i noticed that there plenty of web sites which offer to connect by ssh through thier website. they have installed some implementation for that.
 
i would like to install such thing in my own server so i'll be able to access it by from the web.
 
do you have any idea how am i supposed to do that ?

---

### Post by Lars Noodén on 2012-12-20
SSH access is provided by the package OpenSSH-Server.  You only need to install that on your server and then you can connect via SSH.  SSH clients are built into all systems except Windows.  If you are still on that system, you can add [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).  From what I recall, PuTTY should also run from a USB stick.

---

### Post by lg8 on 2012-12-20
> **Lars Noodén said:**
> SSH access is provided by the package OpenSSH-Server. You only need to install that on your server and then you can connect via SSH. SSH clients are built into all systems except Windows. If you are still on that system, you can add [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html"). From what I recall, PuTTY should also run from a USB stick.
 
what i'm saying is that in my work i cannot have securecrt or putty installed.
and i want to find a way to connect by ssh from a web site to my server.
 
like you can have in some websites an implementation for irc chat ? i want one for ssh .
 
how can we do this ?

---

### Post by dannyboy79 on 2012-12-20
putty and winscp can run from a usb stick. I have never heard of a ssh webserver.

---

### Post by Lars Noodén on 2012-12-20
If you have regular systems installed at work, then you do not need to add anything.  It's only if you still have Windows where you have to add PuTTY.  As mentioned twice above, PuTTY can run from a USB stick.

About web-based clients, a quick search found these, but I haven't used or evaluated them.  They might be good or might be garbage.

[https://github.com/antonylesuisse/qweb](https://github.com/antonylesuisse/qweb)
[http://anyterm.org/](http://anyterm.org/)
[http://commando.io/](http://commando.io/)
[http://liftoffsoftware.com/Products/GateOne](http://liftoffsoftware.com/Products/GateOne)
[http://www-personal.umich.edu/~mressl/webshell/](http://www-personal.umich.edu/~mressl/webshell/)
[http://code.google.com/p/shellinabox/](http://code.google.com/p/shellinabox/)
[https://github.com/chjj/tty.js/](https://github.com/chjj/tty.js/)

You're best off if you can use the SSH client that came with your system.

---

### Post by lg8 on 2012-12-20
> **Lars Noodén said:**
> If you have regular systems installed at work, then you do not need to add anything. It's only if you still have Windows where you have to add PuTTY. As mentioned twice above, PuTTY can run from a USB stick.
 
About web-based clients, a quick search found these, but I haven't used or evaluated them. They might be good or might be garbage.
 
[https://github.com/antonylesuisse/qweb](https://github.com/antonylesuisse/qweb)
[http://anyterm.org/](http://anyterm.org/)
[http://commando.io/](http://commando.io/)
[http://liftoffsoftware.com/Products/GateOne](http://liftoffsoftware.com/Products/GateOne)
[http://www-personal.umich.edu/~mressl/webshell/](http://www-personal.umich.edu/~mressl/webshell/)
[http://code.google.com/p/shellinabox/](http://code.google.com/p/shellinabox/)
[https://github.com/chjj/tty.js/](https://github.com/chjj/tty.js/)
 
You're best off if you can use the SSH client that came with your system.
 
 
these sites are exactly what i'm talking about.
i would like to setup such page in my apache server. how can i do this ?
 
believe me, **if could use a normal ssh client in my terminal at work i would of done this.**

---

### Post by CharlesA on 2012-12-20
If you are unable to use a normal SSH client at work due to firewall rules or a proxy, it is not a good idea to try to circumvent those restrictions.

Just an FYI.

---

### Post by lg8 on 2012-12-20
> **CharlesA said:**
> If you are unable to use a normal SSH client at work due to firewall rules or a proxy, it is not a good idea to try to circumvent those restrictions.
 
Just an FYI.
 
i'm sorry guys but i do not understand something.
i came here asking a specific question.
i don't need you to teach me how to behave in my work .
 
i need to you to try helping me solve my problem. that's why this forum is up for.
and because i have something specific i need to solve i also don't need any suggestions of doing something else because i already tried the normal stuff.
 
i need to implement a web-based ssh client to my web site which runs under an apache server on my own server.
 
that is the issue and that is the topic.
 
i'm sorry that i'm sound like this you are just trying to help me, but please - go with the direction of the topic not any other direction.
 
i've just got probably all the answers for how NOT to do what i want to do .
 
Thank tou.:popcorn:

---

### Post by HermanAB on 2012-12-20
Hmm, I think what you should do is install Webmin on your web server.  It has SSH, FTP and terminal features that you access through a web browser.  By default, webmin runs on a high numbered port.  You may have to change that to a dedicated IP address and port 443 in order to get to it through your company firewall.

I have to jump through various kinds of hoops since I live behind a country-wide firewall, so I can feel your pain.

---

### Post by lisati on 2012-12-20
Thank you for the clarification about your question and how it relates to your own server. 

Many of us get nervous about providing support for what, at first reading, looks like someone trying to circumvent the rules imposed by their work place or school. Such things have a habit of going horribly wrong for those involved.

What I did for my own server was to install webmin, which allows me to access most of the tools I might need while at work. 

If you have a good working relationship with your collegues, and take care to keep the lines of communication open with those who might be concerned, you should be able to come up with a workable solution.

---

### Post by KiwiNZ on 2012-12-20
> **lg8 said:**
> i'm sorry guys but i do not understand something.
i came here asking a specific question.
i don't need you to teach me how to behave in my work .
 
i need to you to try helping me solve my problem. that's why this forum is up for.
and because i have something specific i need to solve i also don't need any suggestions of doing something else because i already tried the normal stuff.
 
i need to implement a web-based ssh client to my web site which runs under an apache server on my own server.
 
that is the issue and that is the topic.
 
i'm sorry that i'm sound like this you are just trying to help me, but please - go with the direction of the topic not any other direction.
 
i've just got probably all the answers for how NOT to do what i want to do .
 
Thank tou.:popcorn:

Aggression to staff giving advice is not going to help your cause.

In this case, please re read the Forum code of conduct and thread closed.

---

