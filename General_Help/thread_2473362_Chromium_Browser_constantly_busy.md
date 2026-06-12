---
title: "Chromium Browser constantly busy"
date: 2022-04-01
forum: General Help
---

### Post by WacoJohn on 2022-04-01
Raspberry Pi 400, Ubuntu PRETTY_NAME="Ubuntu 21.10" Impish.  Chromium Version 99.0.4844.84 (Official Build) snap (64-bit).  Chromium seems to be constantly busy.  The rotating 'gadget' spins constantly.

  In the attachment, is the top bar of Ubuntu ..... showing Activities, Chromium Web Browser, a spinning circle indicating busy, the date, and shutdown options etc.  The circle spins constantly no matter what web page.

Earlier, I was running Firefox SNAP and several experts suggested I replace that with a NON SNAP version of FF.  They walked me through doing that.  I am wondering if I should be running Chromium NON SNAP as well(?)  If so, I would need help doing that.  Until then, I had never heard of SNAP so I AM NO EXPERT. 

 In any case, this rotating activity signal is discerning and I'm not sure what to make of it.  Any comments, opinions, advice welcome in advance.

---

### Post by DuckHook on 2022-04-01
Please use only standard fonts and styles in your posts. Unusual fonts and styles are difficult to read, especially on small screens.

---

### Post by WacoJohn on 2022-04-02
My apologies.  I guess you edited it for me.  I don't recall what I had done and can't see it.  If you can mention the violations, I will avoid making the same mistakes.

---

### Post by DuckHook on 2022-04-02
No problem. I did edit your post to make it more readable.

Your OP used a roboto font in a light colour that lacked contrast against the light forum background, making it difficult to read. It's difficult to guess why it happened, but it likely involved your actively choosing a font and colour in your original post. If you refrain from choosing a font, colour or style when posting, this should allow the forum software to use its default settings and the post will conform to forum standards.

Good Luck and Happy Ubuntu-ing!

---

### Post by WacoJohn on 2022-04-02
WOW!!!    I have no idea how that happened, and I did not notice it when I posted.  No doubt something I did.  Thank you for all the input,. ..  The odds are very slim it will happen again.  :P

---

### Post by DuckHook on 2022-04-02
FTR, you may not have done anything to bring about the above. Forum software may have been acting up, in which case, it was not due to any action on your part and there would not have been anything you could have done about it.

Odd. Staff will be keep eyes peeled for other such anomalies in other threads.

Thanks for your understanding.

---

### Post by WacoJohn on 2022-04-02
I think this glitch hijacked my post.  No offer of Chromium help.  Maybe i should repost???  Never been in this situation before.

---

### Post by DuckHook on 2022-04-02
You are right.

In all of the noise, your initial problem got left behind.

Here's what I would suggest:

[LIST=1]
[*]Run htop to see what your processor and memory are up to when the "busy" icon is rolling.
[*]Check you logs to see if there is anything strange going on.
[*]Invoke Chromium from the command line to see if any errors crop up when running.
[/LIST]
There's not actually a lot I can help you with. I ran Chromium years ago, but not recently. Hopefully, a more recent user sees this thread and can make a more worthwhile contribution.

Remember that you can *bump* your thread every 12 hrs to keep it atop the pile.

---

### Post by WacoJohn on 2022-04-03
> **DuckHook said:**
> 

Here's what I would suggest:

[LIST=1]
[*]Run htop to see what your processor and memory are up to when the "busy" icon is rolling.
[*]Check you logs to see if there is anything strange going on.
[*]Invoke Chromium from the command line to see if any errors crop up when running.
[/LIST]
There's not actually a lot I can help you with. I ran Chromium years ago, but not recently. Hopefully, a more recent user sees this thread and can make a more worthwhile contribution.

Remember that you can *bump* your thread every 12 hrs to keep it atop the pile.

Thank you for ANY help.
[LIST=1]
[*]Never heard of htop before.  Ran it, and it is terrifying.  No clue how to 'extract' any conclusion from it.  Very advanced for me.
[*]Check logs.  I will try to find how to do that.  Uhm ... thank you.
[*]Command line 'Chromium' returned many errors and warnings, but executed Chromium and with no busy icon!
[/LIST]

