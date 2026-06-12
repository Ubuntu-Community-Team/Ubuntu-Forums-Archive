---
title: "Xubuntu 15.04, and Skype"
date: 2015-11-09
forum: General Help
---

### Post by DreadWolf on 2015-11-09
Ok, so I have installed Xubuntu 15.04 64-bit edition on my system, and I am trying to get Skype to work. I have been looking at different solutions to this problem form this forum, and as you can see it's installed, but below shows how it looks once I try to run it.

[IMG]http://i1380.photobucket.com/albums/ah181/FenrisUltra/Screenshot_2015-11-09_19-22-04_zps45qwdfrp.png[/IMG]

I can't select any of the names on the list, and I cannot properly chat in the selected user windows, does anyone know how to fix this?

Thnaks

---

### Post by branau on 2015-11-09
How did you install Skype? I'm running Xubuntu 15.10 and I use Skype quite regularly, without any issues.

---

### Post by Bucky Ball on 2015-11-09
> **branau said:**
> How did you install Skype?

^^^
This. It's in the repositories. Should be installed from the repositories.

Please use 'Go Advanced' or Adv Reply and attach large screenshots rather than inserting them in the body of your posts or provide a link. Have mercy on potential helpers with slow connections or vision issues. Thanks.

---

### Post by DreadWolf on 2015-11-09
> **branau said:**
> How did you install Skype? I'm running Xubuntu 15.10 and I use Skype quite regularly, without any issues.

I tried to install it with command line, then I tried to search for it in the software center, and then I tried to download it directly from the site. It doesn't matter what I do, I can't make it work the way it's suppose to or it wouldn't look like it does in the photo

---

### Post by branau on 2015-11-09
Try this. Run these commands, and then run skype from the command line:

```
sudo apt-get purge skype
```

Also, since you've downloaded it from the website itself, you'll need to manually uninstall it.

```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```

```
sudo apt-get update && sudo apt-get install skype
```

Finally:

```
skype
```

Do you get any errors?

---

### Post by Bucky Ball on 2015-11-09
You might need to go to Software and Updates> Other Software and make sure you have the Canonical Partners repo enabled (ticked) before you see Skype in the repos. Install it from there once you've followed branau's instructions for getting rid of what you already have, and forget, for now, installing it from an external source.

---

### Post by DreadWolf on 2015-11-09
> **branau said:**
> Try this. Run these commands, and then run skype from the command line:

```
sudo apt-get purge skype
```

Also, since you've downloaded it from the website itself, you'll need to manually uninstall it.

```
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
```

```
sudo apt-get update && sudo apt-get install skype
```

Finally:

```
skype
```

Do you get any errors?

It installed correctly without any errors just as you stated....

> **Bucky Ball said:**
> You might need to go to Software and Updates> Other Software and make sure you have the Canonical Partners repo enabled (ticked) before you see Skype in the repos. Install it from there once you've followed branau's instructions for getting rid of what you already have, and forget, for now, installing it from an external source.

I have just configured the software and update settings just as you said...

Guess what...neither of these things have fixed the problem, infact, it has made the problem worse. The contact list is now completely locked up :sad:

---

### Post by branau on 2015-11-09
If you start skype from the terminal, does it give you any errors?

---

### Post by DreadWolf on 2015-11-09
```

fenris@ubuntu:~/Downloads$ skype


(skype:9642): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(skype:9642): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(skype:9642): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


(skype:9642): Gdk-WARNING **: shmget failed: error 28 (No space left on device)

```

Oh I'm sorry, I forgot to mention that part

---

### Post by branau on 2015-11-09
That's what we were looking for :D

As noted [here](http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line), give this command a shot:

```
sudo apt-get install gtk2-engines-pixbuf
```

That ought to take care of the first three error messages.

Which machine are you running this on?

---

### Post by DreadWolf on 2015-11-09
```

fenris@ubuntu:~/Downloads$ sudo apt-get install gtk2-engines-pixbuf
[sudo] password for fenris: 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
gtk2-engines-pixbuf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

```

