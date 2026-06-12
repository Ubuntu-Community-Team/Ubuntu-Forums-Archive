---
title: "Update Manager acting Strangely"
date: 2014-05-08
forum: General Help
---

### Post by foberle on 2014-05-08
I'm using Ubuntu 64 bit 12.04.3 LTS. About a week or so ago, I noticed that when Update Manager runs (which I do pretty much every day) it no longer says "The package information was just updated." after I do the "Install Updates" - it now says "The package information was last updated # days ago." The # is now up to 7. This is even though I have successfully downloaded and updated a number of things over the past week.

Today, for the first time, I began seeing a warning icon at the upper right of the screen (the red triangle with the exclamation point in it); when I click on that it displays the message "The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking on this icon and selecting 'Check for updates' and check if some of the listed repositories fail."

When I do the "Check for updates" as it asks, the warning icon goes away for a bit, but soon returns. I couldn't see any message about any repositories failing.

So: I went to a terminal and ran "sudo apt-get update"; everything went as expected, but i got the following warnings at the end:

[FROM TERMINAL:]
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
END [FROM TERMINAL]

I did find a similarly named thread, but it didn't seem like the same symptoms, so I posted this separately.

So: what does this mean? and, more importantly, how do I fix this?

Thanks.

---

### Post by deadflowr on 2014-05-08
It means the package list needs to be fixed before it will install anything new.
whenever the package list is broken, during an update, the package list reverts to the old one, instead of bringing in a half-bake list. Which would cause even more problems.
Look over this thread on a solution of what to do
[http://ubuntuforums.org/showthread.php?t=1983220](http://ubuntuforums.org/showthread.php?t=1983220)

---

