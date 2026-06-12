---
title: "Setting a command line alias"
date: 2005-08-06
forum: General Help
---

### Post by eelozano on 2005-08-06
Hello, 

I installed the newest version of zsnes from source and I was wondering how I would get it to run like the older version in the repository.

Basically I want to know how to have it run when I type in 'zsnes' from the command line (like the old version).

On another somewhat related note I was wondering if you could tell me why when I type ( alias lls="ls -l" ) in the command line it only works until I restart the computer (at which time the alias is not longer there)

---

### Post by dave9191 on 2005-08-06
You want to make a symlink to the executable binary of the znes and put in your /bin dir or anyother dir in your path. 

Also the alias thing, it only works because you are only putting the command into memory. Once you restart, it loads the config files in, and if the alias isnt there, then it wont work. You need to put the alias into your .bashrc file for it to work in each shell every time. 

Dave

---

### Post by eelozano on 2005-08-06
Two things...

how do I make a symlink

and

where is the .bashrc file (the .bashrc file I'll probabally locate with a search, but if you could say for archival purposes [someone else might have the same problem])

---

### Post by eelozano on 2005-08-07
In case anybody was wondering...it is 

/etc/bash.bashrc

Just append your alias to the end of the file (I couldn't tell by reading the file, but a quick look at the ubuntu guide and I saw some alias examples).

I still do not know how to work with symlink yet.

It seems to be just a normal linking of files (ln link1 file1), however I don't know where the link needs to be (what directory)...I have a guess and I'm going to try it out :)

---

### Post by varunus on 2005-08-07
To make a symlink work, the format is:
```

ln -s filename_to_link_to link_name
```

For example, if you want to link zsnes:
```

ln -s location_of_zsnes /usr/bin/zsnes
```

Linking something to /usr/bin is like making a shortcut, and /usr/bin is autochecked for commands by the shell.

---

### Post by eelozano on 2005-08-07
Ahh, you beat me too it (I had just figured it out).  Now I'm just looking for where it dumped the zsnes file.

P.S. I am also at IU.

---

### Post by eelozano on 2005-08-07
One small correction

You need to be root.


So it will be
```

sudo ln -s location_of_zsnes /usr/bin/zsnes
```


Thank you very much for you help...I am very appreciative.

---

