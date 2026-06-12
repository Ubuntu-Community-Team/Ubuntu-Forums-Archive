---
title: "Flatpak does not keep the settings"
date: 2024-07-13
forum: General Help
---

### Post by flokosx on 2024-07-13
[COLOR=#111111][FONT=Arial]Hi guys[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]In a clean installation of Kubuntu 24.04, after installing FLATPAK support and give all kinds of FLATPAK permission, several flatpaks (Qbitorrent, Clementine and others) present the behavior of returning default configurations when they are opened again, as if they are finished being installed. I've tried to give permission of all kinds, I made a new installation, opened some bug signals in Github but no one can say what is happening and how to solve.[/FONT][/COLOR]

[COLOR=#111111][FONT=Arial]Does any enlightened give me a way?[/FONT][/COLOR]

---

### Post by Tadaen_Sylvermane on 2024-07-13
Make sure /home/$USER/.var has the right permissions and is either actually there or bind mounted. Symlinks cause odd behavior with that folder in my experience.

---

### Post by flokosx on 2024-07-13
I just gave all the writing and reading permits to VAR folder, to all users, but the error continues

---

### Post by #&amp;thj^% on 2024-07-13
Mine:
```
stat /home/$USER/.var/
  File: /home/me/.var/
  Size: 3         	Blocks: 1          IO Block: 512    directory
Device: 0,46	Inode: 135930      Links: 3
Access: (0775/drwxrwxr-x)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2024-06-04 20:07:49.433462091 -0600
Modify: 2024-05-27 16:12:06.216701384 -0600
Change: 2024-06-04 20:38:22.592799143 -0600
 Birth: 2024-06-04 20:25:43.079420282 -0600

```
No problems here.
EDIT: to see
```
flatpak run --command=bash tv.kodi.Kodi
[&#128230; tv.kodi.Kodi ~]$ echo $XDG_CONFIG_HOME
/home/me/.var/app/tv.kodi.Kodi/config

```

---

### Post by flokosx on 2024-07-13
The first command resulted in this output:

Arquivo: /home/bruno/.var/
    Tamanho: 4096       Blocos: 8          bloco de E/S: 4096   diretório
Dispositivo: 259,2      Inode: 25169166    Ligações: 3
     Acesso: (0777/drwxrwxrwx)  Uid: ( 1000/   bruno)   Gid: ( 1000/   bruno)
     Acesso: 2024-07-13 14:19:56.838670776 -0300
Modificação: 2024-07-13 13:22:05.059572358 -0300
  Alteração: 2024-07-13 14:19:56.788670049 -0300
    Criação: 2024-07-13 13:22:05.059572358 -0300

Could you put the second command syntax? I didn't get out of command

---

### Post by #&amp;thj^% on 2024-07-13
> **flokosx said:**
> 
Could you put the second command syntax? I didn't get out of command
Sure,   your very liberal with those permissions "777" but I get why you have that currently.
Please show this:
```
flatpak list
```
Then take one of those installed ie, mine:
```
flatpak list
Name                       Application ID                      Version    Branch      Installation
Flatseal                   com.github.tchx84.Flatseal          2.2.0      stable      system
Freedesktop Platform       org.freedesktop.Platform            23.08.20   23.08       system
Mesa                       org.freedesktop.Platform.GL.default 24.1.1     23.08       system
Mesa (Extra)               org.freedesktop.Platform.GL.default 24.1.1     23.08-extra system
nvidia-555-58-02           &#8230;sktop.Platform.GL.nvidia-555-58-02            1.4         system
openh264                   org.freedesktop.Platform.openh264   2.1.0      2.2.0       system
openh264                   org.freedesktop.Platform.openh264   2.4.1      2.4.1       system
GNOME Application Platfor&#8230; org.gnome.Platform                             46          system
KDE Application Platform   org.kde.Platform                               5.15-23.08  system
Tor Browser Launcher       org.torproject.torbrowser-launcher  0.3.7      stable      system
Kodi                       tv.kodi.Kodi                        21.0-Omega stable      system

```
Lets look with TorBrowser this time:
```
flatpak run --command=bash org.torproject.torbrowser-launcher 
[&#65533;&#65533; org.torproject.torbrowser-launcher ~]$ 

```
Same window on the same prompt:
```
flatpak run --command=bash org.torproject.torbrowser-launcher 
[&#65533;&#65533; org.torproject.torbrowser-launcher ~]$  echo $XDG_CONFIG_HOME


```
After that  hit return/enter and now:
```
/home/me/.var/app/org.torproject.torbrowser-launcher/config

```
"me is my user here"
If I need to look deeper then:
```
ls -la /home/me/.var/app/org.torproject.torbrowser-launcher/config
total 11
drwxrwxr-x 4 me me 5 May 27 16:12 .
drwxrwxr-x 7 me me 7 May 27 16:12 ..
drwxrwxr-x 3 me me 3 May 27 16:12 ibus
drwxrwxr-x 2 me me 3 Jun  5 12:52 torbrowser
-r--rw-r-- 1 me me 0 May  8 06:20 user-dirs.dirs

```

Have you considered installing flatseal, it might just help.

---

### Post by flokosx on 2024-07-13
1- My command "flatpak run --command=bash org.qbittorrent.qBittorrent", returns nothing

2- Unlike your system, mine does not return:"[&#65533;&#65533; org.qbitorrent.qbitorrent ~] $"

3- Flatseal was installed and open and already had all the permission released, which I don't even know what it is for. 

4-I'm desperate, this explains why I am "very liberal" in the permission I give

---

### Post by #&amp;thj^% on 2024-07-13
Yep Mine with qBittorrent:
```
flatpak run --command=bash org.qbittorrent.qBittorrent
bash: 0: command not found
Welcome to  me
 
Saturday 13 July 2024, 14:24:30
Memory Usage: 5921/13829MB (42.82%)
Support - https://www.ubuntuforums.org (Right click, Open Link)

```
Will you now show me this:
```
 flatpak run org.qbittorrent.qBittorrent

```
I just installed qBittorrent as a flatpak and first run I set my settings, then logged out and back in again and all settings were saved.

Since you installed flatpak and added the right remote hub, have you yet rebooted?

---

### Post by flokosx on 2024-07-13
Yes, many times.

Strange thing. I installed the version .Deb together with the FlatPak version and the two began to present the same behavior! Only after I remove the FLATPAK version did the .Deb version return to function as expected. That's weird!? I didn't know that both architectures could share something in common!

---

### Post by #&amp;thj^% on 2024-07-13
Strange Indeed. I'm on Arch ATM, Let me boot to ubuntu where qBittorrent is a .deb.
Be back soon.

---

### Post by #&amp;thj^% on 2024-07-13
This is mine .deb on buntu:
```
apt policy qbittorrent
qbittorrent:
  Installed: 4.6.5-1
  Candidate: 4.6.5-1
  Version table:
 *** 4.6.5-1 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status

```


Now to install it
```

 flatpak install qbittorrent
Looking for matches&#8230;
Remotes found with refs similar to &#8216;qbittorrent&#8217;:

   1) &#8216;flathub&#8217; (system)
   2) &#8216;flathub-beta&#8217; (system)

Which do you want to use (0 to abort)? [0-2]: 

```
I took the stable 1)
permissions on mine:
```
org.qbittorrent.qBittorrent permissions:
    ipc                        network     fallback-x11       wayland
    x11                        dri         file access [1]    dbus access [2]
    system dbus access [3]

    [1] host, xdg-config/kdeglobals:ro
    [2] com.canonical.AppMenu.Registrar, org.freedesktop.Notifications,
        org.freedesktop.PowerManagement, org.gnome.SessionManager,
        org.kde.KGlobalSettings, org.kde.StatusNotifierWatcher,
        org.kde.kconfig.notify
    [3] org.freedesktop.UPower, org.freedesktop.login1

```
With what I wanted to see from yours mine is:
```
flatpak run org.qbittorrent.qBittorrent
Gtk-Message: 14:53:22.752: Failed to load module "xapp-gtk3-module"
_IceTransSocketINETConnect() no usable address for me-Legion-5-zfs:38069
Qt: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
QFSFileEngine::open: No file name specified
QFSFileEngine::open: No file name specified

```
I set my settings now and will reopen qBittorrent, and I find the same behavior you see>>> Settings not Saved. Grrr! Even the .deb has changed back to default settings.

I'm going to file a bug report on flatpak, but don't hold your breath Canonical will do anything to promote their snapd and snaps.

---

### Post by #&amp;thj^% on 2024-07-13
Bug Filed here: [https://bugs.launchpad.net/ubuntu/+source/flatpak/+bug/2073041](https://bugs.launchpad.net/ubuntu/+source/flatpak/+bug/2073041)

Add yourself to it, helps when others are effected.

---

### Post by flokosx on 2024-07-14
Thanks to colleagues on other forums, I managed to solve my problem. I don't understand much about the technicalities of the thing but it's working as expected now.

in short, for a beginner like me, I installed:
sudo apt install apparmor-utils

them:
sudo aa-disable /usr/bin/bwrap


&#8203;&#8203;&#8203;&#8203;&#8203;&#8203;&#8203;Source: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2072811](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2072811)

---

### Post by #&amp;thj^% on 2024-07-14
Yeah I'm not going to be doing that anytime soon. But you are free to run it however you see fit.

Ubuntu has changed the Ubuntu 24.04 kernel so that programs like bubblewrap are not allowed to create a new user namespace unless they are given an AppArmor profile that contains the userns permission. This is their choice, and if it's causing a problem for you, please report it to them. Changes in bubblewrap are not going to solve this.

EDIT: My thoughts, What they are doing instead is adding a profile for each program that uses bubblewrap, including Flatpak, Steam, nautilus/GNOME Files (via libgnome-desktop), epiphany/GNOME Web (via WebKitGTK) and so on, as well as adding a profile for each program that does not use bubblewrap but does similar things a different way, such as Firefox and Chrome. If you are using some different program that invokes bwrap - for example mkosi - my understanding is that they would tell you to add a profile for that program instead of a profile for bwrap.

I personally think their stated reasoning is flawed: they say that the reason is that giving bwrap a profile like this would allow for an arbitrary bypass of their restriction, but programs like the ones for which they are adding profiles are not designed to impose a security boundary that distrusts their caller either, so it's straightforward for an unprivileged user to bypass their restriction anyway. But I didn't design their security model, and what they choose to do in their distro is not my decision.

EDIT2: I also run apparmor on Arch or Arch Based systems but I don't see settings not being saved....This is on Ubuntu where the settings are not preserved.

---

### Post by #&amp;thj^% on 2024-07-15
This is how it now reads:>>in "/etc/apparmor.d/bwrap-userns-restrict"
```

# This profile allows almost everything and only exists to allow
# bwrap to work on a system with user namespace restrictions
# being enforced.
# bwrap is allowed access to user namespaces and capabilities
# within the user namespace, but its children do not have
# capabilities, blocking bwrap from being able to be used to
# arbitrarily by-pass the user namespace restrictions.
#
# Note: the bwrap child is stacked against the bwrap profile due to
# bwraps use of no-new-privs

# disabled by default as it can break some use cases on a system that
# doesn't have or has disable user namespace restrictions for unconfined
# use aa-enforce to enable it

abi <abi/4.0>,

include <tunables/global>

profile bwrap /usr/bin/bwrap flags=(attach_disconnected) {
  allow capability,
  # not allow all, to allow for pix stack
  # sadly we have to allow  m every where to allow children to work under
  # stacking.
  allow file rwlkm /{**,},
  allow network,
  allow unix,
  allow ptrace,
  allow signal,
  allow mqueue,
  allow io_uring,
  allow userns,
  allow mount,
  allow umount,
  allow pivot_root,
  allow dbus,
  allow px /** -> bwrap//&unpriv_bwrap,

  # the local include should not be used without understanding the userns
  # restriction.
  # Site-specific additions and overrides. See local/README for details.
  include if exists <local/bwrap-userns-restrict>
}

profile unpriv_bwrap flags=(attach_disconnected) {
  # not allow all, to allow for pix stack
  allow file rwlkm /{**,},
  allow network,
  allow unix,
  allow ptrace,
  allow signal,
  allow mqueue,
  allow io_uring,
  allow userns,
  allow mount,
  allow umount,
  allow pivot_root,
  allow dbus,

  allow pix /** -> &unpriv_bwrap,

  audit deny capability,

  # the local include should not be used without understanding the userns
  # restriction.
  # Site-specific additions and overrides. See local/README for details.
  include if exists <local/unpriv_bwrap>
}

```

They are now working on a fix to apparmor 14 Hrs Ago, I would advise to just wait for it to come in.
> Robie Basak (racb) wrote 14 hours ago: 			#19

Due to the "really" version bump, Oracular will also require a bump before it is released, unless a 4.0.2 or similar upload happens in Oracular first. Setting tasks accordingly.
Changed in apparmor (Ubuntu Noble):
status: 	New &#8594; Triaged
importance: 	Undecided &#8594; Critical
Changed in apparmor (Ubuntu Oracular):
importance: 	Critical &#8594; High 

---

### Post by flokosx on 2024-07-20
> **1fallen said:**
> Yeah I'm not going to be doing that anytime soon. But you are free to run it however you see fit.

Ubuntu has changed the Ubuntu 24.04 kernel so that programs like bubblewrap are not allowed to create a new user namespace unless they are given an AppArmor profile that contains the userns permission. This is their choice, and if it's causing a problem for you, please report it to them. Changes in bubblewrap are not going to solve this.

EDIT: My thoughts, What they are doing instead is adding a profile for each program that uses bubblewrap, including Flatpak, Steam, nautilus/GNOME Files (via libgnome-desktop), epiphany/GNOME Web (via WebKitGTK) and so on, as well as adding a profile for each program that does not use bubblewrap but does similar things a different way, such as Firefox and Chrome. If you are using some different program that invokes bwrap - for example mkosi - my understanding is that they would tell you to add a profile for that program instead of a profile for bwrap.

I personally think their stated reasoning is flawed: they say that the reason is that giving bwrap a profile like this would allow for an arbitrary bypass of their restriction, but programs like the ones for which they are adding profiles are not designed to impose a security boundary that distrusts their caller either, so it's straightforward for an unprivileged user to bypass their restriction anyway. But I didn't design their security model, and what they choose to do in their distro is not my decision.

EDIT2: I also run apparmor on Arch or Arch Based systems but I don't see settings not being saved....This is on Ubuntu where the settings are not preserved.


Could you tell me the command to revert the change described? I tried "sudo aa-enable /usr/bin/bwrap" but it returned error  :(

---

### Post by #&amp;thj^% on 2024-07-20
> **flokosx said:**
> Could you tell me the command to revert the change described? I tried "sudo aa-enable /usr/bin/bwrap" but it returned error  :(

Show me the error please:

I would probably use something like:
```
sudo aa-enforce /usr/bin/bwrap
Setting /usr/bin/bwrap to enforce mode.
Warning: profile bwrap represents multiple programs

```

---

### Post by flokosx on 2024-07-21
> **1fallen said:**
> Show me the error please:

I would probably use something like:
```
sudo aa-enforce /usr/bin/bwrap
Setting /usr/bin/bwrap to enforce mode.
Warning: profile bwrap represents multiple programs

```

[COLOR=#000000][FONT=&amp]sudo aa-enforce /usr/bin/bwrap return a error[/FONT][/COLOR][FONT=monospace][COLOR=#000000]:


Traceback (most recent call last):[/COLOR]
  File "/usr/sbin/aa-enforce", line 33, in <module>
    tool.cmd_enforce()
  File "/usr/lib/python3/dist-packages/apparmor/tools.py", line 134, in cmd_enforce
    for (program, prof_filename, output_name) in self.get_next_for_modechange():
  File "/usr/lib/python3/dist-packages/apparmor/tools.py", line 97, in get_next_for_modechange
    aaui.UI_Info(_('Profile for %s not found, skipping') % output_name)
                 ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
TypeError: 'NoneType' object is not callable


An unexpected error occurred!

For details, see /tmp/apparmor-bugreport-j1uym2qs.txt
Please consider reporting a bug at [https://gitlab.com/apparmor/apparmor/-/issues](https://gitlab.com/apparmor/apparmor/-/issues)
and attach this file.

[/FONT]

---

### Post by #&amp;thj^% on 2024-07-21
You just learned a valuable lesson, on running commands off or from the net you know nothing about....It happens though, and your not alone.

I never ran the disable " /usr/bin/bwrap" so might be the difference, plus I'm on 24.10 now.
```
apt policy apparmor
apparmor:
  Installed: 4.0.1-0ubuntu1
  Candidate: 4.0.1-0ubuntu1
  Version table:
 *** 4.0.1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```
```
sudo aa-status|grep bwrap
   bwrap
   unpriv_bwrap

```

They are still working on fix, and may land in 2 weeks.
> 
John Johansen
@jjohansen · 2 days ago
Owner

yes, it will be re-uploaded asap, but that does mean it going to take more than 2 weeks, as it first has to land in 24.10 going through proposed for 7 days and then at least another 7 days in 24.04 proposed.


---

### Post by flokosx on 2024-07-22
> **1fallen said:**
> You just learned a valuable lesson, on running commands off or from the net you know nothing about....It happens though, and your not alone.

I never ran the disable " /usr/bin/bwrap" so might be the difference, plus I'm on 24.10 now.



You have to understand that I had no alternative but to execute the command that was advised. And look: the system is serving me perfectly. As I saw that there was an apparmor update, I became interested in learning how to reverse the procedure I had done. I understand that you are warning me about potential damage I could do to the system, but I would be much happier if you taught me how to undo what I did.

---

### Post by #&amp;thj^% on 2024-07-24
I feel we always have alternative or choice, ie: You have qbittorrent flatpak, and qbittorrent .deb, there may even be a snap qbittorrent IJDK I don't run snaps.

I did not see him advise you to do anything, but merely note what he did to make settings work again. (you took it upon yourself to use the code)
Both versions of installed Faltpak and .deb is the problem in saving settings.

My .deb qbittorrent works as expected. Now if I (note) Remove the .deb install and go with flatpak qittorrent then all is good there as well.

I would also be much happier if there was a reversal for the code "You" decided to run.

I did try to help with "sudo aa-enforce /usr/bin/bwrap" but your system throws errors, but mine dose not.

There may (in theory) be a nuclear approach to this, but it's not my system so I use common sense and remain silent.

And have you tried to ask in the bug report on how to reverse that code you followed

---

### Post by #&amp;thj^% on 2024-07-24
I will take a look at these though to see if I can indeed help, so show me this: (Wrapped in code tags)
```
ls /etc/apparmor.d/*|grep disabled 
```
and
```
 ls /etc/apparmor.d/disable/*

```
This one I really do want to see:
```
ls /etc/apparmor.d/*|grep bwrap-userns-restric

```
But to enable a disabled profile goes just like I showed you earlier:
Now proceed and enable a disabled profile using the command with the below syntax:
```

##Enable a Profile
sudo aa-enforce /path/to/profile
```

BTW You have something else going on with your system look below:
```
 sudo aa-disable /usr/bin/bwrap
Disabling /usr/bin/bwrap.

```
I even rebooted to see if that mattered and as I suspected it did not.
```
sudo aa-enforce /usr/bin/bwrap
Setting /usr/bin/bwrap to enforce mode.
Warning: profile bwrap represents multiple programs

```
```
sudo aa-status|grep bwrap 
   bwrap
   unpriv_bwrap

```

I just read where they are now fast tracking the fix : [https://launchpad.net/ubuntu/+source/apparmor/4.0.1really4.0.0-beta3-0ubuntu0.1](https://launchpad.net/ubuntu/+source/apparmor/4.0.1really4.0.0-beta3-0ubuntu0.1)
>  * This drops /etc/apparmor.d/bwrap-userns-restrict, allowing various
    Flatpak apps to save files again.

EDIT This is more for my notes, but Arch dose not use that bwrap mode, ie:
```
sudo aa-disable /usr/bin/bwrap
Disabling /usr/bin/bwrap.
Profile for /usr/bin/bwrap not found, skipping
bash: Disabling: command not found
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> sudo aa-enforce /usr/bin/bwrap
Profile for /usr/bin/bwrap not found, skipping

```

---

### Post by flokosx on 2024-07-25
ls /etc/apparmor.d/*|grep disabled 
Returns nothing
 

ls /etc/apparmor.d/disable/*
Returns
[FONT=monospace][COLOR=#ff5454]**/etc/apparmor.d/disable/bwrap-userns-restrict**[/COLOR]

[/FONT]ls /etc/apparmor.d/*|grep bwrap-userns-restric
Returns 
[FONT=monospace][COLOR=#FF5454]**bwrap-userns-restrict**[/COLOR]

[/FONT]

---

### Post by #&amp;thj^% on 2024-07-25
I had a feeling I'd hear from you today, but All i have tried and I won't show here for other readers safety, but no changes Ive made
thus far has not solved the unsaved settings. We are just going to have to be patient for the fix to roll in slowly.
I'm running 24.10 with the necessary sources enabled, and nothing yet seen.

I'll update this when/if I see a change.

---

### Post by #&amp;thj^% on 2024-08-04
UPDATE: In oracular 24.10 x86_64 the apparmor just came in today.
```
apt policy apparmor apparmor-utils
apparmor:
  Installed: 4.0.1really4.0.1-0ubuntu2
  Candidate: 4.0.1really4.0.1-0ubuntu2
  Version table:
 *** 4.0.1really4.0.1-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status
apparmor-utils:
  Installed: 4.0.1really4.0.1-0ubuntu2
  Candidate: 4.0.1really4.0.1-0ubuntu2
  Version table:
 *** 4.0.1really4.0.1-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu oracular/main amd64 Packages
        100 /var/lib/dpkg/status

```

And flatpak seems to function correctly now..

[s]If your not on 24.10 it will be 2 to 3 weeks more to see how this is working on other versions of Buntu.[/s]
EDIT: It is Noble as well
```
apparmor | 4.0.0-beta3-0ubuntu3              | noble           | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 apparmor | 4.0.1really4.0.0-beta3-0ubuntu0.1 | noble-updates   | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x
 apparmor | 4.0.1really4.0.1-0ubuntu2         | oracular        | source, amd64, arm64, armhf, i386, ppc64el, riscv64, s390x

```

---

