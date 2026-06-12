---
title: "Applications, Manual Style"
date: 2004-12-15
forum: General Help
---

### Post by ThePrawn on 2004-12-15
For applications not installed via apt-get, e.g. simple tar.gz packages, how does one go about making these applications available at the command line (e.g. simply type the application name, rather than navigate to the directory) ?  I know how to do it by creating an alias, but that only works if first open the shell -- which doesn't do much good if I want to simply key in the app name in, say, a Mini-Command module.

I'm sure it's possible, likely just a text file that needs to be edited, but I don't know which file that would be . . .

Also, is /usr/bin the optimal place to "install" apps?

Thanks.

---

### Post by az on 2004-12-15
Usually you put things which are not under the control of the package manager in /usr/local

Just add the thing to your path or just use the full name
Ex:
/home/slartibartfast/firefox/firefox

I would not make a symlink to /usr/bin just so that I can type the command in on a command line.

If you are going to install a precompiled binary of something, you are best to install it in your home directory and never run it as root.  This is not Windows...

---

### Post by ThePrawn on 2004-12-15
Bear with me, here :-)
What do you mean by "Add the thing to your path" ?

I know how to use the full file name, but the whole point was that I really don't want to have to.  Applications installed with apt-get can be executed with a single command at the command line (or in a launcher, etc.) -- how does one achieve this manually?

Thanks...

---

### Post by ThePrawn on 2004-12-15
Ok, for what it's work, I've got it behaving the way I want, now.  My understanding of paths was a bit limited--but is expanding.  If anyone else is ever curious . . .

First, I created a directory in my profile to put links (So I don't have to go in as root, azz :-).  My first mistake, which lead to my last (inept) post was that I'd only added it to the path in .bash_profile. So I could launch the apps linked in my ~/bin but couldn't use them from the gui.  I then added the path export/addition to .gnomerc -- so now, I can call the apps from the command line and/or the gui (assuming I'm in gnome).

I suspect there are similar config files for different windows managers -- question: is there a single file I can add a path to that will be shared with everybody?

---

### Post by jdong on 2004-12-15
**NEVER EVER** manually install into **/usr/bin!!**. Use **/usr/local/bin**. Don' t pollute APT's domain.

---

### Post by ThePrawn on 2004-12-15
They're installed in ~/bin . . .

---

### Post by jdong on 2004-12-15
If you put them in ~/bin, then it's best if only that user can access the program.

If you want multiple users to use the program, try **/usr/local/bin** or **/opt**.


/usr/local/bin is already in the path. /opt is more for storing the bulk of the program's data, then symlinking the main executable (or a launcher for it) into /usr/local/bin.

If you want to add a new environment variable, use **/etc/environment**.

---

