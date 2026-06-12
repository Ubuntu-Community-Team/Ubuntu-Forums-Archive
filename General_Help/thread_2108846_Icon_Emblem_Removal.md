---
title: "Icon Emblem Removal"
date: 2013-01-25
forum: General Help
---

### Post by matthornish on 2013-01-25
Hello, Everyone.

I had installed Insync in order to sync my files between Ubuntu 12.10 and Google Drive.  I have since switched to Dropbox as it has better Nautilus integration. 

My problem is that now I have 2 big green checkmark emblems on the icons in my synced folder.  One is for Dropbox, but the other is left over from when Insync was installed.

Can anyone tell me how to remove the emblems from the file icons?  I have searched in vain for a solution.

Thanks!

---

### Post by gifford on 2013-01-25
Good question! Don't have a simple answer other than to copy the contents of the folder to a new one, delete the old folder and then create a new Dropbox folder and copy back the contents. Maybe someone else has a better answer.

---

### Post by matthornish on 2013-01-25
Thanks for the suggestion.  Unfortunately the Insync icons are persistent and copy across folders, synced or not.  Wat I have been having to do is go a step further:
I aam opening the documents, then saving again in a new location.  Once I do that, I can delete the originals in the Dropbox folder and move the new ones in.  Seems to work that way, but what a pain in the butt!

Thanks for the quick advice!

---

### Post by tjconcept on 2013-07-08
Try the uninstall procedure from this blog post: [http://www.liberiangeek.net/2013/03/insyncgoogle-drive-client-for-linux-out-of-beta-for-windows-and-mac/](http://www.liberiangeek.net/2013/03/insyncgoogle-drive-client-for-linux-out-of-beta-for-windows-and-mac/)

Run the following command line: "sudo apt-get purge insync-beta-ubuntu && sudo apt-get autoremove"

It worked for me :-)

---

