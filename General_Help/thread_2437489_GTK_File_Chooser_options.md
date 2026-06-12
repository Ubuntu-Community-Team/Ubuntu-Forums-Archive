---
title: "GTK File Chooser options"
date: 2020-02-24
forum: General Help
---

### Post by sevensixtwo on 2020-02-24
When I view my files in Nautilus, I can see the thumbnails of the files, or I have the option to only display file names.  When I'm using my browser to upload files to the internet, the gtk-file-chooser does not give me the options to view thumbnails, and instead if I want to see the images, I have to click on them one at a time in the gtk-file-chooser to get them to show up in the file previewer.  How can I change it so that I can see the thumbnails in the file chooser?

Example: [https://ibb.co/qs0bjWy](https://ibb.co/qs0bjWy)

---

### Post by Dennis N on 2020-02-24
The only options you can change for the file chooser are found in dconf-editor under:
**org > gtk > settings > file chooser**
There is no option to change display from the list mode to thumbnails. Take a look.

---

