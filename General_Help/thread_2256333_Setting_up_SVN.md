---
title: "Setting up SVN"
date: 2014-12-11
forum: General Help
---

### Post by Maheriano on 2014-12-11
I set up SVN on my server and was able to checkout the project, then successfully add and commit all my files for the project.
Since I'm recovering from a crash, I then copied all the files from the previous SVN install into the new install and retested the commit. I can successfully see all the previous commits and associated messages in SVN Workbench's log history but my command line commits don't work any more.

I created a test directory and tried to check the project out again but this time it checked out everything including all the branches, tags and every previous tag version I had in there, it would have taken days to check all that out. It appears as if copying the files from the old install changed a setting to point the project to the wrong place and now it's checking out the base folder instead of just the project.

Previous to crash my SVN folder setup was svn/web/trunk/portal/website (I'm not sure what the root directory was)
Now after the reinstall my SVN folder sites at /home/svn/web/trunk/portal/website
I'm not sure what I was supposed to use when creating the project with svnadmin but I created it on the website folder. Should it have been on the web folder? Is that the problem?

I copied all the old files into the website/db folder which is what made all the old commits show up in SVN Workbench which is great. However that's when the checkout started pulling every folder instead of just the project. I can access and checkout fine, I just don't know how to check out only my project.

---

