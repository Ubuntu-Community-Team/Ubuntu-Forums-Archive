---
title: "Minimize, close, maximize not the same in all windows in ubuntu 14.10.."
date: 2014-11-09
forum: General Help
---

### Post by Pedro_Pdr on 2014-11-09
Hi there. Sorry if  im posting this in the wrong section.
I have installed ubuntu 14.10 and afterwards gnome shell and i dont know if installing gnome shell caused this but my windows in "Files" look like this:
[IMG]http://i.imgur.com/sMMGd8L.png[/IMG]
Screenshot app that opens when i take one looks the same. Terminal, ubuntu software center, etc etc.. the minimze close maximize looks good like screenshot of system settings as above.

and system settings is weird with white boxes behind icons..
[IMG]http://i.imgur.com/0OjaPI6.png[/IMG]

I have already unninstalled gnome shell but it still the same.. Im not sure if was the installation of gnome shell that caused this issues...
Any help?

Another thing is that open files from left launcher doesnt work.. neither in dash.. only open my personal folder "Pedro".
Thanks in advance.

---

### Post by grahammechanical on 2014-11-09
When we install an alternative desktop it does not just bring in a different user interface but it brings in the utilities associated with that desktop environment. What you are seeing is the Gnome 3 shell version of the file manager (Nautilus). Ubuntu Unity uses Nautilus (Gnome file manager) as the file manager but it has been modified slightly by the Ubuntu developers. So, there are differences between Nautilus in Ubuntu Unity and Nautilus in Gnome 3 shell.

The same can be said about System Settings. The developers took Gnome control center and modified it into Unity control center.

Sadly, the act of un-installing an alternative desktop environment does not put things back the way they were. I give an explanation but not a solution. sorry.

Regards.

---

### Post by Pedro_Pdr on 2014-11-09
Thank you! Your awnser was helpful and i have done some searching and found the solution! 

Here is the solution:
sudo ppa-purge ppa:gnome3-team/gnome3-staging
sudo ppa-purge ppa:gnome3-team/gnome3-next
sudo apt-get purge gnome-shell

Working now =)

---

### Post by Frogs Hair on 2014-11-09
I don't see this change in Unity on my current 14.10/Gnome Shell installation. I did see changes in Nautilus, the Gnome Terminal, and Gedit  when adding a ppa for gnome 3.12 packages not included in in the Ubuntu repository on a prvious 14.10 installation. The title bar in Nautilus/Files does appear as the screen shot when logged into the Gnome Shell but not Unity.

---

