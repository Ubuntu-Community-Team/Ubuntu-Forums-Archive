---
title: "Some general questions"
date: 2008-07-05
forum: General Help
---

### Post by baistaef on 2008-07-05
I have these questions i need an answer for:
1- How can i log in automatically without the system asked me for username and password? It is my machine and there is one user.

2- After i configured my nvidia card i can change screen resolution to more than 1024*768. How can i change that? I need 1280*1024.

3- How can i install .bin software like firefox, blender, Google earth, realplayer and others that are not downloaded from repository.

4- How can i save the softwares and updates downloaded from repository to use on other machine?

5- I need a proxy software like ultrasurf or hotspot shield ( windows programs ) to surf the web anonymously, is there any working under linux?

6- When i download an image or pdf file to my desktop or any folder it shows what the file is ( like thumbnail ), how can i prevent it from showing like that and to see the program icon that opens this file instead?

---

### Post by drs305 on 2008-07-05
> **baistaef said:**
> I have these questions i need an answer for:
1- How can i log in automatically without the system asked me for username and password? It is my machine and there is one user.

System, Administration, Login Window, Security tab.

> 3- How can i install .bin software like firefox, blender, Google earth, realplayer and others that are not downloaded from repository.


Google Earth and firefox are both available in the repositories. Firefox is in the Hardy Updates repository. (Synaptic, Settings, Repositories, Updates.

For Google Earth in hardy, enable the Medibuntu repository:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Once the repository is enabled, install Google Earth (this is a metapackage, no version number required. current version 4.3):
```
sudo apt-get install googleearth
```



How to install ANYTHING in Ubuntu!:  [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
Ubuntu Guide: Hardy: [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

### Post by Powerman2442 on 2008-07-05
1- System --> Administration --> Login Window --> Security --> Check "Enable Automatic Login" Select your name. That should do the trick.

2- System --> Preferences --> Screen Resolution

Other than that I am not sure how to answer your other questions. Good luck.

---

### Post by rossjman1 on 2008-07-07
> 6- When i download an image or pdf file to my desktop or any folder it shows what the file is ( like thumbnail ), how can i prevent it from showing like that and to see the program icon that opens this file instead?
Open Nautilus and go to Edit > Preferences > Preview, and change show tumbnails from Local Files only to Never.

---

### Post by sujoy on 2008-07-07
4. save the files in /var/cache/apt/ or just use aptoncd (in the repos)
5. check out squid.

---

