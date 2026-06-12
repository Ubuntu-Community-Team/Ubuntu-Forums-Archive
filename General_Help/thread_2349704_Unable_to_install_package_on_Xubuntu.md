---
title: "Unable to install package on Xubuntu"
date: 2017-01-17
forum: General Help
---

### Post by peter1897 on 2017-01-17
I am trying to install slingshot launcher on Xubuntu - [https://launchpad.net/slingshot](https://launchpad.net/slingshot). I added the repository with this command: _sudo apt-add-repository ppa:elementary-os/daily_. Then run _sudo apt-get update_ and after that _sudo apt-get install slingshot-launcher_ but i got this:

```
root@osboxes:/home/osboxes# apt-get install slingshot-launcher
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 slingshot-launcher : Depends: libgranite3 (>= 0.2.0) but it is not going to be installed
                      Depends: libgtk-3-0 (>= 3.14.0) but 3.10.8-0ubuntu1.6 is to be installed
                      Depends: libplank0 (>= 0.10.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Then i run this _apt-get install libgranite3 && libgtk-3-0 && libplank0_ but i get this:

```
root@osboxes:/home/osboxes# apt-get install libgranite3 && libgtk-3-0 && libplank0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libgranite3 : Depends: libgtk-3-0 (>= 3.12) but 3.10.8-0ubuntu1.6 is to be installed
               Recommends: apport-hooks-elementary but it is not going to be installed
               Recommends: contractor but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

How to solve the problem with the dependencies?

---

### Post by TheFu on 2017-01-17
Dude - you are running a DAILY compile?  That isn't exactly safe.  Lots of issues.  They probably have an automatic nightly pull from the repo and automatic build. ZERO testing. ZERO package management checks.  Probably.  End-users shouldn't do that. It is meant for the developers on the team.  Developers often work from development versions of other libraries too. If they are smart, they are trying to match what the next release of their favorite distro will include.  That may not be Ubuntu 17.04. I didn't do any research to know.

Plus mixing repos from other distributions isn't exactly safe either.

Find their last stable release and try it. Hopefully, they put the effort into making the package dependencies correct. Hopefully.  If there are issues, find the project page and open an issue/bug.

---

### Post by peter1897 on 2017-01-17
Xubuntu is installed on virtual machine so safety is not a concern. Is it possible to install Slingshot manually from the .tgz file. I downloaded the .tgz file and in the INSTALL file there are these instructions for manual installation:

```
You can also compile Slingshot from source.
You need the following dependencies (on Ubuntu/Debian):
- cmake
- libclutter-1.0-dev
- libclutter-gtk-1.0-dev
- libgee-dev
- libgnome-menu-dev
- libgranite-dev
- libgtk-3-dev
- libunity-dev
- libwnck-3-dev
- libzeitgeist-dev
- pkg-config
- valac-0.16 | valac (>= 0.16)
then:
$ mkdir build
$ cd build/
$ cmake .. -DCMAKE_INSTALL_PREFIX=/usr
$ make
$ sudo make install
```

I tried to insall the dependencies but i get the same error for missing dependencies. 

I also tried to install Slingshot from another repository: _sudo apt-add-repository ppa:elementaryart/elementary-dev_ but it doesn't want to add the repository.

Why installing software in linux have to be such a pain!

---

### Post by TheFu on 2017-01-17
None of this help you.  

Going off the ranch, means you accept the difficulties.

[https://launchpad.net/slingshot](https://launchpad.net/slingshot) is their project page.  It says "designed for elementaryOS" there.
To report a bug: [https://bugs.launchpad.net/slingshot/+filebug/+login](https://bugs.launchpad.net/slingshot/+filebug/+login)  When the project team sees it, they should try to help and hopefully update their dependencies AND install instructions.  Or they will not respond and I'd assume it is dead. They were/are likely volunteers or only test on their favorite OS.

BTW, installing software created for Ubuntu onto Ubuntu installations using the Ubuntu repos is easy.  Your system probably has over 2500 packages installed as proof.  

If you think installing software is hard now, you should have been trying to do it in the 1990s before package managers existed.  We had to manually manage all dependencies. I was constantly breaking different software, but not completely because different versions of shared libraries CAN exist on the same machine. It is best to start with a specific set of base libraries and work our way up when building a distro, however.

---

### Post by peter1897 on 2017-01-17
Is it possible to export installed package along with its dependencies and settings as .deb file and use the .deb file to install this package later on another machine with Xubuntu or Ubuntu? Will it work if i want to install this .deb file on newer version of Xubuntu? For example, can i export Firefox?

---

### Post by TheFu on 2017-01-17
> **peter1897 said:**
> Is it possible to export installed package along with its dependencies and settings as .deb file and use the .deb file to install this package later on another machine with Xubuntu or Ubuntu? Will it work if i want to install this .deb file on newer version of Xubuntu? For example, can i export Firefox?

You probably want to look into "snaps" for something like this.
[https://www.ubuntu.com/desktop/snappy](https://www.ubuntu.com/desktop/snappy) - it ignores any system libraries and requires each application to bring all there dependencies. That impacts storage and RAM use. If it causes the system to swap, then it could impact total system performance as well.

Snap packages are mostly intended to be used for enterprise software to make all their dependencies (and security issues since they tend to use outdated libraries) go away.  When you are trying to sell $200K-$50M software, the last thing you want is for there to be install dependency issues.  I haven't done much research about snaps.  Don't know how well any GUI program would work, since they could implement them using Linux containers which would limit their interaction with any other programs on the platform, except through network interfaces. That would be by-design.
[http://snapcraft.io/docs/snaps/intro](http://snapcraft.io/docs/snaps/intro) - mentions "confined from the OS and other apps through security mechanisms" - that is often code for containers, as I suspected. In short, apache inside a snap - is a good thing.  A desktop application that manages launching of other desktop applications ... not so much.  But there is probably a way.  Snaps are relatively new and not meant for end-users to create.

---

### Post by ian-weisser on 2017-01-17
Not sure what you mean by 'exporting'.

If you mean: 'I want to send Sally a list of packages that are in the Ubuntu (and Xubuntu) repositories' you sure can. That's one purpose of packages, and it's a one-sentence email: "Dear Sally,please install the 'firefox' package".

However, I doubt that's what you mean.
If you mean: "I want to send Sally my customized Firefox application, including my customized 'firefox', 'libfire', 'libfox1', and 'libfox2' packages", you can do that. But you must include detailed install instructions for dpkg (not apt), or she won't know how to install it.

Most customizers create a PPA, and place the packages there. Sally adds the PPA to her /etc/apt/sources.list, adds your Key, then installs firefox from your PPA using apt. Building custom packages requires a bit of learning - it's complex.
On 16.04 and later, you can bundle the application and all dependencies [into a Snap package]("http://snapcraft.io/docs/build-snaps/"), which Sally can install easily. It's new and can be quite complex.

---

### Post by peter1897 on 2017-01-18
Why dependencies are such a big problem in linux? In Windows when installing program from .exe file in most of the cases you don't need to install dependencies, in some cases you may need to update the .net framework and install java, but this is rare.

In linux if i want to have a program for offline install i can download the .deb file of a program and i can copy the settings of the program which are located in the home folder in most cases but dependencies will be a program in most cases when i try to install the program on another machine.

For example, in the current case, if i try to install Slingshot i get error for missing dependencies and if i try to install the missing dependencies i get error again for other missing dependencies. Why it that?

---

### Post by ian-weisser on 2017-01-18
> **peter1897 said:**
> Why dependencies are such a big problem in linux?

Because you are looking at the problem from a Windows perspective.
Handling dependencies can be just as easy in Debian and Ubuntu...but requires different skills, and occasionally a bit of subtlety.

Your problem seems a classic version conflict. This happens when you install some non-Ubuntu software, or the wrong version of the software.
Disable the non-Ubuntu source, refresh your package database, delete packages from that source from your local cache (so they don't get reinstalled), and uninstall all packages from that source.
Those four steps will get apt functioning again. Then we can show you the easy way to install slingshot.

---

