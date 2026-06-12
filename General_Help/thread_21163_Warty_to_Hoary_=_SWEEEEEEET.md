---
title: "Warty to Hoary = SWEEEEEEET"
date: 2005-03-20
forum: General Help
---

### Post by TheCondor on 2005-03-20
Hello everybody  :-o 

I just upgraded my system to hoary and all i can say is ITS SOOOOOOOOOOOO GOOOOOOD!!!! Congratulations to each and every one of the people that contributed to this release ( i know its not final yet ), it just rocks !!!! 

Everything is working perfectly, everything works faster, everything looks neater, everything is better, everything is soooo good! 

Since I am not allowed to post in the gnome desktop support thread ( i dont know why ) I decided to open this thread to ask some minor things that I havent figured out yet. 

Im having a problem with my themes. I had this for some days now, so its not caused by hoary, cos I just upgraded. My problem is as follows : 

Say that I want to use the Redhat theme, Bluecurve, which has its own window borders, its own controls and its own colors. If I choose the bluecurve theme, what happens is that even though the window borders change, the icos change too, the main color stays greyish ( the default Ubuntu one ). And this happens to any theme I choose. For example, when someone opens nautilus while using the blucurve theme, he should see the bar on the right side of nautilus ( the scroll bar ) in blue color. But i see this bar in this grey Ubuntu color. ( i have nothing against ubuntu colors, i love them actually, but i change my desktop very often and this issue kinda bothers me ). 

What is more strange is that if I open synaptic, I will see these scrollbars just as they were meant to be, the proper Blueucurve bars that nautilus should have had, blue coloured as well. This is giving me a head ache because any theme I choose has this issue and I dont know how to deal with it.

I would appreciate any help related to my issue, its the last step from heaven in Ubuntu believe me....  :-o 

The more I use Ubuntu the more I love it! ( thank god my connection had problems and I at last decided to download ubuntu to try it instead of downloading fedora-suse dvds  :lol:  )

Keep up the good work folks, a distro done the way it should be, fast stable and neat!!

---

### Post by fjleal on 2005-03-20
[QUOTE=TheCondor]Hello everybody  :-o 

I just upgraded my system to hoary and all i can say is ITS SOOOOOOOOOOOO GOOOOOOD!!!! Congratulations to each and every one of the people that contributed to this release ( i know its not final yet ), it just rocks !!!! 

Everything is working perfectly, everything works faster, everything looks neater, everything is better, everything is soooo good! 

Since I am not allowed to post in the gnome desktop support thread ( i dont know why ) I decided to open this thread to ask some minor things that I havent figured out yet. 

Im having a problem with my themes. I had this for some days now, so its not caused by hoary, cos I just upgraded. My problem is as follows : 

Say that I want to use the Redhat theme, Bluecurve, which has its own window borders, its own controls and its own colors. If I choose the bluecurve theme, what happens is that even though the window borders change, the icos change too, the main color stays greyish ( the default Ubuntu one ). And this happens to any theme I choose. For example, when someone opens nautilus while using the blucurve theme, he should see the bar on the right side of nautilus ( the scroll bar ) in blue color. But i see this bar in this grey Ubuntu color. ( i have nothing against ubuntu colors, i love them actually, but i change my desktop very often and this issue kinda bothers me ). 

What is more strange is that if I open synaptic, I will see these scrollbars just as they were meant to be, the proper Blueucurve bars that nautilus should have had, blue coloured as well. This is giving me a head ache because any theme I choose has this issue and I dont know how to deal with it.

I would appreciate any help related to my issue, its the last step from heaven in Ubuntu believe me....  :-o 

The more I use Ubuntu the more I love it! ( thank god my connection had problems and I at last decided to download ubuntu to try it instead of downloading fedora-suse dvds  :lol:  )

Keep up the good work folks, a distro done the way it should be, fast stable and neat!![/QUOTE]
 Just a thought: whem you use Synaptic, the application actualy runs under the root account, right? So the difference may be due to different profiles between your regular usar and root user... I'm not sure if this helps...

---

### Post by TheCondor on 2005-03-20
[QUOTE=fjleal]Just a thought: whem you use Synaptic, the application actualy runs under the root account, right? So the difference may be due to different profiles between your regular usar and root user... I'm not sure if this helps...[/QUOTE]


Mmmm, I tried running sudo nautilus and the window was shown as it was supposed to be ( the normal bluecurve controls ). So I guess you are right, but how do I fix that, do you have any suggestions?  :-k

---

### Post by lukem on 2005-03-20
I'm in warty, but it looks like all the themes are owned by root.  Maybe it makes a difference where your new theme is located.  Is it in /usr/share/themes?

---

### Post by TheCondor on 2005-03-20
I found the solution to this by removing the gtkrc-2.0 file from my home directory, as it seems that it was conflicting with the gtkrc file. 

include "/usr/share/themes/Human/gtk-2.0/gtkrc"  is what was in the gtkrc2.0 file, which probably made every theme have the human brown ( not grey as i mentioned above lol i just found out ) color in it, now its all fixed  :-o

---

