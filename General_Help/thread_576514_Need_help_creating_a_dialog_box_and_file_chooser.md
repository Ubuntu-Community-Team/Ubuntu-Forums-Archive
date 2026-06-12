---
title: "Need help creating a dialog box and file chooser"
date: 2007-10-15
forum: General Help
---

### Post by kseise on 2007-10-15
I AM NOT A PROGRAMMER
That being said, I am looking to create a dialog box to use as a custom launcher for Flightgear.  My idea is to create a dialog box that will take the list of installed aircraft using the "fgfs --show-aircraft" command and the airport codes found in the file apt.dat in the fgfs directory use GREP to locate the airport code, then lanuch flightgear with the commandline options typed in such as

fgfs --aircraft=XXXX --airport=YYYY

Can anybody guide me to create such a box?  Has this already been done?

---

### Post by erginemr on 2007-10-15
I am not very much into the detail of this but you may create dialog boxes from within the shell with the 'dialog' command. It may not have been installed by default, 'sudo aptitude install dialog' will do the trick.

Then all you need to do is to read its man page 'man dialog' thoroughly.

Here is its original definition:

Dialog: Displays user-friendly dialog boxes from shell scripts
This application provides a method of displaying several different types of
dialog boxes from shell scripts.  This allows a developer of a script to
interact with the user in a much friendlier manner. 
 
The following types of boxes are at your disposal: 
yes/no           Typical query style box with "Yes" and "No" answer buttons
menu             A scrolling list of menu choices with single entry selection
input            Query style box with text entry field
message          Similar to the yes/no box, but with only an "Ok" button
text             A scrollable text box that works like a simple file viewer
info             A message display that allows asynchronous script execution
checklist        Similar to the menu box, but allowing multiple selections
radiolist        Checklist style box allowing single selections
gauge            Typical "progress report" style box
tail             Allows viewing the end of files (tail) that auto updates
background tail  Similar to tail but runs in the background.

But you also need to develop a small shell script that will collect the information in the apt.dat file with GREP and will use dialog in the end.

---

### Post by cwaldbieser on 2007-10-15
> **kseise said:**
> I AM NOT A PROGRAMMER
That being said, I am looking to create a dialog box to use as a custom launcher for Flightgear.  My idea is to create a dialog box that will take the list of installed aircraft using the "fgfs --show-aircraft" command and the airport codes found in the file apt.dat in the fgfs directory use GREP to locate the airport code, then lanuch flightgear with the commandline options typed in such as

fgfs --aircraft=XXXX --airport=YYYY

Can anybody guide me to create such a box?  Has this already been done?

There are lots of options to do this.  I would use tcl/tk or zenity, but there are lots of GUI toolkits available.
I am not familiar with the Flightgear program or its config files, but I can help you with the technical side of what needs to be done.

You already seem to have an idea of the basic steps.  Can you give some more detail as to what you think the dialog should look like (e.g. should the controls be text-entries or drop-downs)?  Can you show what the relevant output of fgfs --show-aircraft looks like?

Have you ever written a shell script before?

---

