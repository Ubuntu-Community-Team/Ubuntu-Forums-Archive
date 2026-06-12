---
title: "how to use IE in ubuntu"
date: 2005-04-14
forum: General Help
---

### Post by Toastermax on 2005-04-14
I have come upon a situation that require the use of this vile application, Internet explorer. I wished i didnt have to but i do, no getting around it. The only problem is that funds are limited and i cant use the application that you have to pay for, i forget the name. I found an a script that is supposed to work but it does not and i have to get this working , its imperative. Does anyone have a clue as to how to do this and the exact newbie proof steps to accomplish this task?

---

### Post by crane on 2005-04-14
[QUOTE=Toastermax]I have come upon a situation that require the use of this vile application, Internet explorer. I wished i didnt have to but i do, no getting around it. The only problem is that funds are limited and i cant use the application that you have to pay for, i forget the name. I found an a script that is supposed to work but it does not and i have to get this working , its imperative. Does anyone have a clue as to how to do this and the exact newbie proof steps to accomplish this task?[/QUOTE]


You could try using wine I guess, just use spt or synaptic to install it then I guess you would have to find an installable version of explorere and run $sudo wine /file/location/explorer.exe

Although the thought of run IE just horrifies me LOL

---

### Post by Toastermax on 2005-04-14
i know i have to use wine but how?? what are the exact steps for getting the correct version of wine and how do i get it to work?

---

### Post by banadushi on 2005-04-14
Use apt-get or synaptic or whatever to install wine:

```
# apt-get install wine
```

Then follow the guide at Frank's Corner:

[http://frankscorner.org/index.php?p=ie6](http://frankscorner.org/index.php?p=ie6)

---

### Post by T31 on 2005-04-14
Just do this "sudo apt-get install wine" :razz:

aaaaaaaaahhh how hard is to install apps in gnu/linux    \\:D/ 

hope will help u

---

### Post by burlap on 2005-04-14
I'd recommend:
```

sudo apt-get install wine wine-utils winetools
winetools

```

With winetools you don't have to mess with dlls yourself - it will automagically install all the required files and IE (English or German, but there are probably ways to change it). And if you need anything else (e.g. wordviewer) it is also very helpful.

---

### Post by Toastermax on 2005-04-14
root@linux:/home/******* # sudo apt-get install winetools
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package winetools




now what??

---

### Post by nocturn on 2005-04-14
[QUOTE=Toastermax]root@linux:/home/******* # sudo apt-get install winetools
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package winetools




now what??[/QUOTE]

Have you enabled universe/multiverse in /etc/apt/sources ?

---

### Post by shakin on 2005-04-14
[QUOTE=nocturn]Have you enabled universe/multiverse in /etc/apt/sources ?[/QUOTE]

winetools isn't in any of the standard repositories.

---

### Post by gil-galad on 2005-04-14
winetools is in the wine repository which has the latest version of wine along with winetools.  Winetools has a gui for configuring wine AND it can install internet explorer for you.  

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

---

### Post by shakin on 2005-04-14
[QUOTE=gil-galad]winetools is in the wine repository which has the latest version of wine along with winetools.  Winetools has a gui for configuring wine AND it can install internet explorer for you.  

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/[/QUOTE]

Thanks. I also found it in the Marillat repository. Winetools is quite good, although it is not able to install the Arial fonts because the Sourceforge mirror appears to be down. IE and Media Player still install and work without problems.

---

### Post by Toastermax on 2005-04-14
Okay , it installed , at least i think it did. after doing this sudo apt-get install wintools, it appeared to install but no gui to configure and it not on my list of apps. Is it installed?

---

### Post by shakin on 2005-04-14
[QUOTE=Toastermax]Okay , it installed , at least i think it did. after doing this sudo apt-get install wintools, it appeared to install but no gui to configure and it not on my list of apps. Is it installed?[/QUOTE]

run 'winetools' from the command line. I don't think I had to run as sudo. You only need to run winetools once because it just creates your wine config file and installs IE and Media Player. I used the menu editor to add IE and MP to the menu afterwards. I've attached the two icons I made (er... modified from a google image search) that work nice in the menu.

---

### Post by dataw0lf on 2005-04-14
Good thread, I've been putting off getting IE on my machine, but I guess I'll give it a crack now.

---

### Post by burlap on 2005-04-14
I haven't noticed winetools came from backports (a lot of useful software - it's already almost replaced all custom debian repositories I used to use) not from universe/multiverse... I have this bad habit to treat backports as an official Ubuntu repository...  ;-) 

> I don't think I had to run as sudo**DO NOT** run winetools as sudo. Winetools creates folders in your home directory and if you run sudo, you won't be able to do anything to them (unless you sudo again)... 

And stick to the sequence - first base setup/ later Windows system software.

One of the folders created by winetools will be "bin" (in your home dir), where all the scripts to launch windows programs are located. 

There is also one important thing to note: IE is not free software - it is free as in beer. According to its license you have to own a license for MS operating system to be able to use IE. Winetools kindly warns you, but I have to confess that I did not know that before. (And I have a MS-tax-free computer....).

---

### Post by Toastermax on 2005-04-14
i thought typing sudo apt-get install winetools  would install this??

what do i type at the terminal to install this ? and how do i run the base install and where is it located so that i can run it?

---

### Post by burlap on 2005-04-14
Well, first you have to install winetools:

You may use ```
sudo apt-get install winetools
```if you have proper repositories (like one posted by gil-galad in this thread or backports - here is the [backports home page](http://backports.ubuntuforums.org/) and here is [the Ubuntu starter guide](http://ubuntuguide.org/) with all the explanations on adding repositories - including backports). 

When you have winetools, run it from terminal as a normal user (NOT sudo) by typing```
winetools
``` You may use "Launch" option from the applications menu. Read the intro and follow instructions in winetools. 

(To install and manage packages you can use Synaptic which is a great tool: it is in System -> Administration -> Synaptic Package Manager; in Synaptic go to Settings -> Repositories and add repostiories).

---

