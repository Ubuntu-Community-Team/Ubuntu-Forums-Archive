---
title: "Upgrade problem"
date: 2005-06-08
forum: General Help
---

### Post by granite230 on 2005-06-08
I recently installed a program called Gramofile. I need to record some sound on my Hoary system so I thought: lets try Gramofile.
But the program needed a few packages before I could run it... not sure which packages that were but I got them from debian.org/packages or something like that.
The program runs fine now, havent tested it yet but it runs.

The only problem is that whenever I try sudo apt-get upgrade (update works fine) I get this big list:

granite@granite:~ $ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  capplets: Depends: libesd0 (>= 0.2.29-1) or
                     libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  esound: Depends: libesd0 (>= 0.2.29-1) or
                   libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  evolution: Depends: libesd0 (>= 0.2.29-1) or
                      libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  evolution-data-server: Depends: libesd0 (>= 0.2.29-1) or
                                  libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  file-roller: Depends: libesd0 (>= 0.2.29-1) or
                        libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gcalctool: Depends: libesd0 (>= 0.2.29-1) or
                      libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gconf-editor: Depends: libesd0 (>= 0.2.29-1) or
                         libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gdm: Depends: libesd0 (>= 0.2.29-1) or
                libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gedit: Depends: libesd0 (>= 0.2.29-1) or
                  libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gnome-games: Depends: libesd0 (>= 0.2.29-1) or
                        libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gnome-gv: Depends: libesd0 (>= 0.2.29-1) or
                     libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gnome-media: Depends: libesd0 (>= 0.2.29-1) or
                        libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gnome-panel: Depends: libesd0 (>= 0.2.29-1) or
                        libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gnome-pilot: Depends: libesd0 (>= 0.2.29-1) or
                        libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gnome-session: Depends: libesd0 (>= 0.2.29-1) or
                          libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gnome-terminal: Depends: libesd0 (>= 0.2.29-1) or
                           libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gnomemeeting: Depends: libesd0 (>= 0.2.29-1) or
                         libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  gstreamer0.8-esd: Depends: libesd0 (>= 0.2.29-1) or
                             libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is installed
  libgnome2-0: Depends: libesd0 (>= 0.2.29-1) or
                        libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  libgnomeui-0: Depends: libesd0 (>= 0.2.29-1) or
                         libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  libopenal0: Depends: libesd0 (>= 0.2.29-1) or
                       libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  locales: Depends: glibc-2.3.2.ds1-20ubuntu13
  mplayer-386: Depends: libesd0 (>= 0.2.29-1) or
                        libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  nautilus: Depends: libesd0 (>= 0.2.29-1) or
                     libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  nautilus-cd-burner: Depends: libesd0 (>= 0.2.29-1) or
                               libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
  nautilus-sendto: Depends: libesd0 (>= 0.2.29-1) or
                            libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed  rhythmbox: Depends: libesd0 (>= 0.2.35) or
                      libesd-alsa0 (>= 0.2.35) but 0.2.23-3 is installed
  totem-gstreamer: Depends: libesd0 (>= 0.2.29-1) or
                            libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed  vino: Depends: libesd0 (>= 0.2.29-1) or
                 libesd-alsa0 (>= 0.2.29-1) but 0.2.23-3 is installed
E: Unmet dependencies. Try using -f.
granite@granite:~ $


I'm not sure if the Gramofile packages I installed are the cause of it but I think it is.

What's all this stuff about? It doesn't look very pretty...

---

### Post by Joeb on 2005-06-08
Try disabling the repository you installed gramofile from and then reload the package list.  It sounds like, since you have a mix of two different repositories that something in the gramofile one is more recent and trying to upgrade, but it's dependancies aren't met by your other repositories.

---

### Post by MicroChris on 2005-06-08
try what it said:

apt-get -f install

---

### Post by Joeb on 2005-06-08
I'm not sure he wants to do that apt-get -f or that it will actually work.  If you look at the list of files with unmet dependencies, there are a lot of them that are included with Ubuntu, but the ones listed are not the Ubuntu packages.  I think what he has done is added the actual debian repository along with the Ubuntu ones.  Some package in the debian repository is newer than the Ubuntu one and wants to upgrade, however, it's requiring packages from the debian repository that conflict with the Ubuntu ones.  Ubuntu has it's own repositories to keep this from happening, but since he's mixed the respositories apt-get can't do the upgrade because of conflicts with the two different repositories.

Since his Gramofile is installed, if he disables the the repository it came from, then apt-get won't see the conflicting packages and he should be able to do the upgrade.

---

### Post by granite230 on 2005-06-09
It's true that I mixed the Debian packages with the Ubuntu packages... my bad.
I don't exactly remember where I got Gramofile from but I think I downloaded a .deb package from a website. It's not that I changed anything in my sources.list so I cant out-comment them by using #.

---

### Post by Joeb on 2005-06-09
[QUOTE=granite230]It's true that I mixed the Debian packages with the Ubuntu packages... my bad.
I don't exactly remember where I got Gramofile from but I think I downloaded a .deb package from a website. It's not that I changed anything in my sources.list so I cant out-comment them by using #.[/QUOTE]

Assuming that you also downloaded the .debs from a debian site, I think that your only recourse will be to try the apt-get -f  option already mentioned.  Well actually, another recourse would be to manually uninstall all of the packages you installed, then do your upgrade, then add the debian source and install gramofile and then disable the debian source.

Before doing that last alternative, are you sure that gramofile isn't in the Ubuntu repositories?  They usually are an updated mirror of the debian repositories.  If gramofile is in the Ubuntu repository, then I'd uninstall the manual one and it's dependancies and install it from Ubuntu.

---

### Post by granite230 on 2005-06-10
yes, but I dont remember the names of the packages and since my dist-upgrade to Hoary I don't have Synaptic anymore...
sudo apt-get install synaptic gives the same list as mentioned above

so... I forced the upgrade (sudo apt-get upgrade -f). I think everything upgraded smoothly. 

sudo apt-get install synaptic also worked!

---

### Post by Joeb on 2005-06-10
[QUOTE=granite230]yes, but I dont remember the names of the packages and since my dist-upgrade to Hoary I don't have Synaptic anymore...
sudo apt-get install synaptic gives the same list as mentioned above

so... I forced the upgrade (sudo apt-get upgrade -f). I think everything upgraded smoothly. 

sudo apt-get install synaptic also worked![/QUOTE]


So does that mean you got the problem solved?  

As for finding dependencies for already installed packages, I think you can do an apt-cache showpkg package-name and it will tell you what the dependencies are.  So, in your case, you would say apt-cache showpkg gramofile

---

