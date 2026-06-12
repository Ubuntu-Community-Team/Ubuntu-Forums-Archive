---
title: "gdesklets not starting up with parameters (feisty)"
date: 2007-05-01
forum: General Help
---

### Post by schnupi on 2007-05-01
Hey everyone

I am more or less new to ubuntu or linux in general but loving it so far. I gotta thank everyone here first cause this forum helped me so much.. 

now i have to issues at the moment and i think they both originate from the fact that in my uni i have to use a proxy.  one is gaim(which hopefully will be alright after the next release) and this..

i am running gdesklets but wanted to run a water forecast. now for this i would need a working internet connection which i have but only through a proxy. gdesklets does not seem to like to use the ubuntu general proxy settings so i had to come up with something else...

i tried to run gdesklets  like this 

```
proxy_http="proxy:port" gdesklets
```

and it works perfectly.. the only issue i have is that when i put the same command in the startup list (system -> preferences ->sessions) it does not start up after a boot

i have it set currently like this 
```

Name: gdesklets
Command: proxy_http="proxy:port" gdesklets

```

i always have to start it manually.. any one know why this is not working?

---

### Post by Haywood on 2007-05-02
Try going to System / Preferences / Sessions, select "New" and adding your line there.  Hope this helps.

R/ Bill

---

### Post by schnupi on 2007-05-02
well yea see thats what i have.. under system -> preferences -> sessions and start up i added that but it doesnt start up. but when i type the  exact same code into the terminal gdesklets starts with proxy support.. :( :confused: :confused:

---

### Post by NikoC on 2007-05-02
Are you using beryl or compiz? I've experienced that sometimes when using these window decorators gdesklets actually starts up but doesn't show due to the 3D window manager. 
Perhaps you can try [this]("http://ubuntuforums.org/showthread.php?t=369961") thread as a solution and more specifically post #3 and #4...

Good luck!

---

### Post by schnupi on 2007-05-02
> **NikoC said:**
> Are you using beryl or compiz? I've experienced that sometimes when using these window decorators gdesklets actually starts up but doesn't show due to the 3D window manager. 
Perhaps you can try [this]("http://ubuntuforums.org/showthread.php?t=369961") thread as a solution and more specifically post #3 and #4...

Good luck!

i didnt install any of them.. i think compiz is installed by default. i am just using the provided effects in feisty.. (system->preferences->desktop effects) ... i am going to try the suggestions(if i understand them :P) u provided and come back with hopefully positive feedback :)

---

### Post by ayoli on 2007-05-02
if you use cesktop effects you may want to try screenlets instead of gdesklets
here's the [install guide]("http://hendrik.kaju.pri.ee/screenlets/?q=node/5")
once installed try screenlets-tray from accessories menu, if you wsant it at each startup go to Admionistration>System>Preferences>Session then pick startup apps tab and add screenlts-tray.

---

### Post by schnupi on 2007-05-02
nothing worked so far.. :/ and screenlets is nice but i cant seem to be able to work it with a proxy and it just doesnt come wit the same desklets as gdesklets. i really like the calendar with the picture on top :cool: .. and the good weather desklet is also my favourite but it only works when i start the whole thing with http_proxy etc... 

well nothing i can do. i will probably stop using gdesklets then.. i hope that stupid reading error in msn with pidgin gets fixed soon.. very annoying but thats fairly off topic anyways

---

