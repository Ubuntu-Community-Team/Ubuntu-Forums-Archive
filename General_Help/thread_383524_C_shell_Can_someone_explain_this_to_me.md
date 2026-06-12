---
title: "C shell? Can someone explain this to me?"
date: 2007-03-13
forum: General Help
---

### Post by Starks on 2007-03-13
From [http://www.esri.com/software/arcexplorer/download9.html](http://www.esri.com/software/arcexplorer/download9.html)


"Additional installation steps for UNIX and Linux
Setting up your account for UNIX and Linux

ESRI recommends that you execute ArcExplorer from a C shell. The following instructions are for a C shell environment setup.

To use ArcExplorer after installation, add the following lines to your .login or .cshrc file:
setenv AEJHOME /ArcExplorer
set path = ( $path $AEJHOME/bin )

To enable the changes, type:
% source <.login or .cshrc>

Editing the user $HOME/aimsclient.properties file

Copy the aimsclient.properties file from the $AEJHOME/Xenv directory to your user $HOME location. Update the value of the WebBrowser key in the aimsclient.properties file to point to the location of your default browser. Update the value of the AEJavaHelp key in the aimsclient.properties file to point to the location of the ArcExplorer online Help files."



Can anyone make sense of this?

---

### Post by mbeierl on 2007-03-13
There are multiple equivalents of the DOS cmd program on linux:

bash, ksh, csh, dash, zsh, ...

The c shell is csh, so they're just saying you need to use that shell as a wrapper to start their program.

As for the rest, I'm not sure what the program is (yet) so I don't know what impact it has.

---

### Post by gus sett on 2007-03-15
not sure which parts need clarification most, so pardon anything redundant.

the filenames proceeded with dots, .login and .cshrc are hidden files, so use -l
with ls when you want to see them listed to keep your bearing. They are
located in each user directory.  That explains   source .login   somewhat.
$HOME is an abbreviation for the combination string of directory names
leading to the directory containing aimsclient.properties on your system.
In their example, AEJHOME is set to point to /ArcExplorer.
They leave it to you to point WebBrowser and AEJavaHelp to the appropriate
locations on your system, and each should remain on its separate line in the
file.
set path =         is also an example of pointing, so edit as makes sense. ;) 


> 

"Additional installation steps for UNIX and Linux
Setting up your account for UNIX and Linux

ESRI recommends that you execute ArcExplorer from a C shell. The following instructions are for a C shell environment setup.

To use ArcExplorer after installation, add the following lines to your .login or .cshrc file:
setenv AEJHOME /ArcExplorer
set path = ( $path $AEJHOME/bin )

To enable the changes, type:
% source <.login or .cshrc>

Editing the user $HOME/aimsclient.properties file

Copy the aimsclient.properties file from the $AEJHOME/Xenv directory to your user $HOME location. Update the value of the WebBrowser key in the aimsclient.properties file to point to the location of your default browser. Update the value of the AEJavaHelp key in the aimsclient.properties file to point to the location of the ArcExplorer online Help files."



Can anyone make sense of this?

---

