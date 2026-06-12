---
title: "why? I need to restart the gdm"
date: 2008-05-09
forum: General Help
---

### Post by DeadInQ on 2008-05-09
Badly, just like the title says I have to restart the gdm  every time after login ubuntu , or  when  I switch the desk two or more,  desktop just show me the background without   panels and I also  can't open the  menu with the right key of mouse:lolflag:

---

### Post by Patb on 2008-05-10
Deadinq, I think you need to give more information so that this forum can help.  Could you please post what desktop environment or window manager you are using.  Is it Gnome, KDE, Fluxbox, Blackbox, XFCE?  What version of Ubuntu?  What type of computer, desktop, laptop, stand alone or networked?  Also anything else you think might be relevant.  

Cheers, Pat.

---

### Post by jocko on 2008-05-10
> **Patb said:**
> Deadinq, I think you need to give more information so that this forum can help.  Could you please post what desktop environment or window manager you are using.  Is it Gnome, KDE, Fluxbox, Blackbox, XFCE?  What version of Ubuntu?  What type of computer, desktop, laptop, stand alone or networked?  Also anything else you think might be relevant.  

Cheers, Pat.

He's already (indirectly) said he uses gnome.
Look at the [Ubuntu] tag in the thread title. That means he uses Ubuntu (i.e gnome).
The fact that he has problems with gdm (gnome display manager) may also be a clue...

To the actual problem: Unfortunately I have no clue how to fix it. It's happened to me a few times, but not often enough that I have been able to figure out what caused it.
Do you use compiz? Try disabling it.
Which graphics card do you have? Which driver?

---

### Post by DeadInQ on 2008-05-11
Thank you so  much and sorry  I am here so late, 
just like  jocko guess , I use the ubuntu 7.10 , the detail show below:
computer:laptop and ,of course ,networked
graphics card:NVIDIA 8400 GS
driver: NVIDIA-Linux-x86-169.12-pkg1.run(I install it)
gnome display manger
and the jocko's words recall me it seems that  my question appear after I install the compize  Fusion  Icon.
And I have tried to disable it ,and just like you see that there is no "solved" in this post, so ........

---

### Post by bingoUV on 2008-05-11
> **DeadInQ said:**
> Badly, just like the title says I have to restart the gdm  every time after login ubuntu , or  when  I switch the desk two or more,  desktop just show me the background without   panels and I also  can't open the  menu with the right key of mouse:(:confused:.

What do you mean by "switch the desk two or more" ? 
1. You have 2 or more desks (furniture) which you keep switching?
2. Virtual desktop : You change to another virtual desktop , of which there are 4 by default in ubuntu? Might call them workspaces. When desktop on a cube is enabled, you visualize these as sides of a cube.
3. Ctrl-alt-F1 : You move to 2 or more virtual terminals, maybe Ctrl-alt-F1, Ctrl-alt-F2, and back to Ctrl-alt-F7?

---

### Post by spamzilla on 2008-05-11
I have the same problem

[http://ubuntuforums.org/showthread.php?t=790272](http://ubuntuforums.org/showthread.php?t=790272)

Compiz/awn is enabled and the virtual terminals work but not a lot else does.

---

### Post by anuban on 2008-05-11
I have the same problem...It happens when I login.
I see everything except the window borders which shows the close/minimize buttons and all.
I am using Compiz with advanced setting and AWN.
I usually get it to work by doing the following:

[LIST=1]
[*] Install Compiz Fusion Icon.  (One time only)
[*] When you login, you don't see window borders, so go to Applications>System Tools>Compiz Fusion Icon.
[*] This icon appears on your task bar in notification area.
[*] Right click on that icon and select 'Reload Windows Manager'.
[*] That's it.  Your windows borders are back.
[/LIST]
 But I was wondering why it is happening in the first place.  I know how to solve it with above method, but it shouldn't be there at all.  
I am using Dell Inspiron E1505 with NVIDIA using the latest driver from Ubuntu repo.

Hope someone knows the issue and devs are working on it to fix it.

Thanks

---

### Post by DeadInQ on 2008-05-11
"switch the desk two or more " ? 
I represent it like this just because of  there are four small grey rectangle  appear in the right bottom of desktop, and when I transfer cursor on one of them ,  some words appear (click  to switch to "Desk 1 "), of course, if you want ,the number could be replaced with two, three, or four.

---

### Post by DeadInQ on 2008-05-17
Ok! I just want to say it works well now, I mean it is not still there, and I don't need to restart the gdm :)

---

