---
title: "Dropbox is asking for authentication : org.freedesktop.policykit.exec : /bin/sh"
date: 2019-10-15
forum: General Help
---

### Post by schworak on 2019-10-15
I upgraded some packages and shortly after rebooting I started getting a message asking me to give an app elevated rights. The app was trying to access /bin/sh and clicking details only told me it was org.freedesktop.policykit.exec which really wasn't helpful.

I found that this happened right after I logged in so I disabled all of the startup activities and rand them one at a time until I triggered the issue. It turned out to be dropbox causing the problem. But it had worked for a long time without this.

I uninstalled and reinstalled but the problem continued.

[COLOR=#242729][FONT=Arial]To fix this problem, here are the steps I took. These commands were executed from a terminal CTRL+ALT+T[/FONT][/COLOR]
```
rm -R ~/.dropbox*
sudo apt purge -y dropbox
sudo apt install -y dropbox python3-gpg

```[COLOR=#242729][FONT=Arial]

Then you can start dropbox again. It will require you log back into your dropbox account, but after that it should work correctly without prompting you when it starts.

I wanted to post this so others could find the information if they get stuck. I saw others while searching with this issue but no good answer to fully fix it.[/FONT][/COLOR]

---

