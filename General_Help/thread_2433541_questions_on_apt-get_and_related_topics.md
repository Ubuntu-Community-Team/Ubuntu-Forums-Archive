---
title: "questions on apt-get and related topics"
date: 2019-12-20
forum: General Help
---

### Post by rich-morin on 2019-12-20
I'm building a VirtualBox VM based on Ubuntu, for use under Vagrant. Because I'm explicitly installing about 200 packages (and implicitly installing a few thousand more), I have no interest in answering configuration questions interactively. So, I have scripted the installation process using "apt-get install -y".

This works for almost every package, but there are several (e.g., chef, chef-zero, emacspeak, jack, kde, mailutils, nodm) which still want to ask questions about configuration settings. It seems to me that there should be a way (e.g., configuration file, environment variable) to specify these settings in advance. However, I haven't found any documentation on that possibility. Can anyone provide me with information and/or pointers on this?

More generally, I'd like to examine the APT-related files for these packages, but I'm not sure about the easiest way to do this. I've tried looking at pages such as "[https://launchpad.net/ubuntu/+source/nodm](https://launchpad.net/ubuntu/+source/nodm)" and "[https://code.launchpad.net/ubuntu/+source/nodm](https://code.launchpad.net/ubuntu/+source/nodm)", but they don't seem to lead to anything useful. What's the Golden Path for getting to these files?

-r

---

### Post by TheFu on 2019-12-20
For doing stuff like this, I use ansible.  If you are using chef, why not install the base chef as part of the image, then use chef to handle the rest?

There is away using an environment variable to tell dpkg only to install, but not configure any packages.  I've used it, but couldn't find it quickly. APT front-ends will pass that environment variable through to dpkg.

I've never used vagrant. Don't know what that does to this.

---

### Post by rich-morin on 2019-12-25
Here's a great HowTo on handling (eg, pre-setting) configuration parameters:

  Perform an unattended installation of a Debian package
  [http://www.microhowto.info/howto/perform_an_unattended_installation_of_a_debian_package.html](http://www.microhowto.info/howto/perform_an_unattended_installation_of_a_debian_package.html)

-r

---

