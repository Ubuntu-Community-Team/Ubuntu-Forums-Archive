---
title: "Gdesklet problem with staterbar.display"
date: 2004-11-19
forum: General Help
---

### Post by Perfect Storm on 2004-11-19
Hi.
  
  I got a problem with the starterbar theme in gdesklets. I can't add any application(s) to it or anything. 
 All my other gdesklets theme are working perfect exept this one. I'd try to download a newer version of starterbar but with the same result.
  
  
  Thanks

---

### Post by Perfect Storm on 2004-11-19
**bump**

---

### Post by Rancoras on 2004-11-19
[QUOTE=Artificial Intelligence]Hi.
  
  I got a problem with the starterbar theme in gdesklets. I can't add any application(s) to it or anything. 
 All my other gdesklets theme are working perfect exept this one. I'd try to download a newer version of starterbar but with the same result.
  
  
  Thanks[/QUOTE]

You're right clicking and clicking "new launcher" correct?  Drag and drop should also work.  What happens when you do either of these?

---

### Post by Perfect Storm on 2004-11-20
Tried both with the drag&drop and add new.

---

### Post by Rancoras on 2004-11-20
[QUOTE=Artificial Intelligence]Tried both with the drag&drop and add new.[/QUOTE]

And I repeat, what happens when you try those?

---

### Post by Perfect Storm on 2004-11-20
Not a thing. No icons, no indication of a shortcut. None, nada, zip, zero :|
 It's empty.
 
 I did tried with a newer version of gDesklets but with the same result.

---

### Post by Rancoras on 2004-11-20
The first time you run starterbar it has a single launcher for the home folder I believe.  Is that the only one you see?  Maybe a screenshot will help.

---

### Post by Perfect Storm on 2004-11-22
Here it is. I attached it to this post. (935 kb). Only a black dot is shown when I starting it.

---

### Post by Rancoras on 2004-11-22
Well that has me completely stumped.  Sorry I can't help.  :?

---

### Post by Perfect Storm on 2004-11-22
okay, no problem. Thanks for the time you used on my problem :)

---

### Post by Tsjoklat on 2004-11-22
I had the same problem and I downgraded gdesklets to gdesklets_0.26.2-5ubuntu1_i386.deb and that solved the problems. I did not downgrade any other package such as the date .deb. I also, after downgrading, pinned gdesklet so that apt/synaptic would not upgrade it again. Hope this helps for you,

D

---

### Post by Perfect Storm on 2004-11-22
But I am using that version. Also tried the newest one from Hoary. Tried with a new installation of Ubuntu, but none helps :/

---

### Post by Joo-Hyun Kim on 2005-01-25
Sorry, but I just had to bump this old thread.

I get exact same problem like the thread starter.

I have one small dot, and that's it, and I can't add anything to the starterbar.

Does anyone have solution for this?

Again, I'm sorry for bumping the old thread, but since there is no solution I thought it was better to resurrect it rather than making a new thread.

---

### Post by bobmitch on 2005-04-03
Another bump from me - I have also rolled my own version of 0.34 (the latest from cvs) and this has the same issue.

---

### Post by eldados on 2005-04-05
same problem here after the last upgrade... I miss my gdesklets :(
any ideas?

---

### Post by Leif on 2005-04-05
Can't add anything either, thru menu or drag and drop.

---

### Post by vishna on 2005-04-07
same probleme here  :neutral: 

i wish i knew why it does not want to work, anybody knows :???:

---

### Post by risager on 2005-04-07
I have the same problem also. 

[QUOTE=vishna]i wish i knew why it does not want to work, anybody knows :???:[/QUOTE]

Well after searching a bit in the gdesklets forum the following could be the reason: python-xdg recently changed it's API and python-xdg was recently upgraded on Ubuntu Hoary (March 23th on my laptop). This upgrade coincided with the time my starterbar stopped working.

Some people on the [gdesklets forum](http://gnomesupport.org/forums/viewtopic.php?t=9241&highlight=starterbar)  had success downgrading python-xdg but I'm not sure what that would break on Hoary.

---

### Post by crane on 2005-04-09
I ran into this problem too. I am running gdesklets in warty, When I added new launcher I got nothing. Then I right clicked on desklet and selected restart desklet and boom it appeared with the icons/launcher I added.

---

### Post by MetalMusicAddict on 2005-04-09
[QUOTE=crane]I ran into this problem too. I am running gdesklets in warty, When I added new launcher I got nothing. Then I right clicked on desklet and selected restart desklet and boom it appeared with the icons/launcher I added.[/QUOTE]
That works for Warty only. ;)

---

### Post by tigger on 2005-04-10
There is a new version of StarterBar available! You can download it from [here]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=210"), it comes with PyXDG 0.8, so the problem with the newer PyXDG is 'solved'! It at least works here :D


Edit: some install notes:
close gDesklets first (don't know if it is necessary)
After downloading it to [path] (by example: ~/Desktop):
 ```
cd ~/Desktop
tar zxf starterbar-desklet-0.31.3.tar.gz
cd starterbar-desklet-0.31.3.tar.gz
python Install*.bin
```

And then you can start gDesklets again and use the StarterBar

---

### Post by risager on 2005-04-11
Sorry for stating the obvious but 
 ```
cd ~/Desktop
tar zxf starterbar-desklet-0.31.3.tar.gz
cd starterbar-desklet-0.31.3
python Install*.bin
```
should be the right thing

---

### Post by shakin on 2005-04-19
I actually found this thread on Google while searching for more gDesklets to install, but luckily enough I happened to fix the starter bar problem just this morning.

It's a permissions problem. I chmodded /usr/share/gdesklets and /usr/lib/gdesklets to 777 and now it works.

---

