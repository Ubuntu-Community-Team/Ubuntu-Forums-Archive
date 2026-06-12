---
title: "Command line download tool that can handle php redirection?"
date: 2008-03-19
forum: General Help
---

### Post by chochem on 2008-03-19
As the title says I'm looking for a command line download tool that will be able to deal with php redirects, such as '.../download1.php?id=33038' - or just a way of setting up a script to easily figure out what the proper file url is so it can be handed to wget. Googling hasn't helped me so far.... :(

(and if there's any chance of javascript too, that would be cool :) )

EDIT: I tried some of the terminal based browsers (lynx, links, etc.) and they work very well at finding the file. Only problem is they present me with the option to download or display where I'd like automatic download with no user interaction...

---

### Post by chochem on 2008-04-16
I guess I found out that wget and most others can do this... The only problem is that the file gets assigned the name of the original link (e.g. a php id like '1286919') and I have to use the -O argument to assign a semi-useful name. Still involves a loss of information, though. Really no suggestions?

---

