---
title: "TBird Doesn't see Profile Folder"
date: 2015-07-09
forum: General Help
---

### Post by Rick St. George on 2015-07-09
Just installed Xbuntu v14.04 LTS to HP Elitebook. Had copied .thunderbird folder over to home/user directory.

After installing Thunderbird, it apparently does not see it, as it wants to setup a new user.  I utilized this procedure before, but must  be doing something wrong. It worked with my Mozzila Firefox.

Any suggestions would be appreciated.

Rick

---

### Post by howefield on 2015-07-09
Try from a terminal using the command

```
thunderbird -P
```

Delete the profile already there if there is one (using the Don't Delete Files option), and then create a new profile navigating to the profile folder, eg for me it's.. /Data/.thunderbird/p6ixchl1.default

Then press the Start Thunderbird button.

---

### Post by oldfred on 2015-07-09
I always started both Thunderbird & Firefox so it creates its default profiles. 
Then I copy my old profile into the folder and edit profile.ini with my profile xxxx.default instead of the default just created.

---

### Post by Rick St. George on 2015-07-10
My apologies and my fault. When I looked at the source file I copied from, apparently I had already Zeroed it out for a new buyer of my old laptop. Therefore, it was ready for a new account.

Case Closed.

---