```
owner@pi400:~$ sudo chromium
mkdir: cannot create directory '/run/user/0': Permission denied
[5562:5562:0403/105921.868139:ERROR:zygote_host_impl_linux.cc(90)] Running as root without --no-sandbox is not supported. See https://crbug.com/638180.
owner@pi400:~$ chromium
Gtk-Message: 10:59:32.321: Failed to load module "canberra-gtk-module"
Gtk-Message: 10:59:32.326: Failed to load module "canberra-gtk-module"


(chrome:5680): dbind-WARNING **: 10:59:32.608: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-dsAuTDCYDW: No such file or directory
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to open kms_swrast: /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri/kms_swrast_dri.so: cannot open shared object file: Permission denied (search paths /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri)
failed to load driver: kms_swrast
MESA-LOADER: failed to open swrast: /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri/swrast_dri.so: cannot open shared object file: Permission denied (search paths /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri)
failed to load swrast driver
[5680:5805:0403/105938.669399:ERROR:udev_watcher.cc(98)] Failed to begin udev enumeration.
[5789:5789:0403/105939.223430:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 1 times!
[5680:5680:0403/110036.764641:ERROR:object_proxy.cc(623)] Failed to call method: org.freedesktop.ScreenSaver.GetActive: object_path= /org/freedesktop/ScreenSaver: org.freedesktop.DBus.Error.NotSupported: This method is not implemented
[5680:5680:0403/110036.768594:ERROR:object_proxy.cc(623)] Failed to call method: org.gnome.ScreenSaver.GetActive: object_path= /: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.151" (uid=1000 pid=5680 comm="/snap/chromium/1955/usr/lib/chromium-browser/chrom" label="snap.chromium.chromium (enforce)") interface="org.gnome.ScreenSaver" member="GetActive" error name="(unset)" requested_reply="0" destination="org.gnome.ScreenSaver" (uid=1000 pid=1643 comm="/usr/bin/gjs /usr/share/gnome-shell/org.gnome.Scre" label="unconfined")
[5789:5789:0403/110804.126239:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 2 times!
[5789:5789:0403/111142.119200:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 3 times!
```

And Terminal did not exit.  It's sitting right there, but Chromium ran ... no busy indicator.  This info is provided for anyone who can help.  I'm a Linux 1st grader .. been one for many years.

---

### Post by dragonfly41 on 2022-04-03
I have no experience with running Ubuntu on Raspberry Pi (although I would like to try it one day).

I tend to look at keywords in posts (as clues) and I found this ..

