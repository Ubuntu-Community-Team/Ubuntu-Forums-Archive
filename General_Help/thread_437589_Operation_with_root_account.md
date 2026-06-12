---
title: "Operation with root account"
date: 2007-05-08
forum: General Help
---

### Post by Dipper on 2007-05-08
I know everyone says it is not recommended, but I want to operate my system permanently in the root account.  It's a real pain having to use the sudo commands whenever installing or making changes.  I am the only one who ever touches my machine so I am not worried about security.  I remember seeing some instructions on how to do that but I can't seem to find them.

---

### Post by thelocust on 2007-05-09
[This]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_allow_root_user_to_login_into_GNOME") is for Gnome Tell me if your using KDE.

---

### Post by Dipper on 2007-05-09
Yes I am using KDE.

---

### Post by tkjacobsen on 2007-05-09
You can find some information on the ubuntu Wiki [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Here you can see how to enable the root account in the first place.

(I hope your machine is not on the internet, 'cause then you are doomed)

---

### Post by mcduck on 2007-05-09
> **Dipper said:**
> I know everyone says it is not recommended, but I want to operate my system permanently in the root account.  It's a real pain having to use the sudo commands whenever installing or making changes.  I am the only one who ever touches my machine so I am not worried about security.  I remember seeing some instructions on how to do that but I can't seem to find them.

If you have Internet connection, then you are never the only one trying to access the computer ;)

---

### Post by Dipper on 2007-05-09
I realize that whenever you are connected to the internet you are susceptible to your system being invaded.  However, I feel that the risk is low enough to justify loosening security measures.  I have always used Windows in superuser mode and never had any problems out of the ordinary.  Linux has fewer viruses simply because fewer people use it.

---

### Post by aysiu on 2007-05-09
> **Dipper said:**
> Linux has fewer viruses simply because fewer people use it. Actually, that's only one of many factors.

Read more here:
[why linux doesnt need an antivirus?](http://ubuntuforums.org/showthread.php?t=435734&highlight=anti-virus+why)

---

### Post by Dipper on 2007-05-10
Right now I have to edit a file to get my adept manager back up and running.  As it is I cannot edit the file because I do not have proper permissions.  I really resent getting a message saying I do not have permission to do something on my own machine.  

I tried following the instructions provided (Thanks, tkjacobsen).  Unfortunately, that only allows temporary root access within the console.  I am trying to fix my machine so that any time I am logged on, I have complete unfettered superuser access at all times, just as I would on Windows.  I recall there was a very simple edit that needs to be made to a file, I just can't find that file and can't remember the edits that need to be made.  Any help would be graciously appreciated.

---

### Post by zvacet on 2007-05-10
[http://ubuntuforums.org/showthread.php?t=435906&highlight=visudo]("http://ubuntuforums.org/showthread.php?t=435906&highlight=visudo")

---

### Post by z0phi3l on 2007-05-10
> **Dipper said:**
> Right now I have to edit a file to get my adept manager back up and running.  As it is I cannot edit the file because I do not have proper permissions.  I really resent getting a message saying I do not have permission to do something on my own machine.  

I tried following the instructions provided (Thanks, tkjacobsen).  Unfortunately, that only allows temporary root access within the console.  I am trying to fix my machine so that any time I am logged on, I have complete unfettered superuser access at all times, just as I would on Windows.  I recall there was a very simple edit that needs to be made to a file, I just can't find that file and can't remember the edits that need to be made.  Any help would be graciously appreciated.

Superuser and ROOT are two very different creatures, ROOT is more like being logged in as Administrator, THE admin account. Like you said highly unrecommended but if you absolutely have to, follow the previously linked posts.

---

