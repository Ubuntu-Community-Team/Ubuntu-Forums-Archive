---
title: "i screwed up....please help!"
date: 2007-05-31
forum: General Help
---

### Post by molsen on 2007-05-31
i just recently installed xubuntu 7.04 on my laptop.  this is my first linux system ever.  i was trying to figure out how to get permission to edit my xorg.conf file so i edited my home directory to /root.  that was a bad idea and now the only way i can log in is under the terminal....any other login attempt gives me an error message...basically i shouldn't have changed my home directory from what it was.  how can i fix my home directory back to /home/Matt in the terminal????

also, i can boot via my install CD and gain some access to files on my disk, can i fix this that way?

please help for a total noob!

---

### Post by g8m on 2007-05-31
yes.

Boot live cd.
open terminal
create mointpoint
  mkdir mp
  mount /dev/sda mp 
  cd mp
 
rename/move/copy your directory. perhaps using sudo
   mv or cp directory.

search for the correct syntax, 'm just sketching the scenario

---

### Post by Bigdog60 on 2007-05-31
I would just reinstall it dude.

---

### Post by molsen on 2007-05-31
hmm, well i'm a complete noob with this.  i dont have any clue with the syntax.  i haven't even used the terminal yet.... can you direct me towards the proper syntax or something more specific?  sorry and thanks..

---

### Post by molsen on 2007-05-31
> **Bigdog60 said:**
> I would just reinstall it dude.

yea, well this is an option.  i havent done much customization of the interface or installing new programs except a firewall....so i won't lose much by reinstalling.  but if i could fix it easily, i'd prefer that route

---

### Post by Bigdog60 on 2007-05-31
Dude it would just be easiest to reinstall because you are going to spend hours to fix that problem there is something wrong with the drivers or operating system just reinstall it.

---

### Post by JSThePatriot on 2007-05-31
@Bigdog60

Some people dont like the idea of re-installing a complete operating system even if in your mind it would be the easiest.

@molsen

How did you first "edit" your home file? I am sure we can figure out a quick and simple way to fix it from a terminal session.

JS

---

### Post by molsen on 2007-05-31
i appreciate the help.  i tried a couple different things, including

sudo chown -R matt:matt /home/matt

that didn't do it either

i just reinstalled.  thanks anyways

---