[https://forums.raspberrypi.com/viewtopic.php?t=323687](https://forums.raspberrypi.com/viewtopic.php?t=323687)

Can you try clearing the Chromium cache?

And what size RAM is installed?

[P.S.] Tried another search strategy. Keys: "Ubuntu" and "spinning" as you wrote in post#1.

[https://forums.raspberrypi.com/viewtopic.php?p=1639170&hilit=ubuntu+spinning#p1639170](https://forums.raspberrypi.com/viewtopic.php?p=1639170&hilit=ubuntu+spinning#p1639170)

---

### Post by WacoJohn on 2022-04-03
> **dragonfly41 said:**
> I have no experience with running Ubuntu on Raspberry Pi (although I would like to try it one day).

I tend to look at keywords in posts (as clues) and I found this ..

[https://forums.raspberrypi.com/viewtopic.php?t=323687](https://forums.raspberrypi.com/viewtopic.php?t=323687)

Can you try clearing the Chromium cache?

And what size RAM is installed?

**Pi 400s come maxed out at 4GB.**

Thank you for your post.  That link is for Raspberry OS 'Buster' which has been replaced by 'Buster' (CORRECTON:  _BULLSEYE_) some time ago.  I am running Ubuntu.
Yes, I can try clearing the cache.  Right now, I am puzzled by the outcome of the troubleshooting outlined just above.  Chromium busy went away as soon as I ran Chromium from terminal.  I forced closed terminal, ..... still no Busy (problem solved???).  Have not yet closed and reopened Chrome from desktop.  Will do that and come back here to update this reply.

EDIT:  So I rebooted machine.  Busy problem came back on desktop execution of Chromium.  Rebooted, ran Chromium from terminal again (with errors and warnings).  Chromium opened with NO busy indication!

Terminal errors and warnings:

```
owner@pi400:~$ chromium
Gtk-Message: 12:15:01.236: Failed to load module "canberra-gtk-module"
Gtk-Message: 12:15:01.274: Failed to load module "canberra-gtk-module"

(chrome:1752): dbind-WARNING **: 12:15:24.433: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-mtE5u5CTXk: No such file or directory
[1752:1752:0403/121525.380609:ERROR:gpu_process_host.cc(974)] GPU process exited unexpectedly: exit_code=512
[1752:1752:0403/121526.408278:ERROR:network_service_instance_impl.cc(978)] Network service crashed, restarting service.
[1752:2183:0403/121537.818937:ERROR:udev_watcher.cc(98)] Failed to begin udev enumeration.
[1752:1752:0403/121540.610263:ERROR:gpu_process_host.cc(974)] GPU process exited unexpectedly: exit_code=512
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to open kms_swrast: /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri/kms_swrast_dri.so: cannot open shared object file: Permission denied (search paths /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri)
failed to load driver: kms_swrast
MESA-LOADER: failed to open swrast: /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri/swrast_dri.so: cannot open shared object file: Permission denied (search paths /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri)
failed to load swrast driver
[2432:2432:0403/121635.430664:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 1 times!
[2432:2432:0403/121640.992716:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 2 times!
[2432:2432:0403/121640.999845:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 3 times!
[1752:1752:0403/121644.166917:ERROR:object_proxy.cc(623)] Failed to call method: org.freedesktop.ScreenSaver.GetActive: object_path= /org/freedesktop/ScreenSaver: org.freedesktop.DBus.Error.NotSupported: This method is not implemented
[1752:1752:0403/121644.171051:ERROR:object_proxy.cc(623)] Failed to call method: org.gnome.ScreenSaver.GetActive: object_path= /: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.122" (uid=1000 pid=1752 comm="/snap/chromium/1955/usr/lib/chromium-browser/chrom" label="snap.chromium.chromium (enforce)") interface="org.gnome.ScreenSaver" member="GetActive" error name="(unset)" requested_reply="0" destination="org.gnome.ScreenSaver" (uid=1000 pid=1570 comm="/usr/bin/gjs /usr/share/gnome-shell/org.gnome.Scre" label="unconfined")
[2432:2440:0403/121709.969959:ERROR:x11_software_bitmap_presenter.cc(141)] XGetWindowAttributes failed for window 10485785
```

One more comment, .. since managing the busy situation with running from command line, Chromium is much more stable, doesn't stop responding (nearly as much) and I can now have more than 3 tabs open.  I REALLY hope we can get this fixed 'the right way'.  Maybe solution is to uninstall/reinstall Chromium(?)

---

### Post by WacoJohn on 2022-04-05
OK ... no help.  Let us try this.  This forum helped me replace a Firefox SNAP with a Firefox NONSNAP.  Did not work out for other reasons.  I think that may be the problem with this Chromium.  Could anyone possibly lead the way to obtaining/installing Chromium NONSNAP version?  Again, thank you in advance.

EDIT:
Perfect screen shot on how we downgraded(?) FF.  I would think it would be the same for Chromium .... but would not know for sure.  I hope it is as easy as it was for FF. Unfortunately, for some reason it won't upload/attach.

trying this:

[https://1drv.ms/u/s!AufnVD2fVv0Yh-xZ3kyF5bZO5HlMNw](https://1drv.ms/u/s!AufnVD2fVv0Yh-xZ3kyF5bZO5HlMNw)
[IMG]https://1drv.ms/u/s!AufnVD2fVv0Yh-xZ3kyF5bZO5HlMNw[/IMG]

---

### Post by DuckHook on 2022-04-05
Please post back to this thread the output of:```
apt policy libcanberra-gtk-module libcanberra-gtk3-module
```

---

### Post by WacoJohn on 2022-04-05
Restarted machine, ran Chromium from Desktop (Busy state).  Here is the output:

```
owner@pi400:~$ apt policy libcanberra-gtk-module libcanberra-gtk3-modulelibcanberra-gtk-module:
  Installed: (none)
  Candidate: 0.30-7ubuntu2
  Version table:
     0.30-7ubuntu2 500
        500 http://ports.ubuntu.com/ubuntu-ports impish/universe arm64 Packages
libcanberra-gtk3-module:
  Installed: 0.30-7ubuntu2
  Candidate: 0.30-7ubuntu2
  Version table:
 *** 0.30-7ubuntu2 500
        500 http://ports.ubuntu.com/ubuntu-ports impish/main arm64 Packages
        100 /var/lib/dpkg/status
owner@pi400:~$ 



```

If you want output after Terminal command Chromium let me know.

---

### Post by ajgreeny on 2022-04-05
If you want to use a non-snap chromium use the beta (or dev) version from the ppa available at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta) along with all details of how to enable it.

I have been using the dev version from the same ppa developer on one of my machines for a long time with no difficulties, and the beta version on another, also with no problems.

---

### Post by WacoJohn on 2022-04-05
> **ajgreeny said:**
> If you want to use a non-snap chromium use the beta (or dev) version from the ppa available at [https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta](https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta) along with all details of how to enable it.

I have been using the dev version from the same ppa developer on one of my machines for a long time with no difficulties, and the beta version on another, also with no problems.

Yes.  I would like to use a NONSNAP ver.  Thank you for the reply and the link.  Viewed the link, and about 75% is over my head.  Might be that someone has the time to guide me through it.  Way too many requirements which I have never done.  It mentions the use of a Chrome Folder and other things I do not have nor know how to get.  Thank you again.

---

### Post by DuckHook on 2022-04-05
> **WacoJohn said:**
> Restarted machine, ran Chromium from Desktop (Busy state).
--snip--
If you want output after Terminal command Chromium let me know.
Okay, it's a long shot, but do:```
sudo apt install libcanberra-gtk-module
```
This installs the older canberra gtk module. Current Chromium shouldn't really need it, but who knows? No harm in having the module installed, so give it a shot.

---

### Post by WacoJohn on 2022-04-05
Executed the code.  Restarted computer. Ran Chromium from Desktop.  No fix for the busy indicator.  Thank you again.

---

### Post by ajgreeny on 2022-04-06
I'm using an Android tablet at the moment so its difficult to copy/paste links and give you details of how to enable that ppa but basically all you need to do is remove the snap version then run the command sudo add apt repository as mentioned, ie,
```
Adding this PPA to your system
You can update your system with unsupported packages from this untrusted PPA by adding ppa:saiarcot895/chromium-beta to your system's Software Sources. (Read about installing)

sudo add-apt-repository ppa:saiarcot895/chromium-beta
sudo apt-get update
```
I've never bothered with all the palaver to get full acceleration as mentioned in all the long notes and chromium runs well for my needs without it; you may need it for other reasons, however I can't help with that.

EDIT:
I have just realised that you're using a Raspberry Pi so all my info about that ppa may be irrelevant as my knowledge of ppa use on them is zero..

---

### Post by WacoJohn on 2022-04-06
I immensely appreciate your time and input.  Just a recap on where I am at the moment.
Raspberry PI 400.
Chromium [COLOR=#5F6368][FONT=Roboto]Version 100.0.4896.60 (Official Build) snap (64-bit)
[/FONT][/COLOR]Ubuntu VERSION="21.10 (Impish Indri)"

Running Chromium from Desktop results in a constant 'Chromium Web Browser" busy state.  Performance is general lousy ...lots of failing to respond.
Running Chromium from Terminal results in a long list of errors and warnings:

```
owner@pi400:~$ chromiumGtk-Message: 08:21:22.042: Failed to load module "canberra-gtk-module"
Gtk-Message: 08:21:22.070: Failed to load module "canberra-gtk-module"
[1599:1779:0406/082122.427712:ERROR:object_proxy.cc(623)] Failed to call method: org.freedesktop.DBus.ListActivatableNames: object_path= /org/freedesktop/DBus: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.105" (uid=1000 pid=1599 comm="/snap/chromium/1955/usr/lib/chromium-browser/chrom" label="snap.chromium.chromium (enforce)") interface="org.freedesktop.DBus" member="ListActivatableNames" error name="(unset)" requested_reply="0" destination="org.freedesktop.DBus" (bus)


(chrome:1599): dbind-WARNING **: 08:21:24.918: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-EJzymrEM1s: No such file or directory
[1599:1714:0406/082130.986424:ERROR:udev_watcher.cc(98)] Failed to begin udev enumeration.
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to retrieve device information
MESA-LOADER: failed to open kms_swrast: /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri/kms_swrast_dri.so: cannot open shared object file: Permission denied (search paths /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri)
failed to load driver: kms_swrast
MESA-LOADER: failed to open swrast: /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri/swrast_dri.so: cannot open shared object file: Permission denied (search paths /snap/chromium/1955/gnome-platform/usr/lib/aarch64-linux-gnu/dri)
failed to load swrast driver
[1791:1791:0406/082149.341318:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 1 times!
[1791:1791:0406/082149.352287:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 2 times!
[1791:1791:0406/082149.358717:ERROR:gl_surface_presentation_helper.cc(260)] GetVSyncParametersIfAvailable() failed for 3 times!
[1599:1599:0406/082225.212993:ERROR:interface_endpoint_client.cc(659)] Message 0 rejected by interface blink.mojom.WidgetHost
[1599:1786:0406/082335.743215:ERROR:udev_watcher.cc(98)] Failed to begin udev enumeration.
[1599:1599:0406/082525.978382:ERROR:interface_endpoint_client.cc(659)] Message 0 rejected by interface blink.mojom.WidgetHost
[1599:1599:0406/082533.138887:ERROR:object_proxy.cc(623)] Failed to call method: org.freedesktop.ScreenSaver.GetActive: object_path= /org/freedesktop/ScreenSaver: org.freedesktop.DBus.Error.NotSupported: This method is not implemented
[1599:1599:0406/082533.146327:ERROR:object_proxy.cc(623)] Failed to call method: org.gnome.ScreenSaver.GetActive: object_path= /: org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.116" (uid=1000 pid=1599 comm="/snap/chromium/1955/usr/lib/chromium-browser/chrom" label="snap.chromium.chromium (enforce)") interface="org.gnome.ScreenSaver" member="GetActive" error name="(unset)" requested_reply="0" destination="org.gnome.ScreenSaver" (uid=1000 pid=1500 comm="/usr/bin/gjs /usr/share/gnome-shell/org.gnome.Scre" label="unconfined")
[1791:1791:0406/085659.511835:ERROR:gl_utils.cc(315)] [.RenderCompositor-0xffff84004f50] GL_INVALID_FRAMEBUFFER_OPERATION: Framebuffer is incomplete: Attachment is not renderable.
[1791:1791:0406/085659.517219:ERROR:gl_utils.cc(315)] [.RenderCompositor-0xffff84004f50] GL_INVALID_FRAMEBUFFER_OPERATION: Framebuffer is incomplete: Attachment is not renderable.
[1791:1791:0406/085659.518981:ERROR:gl_utils.cc(315)] [.RenderCompositor-0xffff84004f50] GL_INVALID_FRAMEBUFFER_OPERATION: Framebuffer is incomplete: Attachment is not renderable.
[1791:1791:0406/085659.714181:ERROR:gl_utils.cc(315)] [.RenderCompositor-0xffff84004f50] GL_INVALID_FRAMEBUFFER_OPERATION: Framebuffer is incomplete: Attachment is not renderable.
[1791:1791:0406/085659.717404:ERROR:gl_utils.cc(315)] [.RenderCompositor-0xffff84004f50] GL_INVALID_FRAMEBUFFER_OPERATION: Framebuffer is incomplete: Attachment is not renderable.
[1791:1791:0406/085659.718744:ERROR:gl_utils.cc(315)] [.RenderCompositor-0xffff84004f50] GL_INVALID_FRAMEBUFFER_OPERATION: Framebuffer is incomplete: Attachment is not renderable.
owner@pi400:~$
```

BUT Chromium opens .... NO constant BUSY indication at top of Desktop and Chromium performs Much, much better.  Faster, few response failures.

**This is posted for anyone willing to help won't have to go through the entire thread.**

---