It's running in a 64 bit platform within VMware Workstation 11.1.2

---

### Post by branau on 2015-11-10
Ok, try this one:

```
sudo apt-get install gtk2-engines-pixbuf:i386
```

Found that one in the comments [here](http://askubuntu.com/questions/106959/issues-with-quickly-tk-warning-unable-to-locate-theme-engine-in-module-path#comment496342_107089)

---

### Post by DreadWolf on 2015-11-10
```

fenris@ubuntu:~$ **sudo apt-get install gtk2-engines-pixbuf:i386**

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

It got stuck trying to download the files from the ubuntu archive for the past 10 minutes

---

### Post by branau on 2015-11-10
You'll have to wait until any other apt-get commands finish before you can run that one. Try it again once all the other processes have ended

---

### Post by DreadWolf on 2015-11-10
> **branau said:**
> You'll have to wait until any other apt-get commands finish before you can run that one. Try it again once all the other processes have ended

I was unable to get any of the apt-get commands to properly shutdown, so I had to do a sudo shutdown now command and kill everything, but when xubuntu reloaded, skype just magically started to work like it was suppose to. I don't know why it works

---

### Post by Bucky Ball on 2015-11-10
If it's still working tomorrow perhaps mark thread solved. :)

(That won't close the thread to further discussion but will assist others.)

---

### Post by branau on 2015-11-10
> **DreadWolf said:**
>  skype just magically started to work like it was suppose to. I don't know why it works  Well I'm glad it's finally working for you! As BuckyBall says, if you don't have any more problems with this particular issue, please mark it solved.  And enjoy Xubuntu!

---

### Post by DreadWolf on 2015-11-10
> **branau said:**
> Well I'm glad it's finally working for you! As BuckyBall says, if you don't have any more problems with this particular issue, please mark it solved.  And enjoy Xubuntu!

Well it looks like I jumped the gun a bit, it doesn't look like it works completely. The contact list is visible, but some of the chat windows still look the same in the picture.

---

### Post by branau on 2015-11-10
Did you run this command?  ```
sudo apt-get install gtk2-engines-pixbuf:i386
```  And then run skype from the terminal again so we can get those error messages

---

### Post by DreadWolf on 2015-11-10
> **branau said:**
> Did you run this command?  ```
sudo apt-get install gtk2-engines-pixbuf:i386
```  And then run skype from the terminal again so we can get those error messages

Yes I had ran it, and I did it again, this is how it looks...

```

fenris@ubuntu:~$ **sudo apt-get install gtk2-engines-pixbuf:i386**
[sudo] password for fenris: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gtk2-engines-pixbuf:i386
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 19.4 kB of archives.
After this operation, 605 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ wily/main gtk2-engines-pixbuf i386 2.24.28-1ubuntu1 [19.4 kB]
Fetched 19.4 kB in 0s (34.8 kB/s)             
Selecting previously unselected package gtk2-engines-pixbuf:i386.
(Reading database ... 192349 files and directories currently installed.)
Preparing to unpack .../gtk2-engines-pixbuf_2.24.28-1ubuntu1_i386.deb ...
Unpacking gtk2-engines-pixbuf:i386 (2.24.28-1ubuntu1) ...
Setting up gtk2-engines-pixbuf:i386 (2.24.28-1ubuntu1) ...
fenris@ubuntu:~$ 

```

---

### Post by branau on 2015-11-10
Sorry, I meant post the output of running skype in the terminal so we can see what's going on there.

---

### Post by DreadWolf on 2015-11-10
> **branau said:**
> Sorry, I meant post the output of running skype in the terminal so we can see what's going on there.

Weird, now it seems to look like its running the way its suppose to without the chat windows all grayed out. I will see how it goes tomorrow to see if I can catch it graying out

---

### Post by branau on 2015-11-10
Haha sounds good. If I were you, I'd start it with the terminal for the next few days so that you can catch any error messages that may come up.

---

