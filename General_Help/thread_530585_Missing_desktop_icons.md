---
title: "Missing desktop icons"
date: 2007-08-20
forum: General Help
---

### Post by mindfields83 on 2007-08-20
Hi

I am a new feisty ubuntu user, I clicked on the firefox icon on the desktop and it turned into firefox.desktop. Same thing then happened to every other icon on my desktop, Now double-clicking the icons just bring up a text file.

Any ideas how i get my icons working

Cheers

---

### Post by fragos on 2007-08-20
Right click one of those icons and select Properties.  The Basic tab is where you select an icon by cliking the one n ext to "Name:".  Mime type: should be application/x-desktop.  Click the Launcher tab to insure the correct parameters are there.  name.desktop is the file name you'll see with the "ls" terminal command.

---

### Post by mindfields83 on 2007-08-20
Hi 

In mime type it says text/plain, how do I change it back to application/x-desktop.

Also I'm not sure what you mean by the launcher tab? 

Cheers

---

### Post by fragos on 2007-08-20
Since thw mime type was changed to text, there is no launcher tab in the properties view.  Lets try a little experiment.  Right click empty space on the desktop and select "Create Launcher.."  Leave the type as Application.  Set Name to "Epiphany" and Command to "epiphany %U".  Click OK.  Now click the resulting link and see what happens.

---

### Post by mindfields83 on 2007-08-21
Ok

Tried what you said and just end up with a epiphany.desktop text file on my desktop. Clicking on it just brings up a text file.

any ideas?

Cheers

---

