---
title: "what issues exist using backports?"
date: 2019-06-07
forum: General Help
---

### Post by Skaperen on 2019-06-07
what issues exist, in general, not of specific packages, in using backports?  can i upgrade a specific package to a newer version?  would it be better to just download its deb file(s) rather than adding it to my sources?

---

### Post by kc1di on 2019-06-07
[This Wiki ]("https://help.ubuntu.com/community/UbuntuBackports")should answer many of your questions. Good luck. 

As to downloading the deb file, that may work for some packages but you run the risk of not getting all dependencies satisfied. Which in turn can lead to what we used to call dependency hell.

---

### Post by Skaperen on 2019-06-08
the wiki answers most questions, but brings up a couple that it didn't answer:

1.  how do i get a list of which packages are available in backports?

2.  is there a way to pick a version of the package?

---

### Post by #&amp;thj^% on 2019-06-08
To  list installed packages that have available backport upgrades

```
aptitude search '?and(~i, ~Araring-backports)'
```
Replace raring with your OS version.
To list all available backport packages (installed or not)

```
aptitude search '~Abackports ?not(~S ~i ~Abackports)'
```
And you may have guessed "aptitude "needs to be installed.
EDIT: Forgot to mention I think synaptic will work also. (I'm using less and less GUI's)

---

### Post by deadflowr on 2019-06-08
This one liner will show all backported packages:
```
grep ^Package /var/lib/apt/lists/*-backports*_Packages | awk '{print $2}' | sort -u
```


Or just install synaptic, as already suggested.

---

### Post by Skaperen on 2019-06-08
two more questions:

3.  when installing a backport, is it getting an already compiled binary, or is it download source and building it right here?

4.  can i backport the toolchain version and how will this affect building packages intended for backporting?

i'm thinking that maybe i should set up a container or VM for a new toolchain version.

---

### Post by kc1di on 2019-06-08
Answer to # 3 They are binary packages already built for you.

---

### Post by #&amp;thj^% on 2019-06-08
BTW: Haven't seen you on stackexchange for a while now.
Basically its a binary that your computer compiles with the commands used.
See if this helps sort all this out: [http://www.alandmoore.com/blog/2012/06/02/backporting-with-apt-src/](http://www.alandmoore.com/blog/2012/06/02/backporting-with-apt-src/)
It's an older blog but you'll understand I'm sure.
As far as  the toolchain >>>IJDK, sounds fun though. ;)

---

### Post by Skaperen on 2019-06-08
i'm doing almost everything local via terminal+bash command line.  i already have lots of my own automation around many system tools such as apt and apt-get.  new tools may not work out for me, especially if they are GUI and/or organize system data in a different way.

---

### Post by Skaperen on 2019-06-08
@1fallen health issues forced me into retirement so i have been minimally online for a while.  that and i have been putting more time into automation development around AWS cloud.  i recently occasionally read some of the stackechange sites.

---

### Post by #&amp;thj^% on 2019-06-08
I wish you the best, I can relate to the age related health issues though. :)
Take good care.

---

### Post by Skaperen on 2019-06-08
@1fallen that looked like an interesting link but it drove my CPU up to 330% usage so i had to bail out.  i've had some death crashes when the CPU gets hot and suspect that may be the cause.  i've never seen a single Web Content process go up that high, before.  maybe i can try it w/o java/javascript later on.

---

### Post by Bashing-om on 2019-06-08
Skaperen; Ouch ! confirmed !

> **Skaperen said:**
> @1fallen that looked like an interesting link but it drove my CPU up to 330% usage so i had to bail out.  i've had some death crashes when the CPU gets hot and suspect that may be the cause.  i've never seen a single Web Content process go up that high, before.  maybe i can try it w/o java/javascript later on.

[http://www.alandmoore.com/blog/2012/06/02/backporting-with-apt-src/](http://www.alandmoore.com/blog/2012/06/02/backporting-with-apt-src/) also saturated and crashed my system :(

[INDENT]UNgood[/INDENT]

---

### Post by #&amp;thj^% on 2019-06-08
UNgood is a understatement,:o sounds like backporting is not the answer here.
I'll try and play around with it this weekend.

---

### Post by Bashing-om on 2019-06-08
1fallen; Ole buddy :)

> **1fallen said:**
> UNgood is a understatement,:o sounds like backporting is not the answer here.
I'll try and play around with it this weekend.

The issue is present in just opening the link to the blog, after a period of time. I have not taken the time - as of yet - to investigate the why.

[INDENT][INDENT]strange things - can happen
[/INDENT][/INDENT]

---

### Post by #&amp;thj^% on 2019-06-08
> **Bashing-om said:**
> 1fallen; Ole buddy :)



The issue is present in just opening the link to the blog, after a period of time. I have not taken the time - as of yet - to investigate the why.

[INDENT][INDENT]strange things - can happen
[/INDENT][/INDENT]

Thanks B-om, you now have my interest peaked here. (A challenge has been issued :))

---

### Post by Skaperen on 2019-06-08
the motivation to look at backporting was to use a Python version later than 3.5.2 while staying on 16.04.  that is not the goal, though, which is to use newer versions of a few things while i wait for 2020.04 before i do a re-install, due to so many things i expect to break, even in 18.04.

i kinda abuse lightdm, autologging on 10 to 12 users that i frequently switch around on with os.execvp('dm-tool',['dm-tool','switch-to-user',sys.argv[1]]).

---

### Post by #&amp;thj^% on 2019-06-08
> **Skaperen said:**
> 
i kinda abuse lightdm, autologging on 10 to 12 users that i frequently switch around on with os.execvp('dm-tool',['dm-tool','switch-to-user',sys.argv[1]]).
:lolflag: You Too, welcome to the abuse club.
I'm going to try to fool around with it tomorrow or Monday.

