---
title: "Installing Google Desktop Linux - Help?"
date: 2007-07-01
forum: General Help
---

### Post by Old Pink on 2007-07-01
Details: [http://groups.google.com/group/Google-Desktop-Linux-Something-Broken/browse_thread/thread/df21f6898e7f0ec2/e8f3bfe0bf8093c1#e8f3bfe0bf8093c1](http://groups.google.com/group/Google-Desktop-Linux-Something-Broken/browse_thread/thread/df21f6898e7f0ec2/e8f3bfe0bf8093c1#e8f3bfe0bf8093c1)

Basically, when installing, dpkg opens "google-desktop-" which then attaches to dpkg, and hangs, hangs hangs....

Then I kill "google-desktop-" and the thing goes nuts and won't install.

Bloody closed source

---

### Post by rfruth on 2007-07-01
Not sure what the solution is but when you find out let us know !  (troubleshooting link [http://desktop.google.com/support/linux/bin/answer.py?answer=63285&query=dpkg&topic=&type=]("http://desktop.google.com/support/linux/bin/answer.py?answer=63285&query=dpkg&topic=&type=");)

---

### Post by defishguy on 2007-07-01
[Google Feisty Repository]("http://www.google.com/linuxrepositories/ubuntu704.html")

Follow the instructions on the above webpage to add the official Google Feisty Repository and try installing from there.

Good luck!

---

### Post by Old Pink on 2007-07-01
defishguy, tried, it downloads the same .deb - read "Details"

To confirm, I have it installed via alien & RPM, just annoyed at the .deb

---

### Post by defishguy on 2007-07-02
If the rpm & alien combination is working for you then kudos.  If you're stilling having problems trying purging the apt cache.

In case you don't already know the command is:
> sudo apt-get clean

Glad to hear that it's at least working for you!

---

### Post by Old Pink on 2007-07-05
Progress.

Installing the deb, the following things happen:
[LIST=1]
[*]dpkg installation process waits on (waitpid) google-desktop-
[*]google-desktop- waits on pid -1 which doesn't exist
[*]Three "install_thunder" processes start and sleep, a fourth starts, runs, vanishes, starts, runs, vanishes
[*]Leaving this for hours does nothing.
[*]Kill alll "install_thunder" processes and the installation completes without error.[/LIST]What the **hell** is "install_thunder" ?!

---

### Post by defishguy on 2007-07-05
Beats me.  Install_drizzle would have made more sense.

---

### Post by jetpeach on 2007-08-07
hmm, "ps aux" doesn't show an "install_thunder" but i'm still hanging on "Setting up google-desktop-linux ..."
i tried installing using the DEB and from the google repositories. any more help?

---

