---
title: "Incurable login loop, help please"
date: 2021-02-05
forum: General Help
---

### Post by MibunoOokami on 2021-02-05
Turned my machine on today typed my password, hit enter and nothing happened kind of. It sort of hung for a few minutes then went back to the screen for choosing user. 
A solution I found to this problem was to enter tty1 and then move the .Xauthority file/directory to .Xauthority.bak, the problem is I get told ```
mv: cannot stat ‘.Xauthority”: No such file or directory.
```

Something else unusual… I have to enter my home partition passphrase twice before it unlocks to bring me to the login screen. Not because I entered the wrong password, as I’ve double checked it, four times now. 

Could the two be related? How could the .Xauthority file/directory just vanish? I thought perhaps the solution was dated and that .Xauthority might have a different name in ubuntu 20.04, except when I gpogled it, that doesn’t seem to be the case.

Can someone help me figure out how to fix this ASAP please?
Thanks.

---

### Post by MibunoOokami on 2021-02-05
Some pertinent information. I just remembered, I used fdupes to delete some duplicate files but only in the desktop directory. 
The command was ```
fdupes -r -d -N home/user/Desktop
```, upon completion I shut the machine down, and it was the first power up after using fdupes that this occurred. 
Is that just uncanny timing, or could fdupes have deleted a file it shouldn’t have and thus creating this problem?

---

### Post by Portaro on 2021-02-05
Maybe this can help you I wrote a guide on a forum to this type of problems in past but I'm still use 14.04.

When .xauthority is corrupt all seession is broken and simply you can enable X in graphic mode you only have text mode, so the problem needs to be solved on text mode.

My steps are :

> [COLOR=#AAAAAA][FONT=Inter]sudo service lightdm stop[/FONT][/COLOR]

> [COLOR=#AAAAAA][FONT=Inter]rm ~/.Xuathority[/FONT][/COLOR]

> [COLOR=#AAAAAA][FONT=Inter]sudo service lightdm start[/FONT][/COLOR]

If still cant work the you need to do this :

> [COLOR=#AAAAAA][FONT=Inter]sudo killall Xorg[/FONT][/COLOR]

> [COLOR=#AAAAAA][FONT=Inter]touch ~/.Xauthority[/FONT][/COLOR]

> [COLOR=#AAAAAA][FONT=Inter]chown username:username ~/.Xauthority[/FONT][/COLOR]

[https://docs.citrix.com/en-us/linux-virtual-delivery-agent/7-15-ltsr/configuration/configure-xauthority.html](https://docs.citrix.com/en-us/linux-virtual-delivery-agent/7-15-ltsr/configuration/configure-xauthority.html)

Link to my guide on the forum 
[https://gnulinuxvagos.es/topic/11467-no-me-deja-iniciar-sesion/](https://gnulinuxvagos.es/topic/11467-no-me-deja-iniciar-sesion/)

---

### Post by MibunoOokami on 2021-02-05
> **Portaro said:**
> Maybe this can help you I wrote a guide on a forum to this type of problems in past but I'm still use 14.04.

When .xauthority is corrupt all seession is broken and simply you can enable X in graphic mode you only have text mode, so the problem needs to be solved on text mode.

My steps are :







If still cant work the you need to do this :







[https://docs.citrix.com/en-us/linux-virtual-delivery-agent/7-15-ltsr/configuration/configure-xauthority.html](https://docs.citrix.com/en-us/linux-virtual-delivery-agent/7-15-ltsr/configuration/configure-xauthority.html)

Link to my guide on the forum 
[https://gnulinuxvagos.es/topic/11467-no-me-deja-iniciar-sesion/](https://gnulinuxvagos.es/topic/11467-no-me-deja-iniciar-sesion/)


 Thanks for your reply Portaro,
 
 

 First step, no .Xauthority file or directory, and ```
job for lightdm.service failed because the control process exited with error code.
```

 
 
 Second step ```
Xorg: no process found
```

 
 
 Other methods I have tried since making the post are:  
 1) Create a new user, except the new user also ends up in login loop. Not sure of the the reason creating a new user account would have achieved if not looping.
 2) Install lightdm, login loop persists there
 3)Ran apt full-upgrade, this produced a long list of (22) messages about possible missing firmware, I really don't know what would cause that, I doubt it would have been fdupes.
At the end of the upgrade it reported how many files and directories are installed, and it looks to be accurate.

---

### Post by MibunoOokami on 2021-02-06
> **MibunoOokami said:**
> 
Something else unusual… I have to enter my home partition passphrase twice before it unlocks to bring me to the login screen. 
Not because I entered the wrong password, as I’ve double checked it, four times now. 


                        Long story short. Contrary to my earlier comment, I was in fact using an incorrect passphrase :oops:, and rather than warn me like in times past, 
ecryptfs was bringing me to the login screen which lead me to believe I was entering the correct passphrase... 

 
 
 Normally when an incorrect passphrase is used it would give a warning to the effect of “ecryptfs unlock unsuccessful” until such time as you got it right, 
and if you entered the correct one it would say something to the effect of “ecryptfs unlocked successfully”.  

 At no point over the past few days has it given me either of these messages, which is most frustrating ](*,)

---

