---
title: "HELP!! I deleted /usr by accident"
date: 2007-04-29
forum: General Help
---

### Post by nSTER on 2007-04-29
Tried to delete a folder I moved in there and i managed to delete the whole directory.... Is there anyway to get i back? With out reinstalling...

---

### Post by floke on 2007-04-29
It should be in the trash. Since you would have had to have been root to do this it will be in root's trash. Open nautilus or whatever file manager you use as root, navigate to the root desktop files - its around there somewhere - and get it from the trash and move it back to where it was.

---

### Post by nSTER on 2007-04-29
I cant open trash i used sudo rm-r rar /usr/bin/

to delete it ad u can see i was trying to delete a folder rar in there that i put in.

Edit i cant even open nautilus

---

### Post by floke on 2007-04-29
Oh dear.
No idea on this.
Hope you get it fixed though.

---

### Post by nSTER on 2007-04-29
I had a naut open at the moment where Am i supposed to locate it? the its not in the trash in nster/.trash

---

### Post by m.musashi on 2007-04-29
Did you do this from the command line with rm? If so, I think you pretty much out of luck. You might be able to copy the /usr dir from a live CD but I doubt it would be an exact replacement.

It's a little late now, but it's best to not use rm around your root files.

EDIT: wow, I'm a slow typist. Okay, you use rm so I think you are out of luck.

---

### Post by nSTER on 2007-04-29
Wow i hate root so much right now..

---

### Post by floke on 2007-04-29
Put it down to experience.
Everyone buggers something up at some point.

---

### Post by m.musashi on 2007-04-29
> **Steve.K said:**
> Put it down to experience.
Everyone buggers something up at some point.

In my case about once a week. I bought myself a couple nice books to refer too. One, the Linux Phrasebook, is worth it's weight in gold. I am not a CLI guru by any means and now I can just look up anything I need.

---

### Post by nSTER on 2007-04-29
Im in live cd right now how do i move the folder into there using the terminal?

---

### Post by floke on 2007-04-29
You'll need to mount the partition that the USR stuff was on. Eg if its sda1 then mount it on the desktop - I think the path in the live CD is /home/ubuntu/Desktop (but could be wrong) - so

sudo mount /dev/sda1 /home/ubuntu/Desktop

then sudo nautilus - might need to do this twice to open two windows

navigate in the LiveCD filesystem to the usr stuff; navigate in the mounted filesystem to where it is going to go - and drag and drop from the former.

This is what I would try to do - I'm sure there's an easier way from the command line, but anyway...

---

### Post by BRAXS69 on 2007-04-29
how new is your installation?  because any packages or updates you have install would of had a very high chance of changing files in that directory.. :(  recopying the files from the CD may work otherwise. and it might still work even if so...

yeah the rm command is a little bit of a bugger when you make a mistake with it. might i make a suggestion for when you get your system back up and running, create a script that will move the files to the trash instead of  deleting them. it should be easy enough.

```

#!/bin/bash
mv $1 ~/.Trash/

```
call it something simple, it not annoying to type, like "mft" ("Move Folder Trash" makes sense) and make it executable then pop it into the "/bin" directory.
then whenever you wish to delete a folder just type "sudo mtt /folder" and things should be safe. :) 
you could also move it to the /tmp instead of the users trash so that when you restart your computer then it will delete it for good. just cange the last part "~/.Trash" to "/tmp/"

yeah everyone makes mistakes i do it a lot. :popcorn: but at least we never make the same twice...:)

---

