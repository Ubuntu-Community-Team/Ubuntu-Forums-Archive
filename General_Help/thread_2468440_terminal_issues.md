---
title: "terminal issues"
date: 2021-10-29
forum: General Help
---

### Post by coley9225 on 2021-10-29
I have encountered a rather strange behavior in my terminal. I'm attempting to enter a command, and when it reaches the edge of the window, instead of dropping to a new line, it returns on same line and begins typing over the prompt. If I backspace, it deletes only to the right of my current spot, will only go back partway, or backs up to other lines, including into remnants of previous commands. Sometimes, if I close the terminal, and relaunch it works as it should, and sometimes it continues this strange behavior. It's quite maddening, to be honest. I can't get screengrab to work right, so I can't post a screenshot, sorry. Any ideas on what would cause such craziness, and how I can fix this. Thanks in advance for any tips.
I'm using Lubuntu 20.04 with all updates and the issue is in qtterminal 0.14.1

---

### Post by TheFu on 2021-10-29
Try entering:
stty sane

Even if you can't exactly see the text - type those characters and <enter>.  Then see if that doesn't fix it.  If not, kill the terminal and open a new one. Should be fine now.

---

### Post by coley9225 on 2021-10-30
Thanks thefu, but it is still doing it. I rebooted and no help. I have also tried konsole and xterm, and they do the same thing. This is nutty. I changed my prompt a few months ago and terminal worked fine since. I recently added an echo command and cowsay and fortune lines to terminal, and have since commented out those lines. I'm ruling those mods out because terminal was doing this off and on well before I made those changes. I can run any commands as long as they fir on 1 line, so I can go full screen or at least full width, and everything seems to be ok.

---

### Post by TheFu on 2021-10-30
Did you change locale/languages?

---

### Post by coley9225 on 2021-10-30
thefu...I haven't made any changes to my system except install a couple of terminal based apps and any recommended upgrades. The apps I installed are 'fortune', which I've had before, 'tt' which is a typing tutor type app for teerminal, 'cowsay, just because it's another cool thing I can do with linux, 'sl' just to check it out. All of these  were installed from terminal with apt install, from the repositories, and none should change any system settings such as locale or language. I can just continue to widen my screen, or use a tty console to run some of the longer commands, I use 2 monitors so terminal on 1 and run fullscreen, it's more of inconvenience than anything else. All commands seem to run fine. If it matters, I do upgrades from either discover, or from terminal with sudo apt update, apt list upgradable, and sudo apt upgrade.

---

### Post by sudodus on 2021-10-30
Are you willing to try some other terminal emulator, for example

```

sakura

```

---

### Post by TheFu on 2021-10-30
What about "sudo apt full-upgrage" to get on the supported kernel?

---

### Post by coley9225 on 2021-10-30
sudodus..I've tried konsole and xterm, but always willing to try new thing(which sometimes leads me to trouble..lol). I'll give the terminal emulator you mentioned and see what happens, as long as it defaults to bash, don't want to overload myself learning a new shell at this time. Thefu, I'll try that, but out of curiosity, what's the difference between that and the standard sudo apt upgrade?

---

### Post by TheFu on 2021-10-30
> **coley9225 said:**
> Thefu, I'll try that, but out of curiosity, what's the difference between that and the standard sudo apt upgrade?

As usual, the manpage answers:
```
       upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.

       dist-upgrade (i.e. full-upgrade)
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The dist-upgrade
           command may therefore remove some packages. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.

```
apt and apt-get use the same backends. Typically, apt passes commands to apt-get ... except where apt has added processing like how it can install .deb files directly, then resolve dependencies, which apt-get doesn't handle.  For normal weekly patching, there isn't a difference.
The apt manpage says this:
```
       upgrade (apt-get(8))
           upgrade is used to install available upgrades of all packages
           currently installed on the system from the sources configured via
           sources.list(5). New packages will be installed if required to
           satisfy dependencies, but existing packages will never be removed.
           If an upgrade for a package requires the removal of an installed
           package the upgrade for this package isn't performed.

       full-upgrade (apt-get(8))
           full-upgrade performs the function of upgrade but will remove
           currently installed packages if this is needed to upgrade the
           system as a whole.
```
Notice how it points to apt-get's manpage for both options?  Basically, using apt saves typing "-get"  ;)

