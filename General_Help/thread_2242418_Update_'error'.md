---
title: "Update 'error'"
date: 2014-09-01
forum: General Help
---

### Post by Inisfad on 2014-09-01
Distro is 12.04.  While I get updates every day, and update manager advises 'there are no new updates', as of yesterday I have the red triangle with the exclamation point on my screen.  When running this, I get the following error:

W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG B998019EC07BBEC4 Launchpad PPA for Philip Langdale, W:Failed to fetch [http://ppa.launchpad.net/atareao/indicators/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/atareao/indicators/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/atareao/indicators/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/atareao/indicators/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I believe that 'atareao' is the weather app, which I uninstalled via synaptic.  But I don't understand what the rest of this means.  Hopefully someone can give me some direction?  Thanks

---

### Post by yancek on 2014-09-01
That would mean that you have entries in your /etc/apt/sources.list file for those two ppa links which apparently no longer exist.  Comment them out by putting a hash mark (#) at the far left/beginning of each line and try again.

---

### Post by Inisfad on 2014-09-02
Thanks for the reply.  I ended up just uninstalling these PPA's through software sources, so all should be ok now.

---

