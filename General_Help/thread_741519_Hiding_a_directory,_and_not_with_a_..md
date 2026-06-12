---
title: "Hiding a directory, and not with a ."
date: 2008-03-31
forum: General Help
---

### Post by #Reistlehr- on 2008-03-31
Does anyone know of a way, or kernel modules that can be used to hide directories?

And just as the title says, i dont want the simple . prefix. I dont use a GUI, so from the TTY's i dont want to see the directories. 

This is not a security thing, so please don't suggest chmodding the files either. Thanks!

---

### Post by chilinski on 2008-03-31
Okay, this may the be stupidest response you get, but don't you have to do an:

ls -a

to see hidden files and directories (on my Gutsy, I do)? So if I don't use the -a parameter, I never see them in console. 

And, of course, the question arises, if you hid them so you couldn't see them, how would you know they are there..especially if you forgot the name?

---

### Post by #Reistlehr- on 2008-04-01
Right. Well i was looking into it, and Gobo linux seems to use a custom comand to hide their directories, and then they just create links. Im going to look a little more into this.

---

### Post by jocko on 2008-04-01
To hide one or more files or directories within a directory, make a file named ".hidden" containing the names of the files and folders you wish to hide.

As an example, if you wish to hide two folders in your home directory: /home/yourname/secrets and /home/yourname/private, make the file /home/yourname/.hidden, and within it, put the names of the folders as separate lines:```

secrets
private
```

---

### Post by #Reistlehr- on 2008-04-02
Thanks for the reply, but im thinking on more of the FHS, adn not just the home director of a user.

---

### Post by jocko on 2008-04-02
It works anywhere, just put the .hidden file in the directory that contains the files or folders you wish to hide.
I'm sure it worked both in nautilus and terminal when I tried it yesterday, but by some reason it doesn't work in the terminal now, so maybe it's not good enough for you...

---

### Post by #Reistlehr- on 2008-04-02
yeah, but thats nautilus.what i meant to say was,  i dont use a gui, i only use the the virtual terminals, so this would be of no help. 

Thanks for the try!

---

