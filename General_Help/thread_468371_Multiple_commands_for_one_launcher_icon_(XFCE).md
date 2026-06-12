---
title: "Multiple commands for one launcher icon? (XFCE)"
date: 2007-06-08
forum: General Help
---

### Post by jrmclaugh on 2007-06-08
Not sure if it makes a difference what desktop I'm using, but under XFCE, I want to add a launcher for MATLAB.  It requires a license manager to be running, so I'd like to have the same launcher launch that first, and then launch MATLAB.

Is there an easy way to have it run both from the same icon?  Thanks.

- James

P.S.  Is the only difference between Xubuntu and Ubuntu that one runs XFCE and the other uses GNOME?  Just want to make sure if I say I'm running Xubuntu, that's correct, cus I installed Ubuntu, but changed to the XFCE desktop.  Thanks.

---

### Post by diatribe on 2007-06-08
you might be able to if you put program_name1 & ; program_name2 in the path for the executable, just seperate the two by a semicolon and include the & if the first doesnt run as a daemon.  I'm not sure this will work though.  And yes xubuntu is just ubuntu with xfce

---

### Post by x1a4 on 2007-06-08
Put the commands you want to run in a script in your ~/bin/ and execute the script from your launcher.  Or, create a single launcher on your panel, then r-click on the icon and select 'Properties' and add the second command.  This of course will require dual-action to get things up and running.  In some instances that's a good thing.  I have some things set up in this fashion on my system as well.  It's all a matter of personal preference.  There are many ways to get things done (a good thing).  You can customize your system any way you like.  

I love Linux.  Xfce rocks!

---

### Post by jrmclaugh on 2007-06-08
just doing "command1 & command2" works (thanks, heh), but i need it to wait before running command2.  only 15-20 seconds (long enough for the license server to start).  any way to do that?  Thanks again.

- James

---

### Post by akShane on 2007-11-04
try putting sleep 15 in there.

---

