---
title: "OK.....Software Sources done got up and disappeared."
date: 2012-11-04
forum: General Help
---

### Post by Got2thinkin on 2012-11-04
Most likely a knucklehead question.

Can’t seam to find a way to alleviate this problem. After upgrading from 12.04 to 12.10 certain processes are uninstalled...which is fine........conflicts
I chose the servers to which i do my stuff online. Use Software Sources to do this.

Tried starting Updates and received this notice..........

[SIZE=4][COLOR=Red]Failed to load the package list[/COLOR][/SIZE]
This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.

[SIZE=4][COLOR=Red]Details:[/COLOR][/SIZE]
**E:Type 'wget' is not known on line 53 in source list /etc/apt/sources.list**

Thought it might be a server so tried to start Software Sources.....(Nuttin)!

[SIZE=4][COLOR=Red]Question:[/COLOR][/SIZE]
How can I edit (source list) of that bad line? IDK
Thanks in advance.

---

### Post by idoitprone on 2012-11-04
> **Got2thinkin said:**
> Most likely a knucklehead question.

Can’t seam to find a way to alleviate this problem. After upgrading from 12.04 to 12.10 certain processes are uninstalled...which is fine........conflicts
I chose the servers to which i do my stuff online. Use Software Sources to do this.

Tried starting Updates and received this notice..........

[SIZE=4][COLOR=Red]Failed to load the package list[/COLOR][/SIZE]
This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.

[SIZE=4][COLOR=Red]Details:[/COLOR][/SIZE]
**E:Type 'wget' is not known on line 53 in source list /etc/apt/sources.list**

Thought it might be a server so tried to start Software Sources.....(Nuttin)!

[SIZE=4][COLOR=Red]Question:[/COLOR][/SIZE]
How can I edit (source list) of that bad line? IDK
Thanks in advance.

please post the contents of the sources.list if you wish to get from the forum

```
cat /etc/apt/sources.list
```

to edit it
```
sudo gksudo /etc/apt/sources.list
```

when you are done ```
sudo apt-get update
```

---

### Post by squenson on 2012-11-04
There is a typo in the previous post. To edit the file use:```
gksudo gedit /etc/apt/sources.list
```

---

### Post by idoitprone on 2012-11-04
> **squenson said:**
> There is a typo in the previous post. To edit the file use:```
gksudo gedit /etc/apt/sources.list
```


ooop idoit mistake

---

### Post by Got2thinkin on 2012-11-04
TY
Thought I done buggered up this OS bad.
Brb with results 

Peace/Out

---

### Post by Got2thinkin on 2012-11-04
B4 edit

[SIZE=4][COLOR=Red]cat /etc/apt/sources.list:[/COLOR][/SIZE]


# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal-updates main
restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal universe
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal multiverse
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal-updates
multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal-security main
restricted
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal-security universe
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal-security
multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb [http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/](http://mirror.informatik.uni-mannheim.de/pub/linux/distributions/ubuntu/) quantal-proposed
restricted main multiverse universe
[COLOR=Red][COLOR=Black]deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main

[/COLOR]## Viewizard Games repository deb [/COLOR] [COLOR=Red][http://viewizard.com/linux](http://viewizard.com/linux) debian/
wget [http://www.viewizard.com/linux/viewizard-gpg.asc](http://www.viewizard.com/linux/viewizard-gpg.asc) sudo apt-key add viewizard-gpg.asc
[/COLOR]
^^^^^ Problem line^^^^^^^

Don't recognize that command (wget).....Hmmm :confused:
[SIZE=4][COLOR=Red]
Edit:[/COLOR][/SIZE][SIZE=4] [/SIZE]
Perform non-interactive file downloads from the Web. **wget** works in the background and can be used to set up and run a download without the user having to remain logged on. 

Hmmmm
I guess to keep the integrity of the line it must be replaced with another command.....Which......I have no clue what it should be.
Don't think a dep command would work cuz it's not retrieving a program........IDK
And if I remove the line altogether it might mess up a program installed that might be dependent on that line.

---

### Post by oldos2er on 2012-11-04
Nothing's dependent on the line "wget [http://www.viewizard.com/linux/viewizard-gpg.asc](http://www.viewizard.com/linux/viewizard-gpg.asc) sudo apt-key add viewizard-gpg.asc" 
It's a command to download a gpg key, then install it on your system, so copy and paste it into a terminal, hit Enter.
Edit the line ```
## Viewizard Games repository deb http://viewizard.com/linux debian/
``` so that it looks like ```
## Viewizard Games repository 

deb http://viewizard.com/linux debian/
```
Save and exit the file, run ```
sudo apt-get update
```
Each line in sources.list must begin with either deb or deb-src, unless it's a comment (#).

---

### Post by Got2thinkin on 2012-11-04
> **oldos2er said:**
> Nothing's dependent.......

Seems to have done the trick.    :)
Thank you and all the **others** that have helped with thier suggestions. Was kind of leery of takin out a line within the source list....Newbie Knucklehead  #-o.......So tried your suggestion rather than rip out that whole line ,and now i will do my homework on your code inputs to see how they worked out my problem.
Thank you again.

You Rock!     :guitar:

Peace/Out
G

---

### Post by Got2thinkin on 2012-11-04
> **Got2thinkin said:**
> 
And if I remove the line altogether it might[SIZE=4][COLOR=Red] mess up [/COLOR][/SIZE]a program installed that might be dependent on that line.

Whoops sorry for the potty mouth Mods.
Yes I do work in the construction field....:)
No Excuses!


Peace

---

### Post by oldos2er on 2012-11-04
> **Got2thinkin said:**
> Seems to have done the trick. 

Great! Would you please mark the thread as 'Solved' under Thread Tools at the top?

---

