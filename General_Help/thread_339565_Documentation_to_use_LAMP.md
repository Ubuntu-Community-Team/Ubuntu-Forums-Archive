---
title: "Documentation to use LAMP?"
date: 2007-01-15
forum: General Help
---

### Post by bobleny on 2007-01-15
I recently installed Apache, PHP, MySQL, and php myadmin. On windows, I just downloaded WAMP and it did everything for me. I went through the guide to setup and install LAMP, but I don't know how to use it. For example, I don't know where all the configuration files are, or where to place my web files that are to be in localhost.

Does anyone know of any documentation for this stuff? I would really like to know, but in the mean time, I will continue to look online...

Thanks!

---

### Post by _duncan_ on 2007-01-16
Hi. I used [[COLOR="SandyBrown"]this[/COLOR]]("https://help.ubuntu.com/community/ApacheMySQLPHP") guide to set up LAMP on my development PC. After that, all I have to do is put in my web projects into the /var/www folder.

---

### Post by bobleny on 2007-01-16
Yeah, thats what I did,... but every time I go to say, "http://localhost/test.php", my browser trys to download the file instead of displaying it.
And yes, I must point out that I do know the problem is mentioned in the link above! I'm just saying...

Then, I can't have the www file there, it needs to be changed. How do I change it?

This is frustrating!

Maybe there is no documentation on how to use this, just how to set it up. I keep finding articles on how to install it.... Nothing on how to use it.

I think I will try to find something on how it works instead of how to use it....

I'm not good at looking things up....

---

### Post by bobleny on 2007-01-16
I tried the fix in that was mentioned in the guied to install it, and it still doesnt work...
I already have "libapache2-mod-php5" installed. php4 is not installed anyways.
I have restarted the the machine, which in turn, should restart everything. If not, I also ran the "sudo /etc/init.d/apache2 restart" command, which I believe restarts apache2.

