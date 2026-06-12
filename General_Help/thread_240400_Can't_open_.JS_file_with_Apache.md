---
title: "Can't open .JS file with Apache"
date: 2006-08-20
forum: General Help
---

### Post by jpmonette on 2006-08-20
Hi

I just installed Apache with PHP4. I'm trying to open a .JS file from my browser but the access sounds forbidden:

> Forbidden

You don't have permission to access /jpmonette/LaTeXMathML.js on this server.
Apache/2.0.55 (Ubuntu) PHP/4.4.2-1build1 Server at localhost Port 80


I don't know why, I can open this file manually with Gedit without root powers but I can't open it throw my web browser. Do I need to change the chmod on this file?

Thanks

---

### Post by nanotube on 2006-08-20
> **jpmonette said:**
> Hi

I just installed Apache with PHP4. I'm trying to open a .JS file from my browser but the access sounds forbidden:



I don't know why, I can open this file manually with Gedit without root powers but I can't open it throw my web browser. Do I need to change the chmod on this file?

Thanks

make sure the file gives "everyone" read permission. so chmod it to 644 permissions.

---

### Post by scxtt on 2006-08-20
w/o really (really) thinking about it, i think you're using it in the wrong way ... JS should be used w/in HTML, not as its own separate file (as in pointing your browser to **[http://www.some-website.com/JSexample.js](http://www.some-website.com/JSexample.js)**) ... if you want to keep your *.js files separate, you can just include them in a single line in your HTML:

. . .
<head>
<SCRIPT type="text/javascript" src="/path/to/script.js">
</head>
. . .

---

### Post by jpmonette on 2006-08-21
Thanks, i just fixed the CHMOD for the folder and it's working :)

---

