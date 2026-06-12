---
title: "what is a stable installation?"
date: 2006-11-21
forum: General Help
---

### Post by neoflight on 2006-11-21
hello folks,

I am using edgy now. working great. but as a user, i do some work and for that i might need some new programs. I install them and i am then faced with dependencies. sometimes libs that are not inclided in the repos. I get then from somewhere and then things are fine or they can be messy. so this is the third 'stable' edgy installation i am using. (removed all traces of fedora 6 too last month :d)

so what is the definition of a stable system? is it that the system is working great if  and only if we use the stuff from repos? 

how do i freeze the upgrades? i tried removing ubuntu-desktop but it says its needed for security updates.. so how can i lock (as in synaptics) a "lot" of packages to prevent something overwriting them? ...its a pain to click each item in synaptics to lock....

other way  i think of is to comment out the repos in the sources.list. but that will not help in dependency hell 'if' iam faced with.

kindly correct me if i am wrong and suggest an intelligent way to do this... thanks...

---

### Post by Ramses de Norre on 2006-11-21
Necessary lib's that aren't included in the repo's?!? Are you sure you've got all repo's enabled? I've never seen that on a ubuntu install before..
If you post your /etc/apt/sources.list I'll look through it.

And you could just turn off update-notifier in system>preferences>sessions>startup. You wont get the pop ups no more then.

---

### Post by neoflight on 2006-11-21
> **Ramses de Norre said:**
> Necessary lib's that aren't included in the repo's?!? Are you sure you've got all repo's enabled? I've never seen that on a ubuntu install before..
If you post your /etc/apt/sources.list I'll look through it.

And you could just turn off update-notifier in system>preferences>sessions>startup. You wont get the pop ups no more then.

thanks... i have all the repos enabled...
[PHP]deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
[/PHP]

i guess the problem was when i tried to install one of the java based 3D modeling and rendering tool...[brl-cad]("http://sourceforge.net/projects/brlcad") or [art of illusion]("http://sourceforge.net/projects/aoi")... i dont remember which one....the system completely went really slow... i even forgot what libraries i installed...

fglrxinfo gives me 
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

fgl_glxgears >>
```
2252 frames in 5.0 seconds = 450.400 FPS

```

i made so changes in many different config files...so i had to reinstall...i thot thats better off...

thanks

---

### Post by neoflight on 2006-11-21
i have been using ubuntu since breezy and from my experience i feel that there should be a global command by which the root should be able to restore all the default/factory settings (of the current running release such as dapper/edgy whatever)... may be from the installation cd/image itself without the need for a complete installation...repairing only the changed files...does that exist?

---

### Post by Ramses de Norre on 2006-11-21
You do are missing some repo's, try this sources.list:
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security universe multiverse

```

And I never heard about such a command..

---

### Post by cantormath on 2006-11-21
In the ubuntu case,

I believe it is Using Dapper LTS (LONG TERM SUPPORT) and only upgrading with stable upgrades.

also, be aware of what you install in case there is a problem.

Nothing is perfect, but anything is better then Microsoft.

---

### Post by Nameless_one on 2006-11-21
And use aptitude instead of apt-get, so that you can uninstall whatever you install including all of its dependencies (that are no longer used) so you don't have libraries hanging from things you installed and uninstalled.

---

### Post by neoflight on 2006-11-21
thankyou...i indeed was missing multiverse.... but update yet from dist-upgrade...

i dont know how to keep track of all the changes i make in config files for various installations.... still trying to get grasp of it... may be will comeup with a factory settings restore applications....:rolleyes:

---

### Post by Ramses de Norre on 2006-11-21
You also missed edgy-updates which was more important.

EDIT: seems like they were there after all.. Sorry =)

---

### Post by igknighted on 2006-11-21
The best way to remember your changes is to make a backup of the config file every time you change it, so you can always go back one step to the last setup that worked.

---

