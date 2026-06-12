---
title: "Problem with ubuntu-desktop on Kubuntu"
date: 2005-10-24
forum: General Help
---

### Post by joneall on 2005-10-24
I installed Kubuntu with success.  Then I wanted to be able to try Gnome too, so I did 

   apt-get install gdm

But no Gnome on the logon menu.  Then I saw on these forums that I should have installed

   apt-get install ubuntu-desktop

which I did.  During that process, I saw messages like

   
dpkg: libesd0: dependency problems, but removing anyway as you request:
 libgnome2-0 depends on libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35); however:
  Package libesd0 is to be removed.
  Package libesd-alsa0 is not installed.
 artsbuilder depends on libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35); however:
  Package libesd0 is to be removed.
  Package libesd-alsa0 is not installed.
 akode depends on libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35); however:
  Package libesd0 is to be removed.
  Package libesd-alsa0 is not installed.
 konq-plugins depends on libesd0 (>= 0.2.35) | libesd-alsa0 (>= 0.2.35);  

Why alsa?  :confused: 

Now, when I launch Firefox (under KDE), I get a popup window which tells me:

The file /usr/share/ubuntu-artwork/home/index.html cannot be found.   Please check the location and try again.  :( 

Not surprising.  The file seems to have been moved to

 /usr/share/ubuntu-artwork/home/index-ubuntu.html.  


Setting this as Firefox's initial page works fine.

But why move it?  And how to avoid the problem when I install (K)ubuntu on my prinicipal computer?  

Thanks in advance.  John

---

### Post by red_plague on 2005-10-24
[QUOTE=joneall]
But why move it?  And how to avoid the problem when I install (K)ubuntu on my prinicipal computer?  
[/QUOTE]
Hmmmm, what i did was to first install ubuntu, normally, then i fired up Synaptic and selected kdelibs, kdebase, kdm, and some other kde stuff(can't remember if i saw kubuntu-desktop) This installed all the dependencies, and i had my kde-desktop installed (120 Mb), try to do the same with gnome under kde, see if it works.
when i started firefox, it opened file:///usr/share/ubuntu-artwork/home/index.html
with no problems
 I tried to like Gnome, but the only good thing about it was that it had a "Hibernate" option that worked in the logOut menu.
  My advice: stay with KDE, it's better(Perhaps get gaim, has better emoticon support, and also get ivman to automatically mount & open CD's) .

---

