---
title: "black screen on startup"
date: 2007-01-01
forum: General Help
---

### Post by kadkad19 on 2007-01-01
#little long but read please
i make my main OS to ubuntu 
i use ubuntu for a while 
when i startup the computer i get something like :
> ubuntu-2.6.17-10-generic
ubuntu-2.6.17-10-generic (recovery mode)
ubuntu-memtest86
other operation system :
Microsoft windows XP bla bla bla ...

well i always used the first opation ubuntu-2.6.17-10-gen...
its show for a sec :
Starting up
then the screen goes totally BLACK but not a "no-power" black you know ...
after 2 min in this black screen (that include a underscore beeping like DOS command line underscore)
so after 2 min i get the GDM and all works fine ...
i think the black screen is a normal thing to ubuntu ... because i didn't try it before
in a mistake i click on the recorvey mode 
then i saw like all unix like startup ..
something like : 
> service ------------------- [done / ok]
service ------------------- [done/ ok]
service ------------------- [done / ok]
service ------------------- [done/ ok]
service --------------------[fail]    #no failure there ...
service ------------------- [done / ok]
service ------------------- [done/ ok]

thats goes pretty fast ... 30 sec and ubuntu recrovey is alive

so i understand something is not like its planing to .

what can i do recorve it ?
any suggstion ?
i dont want to reinstall !

---

### Post by kadkad19 on 2007-01-01
any ideas ?

---

### Post by Canadia on 2007-01-01
I have the same thing after installing the 2.6.19 kernel. During startup there is a completely black screen, but everything starts up fine. Any ideas how to get graphical or text  startup back?

---

### Post by kadkad19 on 2007-01-02
i dont really care about the Black screen ...
its goes for 2 mins 
look too much for me ... 
some1 know how to fix ?

---

### Post by hartz on 2007-01-09
I get the same result, the screens go black for a long time, feels like minutes but it realy is about 30 seconds.  Then I get GDM login.

I have 2.6.19.1 kernel and nvidia restricted modules 1-0-9746.

I suspect this is happening in stead of the nvidia driver logo being displayed.

---

### Post by Theimon on 2007-01-09
It means usplash is not working. I've got 2.6.19 installed as well, but the splash will not work, although it's installed (see Synaptic --> usplash). I've tried to install custom splash images but that won't work either. To get bootup to show you information, remove quiet splash from your grub entries.

---

### Post by Canadia on 2007-01-09
Additionally I get a black screen and no command prompt when i hit ctrl + alt + F1 or F2. I think it is more than usplash in my case

---

### Post by Theimon on 2007-01-09
> **Canadia said:**
> Additionally I get a black screen and no command prompt when i hit ctrl + alt + F1 or F2. I think it is more than usplash in my case

The system is still booting. You should get a blinking cursor in the top left corner, but you probably won't get a full command prompt (at least in my case, that doesn't happen).

---

### Post by mk04 on 2007-01-10
In Synaptic, check if the package "ubuntu-desktop" is installed. I had this problem once and that fixed it.

---

### Post by null0 on 2007-01-11
> **kadkad19 said:**
> its goes for 2 mins 
look too much for me ... 
You probably have a ton of services starting, just disable the ones you don't need and you should be fine.

usplash is one of those details i really dislike in ubuntu :/ A themed app with only one (ugly) theme available by default :S

---

### Post by hartz on 2007-01-11
Note: My Linux is not "still booting up" when I get the black screen, and I have nosplash set in all my grub menu.lst items already. 

Two other things worth noting:  
a) I get the same thing any time I restart x-windows / gdm.
b) While this black screen is sitting there, the key sequence to swith to a console terminal is ignored.  The moment the screen mode changes (you hear the clicks and the black screen becomes slightly more brighter, even before the GDM login screen is done being drawn on the display), then the switch to a terminal is also working again.

Note:  I will check the recommendations for checking uslash and ubuntu-desktop package though.

---

### Post by DarkW0lf on 2007-03-03
Isn't ubuntu-desktop installed when you install from the CD ?
I see it depends on usplash and I already have usplash installed.
What is the connection between ubuntu-desktop and fixing usplash ?

---

