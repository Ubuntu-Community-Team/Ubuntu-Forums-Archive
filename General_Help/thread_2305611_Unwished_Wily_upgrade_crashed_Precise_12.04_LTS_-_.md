---
title: "Unwished Wily upgrade crashed Precise 12.04 LTS - packages have unmet dependencies"
date: 2015-12-07
forum: General Help
---

### Post by SenseMaker2011 on 2015-12-07
[I]Hi, folks... I suppose I need your help. :smile:  first: I am only a simple user of Linux. I have started witth 10.04 LTS  in 2011 on first mashine after being 18 years Microsoft victim. :razz:  .This mashine meanwile was updated to 12.04 LTS with no problems. -  When Windows XP run out last year with upgrading services, I installed  UbuntuStudio on a 2nd mashine parallel. 
Both computers are binded in a computer network (with a third Windows Laptop) via DSL16000 Fritz!Box router (both *WLAN and 100Mbps LAN) *and  connected with a WLAN Lexmark Preveil Pro 700 series  printer/scanner/fax. Both Linux mashines mostly are used for regularly  Internet (firefox + google chromium browser, email client). No high  performance mashines for online gaming etc. ... but doing their job very  well.[/I]

The reason of my latest troubles: On the** Precise 12.04 LTS** mashine which had all latest updates I wanted install **Roger Router** to send from there directly eFaxes instead using the Lexmark multi-functional printer... [https://wiki.ubuntuusers.de/Fritzbox/Roger_Router/no_redirect](https://wiki.ubuntuusers.de/Fritzbox/Roger_Router/no_redirect)

... and I did a mistake having integrate into the "*sources.list*"  (pat: ..../etc/apt/sources.list ) via Ubuntu Software manager two links  for automated update. Because I following the instructions [here]("http://installion.co.uk/ubuntu/wily/universe/r/roger-router-cli/install/index.html"). The two links are:

```
 deb http://us.archive.ubuntu.com/ubuntu wily main universe
deb-src http://us.archive.ubuntu.com/ubuntu wily main universe

```

I suppose herewih accidently I mixed an automated upgrading process to  Wily 15.10 version. Was little bit stupid from my side I suppose to  start the command in the terminal "*sudo apt-get update*".  Unluckily a fully upgrading process started to Wily packages when I   initialized in the terminal running an updating of Roger Router   packages, so my original intention. Lately I noticed my own mistake, so I   stopped the terminal process. Probably then the 2nd big mistake :eek:I did.

As I am not an experimental Ubuntu user its more important to have  mashines stable running wiht LTS versions. So I have no intentions to  use Wily 15.10. (Rec.: Meanwhile both upper named links I have  neutralized in the sources.list.)
[B]

Now I have some different troubles. A heavily damaged system so it looks for me:[/B]

***1.)*** I get a **"warning sheeld" button** (red dot with white horizontal bar) in the top menu right sided it says following:

> "An  error occurred, please run Package Manager from the   right-click menu  or ap-get in a terminal to see what is wrong. The   error message was:  'Error: BrokenCount ->0'. This usually means that   your installed  packages have unmet dependencies".

I only have access via the **Synaptic Package Manager **clicking on the button I have locked left sided on the Launcher bar. There it says that **7 packages have unmet dependencies**. See screenshot in big attached.
[B][ATTACH=CONFIG]266031[/ATTACH]
[/B]
**The 7 packages are:**

libc-dev-bin version: 2.15-0 ubuntu 10.12 (embedded GNU C Librar: Development binaries)
libc6-dev version: 2.15-0 ubuntttu 10.12 (embedded GNU C libary: Development Libraries and Header files)
libnih1 version: 1.0.3-4 ubuntu 9.1 (NIH Utilitty Library)

libcgmanager0 version: 0.39-2 ubuntu 2 (Central cgroup manager daemon (client library))
libdevmapper1.02.1 version: 2:1.02.99-1 ubuntu 1 (Linux Kernel Device Mapper userspace libraryy)
nfs-common version: 1:1.2.8-9 ubuntu 10 (NFS support files common to client and server)
nfs-kernel-server version: 1:1.2.8-9 ubuntu 10 (support for NFS kernel server)

*How to repair ?? *I suppose the "password problem" as described in following pos. 2.) is coming from here, right ?

