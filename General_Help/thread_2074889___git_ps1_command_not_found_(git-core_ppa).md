---
title: "__git_ps1 command not found (git-core ppa)"
date: 2012-10-22
forum: General Help
---

### Post by mitch_feaster on 2012-10-22
I'm currently using the git-core ppa [1,2] to get the latest version of git. With the latest upgrade, however, I think a few things fell out of the package... Specifically PS1-related stuff has been has been split out from the other completion stuff into  contrib/completion/git-prompt.sh [3]. Downloading and manually source'ing [3] solves this problem.

I hit this same issue with arch [4] a while back.

Does anyone know how to bring this to the attention of the git-core ppa maintainers? If I don't have any luck I'll email them directly but would rather not for the sake of spamming.

[1] [https://launchpad.net/~git-core/+archive/ppa](https://launchpad.net/~git-core/+archive/ppa)
[2] [https://launchpad.net/~git-core](https://launchpad.net/~git-core)
[3] [https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh](https://github.com/git/git/blob/master/contrib/completion/git-prompt.sh)
[4] [https://bbs.archlinux.org/viewtopic.php?id=147462](https://bbs.archlinux.org/viewtopic.php?id=147462)

---

### Post by andersk on 2012-11-03
This is fixed in git 1.8.0-1.

---

