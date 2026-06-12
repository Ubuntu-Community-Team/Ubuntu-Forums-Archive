---
title: "Needing a GTK GUI for dpkg?"
date: 2005-10-27
forum: General Help
---

### Post by jamyskis on 2005-10-27
While I know that there is already a GUI for apt (Synaptic), I've been unable to find a suitable one that works with dpkg alone. So if your package is in your repository great, but if you've just downloaded a random Debian package (e.g. Skype) and you'd like to install it just by double clicking (and entering your password if need be), there seems to be no solution for people not comfortable with the command line.

Now, I've written a Bash script to create such a GUI with the aid of Zenity and the fundamentals are working - it recognises Debian packages, reports if the installation was successful or not, and asks the password if need be.

Before I add the finishing touches (debconf support etc.), would this project actually be of any use to anyone?

Edit: This really is in its early stages - it doesn't deal with dependencies either, so it's not going to arrive straight away.

---

### Post by ubuntumaneh on 2005-10-27
I think it is a very good idea. Now, something I think it would be good, if you allow me, it is to open a message if the installation failed due to lack of a program. In this message it could have the name of dependencies. I don't even are asking for automatically solve the dependencies, but at least warn people of it. I thing this is a good thing for newbies or for those who doesn't like to read logs.

---

### Post by jamyskis on 2005-10-27
[QUOTE=ubuntumaneh]I think it is a very good idea. Now, something I think it would be good, if you allow me, it is to open a message if the installation failed due to lack of a program. In this message it could have the name of dependencies. I don't even are asking for automatically solve the dependencies, but at least warn people of it. I thing this is a good thing for newbies or for those who doesn't like to read logs.[/QUOTE]

Already done :p It checks if the package is a Debian package (only by checking the file ending) but will reply with an appropriate message if the file in question could not be found (although theoretically the script would be opened by Gnome when the icon is clicked on so it would be impossible to have no file name - someone in the command line would just use dpkg). It then checks the package name (not the file name) and then checks this against the dpkg database to see if the package has been installed - this is the basis for a success/failure message.

What hasn't been done are the following:

* Internationalisation - so currently, if your dpkg returns messages in anything other than English - it won't work, and messages only come up in English. I need to fix it to cope with non-supported dpkg internationalisations.

* Dependencies - it doesn't state whether dependency problems have come up.

* If the package has already been installed, there is no option to install it although you could do this in Synaptic. Still, if the user gets this, it would be nice to have the option to uninstall.

---

### Post by jamyskis on 2005-10-28
OK, done. Here's the 0.01 version minus install script, localisations (this will literally only work in English for the moment) and the ability to resolve dependencies from the program itself. The code is also a complete mess but works.

The file is attached. Is there any chance of a section under "Third Party projects" for this?

---

### Post by JurB on 2005-10-28
There is [Debinstaller.]("http://www.gnomefiles.org/app.php?soft_id=601")

---

### Post by Corvillus on 2005-10-28
Also, gdeb is in the breezy repos.

---

### Post by jamyskis on 2005-10-29
[QUOTE=Corvillus]Also, gdeb is in the breezy repos.[/QUOTE]

**Dohhh!** I spent ages looking for something like that. Ah well, was good for BASH programming practice. Cheers anyhow :p

---

### Post by ubuntumaneh on 2005-10-29
Why would anyone bother creating another OS, there is Windows already? Why would anyone bother creating another distro, there is Debian already? Why would anyone bother creating another programming language, there is assembly already? Why would anyone bother creating new computers? Why would anyone bother creating new window managers? Just to stick with technology.

jamyskis got the idea. If you don't find something, you can create it. Even if it is there, he is learning. Good job.

---

