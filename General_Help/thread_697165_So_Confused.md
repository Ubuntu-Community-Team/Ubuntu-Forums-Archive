---
title: "So Confused"
date: 2008-02-14
forum: General Help
---

### Post by Justin_pikey on 2008-02-14
Im new to ubuntu. iv after had no experience with this os at all. I try to install the amsn for linux but i keep getting this error msg 
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.10 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client.

I dunno what to do .. I have no clue.. If anyone could help me on how to use linux or tell me where to go that gives good explaination on everything be great help

Thank You

---

### Post by paydaydaddy on 2008-02-14
Try installing from synaptic package manager. 'System' - administration - synaptic package manager' I just did a search with all repositories enabled and it popped right up. Synaptic will do the work for you.

---

### Post by polmir on 2008-02-14
Type in terminal
```
man man
```
```
man name_of_program
```

---

### Post by farruinn on 2008-02-14
You will save yourself much headache if you use Synaptic to install all your programs.

Always look there first before downloading things off of websites. Many times a program will rely on other programs or libraries to function (as you just found) and Synaptic will install these "supporting" programs automatically for you.

Good luck and welcome to Ubuntu! I'm sure your confusion will eventually turn into bliss :)

---

### Post by phillips321 on 2008-02-14
polmir, do him a favour, he's trying to install amsn, it would have been easier if you had just told him to type
```
sudo apt-get install amsn
```

what the hell is the point in saying type "man man", if your not going to help people then you are no use to these forums.

To the thread starter. Although you can get linux programs as source files it is usually much easier and quicker to install them using prebuilt packages.

By using synaptic packet manager you can add these packages and all dependencies are added as well for you (dependencies are extra "programs" that the program your trying to install also needs, for example, if trying to install program A but it requires programs X, Y and Z to work correctly then these are called dependencies.)

Either use synaptic package manager to add amsn or install it by using the command line code given at the start of my post.

Any problems just PM me.

---

### Post by farruinn on 2008-02-15
> **phillips321 said:**
> what the hell is the point in saying type "man man", if your not going to help people then you are no use to these forums.

My initial reaction was similar. Saying "man man" is no better than saying RTFM which is basically elitism. It is, however, important that people learn how to get help, and the man pages are, once you've breached the initial learning curve, very useful. Suggesting the man pages to someone that titled their thread "So Confused", though, is simply illogical and just looks like a sick joke.

---

### Post by seventhc on 2008-02-15
Welcome to the wonderful world of Ubuntu ;)

for amsn:
1: go to* System>Administration>Synaptic Package Manager*
/ click on search, do a search for[I] blt
[/I]install it.2: download [http://prdownloads.sourceforge.net/amsn/amsn-0.97-1.tcl84.x86.package](http://prdownloads.sourceforge.net/amsn/amsn-0.97-1.tcl84.x86.package)
3: right click on the saved package, left click properties, left click permissions,
on the bottom check it to[I] Allow executing as a Program
4: [/I]go back to downloaded package[I]
5: double click it and let it install

Y[/I]ou can get the old version from synaptic without any added work but this is the newest version, and from what you say, I do believe this is what you're after.
I just installed it this way, if you have a problem don't worry, just let me know and we'll figure it out. :)

ps.* blt* is just something that will fulfill dependencies, other packages will do the same but *blt* worked for me, so it will work for you too. :D
If not then let me know.

---

### Post by Justin_pikey on 2008-02-15
Thanks guys i really appriciate it . I like lynx alot . its clean looking and seems easy its just a little confusing but i had no idea about Synaptic Package Manager. Now that i know everything is getting easier. Plus a friend of mine that knows lynx well is showing me everything else i need to know . Thanks so much

---

