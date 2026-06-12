---
title: "One drive access in 21.10"
date: 2021-10-24
forum: General Help
---

### Post by hornetster on 2021-10-24
Recently installed 21.10, and added Google Drive and One Drive during the setup process.
Have been able to find where Google drive ends up (bookmark available in Files), but can't figure out how to get to One drive, can't seem to find a link.
Anyone?

---

### Post by ActionParsnip on 2021-10-25
I don't use onedrive but does this help
[https://gist.github.com/starlinq/0f98c6d9339497bb8ac42d67f66f60eb](https://gist.github.com/starlinq/0f98c6d9339497bb8ac42d67f66f60eb)

---

### Post by hornetster on 2021-10-25
Thanks for that, but this seems to be a new thing...
When setting up, it actually asks what clouds you would like to sign in to, and takes you through the procedure of connecting to Google/OneDrive/Dropbox etc.
I did this for Google Drive and OneDrive, and can access Google drive, but can't figure out where to access OneDrive...

Also available through Settongs>Online Accounts, but still can't find Onedrive..

---

### Post by ActionParsnip on 2021-10-25
If you run
```

mount

```
It may give clues. I don't know how Ubuntu uses OneDrive but it may leverage the mounting system in the OS..... maybe

---

### Post by itr2401 on 2022-07-14
> Also available through Settongs>Online Accounts, but still can't find Onedrive..

There are only 5 reliable ways to access OneDrive on Linux:

* Via the OneDrive Client for Linux - [https://github.com/abraunegg/onedrive](https://github.com/abraunegg/onedrive) - this 'syncs' your data, bi-directional operation, open source and free. Supports Personal, Business & SharePoint account types and Shared Folders. A Docker container is also available for all major architectures (x86_64, ARMHF, AARCH64)
* Via the 'onedriver' client - [https://github.com/jstaf/onedriver](https://github.com/jstaf/onedriver) - Native file system that only provides the OneDrive 'on-demand' functionality, open source and free. Supports Personal, Business account types. Currently does not support Shared Folders or SharePoint.
* Via 'rclone' - [https://rclone.org/](https://rclone.org/) - one way sync client, open source and free. Has limitations with SharePoint.
* Via non-free clients such as 'insync', 'ExpanDrive'
* Via the web browser of your choice

---

### Post by hornetster on 2022-07-15
Thanks for the response, but...
If it is offered as a selection when installing AND in the settings menu (online accounts), would think there should be something installed when selected??
Although, just checking again now (in 22.04), looks like the option has been removed, and only Microsoft thing now is Email...

---

