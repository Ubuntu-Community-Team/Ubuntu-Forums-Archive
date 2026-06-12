---
title: "Where did my progams go??"
date: 2007-03-31
forum: General Help
---

### Post by mshale on 2007-03-31
Ok, So i just installed 3 programs, and none of them showed up in my applications menu.  I then tried to install Debain to get a more thorough list of apps, but that install didn't show up either!!  What do I do???  :confused:

---

### Post by geovino on 2007-03-31
What did you install?  Did you use Synaptic or apt-get at the terminal?

Sometimes they are installed and can be opened by typing their name in the terminal (command line). Once you see that is wasn installed you can go to: 

System > Preferences > Menu Layout, and there you can see how and where to place a listing of the program.

---

### Post by Shmifty on 2007-03-31
Go to the menu and click edit, save the configuration and hopefully the new programs (if they even shortcuts that you don't make yourself) should be there. Some programs just won't show up on the menu unless you edit the menu and add those items yourself though.

---

### Post by raul_ on 2007-03-31
one application that helps you to keep track of all your applications is Debian Menu. I think it's in the repositories, so just "apt-get" it . It adds an entry to your applications menu that shows all your applications (organized by type). 

Give it a try.

Another solution is trying to run the program by using the package name. For example if you downloaded a package called "gaim", try running "gaim" in the terminal. You can also use the auto-completion feature to give you some lights (like typing "ga" and then pressing tab once to auto-complete, or pressing tab twice, to see all the options)

---

### Post by mshale on 2007-03-31
> **raul_ said:**
> one application that helps you to keep track of all your applications is Debian Menu. I think it's in the repositories, so just "apt-get" it . It adds an entry to your applications menu that shows all your applications (organized by type). 

I tried to install the Debian Menu by installing Menu-dtx or something like that through synaptic, and that didn't show up in the apps menu either.

*update*  Ok, I got the Debain menu up, but is it normal that I have to add all of the apps myself in debian?  

I Need to copy a dvd.  To do this, i believe i need to run dvd shrink and anydvd.  So to do this I need to run WIne, right?  Can someone tell me how this is done?  I already have my windows partition mounted.  Thanks!!

---

### Post by spankymasterc on 2007-03-31
ok in order to get the debian menu u have to do this 

1. Enable the breezy Universe repository
2. sudo apt-get update
3. sudo apt-get install menu menu-xdg
4. update-menus

then the menu will show up and show all apps and everything thats been installed :D if u need more help then tell me......

 if i doesnt show up right click on applications and click menu edit and look for debian and add a check to it.....

Another thing i forgot to mention u could also look at this thread it might help you a bit here :
[http://www.ubuntuforums.org/showthread.php?t=32220]("http://www.ubuntuforums.org/showthread.php?t=32220")

---

