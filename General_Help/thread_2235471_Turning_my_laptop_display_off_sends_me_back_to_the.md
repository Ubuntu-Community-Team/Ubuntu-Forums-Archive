---
title: "Turning my laptop display off sends me back to the login screen."
date: 2014-07-21
forum: General Help
---

### Post by anubeon on 2014-07-21
[B]Greetings All!

[/B]Ever since upgrading to Ubuntu 'Trusty' 14.04 I've experience an issue with my display. Specifically, whenever I suspend my laptops display I am thrown back to the login screen (unity-greeter). This happens whether the display is suspended automatically (i.e. via the power management settings under system settings) or manually (i.e. via xset dpms commands).  Upon suspension of the display it will typically suspend for a second, then the backlight will flash off and on a couple of times, the nVidia logo will appear and I'll find myself back at the unity-greeter with the display defiantly on.

I should clarify at this point that I am **not** logged out but rather sent to the unity-greeter as a lock-screen. This perplexes me as I was under the impression that as of 'Trusty' Ubuntu had yet to implement a lightDM based lock-screen, and that the distinctive gnome-screensaver was still the default lock-screen. Is this presumption incorrect?

Frankly I haven't the faintest idea how to begin diagnosing this rather annoying issue. I don't even know which logs to check for identifiable errors, but as a start I've included sections of my syslog and auth.log from the approximate time that I issued an *xset dpms force off* command in a terminal. One other thing, I did experience the same issue for a couple of months under 'Saucy' but it seemed to clear itself up after an update about a month or so before the release of 'Trusty'. I don't whether that sheds any light on this issue, but I thought it pertinent to mention. 

> **syslog]
**Jul 21 12:42:23** lees-vaio acpid: client 1467[0:0] has disconnected
**Jul 21 12:42:23** lees-vaio acpid: client connected from 20783[0:0]
**Jul 21 12:42:23** lees-vaio acpid: 1 client rule loaded
**Jul 21 12:43:04** lees-vaio acpid: client 20783[0:0] has disconnected
**Jul 21 12:43:06** lees-vaio pulseaudio[20895]: [pulseaudio] sink-input.c: Failed to create sink input: sink is suspended.
**Jul 21 12:43:08** lees-vaio acpid: client connected from 1467[0:0]
**Jul 21 12:43:08** lees-vaio acpid: 1 client rule loaded
**Jul 21 12:43:19** lees-vaio acpid: client 1467[0:0] has disconnected
**Jul 21 12:43:19** lees-vaio acpid: client connected from 20783[0:0]
**Jul 21 12:43:19** lees-vaio acpid: 1 client rule loaded
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-network: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26 **lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.sleep-wake: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.352': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-network: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.sleep-wake: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wifi: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wwan: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.enable-disable-wimax: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:26** lees-vaio NetworkManager[10233]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.351': no such name
**Jul 21 12:43:27** lees-vaio acpid: client 20783[0:0] has disconnected
**Jul 21 12:43:27** lees-vaio acpid: client connected from 1467[0:0]
**Jul 21 12:43:27** lees-vaio acpid: 1 client rule loaded
[/QUOTE]

