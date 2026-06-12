---
title: "I'm new to Ubuntu and I need help installing a tar.gz file! (Info Included)"
date: 2008-07-01
forum: General Help
---

### Post by XMBuntu on 2008-07-01
I have Ubuntu Gutsy 7.10 on my PS3 (which I am currently using), and I want to install this emulator

[http://www.zophar.net/unix/snes.html](http://www.zophar.net/unix/snes.html)

I have downloaded the "snes9x 1.43 Final" Version.

I have unpacked it and have done everything it says to do in the other guides. I am still having trouble. If someone could download and install this, and post some screen shots it would be greatly appreciated. This way I could get the hang of some of the basic commands and eventually learn to unpackage/install other files. 

Thank you so much,

XMBuntu

---

### Post by lisati on 2008-07-01
Were you getting any error messages? If so, they could help us work out which direction to point you in.

---

### Post by soccerboy on 2008-07-01
there is a version of snes9x in the repos by the way (if you want to take the easy way)

---

### Post by theshadowwithanmp5n on 2008-07-01
they have many emulators in the Add/Remove section of the applicatons menu

---

### Post by camccall on 2008-07-01
Not to just totally skip your question, but you could install this via apt using sudo apt-get install snes9x-x.

Of course if you want to install this via source, meaning using the .tar.gz file you downloaded, we would be more than happy to help.  I would guess you would learn a lot. :)

---

### Post by edm1 on 2008-07-01
As other's have mentioned, it is available in the repositories. Just type 'snes' in synaptics search bar and there's a few options. You will also need a frontend like snes9express or gsnes9x.

p.s. in 3 years of using ubuntu, i've never had to install anything from source.

---

### Post by XMBuntu on 2008-07-01
Here's what I get:

mike@PS3:~$ su
Password: 
root@PS3:/home/mike# tar -xzvf '/home/mike/Downloads/Install Files/snes9x-1.43-linux-x86.tar.gz'
snes9x-1.43/
snes9x-1.43/snes9x
snes9x-1.43/config.info
snes9x-1.43/hardware.txt
snes9x-1.43/problems.txt
snes9x-1.43/changes.txt
snes9x-1.43/faqs.txt
snes9x-1.43/readme.txt
snes9x-1.43/readme.unix
root@PS3:/home/mike# 


I don't know what to do from here. Please if you know, tell me. I tried ./configure , but it doesn't work. I will, for now, use the one under the Synaptic Manager. Thank you for the help. Just for kicks I would like to find out how to use the terminal to install for future reference.

Edit:

I can't find anything on snes when I use the package manager. Could it be because I am using PSUbuntu ?

---

### Post by RATM_Owns on 2008-07-01
Nope.

Just do 
```
./snes9x
```Or the easy way:
```
sudo apt-get install gsnes9x
```
Or
```
sudo apt-get install zsnes
```

---

### Post by XMBuntu on 2008-07-01
Thanks for the help with the code. 

And to the other guys who say it's available on the Add/Remove:

It shows up but this happens:

The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. 

I reload the list, but it still doesn't work. I obviously have a working connection. This happens when I try snes9x and gsnes9x. What could be the problem?

---

### Post by XMBuntu on 2008-07-01
root@PS3:/home/mike# sudo apt-get install gsnes9x
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gsnes9x
root@PS3:/home/mike# 


I don't know what's wrong, I'm logged in as root. This is a pain!

---

### Post by jumponskis on 2008-07-01
son you have no idea what a pain is.  yet. :twisted:

for the majority of linux os users, it is a way to get back at corporate a**faces such as, oh, I don't know, microsoft(-in-the-head)?... but for a great many others it is just a hobby, just like computergames are your hobby(but I wouldn't know about that using ubuntu and having an undeveloped program such as wine) ((and it has so much potential too!))  but this is becoming a rant so I should stop before someone gets angry.(soorry)(Im just sore becuase I have lost 160GB of data today that only costly programs (ew) could every recover)

---

### Post by oldos2er on 2008-07-02
Why are you logged in as root?

 Go to System, Administration, Software Sources, and make sure all repositories are enabled.

---

### Post by pastalavista on 2008-07-02
This might help:
[http://amitech.50webs.com/installing/index.php.html#source](http://amitech.50webs.com/installing/index.php.html#source)

---

### Post by ramjet_1953 on 2008-07-02
I'm afraid this is a case of trying to walk, before you can crawl.

1. You should not be installing stuff as root.

2. If you did enable the root account, it is not a good idea to do so for a new user, as you can easily break your system and also create security risks.

3. Navigate to [COLOR="Blue"]Applications>Add/Remove[/COLOR] and in the top right hand corner, click on the menu and select [COLOR="Blue"]All Available applications[/COLOR].

4.Type gsnes9x into the search bar and it will locate it.

5. Select it and click on [COLOR="Blue"]Apply Changes[/COLOR].

6. Synaptic will now sort out dependencies and install you application.

Until you become more familiar with 'Nix, stay away from sourcecode and compiling. You need to do a lot of reading and work your way through some tutorials, before attempting it.

Regards,
Roger :cool:

---

