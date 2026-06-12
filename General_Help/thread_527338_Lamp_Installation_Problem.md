---
title: "Lamp Installation Problem"
date: 2007-08-16
forum: General Help
---

### Post by zeeshan4it on 2007-08-16
Hello!

I have problem installing PHP5 on Ubuntu7.04 desktop feisty fawn. Apache was installed successfully but PHP5 gives dependencies error. Here is the error list:

# sudo apt-get install php5
OR
# sudo apt-get -f install php5

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libqt4-gui: Depends: libc6 (>= 2.6-1) but 2.5-0ubuntu14 is to be installed
              Depends: libfreetype6 (>= 2.3.5) but 2.2.1-5ubuntu1 is to be installed
              Depends: libgcc1 (>= 1:4.2-20070516) but 1:4.1.2-0ubuntu4 is to be installed
              Depends: libglib2.0-0 (>= 2.13.7) but 2.12.11-0ubuntu1 is to be installed
              Depends: libqt4-core (>= 4.3.1) but it is not going to be installed
              Depends: libstdc++6 (>= 4.2-20070516) but 4.1.2-0ubuntu4 is to be installed
              Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-13ubuntu4 is to be installed
  php5: Depends: libapache2-mod-php5 (>= 5.2.1-0ubuntu1.4) or
                 php5-cgi (>= 5.2.1-0ubuntu1.4)
        Depends: php5-common (>= 5.2.1-0ubuntu1.4)
  polymer: Depends: libqt3-mt (>= 3:3.3.4) but it is not going to be installed
  skype: Depends: libqt4-core (>= 4.2.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Any suggestion?

Best WIshes,

Zeeshan

---

### Post by igknighted on 2007-08-16
when you run "sudo apt-get -f install" you should not include php5 again, just the text that is in the quotes.

---

### Post by Bachstelze on 2007-08-16
This is an Ubuntu-related question, moved to a more relevant section.

---

