---
title: "Firefox (3.0b5) is totally messed up"
date: 2008-04-23
forum: General Help
---

### Post by Pinkbelly on 2008-04-23
Hello, 


Im currently using Ubuntu 8.04 AMD64 and for some reason Firefox is not working right.

Right clicking anywhere does not work, plus external windows (like uploading the picture to this thread, im on opera on WINE now) and the menu bar do not work. The little white box above the address bar is what appears after right clicking.

I tried completely uninstalling forefox and that did not work, plus I tried going back to Firefox 2 and I got the same result.

Any suggestions whould be great, im pulling my hair out here..

---

### Post by warp99 on 2008-04-23
The problem is in your local directory so removing and reinstalling Firefox only put you back in the same position as before. Please do the following:

Backup you bookmarks using the export feature or just copy the file from ~/.mozilla/firefox/*/bookmarks.html, then delete the local directory:
```
rm -rf ~/.mozilla
```
Firefox will generate a new directory with a default user setting. You will have to reinstall any extensions, import you bookmarks, and redo any entries you may have made in the about:config dialog.

---

### Post by Pinkbelly on 2008-04-23
Thank you so much, it's working perfectly now :).

---

