---
title: "Http header &quot;CAPTURE&quot; - web design"
date: 2014-02-28
forum: General Help
---

### Post by sarahfoxnz on 2014-02-28
Hello.

I've got Firefox  26.0, & have one http tool. However its not doing what i want

I'm designing a web-site, & it is going, However i am trying to re-direct to another page. 

it is re-directing OK, however not ending up at the correct page.  It seems to activate the "404" error page.

using the tool, i only get the http headers of the current (last) page. Is there a way to 'capture' the headers of each page in my sequence ?

1 :- My web page (I activate the website form)

2:- it processes the form, & redirects to my ending page

3 :- i end up at my "404" error page

When i activate the form, i expect to end up at step 2, but i only end up at step 3. 

I don't see WHY / How it ends up at step 3. 


Is there a way I can capture the website / browser process for the last xx minutes ?

:- starting page
:- http codes
:- any re-direct commands
:- the website i end up at 

With the ability to "scroll" back, & see the prior http requests - NOT just  the current / last one.

---

### Post by Lars Noodén on 2014-02-28
The place to look would be on the server side in the web server access logs.  Which web server are you using, nginx or Apache2?  

About the redirection, what have you put for that in the web server's configuration?

---

### Post by sarahfoxnz on 2014-02-28
i'm on a shared host -  I've found the error log but its not recording any "errors" - The redurects are correct (as per the server) so its not recording. the only error that is recorded is a repeating CGi/perl script (i havn't touched in many years & is not used by my current PHP scripts.)

is there a tool / utility on the browser i can use ?

---

### Post by Lars Noodén on 2014-02-28
There might be a plug-in for Firefox.  But you can see the headers that the server has responded with using [wget](http://manpages.ubuntu.com/manpages/saucy/en/man1/wget.1.html)

```

wget -S -O /dev/null http://www.google.com/

```

If there are too many, you can pipe the output through [less](http://manpages.ubuntu.com/manpages/saucy/en/man1/less.1.html)

```

wget -S -O /dev/null http://www.google.com/ 2>&1 | less

```

---

### Post by Lars Noodén on 2014-02-28
Here is a one Firefox add-on which shows the headers for the current page:

[https://addons.mozilla.org/en-US/firefox/addon/live-http-headers/](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers/)

It also includes the response headers for all the components retrieved as part of the page.  The wget example above only gets the single page itself and no pictures, etc.

---

