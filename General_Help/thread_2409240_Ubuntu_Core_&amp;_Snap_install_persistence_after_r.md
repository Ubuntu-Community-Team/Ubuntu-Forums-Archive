---
title: "Ubuntu Core &amp; Snap install persistence after reboot (Mir-Kiosk, Chromium-Browser)"
date: 2018-12-30
forum: General Help
---

### Post by otacon-bl on 2018-12-30
Hello Community folks! I'm woefully inexperienced with Ubuntu-Core & Snaps, and hopefully I'm in the right section for this. I'm afraid my issue is a little all over the place, so hopefully the following breaks down everything sufficiently.

[B]
TL;WR:[/B] 
Installed snaps on ubuntu-core won't persist through reboot. Is it because ubuntu-core functions as a live cd until a new image with the installed snaps/configs is created?



[B]The backstory:
[/B]I'm trying to make a kiosk to display a web page that uses (I'm assuming) newer functions of Javascript, on various Raspberry Pi units. Initially I was doing this on a Pi0-w with a custom image based on Raspbian Stretch Lite, and using Chromium-Browser in kiosk mode. Chromium-Browser, despite being the most latest version on Raspbian (65) did not like this. Wouldn't display the custom page parts using that particular bit of JS. 

After trying various flavours of Raspbian, and various browsers, all of them suffered the same issue. Instead of trying new browsers, I started looking at other distros and custom images. After much tinkering, flashing, reflashing and SSHing, I happened upon Ubuntu Core, and loaded it onto a Pi3 b+. 

[B]The midstory:
[/B]Flashed Ubuntu core, set up my SSO & SSH keys as per the Ubuntu website instructions and remoted in. Following [this guide]("https://tutorials.ubuntu.com/tutorial/secure-ubuntu-kiosk#0") *(specifically steps 1-3; step 4 seemed odd, as the tutorials it links to talks about creating applications, which I'm not)*.   Installed mir-kiosk and chromium-browser (beta). Tried the webpage. **It works, hooray!** From what I've read about Ubuntu Core, it's receiving a lot of treatment and attention at the moment, so it's not at all surprising it supports a more updated and fleshed out version of Chromium Browser.

[B]The problem:
[/B]Set my browser homepage, and custom config like removing the navbar, mouse pointer etc. Restarted the Pi, and Ubuntu Core loads up, and presents me with the familiar 'here's your ssh details for logging in.' 

Log in remotely, all previously installed snaps are gone. It was as if I were running a live cd with zero persistence.

Back to Google, Ubuntu support pages etc, and do more reading. Start seeing a lot of material about having to create custom builds which involve combining various snaps, talks about a layers; gadget snaps, kernel snaps, app snaps, etc. Get thoroughly confused.


**The curiosity problem:** 
I'm not a developer, I'm not creating a product or sharing my own work. The guides I saw about publishing snaps talk about creating new images, whipping up YAML configs and publishing to the store for evaluation and deployment - but I'm not creating anything for the community, or selling a product; all I'm doing is using existing snaps and literally adjusting 3 config options. That's it. 

The more I've read, (and please, educate me if I'm wrong) the more it looks like what I'm supposed to do is all of the above, and then export all of the previous work as a new image, flash **that**, and then that image is supposed to do what I'm expecting it to - boot directly into Chromium-Browser in Kiosk mode with the supplied configuration. 

As I'm not **creating** anything, just adding a little extra data to tell Chromium-Browser what to do, it seems wrong to publish that on a public platform. 


[B]In all:
[/B]1) How do I keep my installed snaps persistent through reboot?
2) Am I supposed to publish the image with my configuration changes, and if so, where should I be reading to do so? 


Thank you kindly if you've persisted *(puns!) *through my rambling. Any assistance is much appreciated.

**UPDATE: **Snaps are now persistent through boot, and appear in 'snap list', but the RPi3b+ running the Ubuntu Core image does not boot directly into the Mir-Kiosk & Chromium Browser. Is this by design until a configuration setting I've missed is changed?

---

### Post by clementc on 2018-12-31
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

A quick search unearthed [this bug]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1572125") from 2016.

And according to [this page]("https://github.com/snapcore/snapd/pull/1042"), the issue has been resolved.

