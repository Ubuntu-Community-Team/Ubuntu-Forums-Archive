---
title: "Synaptic's Code::Blocks is version 13, Current Version is 16"
date: 2017-02-09
forum: General Help
---

### Post by coder252 on 2017-02-09
Today is February 9, 2017.
Synaptic's Code::Blocks is version 13.
The current stable version of Code::Blocks is 16.
Why is Synaptic so far behind?

---

### Post by QIII on 2017-02-09
Moved to General Help.

Code::Blocks is in the Universe repository, meaning that there is a volunteer who maintains the package.  If nobody is doing that or the MOTU (the person doing the maintenance) has stopped maintaining it, it may have fallen behind.

Canonical does not directly take responsibility for the contents of the repos outside of Main.

For Yakkety, you can go [here]("http://packages.ubuntu.com/yakkety/codeblocks") to get in touch with the maintainers.  It *looks* like version 16 is the one in that repo.  If you are using an older release of Ubuntu, it is possible you have an older version available in the repo because the repos are frozen at the time of an Ubuntu release and don't get software version updates unless there is a security update.

---

### Post by coder252 on 2017-02-09
If the Yakkety-Yak (Ubuntu 16.10) repositories have Code::Blocks version 16,  then maybe I need to update my Synaptic repositories which have Code::Blocks version 13.

History: Muon Package Manager updated my Kubuntu 14.04 to 16.04 mid-February, 2017.

So maybe my repositories are still those of 14.04.

There may be another issue: per comments at Source Forge,  the Code::Blocks .deb files provided by Source Forge cannot be used to install on Ubuntu because of some library conflict.

---

### Post by coder252 on 2017-02-09
The following commands provided me with an install of Code::Blocks version 16.01. However there is no g++ compiler, so I'm using an Intel c++ compiler. Probably the best solution is to do a fresh install of Ubuntu 16.04, or see if a rolling release distro like Manjaro or PCLinuxOS would avoid such problems.
URL of the following commands: 
[http://ubuntuhandbook.org/index.php/2016/05/install-codeblocks-ide-ubuntu-16-04/](http://ubuntuhandbook.org/index.php/2016/05/install-codeblocks-ide-ubuntu-16-04/)[B]
1.[/B] Add [Code::Blocks Stable PPA]("https://launchpad.net/%7Edamien-moore/+archive/ubuntu/codeblocks-stable"), so you can receive future software updates along with system updates using Software Updater. 

 Open terminal from Unity Dash or by pressing Ctrl+Alt+T combination key. When it opens, paste the command below and hit run:
 sudo add-apt-repository ppa:damien-moore/codeblocks-stable Type in password (no visual feedback) when it asks and hit Enter to add PPA.
 [[IMG]http://ubuntuhandbook.org/wp-content/uploads/2016/05/codeblocks-ppa-600x89.jpg[/IMG]]("http://ubuntuhandbook.org/wp-content/uploads/2016/05/codeblocks-ppa.jpg")
 **2.** If you have Synaptic Package Manager, you can now launch it, search for and install the IDE after clicking Refresh.
 [[IMG]http://ubuntuhandbook.org/wp-content/uploads/2016/05/install-codeblocks-600x346.jpg[/IMG]]("http://ubuntuhandbook.org/wp-content/uploads/2016/05/install-codeblocks.jpg")
 Or just run the commands below one by one to do update and install the software:
 sudo apt update

sudo apt install codeblocks You may need to log out and log in back after installation to make it available in Unity Dash/App Launcher.
 **3.** (Optional) To remove  Code::Blocks IDE, use Synaptic Package Manager or run the command below in terminal:
 sudo apt remove codeblocks && sudo apt autoremove And the PPA can be removed via **Software & Updates** utility -> Other Software tab.

---

