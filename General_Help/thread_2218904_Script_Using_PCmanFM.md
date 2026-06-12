---
title: "Script Using PCmanFM"
date: 2014-04-22
forum: General Help
---

### Post by richwein on 2014-04-22
I want to make a script using a file manager and have some problem.

I'm using pcmanfm in Lubuntu script, and pcmanfm is managing the desktop icons.  When I create a script I want to have the user choose some operation on the files displayed, then close the file manager window at which point my script would continue.

    # do some setup stuff
    pcmanfm
    wait
    # do some closing stuff

That script does not 'wait' if pcmanfm is managing the desktop.  However if I kill the pcmanfm process then it does work when I try it again, but the desktop icons disappear.  

I'm trying to understand what is happening.  I think the script launch of pcmanfm is not creating a new process when it is already running the desktop window, but just finds the existing process and send some sort of signal to open a new window.  

Maybe there is a better file manager to use, suggestions?  I would like the script to take a command line argument that opens a particular device and directory and then I want some way for my script to know when the user closes the file manager window.  I do not need any return of the files that the user touched.

Thanks

Rich

---

