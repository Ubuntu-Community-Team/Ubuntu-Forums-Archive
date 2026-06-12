---
title: "How to remove teamviewer"
date: 2014-01-03
forum: General Help
---

### Post by mcsheffrey on 2014-01-03
I'm running 13.10 with version 6 of teamviewer, my desktop is running 10.4 with version 9 of teamviewer, when I try to connect to the version 9 fron v6, it twlls me the other machine is running a newer ver, woud u like to upgrage, the only option u get is "NO". So I tried redownloading the latest version of tamviewer and re-installing, It ran for over 15 minutest using 100% of the cpu,so I did a re-boot. Now is there a way to remove the old version of teamviewer, so I can start from fresh.   Tks Roy

---

### Post by pqwoerituytrueiwoq on 2014-01-03
search for teamviewer in the software center and click remove or uninstall
you can use synaptic if you prefer

---

### Post by mcsheffrey on 2014-01-03
Doesn't show up in spftware centre or synaptic. Now I suppose I could go into the /opt directory and just delete all the teamviewer directories, but don't know if this will work.

---

### Post by ian-weisser on 2014-01-03
Proper removal often depends upon the method of installation.

How, exactly, did you install the old version of Teamviewer?
Did you get it from a website? From Software Center? Some other way?

---

### Post by mcsheffrey on 2014-01-03
I downloaded it from the teamviewer site and installed it directly.

---

### Post by pqwoerituytrueiwoq on 2014-01-03
you downloaded the .deb file right?

---

### Post by mcsheffrey on 2014-01-04
This was installed a long time ago, so I don't remember, but I know lately whenever I download and install a .deb it invokes the software installer hence it shows up in there so u can remove it, obviously thsi is not the case here. How about my theory about deleteing alll the "teamviewer" directories, think thsi may work? Nothing is working now so I guess its worth a try>

---

### Post by ian-weisser on 2014-01-04
Try the command:
```
dpkg -l | grep teamviewer
```
This will tell you how many packages you have installed that include the name "teamviewer"...and which versions they are.

If your old version does not appear on the list, then either it's not a package or it has a different name.

If the old version is not a package, then I think you should go ahead and delete those old files to your heart's content.
If it is a package, you will have the correct name to uninstall it.

---

