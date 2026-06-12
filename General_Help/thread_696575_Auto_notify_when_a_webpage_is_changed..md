---
title: "Auto notify when a webpage is changed."
date: 2008-02-14
forum: General Help
---

### Post by domherre on 2008-02-14
Im looking for a solution/program which can notify me when a webpage is changed (it has no rss feed). Something like check4change (firefox plugin). But I would prefer if it didnt require firefox to have the tabs up all the time.

---

### Post by redemption on 2008-02-14
You could write a script to wget the page to a directory, then run diff to compare it with a previously saved page (compare the downloaded file to the most recent old version).
Then if you like, dump the difference to a new html file. Use cron to run the script periodicall and sendmail to send you an email if there is a difference in the files (an update)

---

