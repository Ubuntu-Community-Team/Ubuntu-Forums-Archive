---
title: "What is the better way to compare and contrast one's system with a fresh system?"
date: 2013-09-24
forum: General Help
---

### Post by wolterh on 2013-09-24
So we all know that when a system (OS) gets out of control, the solution with less thought involved is to reinstall the system. However, this might not be favorable when the user has installed lots of software, changed some configurations, etc., for all this changes would be lost (unless the user keeps a separate partition for the /usr/local/ directory; in my case I wasn't wise enough to do this back when I was partitioning my HD).

Now, I want to know if there is a way I can find all the differences between my current install and a clean Ubuntu 13.04. What is the simplest way to do this?

I ask this because I have found my system affected by a lot of uncommon bugs, which I think wouldn't be present in a clean install. I have reported them but since they're not in the developers' first interest, they have been somewhat forgotten.

---

### Post by oldfred on 2013-09-27
If you have 10 or 20GB on your hard drive, just install another copy. You can copy your /home settings over. If data is in separate /home you can mount it. Since version is same you should not have any issues of sharing /home that is otherwise not recommended. Upgrading existing /home is ok, but sharing with an older or different version may create issues.

If you want to reinstall all software you can also do that.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by wolterh on 2013-09-28
And how would you go about comparing both efficiently?

---

