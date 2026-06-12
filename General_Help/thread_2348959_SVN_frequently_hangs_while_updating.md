---
title: "SVN frequently hangs while updating"
date: 2017-01-09
forum: General Help
---

### Post by eclay42 on 2017-01-09
I have an old Dell Optiplex 3010 with Ubuntu Mate 16.04 x86 installed that I'm using as a build server. When I first set it up SVN worked without any problems, but one day svn update began having frequent issues when updating. It worked fine on a Friday, and was having problems on Monday with no changes (at least that I'm aware of) being made to the server. I'm using svn 1.9.3 which is the latest version in the Ubuntu repository at the time of this post.

Other than being frequent (>75% of the time), these hangs seem to be random and occur at different places in the update action. Sometimes the update will complete without any issues, other times it will get through a bunch of files before getting stuck, in other cases it will hang immediately after issuing the update command. Some days it fails every time, but if I completely delete the local repository or folder I really need to update and then issue the update command, it is able to download missing files without any issues.

Once SVN hangs, it seems to be completely frozen and ignores ^C, and the only way to kill it is by sending SIGKILL to forcibly end the process. After doing so the local repository will be dirty and I need to run svn cleanup before trying again.

The repository itself looks to be fine, we have several other windows and linux boxes that frequently use the repository and they are all able to access the repository and update without any problems. For whatever reason this problem seems to be limited to this particular machine.

I've done some searching on google and found a handful of posts related to this issue, but none of them had any solutions to this problem and were all several years old. The version of SVN I'm using is dated March 14, 2016.

I suspect the root cause is likely a bug in SVN triggered by a network issue (the network around here can be pretty flaky at times).

Has anyone here on these forums seen this or similar issues and found a workaround? Thanks in advance for any help.

---

