---
title: "Need help removing a web app"
date: 2015-03-30
forum: General Help
---

### Post by LieToPurify3 on 2015-03-30
I set Slack.com to be a web app that stays in my dock and will open as if it's an app. Now when I go to open chrome, it just opens that Slack web-app instead of opening chrome on it's own, and I can't get rid of it. Anyone know how to get rid of it or even how to uninstall chrome and all it's associated files so I can reinstall it clean?

---

### Post by bapoumba on 2015-03-31
May be check what the Chrome startup page is set to ? [https://support.google.com/chrome/answer/95314?hl=en](https://support.google.com/chrome/answer/95314?hl=en)
If not set to the Slack page, may be make a new user profile : [https://support.google.com/chrome/answer/142059?hl=en](https://support.google.com/chrome/answer/142059?hl=en)

---

### Post by LieToPurify3 on 2015-03-31
None of that worked. I can't even find an app called Chrome or Google Chrome when I search my computer. The only thing that comes up is my Slack web-app with the chrome icon. Thanks though.

---

### Post by LieToPurify3 on 2015-03-31
Fixed it, although my method may have been overkill. I ran sudo apt-get purge google-chrome-stable to remove the whole package. Then I deleted ~/.config/google-chrome. I probably could have gotten away with just deleting the ~/.config/google-chrome directory, but I had been so fed up with it that I just went for it all at once. Hope this helps someone else.

---

### Post by bapoumba on 2015-04-01
Well, glad to see you fixed it :)

---