So I have no Idea what is wrong.... :(

---

### Post by _duncan_ on 2007-01-16
sounds like you have both php4 and php5 installed. I had a lot of trouble with that kind of setup also. I reinstalled everything (including Ubuntu) and decided to just stick to php5. After that the installation worked smoothly as mentioned in the article. I'm not saying you should do the same, but that is what worked for me.

> Then, I can't have the www file there, it needs to be changed. How do I change it?
/var/www is a folder owned by root. If you're trying to put files there using the command line, you should add "sudo" before the copy (cp) command. For example:

```
sudo cp /*path_to_your_file*/*filename* /var/www
```

If you're using Nautilus file browser to copy/paste files, you should fire up Nautilus as root by typing "gksudo nautilus" from a terminal. Then you can easily paste files and create subfolders in the /var/www folder.

Please don't take offense at my next statement. I think some of the problems you're having is caused by unfamiliarity with how linux works. Stuff like issuing commands from the terminal as root, etc. Maybe it's worth reading up on terminal commands like sudo and gksudo? For starters try this in a terminal:

```
man sudo
```

This should give you a detailed documentation on how the sudo command works.

The learning curve of migrating from windows to linux is very steep at first, so it really is a bit frustrating at times. Just hang in there.

---

### Post by bobleny on 2007-01-16
I don't want the www in the directory for many reason, not just the damn root crap.

I will only be on ubuntu for a little while. Once I learn more about linux, I'm going going back to Gentoo!!! I like Gentoo.........

And, no, I don't have php4. I never tried to install php4 because I don't want php4... Thats why I only installed php5.
Thats why I said, "php4 is not installed anyways."

---

### Post by bobleny on 2007-01-17
I'm sorry if I sound rood (or however that is spelt), I'm just a little frustrated with all the problems I am havening, because I don't have the technical understanding to figure them out my self, like I can in windows...

I did a reinstall of LAMP and now I can't access "localhost". I think it needs to be configured...
Should I follow the guide above for dapper or breezy, or should I find something else for edgy?
I am currently running edgy eft.

---

### Post by _duncan_ on 2007-01-17
I'm using edgy. The guide for dapper works for edgy. Ignore everything about breezy in the guide and you will be fine.

Take note that I am not an expert in LAMP, not even in Ubuntu. I just saw your thread, no one seems to be helping you, that's why I responded even with my limited knowledge. On the other hand, I was able to make it work in Breezy, then Dapper and now Edgy, so I'm not entirely clueless either. What I do know is that if you follow the guide to the letter, then chances are it will work for you. My knowledge is limited to what is written in the guide, so I can not help you with special customizations not covered by the guide.

I do understand that some of the instructions in the guide may be vague for a newcomer. So if there are stuff in the guide you don't understand, post your questions here and I will try my best to clarify them for you.


Anyway, to answer your specifc problem with localhost: In the guide, there is a section that looks like this:

```
If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then edit sudo gedit /etc/apache2/apache2.conf and add ServerName localhost at the end of the file
```

Did you encounter this error when setting up apache2? I did and followed the suggestion. After that I was able to connect to localhost. That means:

1. Open a terminal and type:
```
sudo gedit /etc/apache2/apache2.conf
```

2. The text editor will pop-up. Go to the end of the file and type:
```
ServerName localhost
```

3. Make sure you pressed the enter key so that the cursor goes to the next line before saving and exiting the text editor.

4. check if you can already access localhost or 127.0.0.1 from the browser.

---

### Post by bobleny on 2007-01-17
I used adept manager to install the stuff, so I didn't get any errors. But, the Servername thing worked. Now I have access to localhost.

My browser is still trying to download the files instead of displaying them even though I did the "sudo a2enmod php5" thing. I also made sure the lib thingy was installed too....

Do you know anything about this?

---

### Post by hasuob on 2007-01-17
Hey, I had the issue of my browser trying to download the .php page instead of display it. I assumed it was because the php module wasn't properly working with apache (I had apache2 and php5 and mysql5 in the default setup which comes with Ubuntu 6.06 So i uninstalled everything to do with php and apache using Synaptec. Then I reinstalled apache and php 5 and now I can't even view localhost's default index.html page! I get a "unable to connect" error saying "Firefox can't establish a connection to the server at localhost." Any help you guys might be able to give me? Advice on doing a completely new install? I'm new at linux so don't assume I know anything :/

---

### Post by bobleny on 2007-01-17
I rebooted my system and now apache I can't access localhost. I thought maybe I had to start it. So I went to the terminal told apache to start, and still doesn't work.

Do you have any ideas? If not, I will ask on another forum or in IRC where I can get more help.

---

### Post by _duncan_ on 2007-01-17
I had the same error the first time I tried to install LAMP in Ubuntu. I initially installed php4, then decided to install php5 as well. Also couldn't get it to work even after adding libapache2-mod-php5, doing sudo a2enmod and restarting apache.

In my case, I was quite sure it was php4 interfering with php5 but didn't know exactly which file to check. Since I was working with a fresh install of Ubuntu at the time and will not lose any data, I reinstalled Ubuntu, then went through the process again, this time making sure to install only php5, and everything worked correctly.

One difference I see is that I normally use apt-get or aptitude instead of adept manager to install the required packages. I'm not familiar with adept, but from what I read in this forum, aptitude is better with package dependencies than apt-get. However, this may not necessarily have anything to do with your problem.

Oh yeah, another trivial difference is I always set the memory_limit value from the default 8MB to 32MB in the /etc/php5/apache2/php.ini file. But I don't see why it would make a difference in your case.

Yes, it would be a good idea to seek more help coz the only remaining advise I have is a bit extreme (reinstalling ubuntu).

---

### Post by bobleny on 2007-01-21
YAY! I finally got it to work!

[http://www.ubuntuforums.org/showthread.php?p=2037801#post2037801](http://www.ubuntuforums.org/showthread.php?p=2037801#post2037801)

---

