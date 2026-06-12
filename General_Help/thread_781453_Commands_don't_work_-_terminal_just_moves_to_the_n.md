---
title: "Commands don't work - terminal just moves to the next line"
date: 2008-05-04
forum: General Help
---

### Post by Wartender on 2008-05-04
I recently got ubuntu 7.10 and installed it on my computer as a dual-boot with windows, and everything was working fine until i tried setting up desktop effects (instead of re-writing the entire story, here's a link to where i did in another thread [http://ubuntuforums.org/showthread.php?p=4825508](http://ubuntuforums.org/showthread.php?p=4825508))
anyway, after that, i found out that i can't enter any commands because i type something, and i hit enter and it just goes to the next line and nothing happens
somebody pleeeeeeeease help me with this and if nobody can then just tell me how to uninstall ubuntu so i can go back to windows and forget all about this :mad:

---

### Post by overdrank on 2008-05-04
> **Wartender said:**
> I recently got ubuntu 7.10 and installed it on my computer as a dual-boot with windows, and everything was working fine until i tried setting up desktop effects (instead of re-writing the entire story, here's a link to where i did in another thread [http://ubuntuforums.org/showthread.php?p=4825508](http://ubuntuforums.org/showthread.php?p=4825508))
anyway, after that, i found out that i can't enter any commands because i type something, and i hit enter and it just goes to the next line and nothing happens
somebody pleeeeeeeease help me with this and if nobody can then just tell me how to uninstall ubuntu so i can go back to windows and forget all about this :mad:

Hi and when you boot into recovery mode and use the reconfigure command yes it will just reconfigure and then give the command prompt. Try using the command startx or reboot the system and see if you reach the desktop.

---

### Post by Wartender on 2008-05-04
no actually this happens after i reboot after using the reconfigure, i choose ubuntu in the boot menu, and it shows some weird things and then i can't enter any commands because it just ignores them, no matter what i type i hit enter and it goes to the next line without doing anything, i'll try again for the sake of trying but i doubt it will work.

---

### Post by Wartender on 2008-05-04
nothing. i boot with ubuntu 7.10, and it displays a bunch of things that flash (if it helps, here's is the last one:)
* loading boot scripts (some direction here i forgot)                 [ OK ]
and then where am typing i can enter commands but it doesn't do anything, for example:
[what i said before with the loading boot scripts]
startx
[here i can type stuff]
and this happens after the graphic loading screen comes up, but i can't do anything, should i try running startx in recovery mode?

---

### Post by overdrank on 2008-05-04
> **Wartender said:**
> nothing. i boot with ubuntu 7.10, and it displays a bunch of things that flash (if it helps, here's is the last one:)
* loading boot scripts (some direction here i forgot)                 [ OK ]
and then where am typing i can enter commands but it doesn't do anything, for example:
[what i said before with the loading boot scripts]
startx
[here i can type stuff]
and this happens after the graphic loading screen comes up, but i can't do anything, should i try running startx in recovery mode?

Hi and yes try running recovery mode. You will need to be at command prompt with login user name and password.

---

### Post by Wartender on 2008-05-04
you mean at the command prompt i have to type my user name, enter, then my password, enter, and then enter startx? when i did the reconfigure i didn't have to enter any username or password, do i have to type anything before the username and password? anyway thanks for actually helping :)

---

### Post by overdrank on 2008-05-04
> **Wartender said:**
> you mean at the command prompt i have to type my user name, enter, then my password, enter, and then enter startx? when i did the reconfigure i didn't have to enter any username or password, do i have to type anything before the username and password? anyway thanks for actually helping :)

HI and when you see the grub loading you will have a choice of which Operating system to choose. Recovery mode is usually the second choice on the list and yes you will need to login at the command prompt where you login with user name and password then you can use the startx command.

---

### Post by Wartender on 2008-05-04
ok, i tried running ubuntu in recovery, and since i only have one profile i guess it logged me on automatically (since the command line said [my username]-desktop: [here i srite stuff])
i tried entering startx and the screen goes black and then he recovery screen comes up again and it says it had a fatal error (something about not finding any screens, idk)
anyway i give up just tell me how to uninstall it so i can go back to windows, thanks for trying to help though

---

### Post by Wartender on 2008-05-04
ok, i tried running ubuntu in recovery, and since i only have one profile i guess it logged me on automatically (since the command line said [my username]-desktop: [here i write stuff])
i tried entering startx and the screen goes black and then he recovery screen comes up again and it says it had a fatal error (something about not finding any screens, idk)
anyway i give up just tell me how to uninstall it so i can go back to windows, thanks for trying to help though

---

### Post by overdrank on 2008-05-04
> **Wartender said:**
> ok, i tried running ubuntu in recovery, and since i only have one profile i guess it logged me on automatically (since the command line said [my username]-desktop: [here i write stuff])
i tried entering startx and the screen goes black and then he recovery screen comes up again and it says it had a fatal error (something about not finding any screens, idk)
anyway i give up just tell me how to uninstall it so i can go back to windows, thanks for trying to help though

Ok if you would like to uninstall you may look at this link
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
_**BUT **_if you had it working why not just reinstall Ubuntu. Just like you did the first time except reinstall Ubuntu on the existing partition.

---

### Post by Wartender on 2008-05-04
yeah i think that's what i'm going to do, considering that my friend ordered the ubuntu 8.04 CD. i'm going to ask him if he can lend it to me so i can install it on my partition, any tips or things that i need to do when or before installing 8.04 on the partition with 7.10 in it?

---

### Post by overdrank on 2008-05-04
> **Wartender said:**
> yeah i think that's what i'm going to do, considering that my friend ordered the ubuntu 8.04 CD. i'm going to ask him if he can lend it to me so i can install it on my partition, any tips or things that i need to do when or before installing 8.04 on the partition with 7.10 in it?

Hi and just back up all your data and when installing use the manual install and select the existing Ubuntu partition.

---

### Post by Wartender on 2008-05-04
i don't have any data on ubuntu, i used it for like a day before it died :P, but should i back up windows data? (i suppose not right?)

---

### Post by overdrank on 2008-05-04
> **Wartender said:**
> i don't have any data on ubuntu, i used it for like a day before it died :P, but should i back up windows data? (i suppose not right?)

HI and yes backup your windows partition also. There is always a chance of a click here of click there and all you data is gone.

---

### Post by Wartender on 2008-05-13
well... i had an idea to try startx while in recovery mode, and it gave me some weird error thing which i don't remember right now, so then i tried using ```
sudo dpkg-reconfigure xserver-xorg
``` again, for the heck of it, and now when i reboot the same thing happense where the screen goes black and the monitor doesn't detect input after the loading screen. i'm going to retry the code AGAIN, but now i've gathered sme information on the monitor and graphics card (ATI RADEON XPRESS 200), if anyone knows what to do please say.

p.s. wish me luck XD

---

