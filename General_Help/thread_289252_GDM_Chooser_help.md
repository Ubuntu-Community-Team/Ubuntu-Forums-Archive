---
title: "GDM Chooser help"
date: 2006-10-30
forum: General Help
---

### Post by tomski on 2006-10-30
I would like to know how i can disable the XDMCP chooser in dapper??

I ask this because i have disabled it in:
System->Administration->Login Window

and i also checked:
Applications->Debian->Apps->System-> GDM setup

that also shows me its disabled but when i login i first have to select the PC i wish to login to?
Is there a config file that these apps are looking at that i can check too?? Or do i have a bit of an odd problem???
I know its a handy tool but i administer the other pc that i have on my lan via SSH/VNC & prefer this way, not via XDMPC

I also think this is affect FGLRX as since i enabled this i now have problems with 3D apps

---

### Post by tomski on 2006-11-29
another unanswered thread to add to the list

but i found the issue 

go to:
System->Administration->Login Window

then click on security tab & at the bottom click the button labled'Configure Xserver' 
in the 'Servers' dropdown menu select 'Standard' 
& make sure the 'Launch' dropdown menu has 'Greeter' selected

hope this helps

also if youo do use the 'chooser' this will affect the 3d display when you login localy because in the chooser you will have to select 'localhost' which is 127.0.0.1 so you are establishing a network connection
If you really like to use the chooser i would have it enabled but only as an option that is availiable in the greeter

---