---

### Post by Skaperen on 2019-06-08
i used to spend over an hour manually setting up my GUI environment.  that was back when i used Unity.  it took many months to work out scripts to do all the setup for me.  then i fell in love with Xfce.  fearing failures, and knowing nothing about lightdm's role, i incrementally changed over to Xfce, one user at a time.  it took almost 2 months (of no upgrades, either).  this is one of the reasons i want to avoid major version changes.  i always do a full fresh install (manually pre-formated) to keep things as clean as possible.  even so, i fear that something in my scripts will fail in a new release.  that's why i skipped 18.04 (i only use LTS).  so i will next install 20.04 around June 2020.

but, i'd like to use newer versions of Python before then.  it has been suggested to use Python Environments (pyenv).  but i cannot get a straight technical answer or find documentation on how they work.  will they impact my system?  maybe i want them to ... in a controlled way ... so that, in theory, i can use a newer version of Python for my system setup scripts.  it seems the people in the Python Forum don't know enough technical details to help resolve system related issues with  Python Environments.

so i have been learning about Linux Containers.  i'm still trying to find a way to run the X server (or Wayland) in a container.  i wonder if lightdm can even be run there.  i can't even figure out how virtual terminals (VTs, all 63 of them) work on containers.  for, example, can i set up a container such that VTs 4 and 5 are on that container while the rest remain on the host.

i am used to working at a rather deep level of OSes since i started on IBM mainframes and migrated through SunOS, NeXT, and 386BSD before finally running SLS Linux and Slackware Linux (and helped test porting it to Sparc since i had 2 of those machines at the time).  i knew i was going to eventually get out of the deep end so i started using Ubuntu (and even got my father to use it at age 81) and have finally stopped using Slackware and hacking the kernel.  a few years ago i learned Python and have mostly migrated away from C.

---

### Post by Skaperen on 2019-06-09
i forgot to mention that my plan for installing 20.04 is to install Xubuntu.  my 16.04 system was installed as Ubuntu but now has Xfce and Xubuntu packages added (Unity is still there and sometimes shows upon a few users).

---

### Post by #&amp;thj^% on 2019-06-09
> **Skaperen said:**
> i used to spend over an hour manually setting up my GUI environment.  that was back when i used Unity.  it took many months to work out scripts to do all the setup for me.  then i fell in love with Xfce.  fearing failures, and knowing nothing about lightdm's role, i incrementally changed over to Xfce, one user at a time.  it took almost 2 months (of no upgrades, either).  this is one of the reasons i want to avoid major version changes.  i always do a full fresh install (manually pre-formated) to keep things as clean as possible.  even so, i fear that something in my scripts will fail in a new release.  that's why i skipped 18.04 (i only use LTS).  so i will next install 20.04 around June 2020.

but, i'd like to use newer versions of Python before then.  it has been suggested to use Python Environments (pyenv).  but i cannot get a straight technical answer or find documentation on how they work.  will they impact my system?  maybe i want them to ... in a controlled way ... so that, in theory, i can use a newer version of Python for my system setup scripts.  it seems the people in the Python Forum don't know enough technical details to help resolve system related issues with  Python Environments.

so i have been learning about Linux Containers.  i'm still trying to find a way to run the X server (or Wayland) in a container.  i wonder if lightdm can even be run there.  i can't even figure out how virtual terminals (VTs, all 63 of them) work on containers.  for, example, can i set up a container such that VTs 4 and 5 are on that container while the rest remain on the host.

i am used to working at a rather deep level of OSes since i started on IBM mainframes and migrated through SunOS, NeXT, and 386BSD before finally running SLS Linux and Slackware Linux (and helped test porting it to Sparc since i had 2 of those machines at the time).  i knew i was going to eventually get out of the deep end so i started using Ubuntu (and even got my father to use it at age 81) and have finally stopped using Slackware and hacking the kernel.  a few years ago i learned Python and have mostly migrated away from C.

I'm very familiar with your skill set, after 14 years on the forums, (here and elsewhere) I grew to have a deep respect for your shares I've read. ;)
Anyway, To run Wayland applications in docker without X, you need a running wayland compositor like Gnome-Wayland or Weston. You have to share the Wayland socket.** You find it in "XDG_RUNTIME_DIR" and its name is stored in "WAYLAND_DISPLAY". As XDG_RUNTIME_DIR only allows access for its owner, you need the same user in container as on host. **
Example:
```

docker run -e XDG_RUNTIME_DIR=/tmp \
           -e WAYLAND_DISPLAY=$WAYLAND_DISPLAY \
           -v $XDG_RUNTIME_DIR/$WAYLAND_DISPLAY:/tmp/$WAYLAND_DISPLAY  \
           --user=$(id -u):$(id -g) \
           imagename waylandapplication
```

_QT5 applications also need -e QT_QPA_PLATFORM=wayland and must be started with imagename dbus-launch waylandapplication._
I'm not sure if have seen this yet but: [https://github.com/mviereck/x11docker](https://github.com/mviereck/x11docker)

---

### Post by Skaperen on 2019-06-09
i'm not intending to use *docker* to do containers.  i'm looking at using *lxd* and probably its new *lxc* command.  i may even go more direct, using specific commands to enable, configure, and access container interfaces directly, such as *cgroups* and *namespaces*.  in many cases. *chroot* has been all i have needed (testing stuff i am confident that is not going to cause problems in other aspects, such as testing out a suspected dependency hell case). if i had a more dangerous case, i would fire up qemu.  raw containers should be fine for most pf what i have used qemu for.

---