***2.) *Sudo commands** are no more working in the  terminal (opening with "strg + alt + T" or "strg + alt + F1") after  login into the regularly user account (with admin rights) because the **password is not recognized anymore**. All three attempts generally are failing whatever speed hitting the single keys I try. 

> "username"@computernamer-desktop:~$ sudo -i
[sudo] password for "user":
Sorry, try again.
[sudo] password for "user":
Sorry, try again.
[sudo] password for "user":
Sorry, try again.
sudo: 3 incorrect password attempts.

In consequences I cannot change to "*sudo -i*" to get "root access". And I cannot start any "sudo ...." command. - Therefor I cannot repair the damaged system, see pos. 1.)
(*Rec.: *I only can start regularly sudo commands if I jump into  the recovery modus during the boot process having there root access.)  Its not even possible to get Sudo function with "Strg + Alt + F1" within  the account. Same problem there:  No password recognized.

I followed instructions to repair "sudo" as described here: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo) (*Rec.: T*he /etc/sudoers file looks exactly like described there.)

I have reset the password, which works well... either in the "User Accounts" tab or via "root" in the recovery modus [as described here]("http://www.psychocats.net/ubuntu/resetpassword").  But the password never was and still isnt accepted in a regularly  terminal. Strange that the new password is recognized for the login, but  not recognized within the terminal. (*Rec.: *I have two  different passwords, one for the root, one for the user account with  admin function). I suppose it related directly to the problems as named  under upper listed pos. 1.) 

Same I have some error messages the password is not recognized to  perform administrative tasks, e.g. calling for an update via the  application "synaptic package manager". It just says after I tried it to  type the password three times, see screenshot: 

> "Failed to run /usr/sbin/synaptic '--update-at-startup' '--non-interactive' '--hide-main-window' as user root.
Wrong password."
[ATTACH=CONFIG]266030[/ATTACH]

***3.)** *The damages I caused by own mistake I dont have access anymore to the **Ubuntu Software Center**,  too. Clicking on the button left sided on the vertical Launcher bar its  just blinking a moment and nothing happens. The result in the terminal  with command "software-center" is following :

>  command "software-center": 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    from gi.repository import Gtk, GObject
  File "/usr/lib/python2.7/dist-packages/gi/__init__.py", line 23, in <module>
    from ._gi import _API, Repository
ImportError: /lib/i386-linux-gnu/libselinux.so.1: undefined symbol: pcre_free_study

"Show updates", "Install all updates", "Check for updates" aren't working too when clicking in the top menu bar.

***4.)*** I also tried following [command in root recovery modus: "sudo apt-get -f install" for fixing broken packages]("http://askubuntu.com/questions/141370/how-to-fix-a-broken-package-when-apt-get-install-f-does-not-work")  to locate the broken packes. And the result is this (Rec.: I took a  screenshot with the smartphone cam, so maybe its little bit blury/shaky  as it's not a direct screenshot):[B]
[ATTACH=CONFIG]266029[/ATTACH]

[/B]As we can read it says similarly as reported upper list of 7 packages:

> "Correcting dependencies... failed.
The following packages have unmet dependencies:

libc-dev-bin : Depends: libc6 (< 2.16) but 2.21-0 ubuntu 4 is installed
libc6-dev: Depends: libc6 (= 2.15-0 ubuntu 10.12) but 2.21-0 ubutu 4 is installed
libcgmanager0: Depends:  libdbus-1-3 (>=1.9.14) but 1.4.18-1 ubuntu 1.7 is installed
libdevmapper1.02.1: Depends: libudev1 (>= 183) but it is not installed
libnih1: PreDepends: libc6 (<2.16) but 2.21-0 ubuntu 4 is installed
nfs-common: Depends: init-system-helpers (>=1.18~) but it is not installable
                  Depends: lsb-base (>= 4.1+Debian11 ubuntu 7) but 4.0-0 ubuntu 20.3 is installed
                  Depends: rpcbind (>= 0.2.0-6 ubuntu 1) but it is not installed
nfs-kernel-server: Depends: init-system-helpers (>=1.18~) but it is not installable
E: Error, pkgProblemResolver:: Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies."
[B]
*5.) *[/B]Last maybe I should mention what I have noticed, too:  The installation of the Lexmark Printer is totally gone. Same the Roger  Router (which is a kind of "virtual printer"). But I still can use the  scanner function of the printer (via software "Simple Scan"). And I  still can listen webradio (via Rhythmbox) and have access to the fully  computer network (with an external file server) via 100Mbps LAN. Sound  management via "PulseAudio Volume Control" is possible, too. Both  browsers (Firefox + Google Chromium) are working properly.

