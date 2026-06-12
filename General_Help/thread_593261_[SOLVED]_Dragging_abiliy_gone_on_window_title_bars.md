---
title: "[SOLVED] Dragging abiliy gone on window title bars"
date: 2007-10-27
forum: General Help
---

### Post by marbig on 2007-10-27
I've been playing around with Compiz setting up a cube. Thinking I'm doing okay, I find that on open windows the title bars are locked up.
i.e. Cannot drag windows around the desktop and unable to close window in top right hand corner.
Any ideas please?

---

### Post by marbig on 2007-10-27
Found this post.>                                           [Reapman]("http://ubuntuforums.org/member.php?u=187807")                     [IMG]http://ubuntuforums.org/images/uf/statusicon/user_offline.gif[/IMG]                                                             
                                  First Cup of Ubuntu
                 [IMG]http://ubuntuforums.org/images/rank_1.png[/IMG]
                                                                                                                  Join Date: Nov 2006
                                            Beans: 9
                                                                            
                 
                                                                                                                                                               **Re: after installing compiz, i can't move windows around the screen**             
                                                                                 I think I might be able to help... basically to move them around I had to add the proper plugins to load:
1) Open up gconf-editor
2) Go apps / compiz / general / allscreens / options
3) modify the active_plugins, mine includes (in this order):
gconf
dbus
decoration
wobbly
fade
minimize
cube
rotate
zoom
scale
move (thats probably the one your missing)
resize
place
switcher
water
screenshot

and volia!  Hope that helps :smile:
But how to open up gconf-editor?

---

### Post by #Reistlehr- on 2007-10-27
in terminal type..

gconf-editor

:D

Note:: If the package isnt installed, sudo apt-get install gconf-editor i think

---

### Post by marbig on 2007-10-27
Thanks.

---

### Post by Presto123 on 2007-10-27
Actually, I am searching for this fix from before and what helped me was fixing the font size. I cannot remember what it was, but...if I find it I will come back with that. It was the easiest thing to do.

---

### Post by marbig on 2007-10-27
Solved. Went to System > Preferences > Appearance > Visual Effects and enabled the 'none' button. Then went into compiz and bit by bit added the effects I wanted. Thanks to all who tried to help.

---

