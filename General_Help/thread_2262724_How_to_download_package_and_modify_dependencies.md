---
title: "How to download package and modify dependencies?"
date: 2015-01-26
forum: General Help
---

### Post by stevenm-wills on 2015-01-26
I've installed NGINX and phppgadmin. They both work. However, Apache2 is a dependency of phppgadmin. So even though NGINX and phppgadmin are working, each time I try to install a package in my terminal I'm given an error saying trying to configure phppgadmin Apache is not running.

Apache is a dependency, but it isn't required by any means when using NGINX. I want to download the phppgadmin package and change the dependencies so I'm not given the error over and over.

How can I do this?

Thanks.

---

### Post by mc4man on 2015-01-26
There could be a couple of ways, one would be to take your currently installed phppgadmin package, unpack, edit the control file to suit, then repack & install the 'new' deb package.
Your current can be gotten from ubuntu packages or launchpad (you didn't mention what release of Ubuntu so a link to source launchpad page - 
[https://launchpad.net/ubuntu/+source/phppgadmin](https://launchpad.net/ubuntu/+source/phppgadmin)

The way I've done this here is thru attached script, unpack, place in a bin folder in PATH & make sure it's executable. The advantage to the script is it will give you a new package that is a minor upgrade to the old one & will maintain proper permissions.

screens should show - 
placed phppgadmin package in an empty folder, then cd'ed to that folder in a terminal
In terminal ran editdeb command, this will open the control file in your text editor.
For this demo purpose removed the apache dep & pipe to httpd (- dep is satisfied by either apache or httpd so something for you to consider first?

After editing the control file,  save the file, then a new (.modified) deb is auto created. You would use dpkg to install it (sudo dpkg -i /path/to/modified deb


Edit: if you can't 'get' from screens just ask. This forum 'downsizes' screenshots & they can be harder to see on higher rez screens...

---

### Post by stevenm-wills on 2015-01-26
> **mc4man said:**
> [COLOR=#000000]Apache dep & pipe to httpd (- dep is satisfied by either apache or httpd so something for you to consider first? [/COLOR][COLOR=#000000]
So what are you saying? 

I am using 14.10, so [/COLOR][COLOR=#333333][FONT=Ubuntu]The Utopic Unicorn. Which file do I want? tar.gz, .deb, .dsc[/FONT][/COLOR][COLOR=#000000]


[/COLOR]

---

### Post by George_Bateman on 2015-03-10
The script takes a .deb file.

---