My first question is: what version of Ubuntu Core are you running?

Can you please try getting the latest release from [https://www.ubuntu.com/download/iot](https://www.ubuntu.com/download/iot) and see if this help resolve your issue?

Please report back once you have tried or if you are already running Ubuntu Core 18 (the latest release at the time of this writing).

---

### Post by otacon-bl on 2019-01-01
Thanks for the response! I'm using *ubuntu-core-18-armhf+raspi3. *Will download the most recent version via your link and let you know my findings.

---

### Post by otacon-bl on 2019-01-01
Okay, I've redownloaded newest core image for RPi3 builds. 
Flashed to microsd card. Popped card into RPi3b+.
Snap Installed Mir-Kiosk.
Snap Installed Chromium-mir-kiosk from the beta channel. 
Set kiosk config, check page. It works as before.

Run snap-list, returns this:


```
Name                Version         Rev   Tracking  Publisher   Notes
chromium-mir-kiosk  69.0.3497.100   32    beta      gerboland   -
core                16-2.36.3       6132  stable    canonical*  core
core18              18              538   stable    canonical*  base
mir-kiosk           1.1.0           1002  stable    canonical*  -
pi                  18-0.1          2     18-pi3    canonical*  gadget
pi-kernel           4.15.0-1028.30  15    18-pi3    canonical*  kernel
snapd               2.36.3          1977  stable    canonical*  snapd
```


Follow up with sudo reboot.

The soft reboot works, and loads into Mir-Kiosk / Chromium-Kiosk.


Turn power off and on again. 
Boots to SSH Login instructions, not Mir & Chromium.

SSH in, check snap list. Everything is there as it should be.

So that's half the problem resolved with a fresh image, so thanks for that advice! The question now is how do I get it to boot straight into the chromium kiosk from powering on and not just login instructions?

---

### Post by clementc on 2019-01-01
Hi [**otacon-bl**]("https://ubuntuforums.org/member.php?u=2115136"),

According to the snapcraft documentation (and more specifically [this page]("https://snapdocs.labix.org/the-snap-format/698")), adding a .destkop file (e.g. myautostart.desktop) with some specific commands under $SNAP_USER_DATA/.config/autostart[FONT=arial] should achieve what you are trying to do.

This is an example for the Ukuu application:

```
[Desktop Entry]
Type=Application
Exec=sh "/home/clement/.config/ukuu-notify.sh"
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_IN]=Ukuu Notification
Name=Ukuu Notification
Comment[en_IN]=Ukuu Notification
Comment=Ukuu Notification
```

Another page I found and which might help you (I hope) is [this one]("https://raspberrypi.stackexchange.com/questions/40631/setting-up-a-kiosk-with-chromium").

Finally, the official snapcraft forum can also be a good place to start: [https://forum.snapcraft.io/](https://forum.snapcraft.io/)

Please let us know how you go about your project and what has worked for you in the end.
[/FONT]

---

### Post by otacon-bl on 2019-01-01
Hi again clementc,

I think there's some crossed wires here, and I'm not sure if they're yours or (probably) mine.

> **clementc said:**
> According to the snapcraft documentation (and more specifically [this page]("https://snapdocs.labix.org/the-snap-format/698")), adding a .destkop file (e.g. myautostart.desktop) with some specific commands under $SNAP_USER_DATA/.config/autostart[FONT=arial] should achieve what you are trying to do.[/FONT]

Whilst very helpful, are these not instructions for the *authors* of the Snaps? As I'm a user, specifying configs via the "snap set" command, *not the developer* of the snaps in question, presumably I wouldn't have the access or even permissions to modify the contents of the snap in the way that you're suggesting?

Regarding the stack-exchange page you helpfully suggested, that refers to a different operating system (Raspbian), so I'm guessing those instructions wouldn't be valid for the config of Ubuntu Core. I did *initially* have a Raspbian install going, but I switched to Ubuntu-Core because Raspbian's latest stable release of Chromium wouldn't work with the Javascript I'm using in the webpage the Kiosk is pointing to. Essentially, the two options have the opposite problem:

[B]Boot Pi3b+ with Raspbian:
[/B]Web Kiosk loads from boot automatically, but Chromium Browser version (65) doesn't support the Javascript

**Boot Pi3b+ with Ubuntu Core:**
Chromium Version supports the Javascript and loads the web page, but doesn't boot into the kiosk automatically. Sits at SSH details login page.

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

Thank you for clarifying the remaining issues, it adds more clarity to this thread.

Regarding your **Pi3b+ with Raspbian**,  and if you still have it, can you please advise if the JavaScript issue  is only experienced when using --kiosk or even without this parameter?

---

### Post by otacon-bl on 2019-01-01
Grabbed a spare SD card and set up Raspbian like I had before; even without using the --kiosk flag for Chromium-browser, the JS elements of the page still didn't function properly. 

Get errors that the referenced .js file can't be found. [This]("https://raw.githubusercontent.com/thomasloven/lovelace-card-tools/master/card-tools.js") is the contents of what it's looking for. Works fine on mobile, Chrome on Windows 10, The version of Chromium that's used in Chromium-Mir-Kiosk.. just doesn't seem to work in the version of Chromium-Browser from the Raspbian Repos. 

This is why I was making the change to Ubuntu-Core for the Pi3b+, until I got hit with the not launching at boot problems.

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

Just to follow on the Raspbian set up running on your Pi3 b+, since this model is equipped with an ARM8 processor I believe, can you please run the following command on Raspbian and tell me the output:
dpkg --print-architecture

---

### Post by otacon-bl on 2019-01-02
Pi3 B+ Raspbian uses *armhf.*

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

This might be a bit of a long shot, but you could try updating Chromium on your Pi3 B+ Raspbian.

Here is the link to the latest version to date for the armhf architecture: [URL="https://packages.debian.org/stretch/armhf/chromium/download"]https://packages.debian.org/stretch/armhf/chromium/download
[/URL]
Updating Chromium (you might have to install the .deb package manually  using dpkg -i) will hopefully resolve your javascript issue (just a  hope).

Please let us know how you do with this.

---

### Post by otacon-bl on 2019-01-02
I think we're starting to get somewhere, but it's not making it easy. The chromium install has a bunch of required dependencies that aren't natively a part of raspbian stretch.

```
sudo dpkg -i chromium_70.0.3538.110-1~deb9u1_armhf.debSelecting previously unselected package chromium.
(Reading database ... 52218 files and directories currently installed.)
Preparing to unpack chromium_70.0.3538.110-1~deb9u1_armhf.deb ...
Unpacking chromium (70.0.3538.110-1~deb9u1) ...
dpkg: dependency problems prevent configuration of chromium:
 chromium depends on libavcodec57 (>= 7:3.2.12) | libavcodec-extra57 (>= 7:3.2.12); however:
  Version of libavcodec57:armhf on system is 7:3.2.10-1~deb9u1+rpt2.
  Package libavcodec-extra57 is not installed.
 chromium depends on libavformat57 (>= 7:3.2.12); however:
  Package libavformat57 is not installed.
 chromium depends on libavutil55 (>= 7:3.2.12); however:
  Version of libavutil55:armhf on system is 7:3.2.10-1~deb9u1+rpt2.
 chromium depends on libflac8 (>= 1.3.0); however:
  Package libflac8 is not installed.
 chromium depends on libminizip1 (>= 1.1); however:
  Package libminizip1 is not installed.
 chromium depends on libnspr4 (>= 2:4.9-2~); however:
  Package libnspr4 is not installed.
 chromium depends on libnss3 (>= 2:3.22); however:
  Package libnss3 is not installed.
 chromium depends on libpci3 (>= 1:3.5.2-1); however:
  Package libpci3 is not installed.
 chromium depends on libpulse0 (>= 0.99.1); however:
  Package libpulse0 is not installed.
 chromium depends on libre2-3 (>= 20160901); however:
  Package libre2-3 is not installed.
 chromium depends on libwebpdemux2 (>= 0.5.1); however:
  Package libwebpdemux2 is not installed.
 chromium depends on libxslt1.1 (>= 1.1.25); however:
  Package libxslt1.1 is not installed.
 chromium depends on libxss1; however:
  Package libxss1 is not installed.
 chromium depends on x11-utils; however:
  Package x11-utils is not installed.
 chromium depends on xdg-utils; however:
  Package xdg-utils is not installed.

```

Are there any install switches for DPKG that I can use to have these downloaded before trying to unpack and install Chromium, or would I have to go through the list manually and install all of them (either via apt-get or more manual wget downloads from security.debian.org)?

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

After running dpkg -i to mark the needed dependencies, please run: *sudo apt-get -f install* to install them.

---

### Post by otacon-bl on 2019-01-02
Aye, I was reading up about installing local packages and saw that may be required. Tried it. Just says Chromium will be removed.

As we've downloaded chromium from the link you gave, I presumed that the sources would need to be updated, so I've made sure to add 
```
deb http://security.debian.org/debian-security stretch/updates main
``` to */etc/apt/sources.list*, but yeah - still just says Chromium will be removed.

---

### Post by clementc on 2019-01-02
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

Did you run *sudo apt update* after adding the line in your sources.list file?

And what if you remove Chromium then reinstall it?

---

### Post by otacon-bl on 2019-01-02
Mea culpa, mea culpa, mea maxima culpa. Forgot to *apt update.*

Nearly there. Chromium seems to have installed properly, but now when running it in the instructions found [here]("https://die-antwort.eu/techblog/2017-12-setup-raspberry-pi-for-kiosk-mode/"), *(replacing chromium-browser references from the Raspi repos with our now updated Chromium from the Debian repos), *when I fire off startx, all I get is a grey screen. Hrm.

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

Would you be able to install *Raspbian Stretch with desktop* rather than *Raspbian Stretch Lite* (from [here]("https://www.raspberrypi.org/downloads/raspbian/")) and try installing the latest version of Chromium the way you just did?

I believe that there is something that the fully fledged version of Chromium might not like with the lite version of Raspbian.

---

### Post by otacon-bl on 2019-01-03
I can certainly do that, but the idea of using the desktop-less image to begin with was to reduce as much bloat as possible and booting straight into a chromium-based kiosk; by using the *desktop* image, will I not have to strip out a lot of excess after? Perhaps more importantly, will the guides I've been following thus far still be as relevant?

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

I understand your reasoning behind using the light version of Raspbian. However, you will still be able to boot straight into Chromium using the full version of the OS as well. It is just a matter of setting it up for it. You will also be able to reduce the size of the image by removing utilities you don't need.

However, please also have a look at the following three websites first, maybe they will suit your needs better:

[https://www.binaryemotions.com/digital-signage/raspberry-digital-signage/](https://www.binaryemotions.com/digital-signage/raspberry-digital-signage/)
[URL="https://sourceforge.net/projects/raspberrywebkiosk/"]https://sourceforge.net/projects/raspberrywebkiosk/
[/URL][https://www.danpurdy.co.uk/web-development/raspberry-pi-kiosk-screen-tutorial/](https://www.danpurdy.co.uk/web-development/raspberry-pi-kiosk-screen-tutorial/)[URL="https://sourceforge.net/projects/raspberrywebkiosk/"]
[/URL]

---

### Post by otacon-bl on 2019-01-03
Edging closer and closer..

Flashed Raspbian Stretch with desktop. Removed the existing Chromium browser (v65), updated sources.list as we did before, used the deb package to install Chromium (v70), and otherwise followed the instructions in the third link you've just provided *(I'd ideally like to build this myself to learn rather than use a pre-made package) *and now we've switched problems again; Rpi boots, into desktop, autoloads chromium, but something still isn't quite supported. 

It loads in Kiosk mode, but then automatically exits after a couple of seconds, before even loading the webpage. In the meanwhile I'll give the pre-made images of the first two links a go, but I'd like to continue to troubleshoot this if you're happy to continue assisting!

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

Can you please try running this command to remove any incorrect chromium config files and try starting it again:

rm -R ~/.config/chromium/*

---

### Post by otacon-bl on 2019-01-03
Done, same issue. Opens and closes almost immediately.

*(And, tried the builds from your first and second links for pre-made images, both the same issue as when I first started. Chromium version isn't up to date enough to recognise it)*

---

### Post by grahammechanical on 2019-01-03
This tutorial might help you. Notice the point about installing mir-kiosk-apps & also the point about using the snap set command to set mir-kiosk-apps apps = to an app.

[https://developer.ubuntu.com/core/examples/snaps-on-mir?_ga=2.218789145.1051351272.1546565707-1326125738.1466083458](https://developer.ubuntu.com/core/examples/snaps-on-mir?_ga=2.218789145.1051351272.1546565707-1326125738.1466083458)

Regards

---

### Post by clementc on 2019-01-03
Hi [**[COLOR=#000000]otacon-bl[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115136"),

Unfortunately, I am running out of things you can try to get this working.

However, I do hope that someone here will be able to help you more. Please do not hesitate to let us know how you do regarding this project.

Good luck and thank you for trying all the commands I provided you with.

---

### Post by otacon-bl on 2019-01-03
Hi **grahammechanical**, thanks for weighing in!

On the microsd running ubuntu core, I've reflashed and restarted everything from the beginning, installing mir-kiosk and chromium-mir-kiosk (beta). Looking at the page you've linked, it looks to me that setting the snap with *'app=' *seems to be just for *'mir-kiosk-apps' , *which I presumably don't need to install as I already know that the snap I need is '[I]chromium-mir-kiosk'. 

[/I]On the chance that I'm wrong, I've run the command 

```
sudo snap set mir-kiosk app=chromium-mir-kiosk
```

to try to set chromium to be the app that mir-kiosk runs. Doesn't seem to have made a difference. Upon sudo reboot, the client pi running ubuntu core just boots back to the host keys info & login address screen.

On ssh-ing back into the machine to check the list, the snaps are still installed, however now using 

```
sudo snap start mir-kiosk
```
or
```
sudo snap start chromium-mir-kiosk
```
seems to do nothing, despite the command line saying they've been started. No change on the display screen that the Pi is plugged into.

If it's of any use, I've just checked the chromium-mir-kiosk logs, and it output the following:

```
otacon-bl@localhost:~$ snap logs chromium-mir-kiosk
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: ln: failed to create symbolic link '/root/snap/chromium-mir-kiosk/32/snap/chromium-mir-kiosk/32/Documents': No such file or directory
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: ln: failed to create symbolic link '/root/snap/chromium-mir-kiosk/32/snap/chromium-mir-kiosk/32/Desktop': No such file or directory
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: ln: failed to create symbolic link '/root/snap/chromium-mir-kiosk/32/snap/chromium-mir-kiosk/32/Downloads': No such file or directory
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: ln: failed to create symbolic link '/root/snap/chromium-mir-kiosk/32/snap/chromium-mir-kiosk/32/Music': No such file or directory
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: ln: failed to create symbolic link '/root/snap/chromium-mir-kiosk/32/snap/chromium-mir-kiosk/32/Pictures': No such file or directory
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: ln: failed to create symbolic link '/root/snap/chromium-mir-kiosk/32/snap/chromium-mir-kiosk/32/Videos': No such file or directory
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: ln: failed to create symbolic link '/root/snap/chromium-mir-kiosk/32/snap/chromium-mir-kiosk/32/Public': No such file or directory
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: ln: failed to create symbolic link '/root/snap/chromium-mir-kiosk/32/snap/chromium-mir-kiosk/32/Templates': No such file or directory
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: Error: Unable to find a valid Wayland socket in /run/user/0
2019-01-04T03:09:23Z chromium-mir-kiosk.chromium-mir-kiosk[8563]: Is a Wayland server running?

```


**Clementc**, thanks for your help nonetheless, tis appreciated very much!

---

### Post by kevinbutchart on 2019-01-13
I tried the same setup and found, while the mir-kiosk and chromium were indeed running, they started up on a different virtual terminal (vt). 

In my case this was vt4. So you could switch to it manually with Ctrl-Alt-F4

In order to make it start on boot, I switched it to vt=1

snap set mir-kiosk vt=1

Rebooting then worked as expected

---

### Post by otacon-bl on 2019-01-13
> [COLOR=#000000]snap set mir-kiosk vt=1[/COLOR]

**Confirmed solution!**

Unfortunately chromium-mir-kiosk doesn't seem to maintain cookies; the page that I'm pointing to as the starting URL redirects to a login page, and those saved credentials don't persist through reboot, but will have a look at solutions to that when I have more time/patience available. Kevin, I owe you several glasses of red!

---

