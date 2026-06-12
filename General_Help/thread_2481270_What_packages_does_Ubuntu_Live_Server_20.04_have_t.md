---
title: "What packages does Ubuntu Live Server 20.04 have that Ubuntu Desktop 20.04 doesn't?"
date: 2022-11-23
forum: General Help
---

### Post by kwalt95 on 2022-11-23
I downloaded Ubuntu Live Server 20.04.5 as a base for a custom version of Ubuntu I'm making for fun. I chose the server version because I want to build my desktop similar to how Arch lets you build your own system. Because I'm using it as a desktop OS, I'd like to remove any packages the server version has that the desktop version doesn't. Could someone help me or at least point me in the right direction to where I can find these packages?

Thank you in advance.

---

### Post by oldfred on 2022-11-24
Did you get the tasksel screen that installs the server apps depending on what type of server you want?
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

You can download the .[.manifest]("http://cdimage.ubuntu.com/ubuntu-server/jammy/daily-preinstalled/current/jammy-preinstalled-server-riscv64+unmatched.manifest") files from the version of Ubuntu you are using and compare desktop to server.

---

### Post by grahammechanical on 2022-11-24
The Ubuntu 20.04 Desktop ISO installer offers a minimal installation that will give you a desktop + a web browser + basic utilities.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup](https://ubuntu.com/tutorials/install-ubuntu-desktop#5-installation-setup)

"Ubuntu for Humans" has been the development philosophy from the beginning.

P.S. We also get something that we do not get in a Server edition. We get a Desktop Environment and a Graphical User Interface. Be careful when removing server stuff. Do not remove the ability to connect to the Internet.

Regards

---

### Post by ian-weisser on 2022-11-24
Let's find the exact list of packages for fun:

First, browse [http://cdimages.ubuntu.com](http://cdimages.ubuntu.com) until we find matching .manifest files for the same release of Desktop and Server.

Second, let's download those. I'll use Pi images because they are easy to find.

```

wget -q -O desktop http://cdimage.ubuntu.com/ubuntu/releases/jammy/release/ubuntu-22.04.1-preinstalled-desktop-arm64+raspi.manifest
wget -q -O server http://cdimage.ubuntu.com/ubuntu/releases/jammy/release/ubuntu-22.04.1-preinstalled-server-arm64+raspi.manifest

```

Now let's simply run a diff on both files, and keep the ones on server only (prepended by diff to have a '<')

```

diff server desktop | grep '<'

```

This gives us a list of 82 packages. A couple might be Pi-specific, so your mileage may vary.

Browsing the list shows us a lot of the expected suspects: byobu, cloud-init, curl, git, htop, openssh-server, openssh-sftp-server, overlayroot, screen, ssh-import-id, tmux, and vim. And a bunch of their libraries and dependencies.

Also there is the metapackage ubuntu-server, which includes most of those applications.

So a SHORT answer is to uninstall the ubuntu-server metapackage, openssh-server, and openssh-sftp-server. That will get you 90% of the way to a non-server system and will leave no forgotten services listening (Don't trust a random internet post: Check that for yourself using "ss")

The longer answer is the complete list of about 80 packages.

---

