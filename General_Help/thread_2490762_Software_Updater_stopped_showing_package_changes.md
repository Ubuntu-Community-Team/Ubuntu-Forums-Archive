---
title: "Software Updater stopped showing package changes"
date: 2023-09-14
forum: General Help
---

### Post by jetlag55 on 2023-09-14
Hello all-

About a month ago my Ubuntu 20.04.6 desktop stopped showing the changes for all proposed updates.  Software Updater still works and I am able to download and install the updates and keep my machine up-to-date.  However, if I'm curious and want to view the changes to the packages, I now receive the messge, "Failed to download the list of changes. Please check your internet connection."  In the past, I was always able to peruse the short summary of each update's changes before approving its installation.  I've tried switching download servers and also installed the package **apt-listchanges** as suggested in a thread from 2011.  Neither solved the issue.  Does anyone have an idea what might have happened here and how I can restore the ability to view information about proposed updates?

---

### Post by MAFoElffen on 2023-09-14
Just something to try, that made it do this in releases from the past...

Open the "Software & Updates" application. In the "Ubuntu Software" tab, the section that says "Download From:", click on the dialog box and select "Main Server".

See if this corrects your problem.

---

### Post by ian-weisser on 2023-09-15
Check your logs around the time of a failure message.

---

### Post by jetlag55 on 2023-09-16
Thanks for the responses guys.  Apologies for the delay but I had to wait for the next update in order to evaluate MAFoElffen's suggestion.  Changing the download server to "Main Server" hasn't fixed the issue and I don't see any failure messages in the logs that might help troublehoot.  Any other ideas?

---