---

### Post by coley9225 on 2021-10-30
I ran sudo apt full-upgrade, and it didn't appear to upgrade anything. At this point, should I try upgradeing the release, upgrade to 20.10, then 21.04, and then to 21.10? I do daily backups with timeshift, so if things go sideways, I can always restore back to todays set up. I just don't want to go through a fresh install and have to reinstall all my apps if I can avoid it.
After running full-upgrade the terminal is still acting strange.

---

### Post by dragonfly41 on 2021-10-30
Curious, I just searched to find this thread ..

[https://unix.stackexchange.com/questions/492809/bash-shell-doesnt-start-a-new-line-upon-return-and-doesnt-show-typed-command](https://unix.stackexchange.com/questions/492809/bash-shell-doesnt-start-a-new-line-upon-return-and-doesnt-show-typed-command)

suggests running /usr/bin/reset

Also suggests running
[COLOR=#000000]stty sane
 as in post #2.


[/COLOR]

---

### Post by coley9225 on 2021-10-30
thanks dragonfly41. I tried all the suggestions in the referred post, and still no fix. Like I mentioned earlier, if I my the terminal window wide enough, then there is no issues, but when a thinner window, rather than continue on the next line it returns without a new line and starts overwriting the same line. I can work around the issue by using full screen or at least full width, but ti's just strange behavior. I'm digging for a fix not just for me, but if someone with only 1 monitor has this issue it would be exponentially more inconvenient than it is for me. I appreciate everyone's help, as always. I will hold off a little longer to see if this can be resolved, but I may just go with the release upgrade plan and cross my fingers.

---

### Post by sudodus on 2021-10-30
I guess sakura did not solve the problem, otherwise you would have told us.

Please try with the same version, 20.04.3 LTS of Lubuntu and Xubuntu. Try them **live, booted from USB** (without installing). That way you can tell if the problem is specific to your particular installed and tweaked Lubuntu system, or if it happens also with a 'clean' version of 20.04.3 LTS in your computer.

---

### Post by Impavidus on 2021-10-30
If you create a new user, does the problem affect that user too? I think it may be a problem with your settings. Either the settings of the shell or something all the terminals have in common.

I remember once seeing a similar problem om my computer, but it must have been over a decade ago. I don't remember if I had to do anything to fix it.

---

### Post by coley9225 on 2021-10-30
I just completed upgading from 20.04.3 to 21.04, and the problem is still there. Now my system seems to be moving in slow motion. I am going to reboot into linux mint and see if the problems are present in that distro, and if not I will install the suggested terminal emulator and see if that helps. Not sure what to do about the major slowdown of my system.

---

### Post by sudodus on 2021-10-30
> **coley9225 said:**
> I just completed upgading from 20.04.3 to 21.04, and the problem is still there. Now my system seems to be moving in slow motion. I am going to reboot into linux mint and see if the problems are present in that distro, and if not I will install the suggested terminal emulator and see if that helps. Not sure what to do about the major slowdown of my system.

The major slowdown may be caused by some old cruft from 20.04.3 that should not be there in 21.04, and it is probably difficult to find. I suggest that you restore to 20.04.3 from backup. But before that you should test the other ideas, that you and several other people have suggested in this thread.

---

### Post by coley9225 on 2021-10-30
I just installed sakura, and it does the same thing. My Linux Mint won't boot. So I'm going to reboot into lubuntu 20.04 from my live usb and see how it works in there.

---

### Post by TheFu on 2021-10-30
Try a new userid. I bet that solves it.

Try moving the user's setup files out of the way so they cannot be used.   ~/.bashrc and ~/.profile are the main ones.  Don't need them to login. They are nice to have. 

I've never seen any upgrade fix stuff. It just makes it worse.  If you want an LTS release, don't upgrade off 20.04 until next July at the earliest.

Do you do any virtual machines?  That's a good place to screw around with non-LTS releases, for fun.

---

### Post by dragonfly41 on 2021-10-30
Assuming that there must always be others with same problem I found this next thread .. 10 years old ..

[https://askubuntu.com/questions/24358/how-do-i-get-long-command-lines-to-wrap-to-the-next-line](https://askubuntu.com/questions/24358/how-do-i-get-long-command-lines-to-wrap-to-the-next-line)

---

### Post by sudodus on 2021-10-30
Good catch @dragonfly41 :KS

---

### Post by coley9225 on 2021-11-01
Sorry I haven't responded in a couple of days. After doing the release upgrade, I tried to revert back to previous setup with timeshift, and ended up with scrambled, unbootable system. Install a linux distro on my machine is a lesson in patience, to say the least. I'm happy to say I have a functional system again. Doing a reinstall fixed the terminal issue, but I still don't know what happened. I'm going to keep better track of my changes,(especially bashrc changes), so if it happens again I will have a better idea of what went wrong. Thanks for all the help, you guys are great. Going to mark as solved, and if it happens again I'll be back to beg for more help.

---

### Post by ajgreeny on 2021-11-01
I am not sure why it should do anything related to your problem but I wonder what might happen if you restored your ~/.bashrc file, which can have some effects on the terminal GUI, to the default of a new installation.

Have you made many, or even a few changes to that file during your use of 20.04 or is is still as it was when you installed the OS?

I am not aware of the terminal GUI being changed in this way; it's normally just the prompt that you see that can be changed but I guess I'm grasping at straws here, just throwing out ideas.

---

### Post by coley9225 on 2021-11-02
Thanks ajgreeny, I think you helped figure out the issue. After I reinstall lubuntu, I tried to change my terminal prompt, and the problem was back, I commented out the PS1 change, and it's working fine again. Now I need to figure out what I'm doing wrong in that endeavor( the default show full path to current working directory and I don't want it to do that). Anyway, thanks again to all for the help.

---

### Post by dragonfly41 on 2021-11-02
[COLOR=#000000]*"Now I need to figure out what I'm doing wrong"*

[/COLOR]Did you follow the tips in link in post #19 which discusses PS1? Again ..

[https://askubuntu.com/questions/24358/how-do-i-get-long-command-lines-to-wrap-to-the-next-line](https://askubuntu.com/questions/24358/how-do-i-get-long-command-lines-to-wrap-to-the-next-line)

---

### Post by coley9225 on 2021-11-03
I did read that post(twice), and I guess I was typing the changes wrong. I found a different article and followed it, changing the '\e' to '033' and now it is working fine again. The line I added is:
PS1="\[\033[32m\]\u:\[\033[00m\]\$ ".  And my new prompt is:  charles:$  It doesn't and the path to the current directory, which is what I wanted. A wise man created the pwd command, so if I lose track of where I am, I can get a map quite easily. Thanks for the help.

---

### Post by johnakers446 on 2021-11-05
I tried restarting the computer, but that didn't work. I've tried konsole  as well, and they all yield the same effects. This is completely ridiculous. My prompt was changed a few months ago, and terminal has been running flawlessly since then. I recently added an echo command, as well as COSWAY and fortune lines, to terminal, which I have since edited out. Because terminal was functioning weirdly before I made those changes, I'm ruling out those customizations. Its insane that I am looking forward to build my career in [android app development]("https://designprosusa.com/android-app-development") and having difficulties to tackle such problems.  I can run any command that fits on a single line, so I can go full screen or at least full width, and everything seems to be working OK.

---

### Post by dragonfly41 on 2021-11-05
> *[COLOR=#000000]Its insane that I am looking forward to build my career in [/COLOR][android app development]("https://designprosusa.com/android-app-development")*[COLOR=#000000]* and having difficulties to tackle such problems. *[/COLOR]

Perhaps look into .bashrc (as earlier in this thread) and also try an IDE such as here ..

[https://www.jetbrains.com/help/idea/create-your-first-android-application.html#107b188b](https://www.jetbrains.com/help/idea/create-your-first-android-application.html#107b188b)

---

