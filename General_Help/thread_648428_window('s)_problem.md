---
title: "window('s) problem"
date: 2007-12-23
forum: General Help
---

### Post by syncu on 2007-12-23
i have a strange problem with my application windows , when i open a program or map the top of the window is not shoving, its hiden behind the top menu panel > [_[COLOR="Blue"]picture[/COLOR]_]("http://shrani.si/f/1z/TJ/4txYZoA8/screenshot.jpg")

this is not the first time that happents , but i dont want to fix it like i dit the first time... with a partition format that is :( 

do someone know how to fix this ?

..btw. the first time this problem happen's was on u7.04 when i installed amarok and this time it was after avant-window-manager.. i uninstalled the awm but still its mest up

any idea? :confused:

---

### Post by heatpumpcontrol on 2007-12-23
do you have visual effects activated? If so, deactivate it and it'll correct the problem. However, visual effects are nice but at a sacrifice.

---

### Post by twist2b on 2007-12-23
ok, so are you using compiz fusion? if thats the case... i forgot the code ill try to get that to you later.... but its simply an addition to the "compiz --replace"

i think you should type this as a startup script in sessions
its something like: "compiz --replace & decorate"

but to tell the truth i forgot the code cause it randomly worked again for me WITHOUGHT the code...

(the official instillation works the best)

---

### Post by syncu on 2007-12-23
deactivating visual efects (emerald and compiz) dit not help, and typing the 'compiz --replace & decorate' command in the sessions ...why ? all efects are running (just not right)^^

---

### Post by syncu on 2007-12-23
heres the guide i used for the awm setup [_http://ubuntuforums.org/showthread.php?t=385981_]("http://ubuntuforums.org/showthread.php?t=385981")

---

### Post by heatpumpcontrol on 2007-12-23
> **syncu said:**
> deactivating visual efects (emerald and compiz) dit not help, and typing the 'compiz --replace & decorate' command in the sessions ...why ? all efects are running (just not right)^^

how about

emerald --replace

only if you have emerald installed. If not, install it and then run as above. 

or you can run

gtk-window-decorator --replace

Another thing you could try is after installing emerald run:

sudo /etc/init.d/gdm restart

or 

sudo /etc/init.d/gdm stop

after that at the (what I call black screen)

log in and enter

sudo /etc/init.d/gdm start

This last step has helped me lots of times... instead of the 'restart' switch for gdm

---

### Post by syncu on 2007-12-23
no nothing works, its realy annoying so i guess i have to reinstall the system  a second time , just wish to know why does this happening so i dont run a third time in it:)

---

### Post by heatpumpcontrol on 2007-12-23
Sorry for the delay. It probably has something to do with your video drivers. This has been my experience since I started with linux in April. Nvidia and ATI will hopefully provide more of a full support. Try uninstalling the video drivers... then reinstall

System--> Admin-->Restricted drivers

Remove and reboot. Don't get discouraged. A bit of patience and you'll be enjoying Ubuntu fully. I myself still loose my Visual Effects whenever I use user switching but, I know that will eventually get fixed on the next release or I upgrade to a better video card... with more memory +156mb or so

---

### Post by syncu on 2007-12-24
the removing of the nvidia drivers is working, the windows are displayed correct, but on the new install of the drivers its again mest up ...what should i do now , ...remove the driver files in /etc/x11after uninstalling the drivers or can i mess something up with that ?

---

### Post by syncu on 2007-12-24
i got it figured out :) the awm install has disabled the place windows plugin in the compiz manager :confused: , so after reenable it all works like before , ...:lolflag:

---

### Post by heatpumpcontrol on 2007-12-24
Alright! Glad you got it working. I hope I helped out some... Ubuntu...!!! enjoy!

---

### Post by antisocialist on 2007-12-24
i just want to put this out there,
it is called AWN (avant-window-navigator) not awm
also, the command metacity --replace should do the trick
when running commands with --replace in them, you normally need to put a space before the --replace part.

---

