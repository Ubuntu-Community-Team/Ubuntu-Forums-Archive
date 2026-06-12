---
title: "How to run .run files?"
date: 2015-09-20
forum: General Help
---

### Post by Nixarter on 2015-09-20
(FWIW, I'm trying to install AMD graphics drivers so I can use Steam for Linux.)

So I went into preferences and set .run files to run as default.  I right-clicked the file to make it executable.  Then, when I double-click the file... it gives an error "You need to run this installer as the super-user."  OK.  Fine.  But there is no prompt for password!  it just offers up an OK button that immediately terminates itself.  -_-

So, I right-clicked on it to open as an admin.  put in my password... and an error comes up from a text editor that ways that the file is corrupt.  It is not corrupt.  I've downloaded it twice now.

I've opened up a terminal and tried "sudo filename.run" but I get errors.  how to run it in terminal?

Also, I would like to run .run files in gui mode by default, without it erroring out.  how do I do this?

Google searches seem to only point back to a video about how to install it, which is what lead me to this point anyway, so it's pointless.  It makes me think this might be an issue with the amd driver installer packages, vs anything else.

---

### Post by oldos2er on 2015-09-20
*.run files, like shell scripts, really are made to run in a terminal rather than a GUI (although there probably is a way to use a GUI for them, but offhand I don't know what that might be). 

Can you try running it in a terminal again and copy/pasting the output here so we can see the errors?

---

### Post by ajgreeny on 2015-09-20
You can often just drag /drop the .run file into a terminal window and it will run.  If it needs to run as root it will tell you, you can then just hit the **Up** cursor key to repeat the command then use **Home** key and add sudo to the beginning of the command.

---

### Post by Nixarter on 2015-09-20
thanks!!! I drag-n-dropped it.  it started, then said I needed to run it as superuser again.  So I did the same thing, but before hitting enter,, I arrowed to the beginning of the string it generated, and simply added sudo before it.  entered password, and I'm good to go.  ty!

---

