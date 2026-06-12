---
title: "Cant access my RAID after creating new user account (16.04 LTS)"
date: 2017-10-21
forum: General Help
---

### Post by sikxsevn on 2017-10-21
Okay, so I've been trying to google how to fix this for about 3 hours now, and no luck; I'm in over my head here. 

so I have a software RAID that I created a while back, and it worked fine until this morning after I made a user account on my computer for my wife. 
I created her account using the GUI and gave her admin access. Then I went to configure permissions on the RAID so she could access, and I did that by doing a command in terminal. I cant remember exactly what I did, but I'm pretty sure I stuffed something up. 

Now when I click on my raid I get an error message that I dont have permission to access it, but if I hit alt+F2 and type "gksu nautilus" to try and see what's going on as root, I dont even see the RAID show up at all. 

everything works just fine from the account I set up for my wife. 

as soon as I get this sorted out my next step is getting Minecraft set up in such a way that we can play it from either one of our accounts and not lose anything. 
I think there's a guide on these forums for that, I was looking at it earlier. I already created a group called family and added both my account and her account to it through terminal

---

### Post by efflandt on 2017-10-21
It would help to know what you did to try to determine how to fix it.

Look through your ~/.bash_history file to see exactly what you did if you did it in a terminal window or vt. In your file manager you might need to hit Ctrl-H if you do not see hidden files (beginning with dot). If you did it in a gui, not sure how you would find out what you did, unless you edited a file (like with gedit) and there is a backup showing what it was before you altered it.

---

