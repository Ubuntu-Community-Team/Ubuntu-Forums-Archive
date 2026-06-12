---
title: "Virtualbox access to folders"
date: 2007-03-13
forum: General Help
---

### Post by vav on 2007-03-13
I'm using XP on Virtualbox and love it so far... I can finally work on Ubuntu 100% at work! (I guess there's a contradiction there :P ) 

The problem I have is:
When I try to save a new document in M$ Word from XP into a location on my shared folder from Edgy, it returns an error with the permissions of the folder.
Now this folder that I've shared from Edgy is fully writable by me, so obviously virtualbox tries to pose as some other user while saving, giving the permissions error... what user is this?

I've symlinked from the shared folder so that all folders in Edgy are seen in Virtualbox. So changing permissions of all folders is not an option...

Thanks!

---

### Post by nalmeth on 2007-03-13
Read the help dialogue, I seem to remember that you have to add vboxuser to some group, that is the user you are referring to.

---

