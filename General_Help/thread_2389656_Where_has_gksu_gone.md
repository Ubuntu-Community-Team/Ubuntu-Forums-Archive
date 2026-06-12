---
title: "Where has gksu gone?"
date: 2018-04-19
forum: General Help
---

### Post by lieven-debels on 2018-04-19
Hi

I just noticed the package gksu (which has been present in ubuntu for over 10 years) was removed from bionic. Is there a specific reason why it was removed?
Is there an alternative that accomplishes the same?

Note: gksu enables you to use sudo in a graphical environment or GUI (not in terminal)
For example, if I wanted to start synaptic, I entered the following command in /usr/share/applications/synaptic.desktop: Exec=gksu synaptic
That way, by clicking the synaptic icon it was started as root (which is needed, because otherwise you won't be able to install additional software)

Any thougths?

---

### Post by deadflowr on 2018-04-19
synaptic uses pkexec.
most gui apps that require root use now pkexec.
If using an app like natuilus or gedit use the admin:// function
[https://ubuntuforums.org/showthread.php?t=2377380]("https://ubuntuforums.org/showthread.php?t=2377380")

---

### Post by lieven-debels on 2018-04-19
Thanks for the answer.
Still I would like to know the reason why gksu was replaced with pkexec?

---

### Post by kerry_s on 2018-04-19
most likely because of age, something newer was needed to handle the newer security.
the whole looking towards the future thing.

you can alias it if that's what your use to.

alias gksu='pkexec'

---

### Post by lieven-debels on 2018-04-19
Thanks, but the default command to start synaptic in /usr/share/applications is Exec=synaptic-pkexec
That doesn't give me a dialog to enter my password (like gksu did) nor does it start synaptic. So am I missing something? Which package do I need to install to make pkexec work?

edit: Ok, it does start synaptic but without root access. Any thoughts how to start synaptic as root?

---

### Post by kerry_s on 2018-04-19
then your most likely using wayland session which blocks the use of gui elevated apps.

you can log out and select gnome-xorg it will work. but synaptic is not a recommended app to use moving forward anyways. that's old tech
ubuntu combines snaps moving forward & it's all made to work with the software center.

using synaptic can kill your install, break apt, dpkg. etc....

---

### Post by deadflowr on 2018-04-19
Which session is logged in
Ubuntu or Ubuntu with wayland?
See: [https://bugs.launchpad.net/ubuntu/+source/backintime/+bug/1713313]("https://bugs.launchpad.net/ubuntu/+source/backintime/+bug/1713313")

half-ninja'd
[B]
Edit:[/B] And here are the list of apps that still use gskudo and are also affected by wayland:
[https://bugs.launchpad.net/ubuntu/+source/nmap/+bug/1713311]("https://bugs.launchpad.net/ubuntu/+source/nmap/+bug/1713311")

As to gksu being gone.
That's been a topic of discussion for some time, so not real a surprise, I guess:
See: [https://ubuntuforums.org/showthread.php?t=2225832]("https://ubuntuforums.org/showthread.php?t=2225832")
There is probably a bug report about it being removed somewhere.

---

### Post by lieven-debels on 2018-04-19
I'm using xorg.
See attached screenshot for the error message (sorry, it's in dutch but in short it says: Starting synaptic without administrative privileges)
I also entered synaptic-pkexec in terminal, which didn't work either
See second screenshot.

---

### Post by QIII on 2018-04-19
I'm not sure if their tune has changed, but for some time the Wayland developers took the position that there was no good reason for users to run graphical apps as root and they weren't about to change their minds, neener, neener, neener.  Never mind that users, not developers, should decide what they want their experience to be.

So there are work arounds, such as ```
xhost si:localuser:root
```

gksu was deprecated long ago and was just now removed from Debian upstream.  So Canonical removed it.

---

### Post by lieven-debels on 2018-04-19
Ok thanks, but where do I have to type your code?

---

### Post by deadflowr on 2018-04-19
> **lieven-debels said:**
> Ok thanks, but where do I have to type your code?

In the terminal
It'll run like any other command.
then run your root command.
```
xhost si:localuser:root
then press enter
then try
synaptic-pkexec or some other root gui app
```
the xhost command switches you to use root apps, but only for the current desktop session in use.
To set as persistent you can add the line to a new Startup Application entry.
That way it'll run everytime you log in.

---

### Post by mc4man on 2018-04-19
> **lieven-debels said:**
> 
For example, if I wanted to start synaptic, I entered the following command in /usr/share/applications/synaptic.desktop: Exec=gksu synaptic
That way, by clicking the synaptic icon it was started as root (which is needed, because otherwise you won't be able to install additional software)

Any thougths?

By default synaptic has been using /usr/bin/synaptic-pkexec & corresponding line in it's .desktop for at least the last 6 years. So no sure why you previously saw fit to change that.
(- unless you were editing synaptic-kde.desktop instead of synaptic.desktop

Is this a fresh install of 18.04 or are you re-using your home folder, i.e you did an upgrade from earlier Ubuntu release or you installed over the previous install's  partition without formatting or whatever..

---

### Post by lieven-debels on 2018-04-19
I did an update of 17.10 to 18.04 by changing every instance of 'artful' to 'bionic' in /etc/apt/sources.list.
Then ran apt-get update, apt-get upgrade and apt-get dist-upgrade.

Still the suggestion from deadflowr (in post #11), doesn't seem to solve the problem.

---

### Post by deadflowr on 2018-04-19
> **lieven-debels said:**
> I did an update of 17.10 to 18.04 by changing every instance of 'artful' to 'bionic' in /etc/apt/sources.list.
Then ran apt-get update, apt-get upgrade and apt-get dist-upgrade.

How recently?
Wonder if there is leftover junk causing issues.

---

### Post by rbmorse on 2018-04-19
I upgraded my 17.10 to 18.04 (beta2) on Xorg using the method here: [https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver](https://linuxconfig.org/how-to-upgrade-to-ubuntu-18-04-lts-bionic-beaver) (Ubuntu method).  

To run synaptic (it's one of those cold, dead hands apps for me) I open a terminal and run:

synaptic-pkexec

That gives me a password dialog followed by Synaptic with root privileges.

---

### Post by Irihapeti on 2018-04-19
To get the pkexec password dialogue, you need to have one of the polkit / policykit agents installed. e.g. lxpolkit, mate-polkit, policykit-1-gnome.

One of those would be installed as a matter of course if you're using a full install of a flavour. Usually, it's only an issue if you have a custom install based on a minimal system.

---

### Post by lieven-debels on 2018-04-20
I do have a custom install, started from the ubuntu 17.10 mini.iso but policykit-1-gnome is installed, so I don't know why it still doesn't work.
Can someone please look at the screenshot of the terminal window I posted yesterday. Does that give some possible clue what's going wrong?
Or can I troubleshoot this in another way?

---

### Post by deadflowr on 2018-04-20
Try a quick pkexec test
```
pkexec test
```
does it open the popup dialog password box?
Or is the password field inside the terminal?

Here's a Debian bug report with similar output of the screenie posted
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=841878]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=841878")
(btw, post the output directly into a post rather then pictures as images can only go so far)

---

### Post by lieven-debels on 2018-04-20
Finally made some progress: First (or after a reboot) I have to run from a terminal:
 ```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```
Then 
```
pkexec synaptic
```
works as expected. However in /usr/share/applications/synaptic.desktop there is:
```
Exec=synaptic-pkexec
```
which does NOT work as expected.
So basically now I need to know how to make this change permanently, and secondly, synaptic.desktop seems to use the wrong syntax (but it doesn't matter, because if i change synaptic-pkexec to pkexec synaptic, synaptic is still started without administrative privileges). It only seems to work if I issue the command pkexec synaptic directly. I was hoping that by typing just 'synaptic' the synaptic.desktop file would translate this to pkexec synaptic, but it doesn't.

---

### Post by deadflowr on 2018-04-20
The syntax is correct.
Perhaps, try a quick reinstall of synaptic.
Maybe a reinstall will do something to clean up any residual problems it has for you.
```
sudo apt install --reinstall synaptic
```

---

### Post by sudodus on 2018-04-20
> **deadflowr said:**
> How recently?
Wonder if there is leftover junk causing issues.

+1

I have seen several problems after upgrading to and from 17.10, so I recommend a fresh installation. It will probably work, if you keep /home (by creating a separate **home** partition).

---

### Post by Irihapeti on 2018-04-20
To make the change permanent, you need to ensure that the command

```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
```

is run after each login. There will be an autostart file, depending on how you have things setup, to which you add that command. (On my openbox system, it's ~/.config/openbox/autostart)

---

### Post by lieven-debels on 2018-04-22
Seems to work so far. A bit more complicated than gksu though. I will mark this thread as solved.

---

### Post by HermanAB on 2018-04-22
Note that you can also make the two or three utilities that you need to run as root "SUID root" and then the whole hassle will go away.

---

