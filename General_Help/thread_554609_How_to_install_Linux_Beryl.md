---
title: "How to install Linux Beryl?"
date: 2007-09-19
forum: General Help
---

### Post by noobie_atlinux on 2007-09-19
--------------------------------------------------------------------------------

Ok I just downloaded Linux Beryl application from my WinXP OS, I have it saved onto cd. Now the Question is, with the Files inside the Linux Beryl folder, when I opened it, how do I install the application onto my Linux Ubuntu

---

### Post by noobie_atlinux on 2007-09-19
Ok doesnt anyone know the easiest way to install Linux Ununtu? Like can anyone give me a step by step instructions on how to do it....

---

### Post by catanzag on 2007-09-19
The easiest way to install beryl in ubuntu is to type ```
sudo apt-get install beryl
``` so all eventual dependencies are downloaded and satisfied. But if you already have got the all the files, and you don't want to use *apt-get* you can cd to the directory and then ```
sudo dpkg -i *deb
``` If it doesn' work, for dependencies, you can install them one by one with repeated ```
sudo dpkg -i *packagename*
```

---

### Post by Zaneyard on 2007-09-19
> **noobie_atlinux said:**
> --------------------------------------------------------------------------------

Ok I just downloaded Linux Beryl application from my WinXP OS, I have it saved onto cd. Now the Question is, with the Files inside the Linux Beryl folder, when I opened it, how do I install the application onto my Linux Ubuntu

well which one is it
i'm gonna go ahead and assume that your trying to install the OS
if so go to the installation thread that they created specifically for installation
if you can't find that than odds are, you shouldn't install Linux
as far as beryl goes... don't even try that, it requires a lot of work and its a dead project
if you really need help finding the thread ill help you when you look

sorry for the harshness, but i am also a noob at linux and ubuntu, but that is what the sticky threads are for.

---

### Post by Zaneyard on 2007-09-19
hehe i feel bad for being mean now.
if your running a live CD its pretty easy, thats the way i did it

go here
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by noobie_atlinux on 2007-09-19
> **catanzag said:**
> The easiest way to install beryl in ubuntu is to type ```
sudo apt-get install beryl
``` so all eventual dependencies are downloaded and satisfied. But if you already have got the all the files, and you don't want to use *apt-get* you can cd to the directory and then ```
dpkg -i *deb
```. If it doesn' work, for dependencies, you can install them one by one with repeated ```
dpkg -i *packagename*
```.

Thanks for the advice, although Im just curious, I already have the folder that contains the Linux Beryl files which I download them, now do i run those commands in the applications>acceriories>terminal? Cause since Im new to Linux, new a lil more simpliified instructions in to run those commands. :( Thanks for the assistance by the way:)

---

### Post by catanzag on 2007-09-19
Yes, all commands should be run in a terminal, just 
```
cd /media/<WindowsDrive>/<path-to-beryl-deb>/
sudo dpkg -i *deb
```
substituting the windows path where your files are.

btw, you should use *sudo* before *dpkg*, I forgot it before.

---

### Post by noobie_atlinux on 2007-09-19
Thanks alot for your assistance, Ill let you know if I have any future difficulties :)

---

### Post by klap-in on 2007-09-19
Why do you install Beryl not directly from internet, instead of downloading the files of Beryl?
Do you have not a internet connection on your ubuntu pc?

When you have a internet connection in your Ubuntu, then the next option is easier!
> **catanzag said:**
> .....
 ```
sudo apt-get install beryl
``` .....

> **Zaneyard said:**
> 
......
go here
[http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

This link also explain how works installing applications in ubuntu .

---

### Post by noobie_atlinux on 2007-09-19
I would have the internet working on my Ubuntu, but I have no clue how to locate the wireless settings for ubuntu so I can set up my wireless internet. As well im talking on my WinXP comp, my other comp is the one with the Linux Ubuntu that im trying to install Beryl with

---

### Post by noobie_atlinux on 2007-09-19
> **catanzag said:**
> The easiest way to install beryl in ubuntu is to type ```
sudo apt-get install beryl
``` so all eventual dependencies are downloaded and satisfied. But if you already have got the all the files, and you don't want to use *apt-get* you can cd to the directory and then ```
sudo dpkg -i *deb
``` If it doesn' work, for dependencies, you can install them one by one with repeated ```
sudo dpkg -i *packagename*
```

Ok I have a new dilemna, When I tried running those commands you wanted me to run in the termal, the first one indicated that "Couldn't find package Beryl." When I ran the second command, it indicated error processing *deb then when i ran the 3rd last command it indicated, "error while processing packagename."
Now I have the Linux Beryl folder with the files that came with the download when i downloaded it off my WinXP comp (Which had the Internet connection: I cant figure out how to work the wireless on Ubuntu) and transferred it over to Beryl. So essentially the Beryl files Which is located in the Linux Beryl folder has all the Beryl files needed, but still having issues with running those commands you gave me. :confused:

---

### Post by catanzag on 2007-09-20
To run the first command, you should be connected to internet .
To run the other two, you have first to cd into the directory where Beryl packages are, and then run them; btw, <packagename> is a placeholder, you have to write the real name of each package you want to install. 

In debian-based linux (like Ubuntu), automatic procedures via synaptic, aptitude or apt-get are advised; the direct use of dpkg can work or not, it depends on the dependencies (sorry for the joke of words). What I can suggest is to set an internet connection in linux and then apply one of the automatic installation procedure.

In general, as you are new to ubuntu, I suggest you to check [https://help.ubuntu.com](https://help.ubuntu.com) website, full of information from novice to expert. For instance, about wireless connection, you can check all the docs in [https://help.ubuntu.com/community/WifiDocs/](https://help.ubuntu.com/community/WifiDocs/) ; if it still doesn't work, you could open a new thread in the networking & wireless section of the forum.

---

### Post by noobie_atlinux on 2007-09-20
aaa ok Ill give that a try. Sorry that Im a noobie at Linux :( But this is why I like these forums, I deffinitely like to get helpful advise from knowledgeable people like yourself. Ya I think Ill try and see if I can somehow get my wireless setup with in Ubuntu, then Ill try do it through your first method. If not, ya ill try the 2nd and 3rd method that you recommeded. Thanks again for your assistance :)

---

### Post by MenZa on 2007-09-20
You would definitely make it easier for yourself, if you attempted to setup your wireless. Try looking at the link in my signature.

---

### Post by catanzag on 2007-09-20
> **noobie_atlinux said:**
> ... Sorry that Im a noobie at Linux ...

Nothing to be sorry!!! Everybody when starts from scratch something knows nothing, then he becomes more and more expert, that's the forums are for!!!! Good luck and enjoy Ubuntu!!!

catanzag

---

