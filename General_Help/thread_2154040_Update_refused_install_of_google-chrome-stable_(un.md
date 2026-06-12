---
title: "Update refused install of google-chrome-stable (untrusted)"
date: 2013-06-13
forum: General Help
---

### Post by Ace..... on 2013-06-13
[SIZE=3]**Update refused install of google-chrome-stable (untrusted)**[/SIZE]

> Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.

Details:
google-chrome-stable


**Here's the description of changes:**
> Changes for the versions:
Installed version: 27.0.1453.93-r200836
Available version: 27.0.1453.110-r202711

This update does not come from a source that supports changelogs.


[B]Normal update
[/B]
The update was part of today/yesterday security update, as this morning, the alert box was displayed on screen.
After discovering the prob with chrome, I checked the list; found and unticked the update for chrome.
This allowed all the other updates to install.
However, I'm left with Chrome awaiting installation.

Does anybody know what went wrong...... and how do i get around it?
:)

---

### Post by oldos2er on 2013-06-13
Run ```
wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -

sudo apt-get update

``` and it should now be authenticated.

---

### Post by Ace..... on 2013-06-13
Thanks Oldos2er

I copied and pasted line 1 to terminal
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -

```I entered my password before entering line 2:
```
sudo apt-get update

```
Terminal indicated the download done.

I rebooted, and discovered updates available, including google-chrome-stable
Clicking on install began the download (after entering my password).
No problems occurred. :)

I'm just wondering....
.... does ubuntu clean up its old files (made redundant thru updates)?

This has been quite a big download at 95Mb...... and we get updates every week.
Should I be doing some housekeeping?

---

### Post by oldos2er on 2013-06-13
To clear the cache of downloaded packages, you can delete them with ```
sudo apt-get clean
```

---

### Post by Ace..... on 2013-06-13
Thanks oldos2er.

I entered in terminal, the code:
```
sudo apt-get clean
```
After entering my password, NO feedback occurred.
Terminal re-set to the prompt.

Perhaps the delete action occurred, without feedback being provided.

If that is the case then fine - DOS never used to provide feedback ;)

---

### Post by vasa1 on 2013-06-13
> **Ace..... said:**
> **Update refused install of google-chrome-stable (untrusted)**
Does anybody know what went wrong...... and how do i get around it?

That seems to have been a bug which is now fixed: [https://code.google.com/p/chromium/issues/detail?id=249188](https://code.google.com/p/chromium/issues/detail?id=249188)

---

