---
title: "Gnome WOn't Start"
date: 2006-08-08
forum: General Help
---

### Post by taekwondodogoof on 2006-08-08
Hi, I recently was updating, but had the power go off during the update. When I started ubuntu again, I could log in, then it loaded the orange screen and the mouse, but the actual desktop didn't come up. I have a modification so taht when I do ctrl-alt-delete the task manager thing for ubuntu comes up. Well, I can get it to come up fine, it's just I can't see my desktop. Can I repair Ubuntu somehow. I'm guessing it's GNOME, am I correct?

---

### Post by Dr. Nick on 2006-08-08
at the gdm logon screen change your session to failsafe xterm of terminal.

then run these commands to redo the update, this may solve it.

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get dist-upgrade


if you get a error telling you to run dpkg --a -configure or something then run it using sudo.

---

### Post by taekwondodogoof on 2006-08-08
Thanks for the quick reply!! I'll try it and get back to you =D!

---

### Post by taekwondodogoof on 2006-08-08
Thanks, you guys are awesome!!  IT WORKED!! I'm soo happy lol, I thought I would have to reinstall my Ubuntu or something! I just had to do the dkpg --a  -configure to get it to work! THanks again!

---

### Post by Dr. Nick on 2006-08-08
yeah, i figured that would work, glad it did.

dpkg is pretty smart that way, Ive accidently killed power to my computer when i had installs running in the bakcground and dpkg -a has helped me out several times

---

