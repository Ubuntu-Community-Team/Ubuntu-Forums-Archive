---
title: "save session of nautilus burn for burning later"
date: 2008-06-23
forum: General Help
---

### Post by notbugme on 2008-06-23
Hi, I want to know if there's a way to save the session of the nautilus burner (the burn:/// directory, not a external app) so I can add more files and burn them later.

There doesn't seem to be a way with the normal interface, but maybe there's a nautilus-script or something for this... does anyone knows about something like this?

Anyway, I'm going to try with other cd burners, which brings my second question, where can I find the list of the real path of the files in the burn:/// directory? I need this to pass the names to the other app... I don't want to waste all the time I've used going trought that ton of pictures...

I've found this file: ~/.nautilus/metafiles/burn:%2F%2F%2F.xml but it only contains the name of the files, not their real location.

Thanks for your help.

---

### Post by notbugme on 2008-06-23
Hey, I've managed to get the files path using that file (thanks to the camera since it doesn't use the same filename twice) just copied the xml somewhere else, removed the xml around the file names with some regex so the file looks like this:

dsc03919.jpg
dsc03920.jpg
dsc03922.jpg
dsc03936.jpg
dsc03948.jpg

then used this command line:
for i in `cat burn` ; do find ~/pictures -name $i >> burn-list.txt; done;

Hope it helps somebody in the same situation. I'll keep searching for a better burner...

---

