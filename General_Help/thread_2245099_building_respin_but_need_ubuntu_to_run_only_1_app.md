---
title: "building respin but need ubuntu to run only 1 app"
date: 2014-09-21
forum: General Help
---

### Post by Leonardvb on 2014-09-21
am i trying somthing that isnt possible , 

im trying to let ubuntu start up a single program after installation. this is no problem , by adding it to the startup. 

but here is what i cant get done , all menu off the desktop enviroment should be disabled , so that the user can not start anything els or do enything else then use the program that started up at boot.

is this possible and if yes , how and what Desktop.Enviroment. to use best . if i get this to work i want to do a respin.

Think of some embedded systems that run 1 application like for example sound modules that run on linux or a tv box with menu. that is wath i want to do on a desktop pc .... yust start that application full screen and no other options

i dont know dinds im new to the forum where i should ask this question so i placed it in general help but it could be it is in the wrong forum threat.


i allready tryed this but i cant get it done : [http://askubuntu.com/questions/10481/how-do-i-enable-or-disable-the-global-application-menu](http://askubuntu.com/questions/10481/how-do-i-enable-or-disable-the-global-application-menu)

(Sorry for my bad english and typo's)
please need help here , kind regards leonard


(edit : better explenation:  
 what i am trying to do is build a application/install distro for non  linux users .. This application runs fluidsynth and linux sampler .  (audio apps) , it also runs netJack to transport audio on network. Im  running this system for my own use but setting everything up is a lot of  work and for most non linux users difficult. wath it needs to do is  running jack as deamon (wordking) running Fluidsynth as deamon (working)  running Linux sampler as Apllication that should be displayed full  screen without any menus of the windows manager. It is ment for users in  there home studio to introduce them to open source and promoot the  linux world of audio production. Linux sampler is a great addon for  every studio that works with midi and Sountfonts. and sinds i have my  system up and running as a sound module with extreame great sound there  are a lot of colleges that askt me to build one for them .. i am a  beliver in non commercial and open source so i think it would be easyer  to create a distro to do this task an let them install themselves on any  old pc and use it but without te menu and apps that come with windows  managers. so if they can acces terminal or ssh that is no problem ,)

---

### Post by buzzingrobot on 2014-09-21
Sounds like you are looking to set up a "kiosk" implementation, i.e., something you might see in a shopping mall or elsewhere that runs just one program and blocks user access to everything else. (Remember that there is more involved than just eliminating menus because a knowledgable user could still open a terminal or flip over to a console and acquire control of the machine.)

I recall seeing discussions of setting up kiosk implementations; I imagine Google might turn something up.  Goog luck.

---

### Post by Leonardvb on 2014-09-21
tanx for replying , what i am trying to do is build a application/install distro for non linux users .. This application runs fluidsynth and linux sampler . (audio apps) , it also runs netJack to transport audio on network. Im running this system for my own use but setting everything up is a lot of work and for most non linux users difficult. wath it needs to do is running jack as deamon (wordking) running Fluidsynth as deamon (working) running Linux sampler as Apllication that should be displayed full screen without any menus of the windows manager. It is ment for users in there home studio to introduce them to open source and promoot the linux world of audio production. Linux sampler is a great addon for every studio that works with midi and Sountfonts. and sinds i have my system up and running as a sound module with extreame great sound there are a lot of colleges that askt me to build one for them .. i am a beliver in non commercial and open source so i think it would be easyer to create a distro to do this task an let them install themselves on any old pc and use it but without te menu and apps that come with windows managers. so if they can acces terminal or ssh that is no problem ,

---

### Post by Leonardvb on 2014-09-21
here is my new approach .. i am trying to go with fluxbox and build a custom menu... replaced the kernel with a low latency kernel and now trying to build custom menu ! then my goal could be reached. so updating later on this try

---

