---
title: "[SOLVED] AutoPackage Coding Failure"
date: 2007-08-10
forum: General Help
---

### Post by Het Irv on 2007-08-10
I am trying to install an Autopackage of Thunder and Lightning 070710.  After downloading the package to desktop from the site I double click the package and a dialog box pops up with the message:

[INDENT][I]gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/I][/INDENT]

The coding it is trying to use is unicode (UTF-8 ).

---

### Post by Het Irv on 2007-08-10
Ahhhh...

I had to change the file permissions to allow it to be an executable.  After double clicking I pressed run and followed the Instructions in the terminal that appered.

---

### Post by Desiree on 2007-09-14
> **Het Irv said:**
> I am trying to install an Autopackage of Thunder and Lightning 070710.  After downloading the package to desktop from the site I double click the package and a dialog box pops up with the message:

[INDENT][I]gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/I][/INDENT]

The coding it is trying to use is unicode (UTF-8 ).

I've also gotten this same error, but for installing amsn.  This is my second time trying to install amsn this week, but the first time it worked flawlessly, (then I reinstalled ubuntu) and now I'm trying to get it again.  

I altered the permissions, as mentioned in this post (rather blindly) then followed along with terminal, but I end up getting this in a "Finished" window:

"Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.04 (apt-get) to install a package with similar name to 'tcl'. 

Error: Unable to prepare package AMSN MSN client."

Any suggestions?  I don't know why I've been having these troubles (among others) after reinstalling Ubuntu when it was flawless the first time (earlier this week).

Should I reinstall again?

:confused:

---

### Post by Desiree on 2007-09-15
[Solved]

I got amsn working by the Add/Remove application, which I'm sure must have been how I did it the first time.  I was mostly approaching it by downloading from the amsn page and then using Snyaptic Package Manager, which apparently I'm not yet sure when to use it or the Add/Remove feature.  I don't know if they are somewhat interchangeable, or completely different.  I'm sure that'll be figured out rather quickly though (I'm new).

Toodles.
:)

---

