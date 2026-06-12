---
title: "How do you set up an apt-server?"
date: 2007-05-22
forum: General Help
---

### Post by frup on 2007-05-22
Is there a way to set a system up where once one computer has been updated, all the other computers can use it to update from and then go to the repositories for the rest... obviously they are running the same version...

I.E I've just installed a game from the repositories and like it and my brother decides he wants to have it too, are we able to make it so that apt-get will check each others computers first for the same version as in the repositories?

---

### Post by MontanaMax on 2007-05-22
Here are howto's on several ways to work with local repositories that might help.

[http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror](http://popey.com/Creating_an_Ubuntu_repository_mirror_with_apt-mirror)

[https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository)

[https://help.ubuntu.com/community/Repositories/Personal](https://help.ubuntu.com/community/Repositories/Personal)

You might be able to use the local or personal repository modes to point to the directory on the other computer where the packages are first downloaded, but I'm not sure if that's a "good recommended solution" or not.

I do use a local repository to store packages and help with dependancy and migration issues, and have had good luck with it in the last 6-9 months of use.

Good luck!

---