[I]It would be pitty, if I'd have to reinstall the whole system newly.  As there is installed Wine, too with some other important programmes it  would cost me lots of time to stat from scratch I suppose. 

Maybe somebody here is so kind to give me advice how to rescue it and  repair the upper named damages. As said, I am just a click monkey  following instructions. Just a "happy Linux user". - Thanks in advance  giving advice.[/I]

---

### Post by Ricardo_Velasco on 2015-12-07
Greeting:

I read  your problem , and in my opinion , the problem of whether it was too serious.

I think you have to think of him only two alternatives.

Run the CD of Ubuntu 12.04 and repair the operating system , I'm not sure , but this option.
I'm sure you still have to be there .

And the other is to reinstall the operating system.


Sorry for my answer. :(

The reason for my answer was an experience with proprietary drivers of Intel graphics card in Ubuntu 12.04 64 BITS

---

### Post by SenseMaker2011 on 2015-12-08
@ Ricardo Velasco (and others): I can boot directly from CDRom (or better to say from DVD). I have both the regularly ISO Ubuntu Desktop and Alternate Version of 12.04.5 LTS (from 2014), both burnt each on a DVD. - Using the Alternate version I can jump directly into the "rescue mode". - Will this method work to repair it from external ? - Will the existing damages be recognized and repaired ? As we can see in the upper list, it is kind of "downgrading" required.

I have read about a smililarly problem  and how to repair thepackages which have unmet dependencie. It is well described here: 
[URL="http://mergy.org/2013/03/repairing-a-badly-damaged-package-system-in-ubuntu/"][B]Repairing a badly damaged package system in Ubuntu
[/B][/URL]
But herefor I'd need to get back the possibility to manage "sudo..." commands in the terminal after login to my user account (with admin function).

---

### Post by Ricardo_Velasco on 2015-12-08
Greetings:

Sorry , but I think I have a possible solution , if you then have the recovery mode attempts to log in as root .

[IMG]http://1.bp.blogspot.com/-Vxc_wr6lzm4/Udp5zb-1IdI/AAAAAAAACOE/jXmbH5tVggs/s400/modorecovery.jpg[/IMG]


[IMG]http://4.bp.blogspot.com/-moWA83qLQ5M/Udp80hvZUsI/AAAAAAAACOU/Aupdug7ZDFM/s400/modorecoveryroot.jpg[/IMG]


try

Sorry for incomplete answer..

You say you want to get the permission to run sudo commands ? ..

Try this command during early root in recovery mode

> usermod -G adm,cdrom,dip,lpadmin,plugdev,sambashare,sudo (user) 


Or:

adduser usuario sudo

I found another way in as root:

In recovery mode creates password to login as root:

> passwd root

First make a copy of the file you are going to play :

> cp -p /etc/lightdm/lightdm.conf /etc/lightdm/lightdm.conf.orig[QUOTE]


Edit " /etc/lightdm/lightdm.conf " :

[QUOTE]nano /etc/lightdm/lightdm.conf[QUOTE]


Appear next file:


[QUOTE] [SeatDefaults]

user-session=ubuntu

greeter-session=unity-greeter 

At last you add this line:

> greeter-show-manual-login=true

And it must be so:

> 

[SeatDefaults]

user-session=ubuntu

greeter-session=unity-greeter

**greeter-show-manual-login=true**[QUOTE]


Save it and restart .

[QUOTE] reboot [QUOTE]


If you want to remove the root follow these steps:

[QUOTE]sudo passwd -l root

sudo cp -p /etc/lightdm/lightdm.conf.orig /etc/lightdm/lightdm.conf

---

### Post by SenseMaker2011 on 2015-12-27
@ [**[COLOR=#000000]Ricardo_Velasco[/COLOR]**]("http://ubuntuforums.org/member.php?u=1962109") Tks... was little bit busy last two weeks... will check the infos.... I already logged in via recovery modus and reset the password before I started this thread to ask for help. But the problem still existed as described. No switch possible in the Terminal to the root and the password is not recognized. 

So I will go ahead to the other options you described. Tks... :-) Will report as soon I have something new. :-)

---

