---
title: "GDM problem"
date: 2008-05-18
forum: General Help
---

### Post by Hamstermerc on 2008-05-18
When i type "gdm" into terminal (aiming to change login display) i get this code:

ben@ben-laptop:~$ gdm
gdm[7747]: WARNING: GDM file gdm-daemon-config.c: line 2033 (): Cannot run seteuid to 0: Operation not permitted
GDM file gdm-daemon-config.c: line 2033 (): Cannot run seteuid to 0: Operation not permitted


When i type gdm into terminal i get this popup:

"GDM (GNOME Display Manager) is not running.
You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm.  If you wish to use this feature, then your system will need to be configured to use GDM instead."

I have absolutely no idea whats going on as i'm a very new Ubuntu user. Furthermore i tried the kubuntu-desktop package, decided against it and am now i the process of trying to get rid of all the little bits and pieces it left behind. Don't know if that affects anything.

Any help would be much appreciated.

p.s. how to you put the code in a little section in these forums? Looks a bit neater :)

---

### Post by FuturePilot on 2008-05-18
To change the login display try System&#8594;Administration&#8594;Login Window. Go to the Local tab.

To get completely rid of the Kubuntu-desktop check this out
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by Hamstermerc on 2008-05-18
> **FuturePilot said:**
> To change the login display try System&#8594;Administration&#8594;Login Window. Go to the Local tab.

To get completely rid of the Kubuntu-desktop check this out
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")
Thanks very much for the uninstall Kubuntu-desktop link worked perfectly. However on my other big problem, when i click do System&#8594;Administration&#8594;Login Window i get the same message as gdmsetup in terminal. :( Any other ideas?

If this helps at the end of my uninstall i got this 

Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by alex_anthony on 2008-05-18
code tags are [ code ] before and [ /code ] after 
(without spaces - they were do it didnt make that into code ```
 like this
``` )

---

