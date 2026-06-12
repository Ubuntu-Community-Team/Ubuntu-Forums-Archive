---
title: "questions/comparison about ubuntu 18.04"
date: 2018-04-29
forum: General Help
---

### Post by Claus7 on 2018-04-29
Hello,

I would like to ask other users about their experience so far concerning ubuntu 18.04.

Just a short story: my current session traces back to 14.04, which was upgraded to 16.04 for a short amount of time and now to 18.04 since alpha days. I have done dconf reset minimum 2 times while in 18.04, I have no orphaned packages and my system is working pretty descently. 

So, my questions-comments are:

1) boot time
after the release of 18.04 my boot time using an hdd is:
```
systemd-analyze time
```
Startup finished in 5.094s (kernel) + 1min 2.272s (userspace) = 1min 7.367s
graphical.target reached after 1min 2.264s in userspace

having uninstalled snapd which was increasing my boot time approximately 5 seconds to the one shown here.

with the 4.15.0-13 kernel and 18.04 beta I had a boot time less than 48 seconds!
(I'm aware of ssd's having boot times maybe 10 times less or so than the one reported here, yet I'm talking about the same specs)

so the question is: those of you that you were experimenting with alpha and beta versions have you noticed an increase in boot time after the final release?

2) packages missing

a) do you miss pdftk not being present for 18.04? There is a bug filling webpage in launchpad for this: [https://bugs.launchpad.net/ubuntu/+source/pdftk/+bug/1764450](https://bugs.launchpad.net/ubuntu/+source/pdftk/+bug/1764450)
I was trying to find an alternative to no avail. The closest was pdfshuffler, yet it does not seem that it can be handled via command line. 

b) have you noticed that gtk-theme-config is deprecated? I do not understand why, since it can be installed from 14.04 and you could change easily basic colors of a theme. It was there with beta version.
As far as I know, there is no ubuntu-tweak tool yet that someone can change the colors of a specific theme. 

3) bugs

a) have you noticed that eclipse does not start? Can you start eclipse in your 18.04 ubu box?
The basic error I get is:
java.lang.ClassNotFoundException: org.eclipse.core.runtime.adaptor.EclipseStarter
I was able to find that this is a known bug, yet is there anyone that does not face such an issue in 18.04?

b) okular: I cannot write a comment using non latin characters: they just do not show up! Have you noticed that as well? 
It is supposed to be a known bug, yet have you noticed if this is affecting you?

4) notifications area

I'm using the gnome-flashback session. In the top panel I have added the notifications area applet(?). It is working fine, yet appart from displaying the notifications it has an additional icon that shows the keyboard preference in white background. 
[ATTACH=CONFIG]279495[/ATTACH][ATTACH=CONFIG]279496[/ATTACH]
Do you know where I could find the source code so I can remove the keyboard layout from notifications area?
Just to mention here that this question was asked in the days of 10.10 with no definite answer.

5) my impression is that with the last versions there were many problems concerning logging in. I was affected from it as well, since I was not able to login to flashback. Looking at the forums I was able to notice that this was either: due to a package hanging there due to upgrade and it had to be removed or due to bad combination of greeter and session.
(this is just a comment)

Thank you,
Regards!

---

### Post by Claus7 on 2018-05-01
Hello,

1) concerning the boot time I selected many different kernels to no avail. I was looking for:
4.15.0-13 which actually looks like:
4.15.0-13.14

I was not able to find it under:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

