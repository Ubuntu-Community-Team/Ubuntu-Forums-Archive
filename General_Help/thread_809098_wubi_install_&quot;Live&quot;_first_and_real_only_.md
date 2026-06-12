---
title: "wubi install &quot;Live&quot; first and real only on order?"
date: 2008-05-27
forum: General Help
---

### Post by nooby on 2008-05-27
How do I know if I am still in the ubuntu live program of if this is 
and actual wubi install? 

I downloaded the installer from its proper place and it say int does an install. Does that mean it installed the "Live" cd virually or a real install. 

As I have indicated before I have had problem with the hardware software combination on my apopen barbone. Spmething with acpi. 

But I am trying to follow a tip that one should do a supend first and shutdown only after resume then it should work. Did for the one giving the tip. 

So I have not tested that yet but will after finishing here now. 

Nooby

Test of swedish keyboard åäö: works

Edit

Back after testing to do suspend. suspend survived. now will test to do shut down

None have told if one should log out first before doing shut down? is that important?

---

### Post by ago on 2008-05-27
see the output of mount. and yes you can shutdown normally without logging out

---

### Post by nooby on 2008-05-27
Thansk but I am too noob to know what output of mount is. 

I will log in again in linux and see if it rememered my bookmarks 
that will show if I am doing all right. 

Doing suspend first and then booting into windows and shutting down 
there survived, and now I am back in wind writing here. 

so next time me write from linux and do a shutdown there too. 
and get back to tell if it survive. 

could it be the updating the make this shut down problem get triggered. 

As I remember durign 2007 me had it I got if after an update initiated by ubuntu? But I was using fiesty then and are on hardy now. I will change profile later. sorry 

edit I am not on "Live" cause it remember my bookmarks. Now the test of shut down

Shut down failed in the end. the alt prntscrn rseiub didn't help and ctrl alt del didn't either. 

hd stopped and fan stopped but the blue led indicating it is not entirely stopped continued to be on. 

I had to do a hard boot. 

But I got lucky this time. the mbr did not get corrupted but I will test 
to always do suspend and boot into windows and shut down from there instead 
until I find a acpi patch or whatever is needed. I want to use linux and 
unfortunately I am too much noob to get the commandline things like sudo. 

am I ubuntu ubuntu in sudo but the chosen user and psw when I log in? 
is that two different names psw maybe? will now test Restart once more

Restart seems to be the workaround for me. If I do Restart and log into 
windows and shut down via win then all is going ok. 

My first failure in May. After the long break with linux. 

I did a restart and it asked for thewindows recovery cd. 

but a new hardboot repaired the mbr? so from now on I 
do suspend before doing restart and shutdown through windows. 

hope that will last a bit longer than a few hours. 

what about this question? I know it is not wubi related but 
do I really need to make a new thread for it? 

[B]what is the alternative "recovery mode" start up of ubuntu? 
what does it do differently? would that solve my shut down problem?[/B]

---

### Post by jackhe22 on 2008-05-28
Recovery mode puts you into a terminal, logged in a Administrator. Dont fiddle! If you need the Desktop in recovery mode type: startx

---

### Post by nooby on 2008-05-28
Would that help me with avoiding hard reboot? 

I'm in Ulteo Linux now and that one have no hard boot problem. 
So it must be possible for Ubuntu too. Ulteo si still a Beta 
so Ubuntu is years ahead of them. But the good thing about them 
is that they had no shut down problem as far as I know but Ubuntu 
have had such on some computers.

---

### Post by ShangTsungOmega on 2008-05-28
Nooby,
  Did you install from inside of windows or from the live cd? If you installed it with windows the first boot after you install it it will prompt you to choose windows or ubuntu. When you choose ubuntu hit esc and choose to install with the acpi workarounds. Yes you may have to do a clean install again but that is the only way i could get mine to install correctly so it might help you as well.

---

### Post by ago on 2008-05-29
Did you boot with ACPI workarounds when you installed?

---

### Post by nooby on 2008-05-29
To Ago and ShangTsungOmega
I didn't know me should do such. None warning about such. 
> When you choose ubuntu hit esc and choose to install with the acpi workarounds. Yes you may have to do a clean install again but that is the only way i could get mine to install correctly so it might help you as well.

Could one do work arounds after the install too? 

After hitting esc button what am I suppose to write and where? 

Much appreciated that you two try to help me. 

It has survived restarts now but still don't shut down fan and the led 
on front. But it doesn't seem to destroy the mbr unless it do it randomly. 
I 've only done one shutdown yet. 

I have the latest updates now so maybe that helped a bit. 

But I want to learn about how to do a clean shut down. 
So what should I write after hitting esc? 

I want to change my username in ubuntu log in too. I chosed a too long one.

I don't mean in this forum that is a short and sweet one. :)

Edit. 

I understand the esc a bit better but now where to write and what to write. 
When I hit esc and e for edit then I get three lines to chose to edit. 
Which one am I supposed to edit and write what? "no acpi" or similar? 

But how do one get cursor to the place after the text? And one what line 
will it work best?

---

### Post by ago on 2008-05-29
Open a terminal and type

cat /proc/cmdline

then post the output

---

### Post by nooby on 2008-05-29
Ago I wil ldo that but first let me ask. 

do this one works? 

> "Shutdown" doesn't
This system powers off with Edgy, Dapper, Knoppix, ... but not Feisty. If I select Shutdown after a while nothing's happening, there's no message on the screen, and the keyboard and mouse are dead. Someone on some forum (where?) suggested:
Do sudo gedit /etc/modules. Add the following line, then save:
apm power_off=1
do sudo gedit /boot/grub/menu.lst (where the l is a lower case L). Find the line that start with "kernel" and add this onto the end, no carriage return, all on the same line which probably wraps over:
acpi=off apm=power_off
then save. Power off however you can, power back up and on "Shutdown" it should. Mine did.
Usual cautions apply when changing system files.....

From here [http://http://ubuntuforums.org/showpost.php?p=3661398&postcount=10]("http://http://ubuntuforums.org/showpost.php?p=3661398&postcount=10")

Ok I try to do what you asked me to do. Tehre should be a short cut for opening a terminal was it ctrl alt backspace?

---

### Post by nooby on 2008-05-29
bash: cat/proc/cmdline: No such file or directory

that was the result of that command could that explain 
the failure to do clean shutdown? 

If I do suspend and then resume and then restart 
then it allow me to go into windows and shutdown 
from there. But after me did update I don't seem 
to need to do suspend first. The restart seems to 
survive each time??? Not sure have to few such. 

But to be able to shut down would be really nice.

---

