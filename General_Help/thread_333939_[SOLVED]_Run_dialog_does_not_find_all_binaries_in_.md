---
title: "[SOLVED] Run dialog does not find all binaries in PATH"
date: 2007-01-08
forum: General Help
---

### Post by olejorgen on 2007-01-08
I guess the title says it all..

When I try to run my warcrat3 startup script from the terminal it works, but when I use "run application" (ALT + F2) it complains: "Could not open location 'file:///warcraft3'" 

Strange thing is that this has worked before. They haven't changed run application to search in some obscure path I hope?

---

### Post by olejorgen on 2007-01-18
bump :P it's still annoying

---

### Post by highneko on 2007-01-18
Enter the full path in your script? Do you have a folder "/warcraft3"? You can check by typing in a terminal "/warcraft3" and pressing enter. Make sure to use quotes. If you need your home directory use "$HOME", not "~". The tilde doesn't expand in quotes.

---

### Post by olejorgen on 2007-01-18
The error is not in the script. The run dialog does not find the script, allthough the script is located in my ~/bin folder which is included in my PATH.

This is the content of my script:

```

#/bin/bash

wine /home/ole/games/wingames/Warcraft\ III/Frozen\ Throne.exe -opengl

```

PS: Thanks anyway :P

---

### Post by taurus on 2007-01-18
Try to put a ! after the # on the first line.

```
#!/bin/bash
```

---

### Post by highneko on 2007-01-18
Lol. That's why people should show some of the script. This could have been solved your first post! 

Why all the escapes? Try this instead:

```
#!/bin/bash

wine "$HOME/games/wingames/Warcraft III/Frozen Throne.exe" -opengl
```

---

### Post by olejorgen on 2007-01-18
Well, that's all good, but it's not the problem. As I've said the script **does** work when run from the command line. (Kinda strange though considering the ! was missing)

Yes, I did edit the script:

```

#!/bin/bash

wine "/home/ole/games/wingames/Warcraft III/Frozen Throne.exe" -opengl

```

---

### Post by olejorgen on 2007-01-18
When I do sudo cp ~/bin/warcraft3 /usr/local/bin it works

---

### Post by chavo on 2007-01-18
This is because Gnome or KDE is not sourcing your .bashrc on login and you are adding ~/bin to your path in your .bashrc. The terminal sees this because it is sourcing that file on startup.

This is what I have done to fix that problem here. It may not be the correct wayof doing things but it works.

I just added a couple of lines in /etc/profile to source your .bashrc wen you login.
Find this part in /etc/profile
```
  
  if [ -f /etc/bash.bashrc ]; then
        . /etc/bash.bashrc
    fi

```
Now add these lines right below it
```


    if [ -f $HOME/.bashrc ]; then
        . $HOME/.bashrc
    fi


```

You'll have to log out and back in for this to work.

---

### Post by olejorgen on 2007-01-19
Thanks! Kinda strange that they changed it though. Oo

---

