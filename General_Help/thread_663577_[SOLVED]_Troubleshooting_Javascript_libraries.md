---
title: "[SOLVED] Troubleshooting Javascript libraries"
date: 2008-01-10
forum: General Help
---

### Post by DugieHowsa on 2008-01-10
After troubleshooting what I thought was a firefox problem, it now appears that I have a javascript problem.

On a single Ubuntu Gutsy machine, I have trouble using web sites that use javascript to redirect to secure (https) sections of the web site.  I first encountered this problem in firefox, but then found it was happeing with opera as well.

Now, I have the sun-java6-plugin installed correctly, but what I just recently realized is that java and javascript are completely different things, and that javascript does not utilize the java plugin.

Back to the javascript.  When I click on a button that executes javascript code that does not redirect to a http site, it operates as expected.  Its only when the button is going to redirect to an https site.

I am able to replicate this issue on the following sites:

[www.citizensbank.com](www.citizensbank.com) 
[www.ticketmaster.com](www.ticketmaster.com)

I will mention I am running on a AMD Athlon 64 X2, and I am running the 2.6.22-14-generic version of the kernel.  Not sure if that is relevant, but some of the reading I have done points to that it may be.  I am also using Firefox 2.0.0.11 and Opera 9.25.

---

### Post by kidders on 2008-01-11
Hi there,

I imagine the javascripts in question aren't well-written. Just in case the problem is something else though, you could post one (or both) of them, if you like.

---

### Post by DugieHowsa on 2008-01-11
Here is the javascript I could pull from the head section of one of the pages in question, and the entire page of the other as it sees to be a frame of the main page.  Unfortunately, if there is an error in the code, I am powerless to change it.

---

### Post by kidders on 2008-01-11
Hey again,

I don't seem to have any problems with those scripts in either Opera or Firefox. Assuming they're not generating any errors for you either, there may be something in your browser preferences that's stopping them from working.

---

### Post by DugieHowsa on 2008-01-11
Problem solved.  I was running peergaurdnf ([http://sourceforge.net/projects/moblock-deb](http://sourceforge.net/projects/moblock-deb)).  As soon as I killed that process the javascripts redirecting to https worked in all browsers.  I also removed the link from the /etc/init.d directory so it will no longer start automatically on startup.

---

