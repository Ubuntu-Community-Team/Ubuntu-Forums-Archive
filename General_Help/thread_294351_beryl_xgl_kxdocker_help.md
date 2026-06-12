---
title: "beryl xgl kxdocker help"
date: 2006-11-06
forum: General Help
---

### Post by jogebau on 2006-11-06
Hi,

Im using edgy, xgl and beryl. Im trying to install kxdocker (with gnome). If I install kxdocker from universe, it shows me kxdocker in a window. After searching in various forums, i found out that there should be patched debs in quinns repo, but i cannot find them.

Can I get these and install them, or if not, how can i get a complete and running istall of kxdocker?

CU

---

### Post by cmost on 2006-11-06
If you get this to work, please post a howto.  I tried using Kxdocker and couldn't get the darned thing to remember my launchers, or their icons.  Plus, it's behavior was erratic.  I found that program completely unintuitive to use.  The Kiba-dock is much better, but I can't get any of the elites over at the Beryl forums to compile a decent Dapper deb for those of us who cannot meet the myriad of dependencies needed to compile it ourselves.

---

### Post by turbojugend_gr on 2006-11-06
ok, I don't know if it should do the trick with the repo version (i compiled from source). But still give it a try.

Open configurator from the tray icon, then navigate to the window tab, and there make the following changes:

IN THE DESKTOP SQUARE: 
"auto send the docker to background layer" (unchecked)
                       "auto raise the dock on events" (checked)
                       "enable fast hiding" (unchecked)
                       "Raise the dock whenever you touch the left corner" (unchecked)*
                       "Raise ................................right corner" (unchecked)*
                       "Hide the dock after" (whatever you like I use 1200ms)
                       "Wait before raise the dock" (20ms)
                       "Desktop shrink (whatever you want-i use the default value)

Store configuration now and close, you might need to restart kxdocker to see the changes (i can't recall). I hope it helps don't forget to say so! I 'll be checking feel free to ask for further infos

*   --> It has to do with your beryl settings, in my beryl config, I have nothing set to right corner gesture, but it is safer to leave noth unchecked for start, then you can experiment. If you mess up the config KILL the process do not exit through the tray, or the messed up config will be saved.

Cheers, TJ

---

### Post by jogebau on 2006-11-06
I really doubt that kibadock is better, but anyway, I remember there was a deb (at least for edgy) though i dont know anymore where it was...

---

### Post by phersotty on 2006-11-06
I don't know much about the compatibility between Beryl and Kxdocker, but I remember reading that even gnome panels sometimes don't cooperate with Beryl either.

---

### Post by turbojugend_gr on 2006-11-06
@phersotty: I can say I think you are wrong, Beryl rocks with kxdocker, as for the panels...what can I say it is like a I am thunderstruck, any link to see this info????

---

### Post by turbojugend_gr on 2006-11-06
Kiba-dock is still only a launcher and nothing else, I am really looking forward to the progress of the project, but since it's main dev is on the move at the moment, he said it would be about 2 months till next release, I hope it becomes as featured as kxdocker, I really like the physics... oh and there are various deb's for kiba out there... try searching the beryl forums for a dapper deb (I am using it in my edgy sometimes, don't worry)

I hope it helps ;)

---

### Post by jogebau on 2006-11-06
@turbojugend_gr: any info how you got this working?

---

### Post by turbojugend_gr on 2006-11-06
Which one kxdocker? THERE"S A WHOLE POST UP THERE!!! --> post#3

---

### Post by jogebau on 2006-11-06
ups sorry, overlooked that...

doesnt work with me, I dont have a tray icon, maybe i have to compile from source...

any way to get it to run with the repos?

---

### Post by turbojugend_gr on 2006-11-06
compile it from source, do you use im, I can can guide you through...
then I will post a how-to maybe.

---

### Post by phersotty on 2006-11-06
> **turbojugend_gr said:**
> @phersotty: I can say I think you are wrong, Beryl rocks with kxdocker, as for the panels...what can I say it is like a I am thunderstruck, any link to see this info????

I think it was this that I read about the panels.  
[http://www.ubuntuforums.org/showthread.php?t=278399&highlight=beryl+gnome+panel]("http://www.ubuntuforums.org/showthread.php?t=278399&highlight=beryl+gnome+panel")

I actually have Beryl running but not kxdocker.  I think I will give it a try and maybe kibadock too.

---

### Post by turbojugend_gr on 2006-11-06
Just when I thought you are lucky, I have a task to perorm so I can't help you at the moment. But there is a pretty nice hoe-to on supriyadisw, try this then do as I say in #3 post, ans ask for further info. I hope it helps.

LINK: [http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake)

---

### Post by turbojugend_gr on 2006-11-06
Well not for me, and as I can see there are only too m8s havingthis issue... anyway it is bad thing, thanx for the link.

---

### Post by jogebau on 2006-11-06
dont worry, ill try myself
maybe after that i will post a how-to

thank you anyway

---

### Post by jogebau on 2006-11-06
Ok seems to have worked. I will post a howto later. Thanks for the help turbo.

Btw: the kxdocker can be expanded by alot of plugins, which are not inluded in the deb in universe, so it might actually be woth compiling anyway

CU

---

### Post by turbojugend_gr on 2006-11-06
Glad it worked m8, I hope you can configure it allright.

---

### Post by spockrock on 2006-11-06
here is a deb that I compiled from quinns sources on edgy. I have updated the version number so synaptic wont try to update it from the edgy repos. enjoy, btw this was made with check install.

---

### Post by jogebau on 2006-11-07
In case anybody didnt notice:

Turbo posted a nice how-to on how to install and configuring this:

[http://www.ubuntuforums.org/showthread.php?t=294511](http://www.ubuntuforums.org/showthread.php?t=294511)

---

