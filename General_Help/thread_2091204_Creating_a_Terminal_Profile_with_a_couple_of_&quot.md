---
title: "Creating a Terminal Profile with a couple of &quot;Starting&quot; Commands"
date: 2012-12-04
forum: General Help
---

### Post by neopiper on 2012-12-04
Hello,

I'm trying to create a terminal profile in Ubuntu.  In order to be able to run some scripts from the program I'm using I usually have to:

1) Open terminal:
2) Type "source /opt/simulation/START.bashrc"
3) go to the folder  "cd /opt/simulation"

and then I can begin running my scripts... I'm trying to create a terminal profile that saves me some time by avoiding this...

So I open a terminal and go to "File"  "New Profile"

and in the command option I write the first one "source /opt/simulation/START.bashrc"  

but when I open the terminal I get the error message :

"There was an error creating the child process for this terminal"
"Failed to execute child process "source" (no such file or directory)"

Can anyone help me to set up this please?  I not only want the "Source" to be executed but the "cd" one too...

The idea is to open a terminal and it should open in my /opt/simulation  directory and it should've already "sourced" 

Thanks

---

### Post by Martom on 2012-12-04
You could just source a script from your .bashrc file. This file is sourced every time you open a terminal.

---

### Post by neopiper on 2012-12-04
Hi Martom..thanks for replying but can you please give me some more detail?  Not quite sure I know how to do that.

---

### Post by Martom on 2012-12-04
There should be a (hidden) file in your home directory called .bashrc. You can use this to set up command aliases and source stuff. This file is sourced every time you open a terminal and it's just a bash script, so you can use it to do whatever you want: echo something, source files and presumably, though I've never tried, cd to another directory.

---

### Post by neopiper on 2012-12-06
Thanks it worked

---

