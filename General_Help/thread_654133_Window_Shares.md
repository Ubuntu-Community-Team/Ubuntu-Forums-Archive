---
title: "Window Shares"
date: 2007-12-30
forum: General Help
---

### Post by fwilliams on 2007-12-30
Previously to 7.10 install, I was able to mount Window Shares with Connect to Server.  Now it just keeps asking me to login.  Another person upgraded from 7.04 and does not have the same problem.  He was also able to connect to Window Shares from the 7.10 LiveCD after he set up the network manually.  It seems that some necessary files are being removed that are on the LiveCD during install.  After the install I have network connectivity, but no ability to connect to Window Shares.

Any ideas of what I need to install after I complete the install so I can mount Window Shares?

---

### Post by fwilliams on 2007-12-31
It turned out the machine name I was using caused the issue.  I saw that the machine name for the liveCD was only 6 characters long.  Previously my machine name was 14 characters, but I changed it to 19 characters and that is what caused the issue.

Our Windows Shares are being served by an netapp appliance.

---

### Post by HermanAB on 2007-12-31
The maximum length for a Windows workgroup or machine name is 15 characters.

Cheers,

Herman

---

### Post by fwilliams on 2007-12-31
it was the name of my Ubuntu box that was to long

---

