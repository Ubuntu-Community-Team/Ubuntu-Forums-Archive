---
title: "thunderbird hotmail extension can not install"
date: 2007-09-05
forum: General Help
---

### Post by sdowney717 on 2007-09-05
there is no install option on my thunderbird email version 2.0.0.6
If I click tools there is no menu extensions to click.


[http://webmail.mozdev.org/installation.html](http://webmail.mozdev.org/installation.html)



How to Install

   1. Right-Click the link above and choose "Save Link As..." to Download and save the file to your hard disk.
   2. In Mozilla Thunderbird, open the extension manager (Tools Menu/Extensions).
   3. Click the Install button, and locate/select the file you downloaded and click "OK".

---

### Post by sdowney717 on 2007-09-05
ok, i got it installed the instructions are not well written.
you click tools - add ons and then install, find the file and install it.
it does not say this in their instructions.
I need step by step just like you would show someone who had never done this before. They cant just assume you already know how to do this when they write these manuals!

now I cant find 'webmail options'
quote
The first step is to check the WebMail extension is running. Go to the WebMail options, on the server panel the status of the three servers is displayed. The status for the enabled server(s) should be "Running". If the WebMail extension fails to start this could be due to the operating system blocking ports below 1024, try setting the port to value higher than 1024 and restart Thunderbird

---

### Post by sdowney717 on 2007-09-05
as you can see I have the extensions installed

---

### Post by sdowney717 on 2007-09-05
I did find if you click preferences when the add-ons are showing you get another page that tells me no hotmail account found. Well I supposedly tried to create one as webmail.
If they want people to use this, why not give good directions

---

### Post by sdowney717 on 2007-09-05
here is my supposed webmail hotmail account

---

### Post by sdowney717 on 2007-09-06
[http://www.scribd.com/doc/128984/howtothunderbirdhotmail-v2](http://www.scribd.com/doc/128984/howtothunderbirdhotmail-v2)

apparently it is buggy and dependent on the moon being in the right spot

---

### Post by sdowney717 on 2007-09-06
[http://www.math.colostate.edu/~reinholz/freebsd/thunderbird_tips.html](http://www.math.colostate.edu/~reinholz/freebsd/thunderbird_tips.html)

this is for future reference for setting ports and a 'how to' set up using a non current version.
and it still does not work.

at least it is not working for anyone else either
[http://forums.mozillazine.org/viewtopic.php?p=3021409&](http://forums.mozillazine.org/viewtopic.php?p=3021409&)

---

### Post by sdowney717 on 2007-09-06
[http://forums.mozillazine.org/viewtopic.php?p=3039194&sid=8641ef3d4a526729b716ec81c630bf2e](http://forums.mozillazine.org/viewtopic.php?p=3039194&sid=8641ef3d4a526729b716ec81c630bf2e)

pakho,
You have to add the @msn.com to the username for it to work.

that is under server settings user name, must include @xxxx.com
This is not  easy info to find.

I got it working, once it recognizes that a hotmail account exists, you will be able to selecr
old hotmail, webdav, live hotmail from within the preferences section of tools add-ons - hotmail extension

And the webmail  extension settings for port pop is 5200, smtp is 5201

---

### Post by sdowney717 on 2007-09-06
for sending mail from hotmail you must set port to 5201

and include @msn.com in user name (or hotmail.com)

this outgoing server has to selected 
and the settings are at the bottom of the list

---

### Post by sdowney717 on 2007-09-27
[http://www.math.colostate.edu/~reinholz/freebsd/thunderbird_tips.html](http://www.math.colostate.edu/~reinholz/freebsd/thunderbird_tips.html)

another link that may help

---