[QUOTE=auth.log]
**Jul 21 12:42:26** lees-vaio lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
**Jul 21 12:42:26** lees-vaio lightdm: PAM adding faulty module: pam_kwallet.so
**Jul 21 12:42:26** lees-vaio lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
**Jul 21 12:42:26** lees-vaio systemd-logind[1395]: New session c6 of user lightdm.
**Jul 21 12:42:26** lees-vaio lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :1
**Jul 21 12:42:42** lees-vaio lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
**Jul 21 12:42:42** lees-vaio lightdm: PAM adding faulty module: pam_kwallet.so
**Jul 21 12:42:42** lees-vaio lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "anubeon"
**Jul 21 12:43:26 **lees-vaio lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
**Jul 21 12:43:27** lees-vaio dbus[1295]: [system] Rejected send message, 2 matched rules said:**
> : [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.362" (uid=110 pid=20961 comm="/usr/lib/x86_64-linux-gnu/indicator-bluetooth/indi") interface="org.bluez.Manager" member="DefaultAdapter" error name="(unset)" requested_reply="0" destination="org.bluez" (uid=0 pid=1356 comm="/usr/sbin/bluetoothd ")


I'm running Ubuntu 'Trusty' 14.04 x86-64 on a Sony VAIO VGN-FZ31M with an nVidia Geforce 8400M GT GPU. I'm also running the latest version of the nidia-331 propritary drivers (version 331.38 at time of writing).

Any assistance in diagnosing and fixing this issue would be greatly appreciated. The limited functionality of xbacklight just won't cut it for much longer, I need to be able to turn my display off.

[B]Kind Regards,

Lee.[/B]

---

### Post by lucke2 on 2014-08-20
It looks like an X server crash. Look at /var/log/Xorg.0.log.

---

### Post by anubeon on 2014-08-21
Thanks for the advice @lucke2. 

I've just triggered a screen blank but since XOrg uses relative time stamps I don't know quite what is relevant in the log file. I've uploaded the whole lot to pastebin and I'd appreciate it if anyone more adept at tracing down bugs of this nature could take a look and see if there's anything obvious.

[Xorg.0.log]("http://pastebin.com/PggncjXq")

Incidentally, is there any way to convert relative time stamps such as these into more human readable time stamps? I've tried the following as directed on numerous forums but it's giving me yesterdays date for the latest timestamp, which is obviously wrong (as one such time stamp was added whilst I had gedit open, so refers to an event today).

```

date -d "-?????.??? seconds"

```

Thanks in advance. :-)

---

### Post by bra|10n on 2014-08-21
I presume you've already checked your settings in System Settings > Brightness & Lock?

---

### Post by anubeon on 2014-08-21
Yes, of course. All's well there as far as I can tell. Regardless, those settings shouldn't have any bearing on manual screen 'suspensions' executed via ```
xset dpms force off
```

---

### Post by lucke2 on 2014-08-21
I see no errors in that log. Did you see lightdm after blanking the screen that time?

Maybe there is something interesting in ~/.xsession-errors.

---

### Post by anubeon on 2014-08-24
> **lucke2 said:**
> Did you see lightdm after blanking the screen that time?

Yes (in the form of Unity-Greeter).

> **lucke2 said:**
> Maybe there is something interesting in ~/.xsession-errors.

These are the only new entries within ~/.xsession-errors:

[QUOTE=xsession-errors]
(gnome-settings-daemon:2482): color-plugin-WARNING **: failed to set screen _ICC_PROFILE: Failed to open file '/var/lib/lightdm/.local/share/icc/edid-fcacff6803f8e06cea6c50e59bd84f83.icc': Permission denied

(gnome-settings-daemon:2482): color-plugin-WARNING **: failed to set screen _ICC_PROFILE: Failed to open file '/var/lib/lightdm/.local/share/icc/edid-fcacff6803f8e06cea6c50e59bd84f83.icc': Permission denied[/QUOTE]

---

### Post by anubeon on 2014-09-05
Upon further reflection, I think that the aforementioned error (in ~/.xsession-errors) was merely coincidental. Having manually changed the permissions of the colour profile mentioned within, the error no longer shows up in ~/.xsession-errors but my issues with screen blanking continue. 

One other think which may or may not be relevant. Suspending the system (as opposed to just the display) will typically work the first 2-3 times, but will fail on the 4th and subsequent attempts per session. Whether successful or not, the display cycles through 2-3 mode changes and on unsuccessful attempts returns me to the nVidia splash-screen followed by Unity-Greeter/LightDM. There's also an unexplained rectangular artefact which persists on the right hand side of the Unity-Greeter (previously reported [here]("http://ubuntuforums.org/showthread.php?t=2221281")). I Don't know whether that sheds any light on the situation at all.

Still at a loss to diagnose much less remedy this issue. So… Bump?

---

