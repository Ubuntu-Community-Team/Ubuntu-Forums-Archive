---
title: "Unable to install a .deb file On ubuntu 20.10"
date: 2020-10-29
forum: General Help
---

### Post by turkeybones11 on 2020-10-29
Hello, i am trying to install Chrome and zoom on Ubuntu Groovy Gorrila (20.10) Help?

---

### Post by howefield on 2020-10-29
Are you ok with using a terminal ?

Assuming that you have downloaded the deb to your Downloads folder, use the following command..

```
sudo apt install /home/USER/Downloads/google-chrome-stable_current_amd64.deb
```

Substitute USER with your actual username, and ensure that the deb package name matches the above, press enter and follow the prompts.

The Zoom .deb package can be installed in the same manner, obviously subbing the file name.

---

