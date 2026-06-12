---
title: "Copying Files via Shell Script - so slow!"
date: 2016-06-27
forum: General Help
---

### Post by jay30 on 2016-06-27
I recently installed rclone to allow me to copy files/pictures to my cloud accounts (Amazon, OneDrive).  It works very well.  I usually use it from the terminal command line to copy pictures to the cloud.  However, when I put the rclone command into a shell script (where there is nothing else) and schedule it via crontab then I begin to have troubles.  To rclone copy command is initiated ok at the appropriate time, however, it grinds my internet connection to a halt and although starts to copy up files to the cloud it does so at a painfully slow rate (perhaps taking 20x as much time).  Any suggestions/ideas?

---

### Post by DuckHook on 2016-06-28
Don't know how to help you here.

rclone is not in the repositories. A Google search shows that it is a standalone binary hosted on GitHub. You are clearly okay with the security implications of installing unvetted apps on your computer, but it means that there are likely few&#8213;if any&#8213;here who have experience with this app. Have you tried asking the developers for help? Is there a rclone help forum?

---

### Post by HermanAB on 2016-06-28
Can't you use rsync?  With rsync, you can set a bandwidth limit to avoid clogging up your network and it will only send changed blocks, so it is much faster the second time around.

---