but I was able to find it under:
[https://answers.launchpad.net/ubuntu/+source/linux/4.15.0-13.14/+build/14466170](https://answers.launchpad.net/ubuntu/+source/linux/4.15.0-13.14/+build/14466170)

and from there I took the files:
linux-headers-4.15.0-13_4.15.0-13.14_all.deb
linux-headers-4.15.0-13-generic_4.15.0-13.14_amd64.deb
linux-image-4.15.0-13-generic_4.15.0-13.14_amd64.deb

and installed them using:
sudo dpkg -i *.deb

then I restarted and during boot I was pressing shift, and as a result grub menu appeared which had the option:
Advanced options for Ubuntu

and from there I selected the generic kernel in question. The problem was that after boot I had no network.

I cannot compare the boot times, since, when installing a kernel for the first time it takes more time to boot.

EDIT

1) Concerning the boot time, I experimented a little bit more.
I added the ubuntu kernel ppa to my system from here:
[https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa](https://launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa)
the new kernel did not have so much of a difference, so I decided to remove the ppa.
At the time there was a requirement to remove some packages, which I did (and most of them were reinstalled afterwards). The end result was that my boot time was improved:
$ systemd-analyze time
Startup finished in 5.202s (kernel) + 41.148s (userspace) = 46.350s
graphical.target reached after 40.623s in userspace

2a) solution of installing pdftk to 18.04 taking packages of pdftk from 17.10 can be found here:
[https://ubuntuforums.org/showthread.php?t=2390293&page=2](https://ubuntuforums.org/showthread.php?t=2390293&page=2)

4) The task is not so easy. The notification area applet is combined with the panel source code which is not something trivial to be installed from scratch. I will describe briefly the steps I followed:

i) the source code of gnome panel for 18.04 can be found here: [https://packages.ubuntu.com/bionic/gnome-panel](https://packages.ubuntu.com/bionic/gnome-panel)

ii) extract the contents of the tar file and enter in the gnome-panel-3.26.0 folder

iii) in order to install it as is the procedure is the common:
./configure
make 
sudo make install

yet it won't work with first try. There are a lot dev packages missing, which they have to be installed first. 

iv) In order to find these packages, either synaptic is used or they have to get downloaded and installed manually. While filling in the requirements, there was a first bunch of packages that were needed, and after that a couple more were required.
The list of packages is more or less the following, while trying to remember which pagkages were installed (mainly the first ones from synaptic):

libgnome-desktop-3-dev
libgdm-dev
libdconf-dev
libpolkit-gobject-1-dev
gtk-doc-tools (among others)
libgeocode-glib-dev
libgweather-3-dev
libsoup2.4-dev
libstartup-notification0-dev
libwnck-3-dev
libgnome-desktop-3-dev
gnome-core (among others)
itstool

vi) Packages that were not found in synaptic, were found either from launchpad or ubuntu packages. Installation procedure, in general, went ok, appart from some complaints about clock.

vii) Tampering with the code is not advised as a procedure, since, after installation the indicator applet had problems. Just for testing I removed some lines of code which had to do with "keyboard" in some of the files, mainly in the notification's area folder, to no avail.

viii) sudo make uninstall 
logging out and back in brings back the panel with all applets functioning again.

---
ix) Just to add that importing applets from mate panel to ubuntu flashback is, in general, not feasible. For example, it is not possible to open -just- terminal from mate panel, yet mate-terminal.
The mate notification applet, which is working without the keyboard layout, cannot be transferred to flashback panel and vice versa. Someone can install the mate panels on top of gnome ones and add the package on the startup applications without having to install the mate session, yet, as mentioned, the applets accompaning the gnome flashback session won't be applicable.

x) There is the indicator-notifications as an alternative from here:
[https://launchpad.net/~jconti/+archive/ubuntu/recent-notifications](https://launchpad.net/~jconti/+archive/ubuntu/recent-notifications)

yet it does not show skype as a small panel icon when is active.

EDIT

Regards!

---

### Post by Claus7 on 2018-09-09
Hello,

> **Claus7 said:**
> 

4) notifications area

I'm using the gnome-flashback session. In the top panel I have added the notifications area applet(?). It is working fine, yet appart from displaying the notifications it has an additional icon that shows the keyboard preference in white background. 
[ATTACH=CONFIG]279495[/ATTACH][ATTACH=CONFIG]279496[/ATTACH]
Do you know where I could find the source code so I can remove the keyboard layout from notifications area?
Just to mention here that this question was asked in the days of 10.10 with no definite answer.


the icons in question are found under:
/home/user_name/.cache/gnome-flashback/input-sources/icons/hicolor/scalable/status

and they can be substituted, for example, with a transparent icon the same for both languages, as a result problem solved without having to tamper with any code.

Regards!

---

