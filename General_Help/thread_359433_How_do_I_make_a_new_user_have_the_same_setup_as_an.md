---
title: "How do I make a new user have the same setup as an old user?"
date: 2007-02-12
forum: General Help
---

### Post by skenagle on 2007-02-12
I apologize if this is somewhere else on this board, i checked and couldnt seem to find anything.

I am trying to set up a new user so that when they log in, they log into XGL and start beryl with all the panel moifications i have made for MY own login.

The situation is, my friend keeps coming over here and she wants to play on my ubuntu.. (*IF you know what i mean..*) but she is nervous about messing up my settings.

So how can i make her a login so that she starts out with an exact copy of my setup?

When she is more comfortable with her settings, she will be able to change her backgrounds and stuff as she is ready.

Is there a way to do this?

Over time, I did alot of things to get beryl to run in xgl using an ATI card in ubuntu... and i cant remember what i did to set it all back up again manually for her.

Thank you so much.

---

### Post by Paerez on 2007-02-12
create a user for her in System->Administration->Users and Groups. Then open a terminal and copy your settings over to her user account.

Do this by running:

"gksudo nautilus --no-desktop"

twice.

Navigate one to her home and the other to your home. Then on your home press CTRL+H. This will show the hidden folders (they start with a dot). Then copy over a bunch of those folders. I suggest copying:

.beryl
.gconf
.gnome
.gnome2

---

### Post by aysiu on 2007-02-12
Let's say your username is *skenagle* and hers is *newuser*. After creating her account, you'd do this: ```
sudo cp -R /home/skenagle/ /home/newuser/
sudo chown -R newuser:newuser /home/newuser
``` At least I *think* that'd work. I'm not too sure about the slashes. Bottom line: copy everything from your home folder to her home folder and then make sure she owns everything in her home folder.

P.S. I've edited all that stuff about her being hot. We value our community as human beings, not as pieces of meat--even though I know you mean well and are saying these things in partial jest. We are trying to create a place that is equally welcoming to women and men.

---

### Post by skenagle on 2007-02-12
After copying the files over as you state using the command line "cp -R" commands.

When i log in as her i just get a blank screen (that pale salmon ubuntu color screen before it loads up the window manager from the login screen)

it just hangs there.

did I copy too much over maybe? is something conflicting?

---

### Post by aysiu on 2007-02-12
As I stated before, I may have messed up with the slashes. I thought what I specified would copy what's in your home directory to what's in her home directory, but it may have ended up as /home/newuser/skenagle instead of putting the contents of /home/skenagle inside of /home/newuser.

Does that make sense?

---

### Post by skenagle on 2007-02-12
yes i think i put my directory in hers, BUT i may have copied "skenagle" into ... /herhome/skenagle...

oops..

let me see what happens now...

thank you for your help.

---

### Post by aysiu on 2007-02-12
If that happened, it's not your oops but mine...

---

