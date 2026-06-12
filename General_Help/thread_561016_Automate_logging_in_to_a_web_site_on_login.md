---
title: "Automate logging in to a web site on login"
date: 2007-09-27
forum: General Help
---

### Post by trevorv on 2007-09-27
Hi, 

I've just started university, and to use the net from where I live you have to fire up a web browser. When you try to get to a website for the first time after a login, it redirects you to a university login page, which you must type your username and password and tick a box before continuing.

I want to automate this process but have no idea how! Is there any web browser which lets you record some kind of macro or something?

Thanks, 
Trevor

---

### Post by kidders on 2007-09-28
Hi there,

> **trevorv said:**
> Is there any web browser which lets you record some kind of macro or something?No. Something like that would be a security disaster! I very much doubt any web browser would let you chain requests together in a way other than those explicitly allowed by the HTTP specification.

Having said that, you could quite possibly write a script of some sort to handle the connection setup for you. For example, imagine that your university did something like this to you...[LIST=1]
[*]-> GET http://www.google.com/
[*]<- HTTP/302
[*]-> GET https://www.youruniversity.edu/login/
[*]<- HTTP/200
[*]-> POST https://www.youruniversity.edu/login/
[*]<- HTTP/200[/LIST]In theory, your script could skip straight to step 5, and POST your authentication information to wherever it needs to go. If I were you, my first step would be to perform as much of the procedure as possible manually (eg with telnet), to get an idea of how much of it needed to be implemented in a script.

The worst case scenario might be...[LIST]
[*]You may need to grab a cookie from one of the HTTP responses.
[*]Part of the exchange might be wrapped in SSL.
[*]There might be hidden form fields in the login page, usually designed to make what you want to do as difficult as possible.
[*]You might need to spend some time tending to irritating little details like user agent spoofing.[/LIST]KDE, Gnome & others will let you auto-run things on login. Even better, you could set your script up as a startup service, so you could go straight online without being tied down to a graphical environment.

As a side note, you could probably use JavaScript to have something like Firefox perform your login for you. Going down that road would force you to open a web browser to use the internet though.

---

