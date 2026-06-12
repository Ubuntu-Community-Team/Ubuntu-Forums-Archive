---
title: "Chromium and Chrome is started in processes but not showing as visible program."
date: 2014-06-25
forum: General Help
---

### Post by STAUNCH on 2014-06-25
Hello,

I have recently purchased a VPS that is using for it's virtualization - [OpenVZ]("http://en.wikipedia.org/wiki/OpenVZ"). On the server is installed as main OS - "Ubuntu **14.04** Server" 64-bit version. Then used those commands to install Lubuntu:

```
dpkg --configure -aapt-get install lubuntu-desktop
apt-get update
apt-get upgrade
```
Installed X2GoServer and logged in via the X2GoClient, all fine. But when I tried to install Chromium:

```
apt-get install chromium-browser
```
All fine, then started and… it's running into the Task Manager but not visible into the desktop as app (it's window). Tried few times, the same thing. Firefox/Thunderbird and other apps are working well.

Then installed Google Chrome following **[this]("http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/")** guide. Started and… the same like Chromium - it's running but not visible. Then I wrote into Putty's terminal:

```
chromium-browser
google-chrome
```
And for both of them is saying this error message:

```
***PID namespaces supported Network namespace supportedbut failed: errno = Operation not permitted***
```
I have browsed around the web and read those similar threads with my issue (but not exactly with the same error):

[http://ubuntuforums.org/showthread.php?t=2217965](http://ubuntuforums.org/showthread.php?t=2217965)
[https://productforums.google.com/forum/#!topic/chrome/2YM0vcVQnV8](https://productforums.google.com/forum/#!topic/chrome/2YM0vcVQnV8)
[http://askubuntu.com/questions/286075/no-satisfiable-dependency-for-dependency-libudev0/286081#286081](http://askubuntu.com/questions/286075/no-satisfiable-dependency-for-dependency-libudev0/286081#286081)
[http://ubuntuforums.org/showthread.php?t=2195570](http://ubuntuforums.org/showthread.php?t=2195570)
[http://ubuntuforums.org/showthread.php?t=2220207](http://ubuntuforums.org/showthread.php?t=2220207)
[http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/](http://itsfoss.com/fix-flash-player-issue-chromium-in-ubuntu-14-04/)
[https://github.com/travis-ci/travis-ci/issues/938](https://github.com/travis-ci/travis-ci/issues/938)
[http://askubuntu.com/questions/258435/sudo-apt-get-install-google-chrome-stable-current-amd64-deb-is-not-working](http://askubuntu.com/questions/258435/sudo-apt-get-install-google-chrome-stable-current-amd64-deb-is-not-working)
[http://ubuntuforums.org/showthread.php?t=2225589](http://ubuntuforums.org/showthread.php?t=2225589)
[http://ubuntuforums.org/showthread.php?t=2228382](http://ubuntuforums.org/showthread.php?t=2228382)

But no link have any resolution regarding my problem. If someone knows what commands I need to test and verify, libs to install, etc. - can write here. Also I can provide you with a direct TeamViewer access to see exactly what is wrong and verify, something that would be way more fast (PM me).

Also to mention that every time when I connect to the VPS using Putty, it's saying an error:

```
***GLib-CRITICAL: Source ID 131 was not found when attempting to remove it***
```
131 is always some other random number. And when I connect to the VPS using X2Go is saying some PID error message that I need to click OK in order to continue and the graphic interface to be shown.

Regards.

---

### Post by STAUNCH on 2014-06-25
Hm, just tried few other things but no success again.

---

### Post by STAUNCH on 2014-06-26
No answers, seems no one knows or?

---

### Post by pretty_whistle on 2014-06-28
Did you try this:

Kill process on both browsers in the task manager.  Then try to open browsers.

This is all I can think of.

---

### Post by STAUNCH on 2014-06-28
Yeah, I have trying killing the process from the Task Manager, then starting the browser again - no change. Don't know if this OpenVZ environment is blocking something, because another member that is using a pricey VPS - the same Kubuntu and Ubuntu - said to me no problem there with Chromium and/or Chrome. But the VPS environment there is not "emulated" it's a dedicated server.

---

### Post by STAUNCH on 2014-06-29
[https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/577919](https://bugs.launchpad.net/ubuntu/+source/gdm-guest-session/+bug/577919)
[https://code.google.com/p/chromium/issues/detail?id=31077](https://code.google.com/p/chromium/issues/detail?id=31077)
[http://lowendtalk.com/discussion/17637/chrome-browser-and-chronium-not-working-opening-in-debian-7-openvz](http://lowendtalk.com/discussion/17637/chrome-browser-and-chronium-not-working-opening-in-debian-7-openvz) - the comment from "dhamaniasad" - **"[COLOR=#000000][FONT=lucida grande]Chrome and chromium don't work on OpenVZ."**

Is that true? Really?[/FONT][/COLOR]

---

