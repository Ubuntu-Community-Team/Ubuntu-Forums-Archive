---
title: "Writing A Script and Executing it At Certain Times?"
date: 2007-11-28
forum: General Help
---

### Post by i.wanna.corndog on 2007-11-28
Hey everyone,

I have a bit of a challenge :)

I need to do a few things:

1.) I need to write a script to do the following:
     -Execute lynx with a specific URL (i.e. "lynx http://www.testurl.com/")
     -Press several keystrokes within lynx (i.e. "username[TAB]password[TAB][TAB][ENTER]q")

2.) Run this particular script every 2 hours. Also, I don't have X (or any other GUI) installed, so it has to be done through the command prompt over SSH.

If you want to know why, here's the deal: I am on a campus network with a headless server (no gui) and they have a web-based logon page that you must login with in order to access the internet. The username and password expire every 2 hours, and I want to keep a persistent connection to the internet so I don't have to ssh over to my headless server every 2 hours.

I will be forever grateful to anyone who can point me in the direction I need to go to figure out how to do these things. I have been searching for about the past half hour and have come up dry.

Thanks!
Dan

---

### Post by bettlebrox on 2007-11-29
Maybe you can use expect?

[http://expect.nist.gov/](http://expect.nist.gov/)

---

### Post by i.wanna.corndog on 2007-11-29
Thanks for the lead...I'll check it out.

---

