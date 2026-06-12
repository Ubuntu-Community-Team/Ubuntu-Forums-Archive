---
title: "Login Screen Returns to Login Screen, Ubuntu 12.10"
date: 2012-12-19
forum: General Help
---

### Post by AbeFM on 2012-12-19
Hey everyone - seen countless topics here and abroad on this subject - they seem to fall into two categories - those with permissions issues in home directory (they seem to be able to login as other accounts) and those with graphics issues, which honestly I haven't tried tracking down.

Basically, machine comes up, I get login screen (I had it set to bypass this). Incorrect passwords get a complaint, correct ones get me a couple seconds of black screen and then it returns. The same happens with the guest account, and I installed gnome-shell and it behaves the same way.

I have like 60,000 characters of log files and errors, which aside from being too much for the forum, are too much to read.

FYI - I can still log in via terminal (alt-ctl-F1 etc), everything seems ok. Permissions are good and I've since written them over anyway. I can access the computer from outside - SSH'ing in, doing updates, and I can get files off it from around the network via windows shares.


A few interesting bits:```

/var/log/auth.log:Dec 18 23:38:29 HBO lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "abe"
```
Odd since I used to log in that way.

```

/var/log/kern.log:Dec 18 23:38:25 HBO kernel: [    4.382811] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \_SB_.PCI0.GFX0.TCOI 1 (20120320/utaddress-251)
```
Not sure if it's meaningful. I had tweaked settings with integrated graphics in the bios, but I have since put them back. Could something have flipped and I need to re-install the graphics driver? If so, how?


```
abe@HBO:~$ cat .xsession-errors
initctl: Unknown job: lightdm-session
The script you are attempting to invoke has been converted to an Upstart
job, but gnome-session --session=ubuntu is not supported for Upstart jobs.

```
Sure seems like something is wrong here. Reinstalled lightdm and restated countless times.

When I run apt-get, it always holds back 2 upgrades, linux kernal and headers.

About the only other thing I can think to mention is that the system is on an SSD - which sometimes has errors. I scanned it and didn't find anything wrong - based on this:
```
abe@HBO:~$ sudo fsck -n /dev/mapper/ubuntu-root
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
Warning!  /dev/mapper/ubuntu-root is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/mapper/ubuntu-root: clean, 346460/1684256 files, 1778855/6725632 blocks

```

Lastly, Subsonic doesn't appear to be running. Not sure if that's important. I can restart the service from the command prompt, but I can't see it running and some of the settings files don't appear to be where they should be. Interesting since it's a recently installed program.

Anyway - very interested in fixing this. It's my main home theater machine and I'd like to do some entertaining over the weekend.

System Info: i3-2100t on an h67(I think) chipset. onchip graphics and sound. I sometimes run a second monitor (projector).

---

### Post by pqwoerituytrueiwoq on 2012-12-19
```
sudo apt-get update;sudo apt-get dist-upgrade
```see if it works after you do that and a reboot
also try to install the ubuntu-desktop/xubuntu-desktop/kubuntu-desktop/lubuntu-desktop package or whichever you are using
does the guest session work?

---

### Post by AbeFM on 2012-12-19
yeah - I tried updating. It always says those two are held back - everything else goes just fine.

OH WAIT! Heh. I swear I tried that before, but now it's working.

Everything I'm running is vanilla. So, I'd do like... 
sudo apt-get reinstall ubuntu-desktop?

eidt: No, guest session doesn't work either. Tried all variants, too, they don't work either.

---

### Post by AbeFM on 2012-12-19
Updated all, force reinstalled ubuntu-desktop. Same result.

Tried to boot in safe graphics mode - it runs fsck twice - once on boot partition, once on root. Both come up clean, then it just sits there.

After a few minutes, I hit ctrl-c and esc and such, and it continues to a text login.

I login, type "sudo lightdm" and screen goes black.... and that's it, unresponsive to all input (no other terminals, etc).... EXCEPT, hitting power button makes it shutdown seemingly cleanly.

---

### Post by linuxcoffeelover on 2012-12-19
I remember I have a problem similar where I was unable to login in via the login screen but was still able to login at the prompt. I think the root account had taken control of the .Xauthority  file or something.

I hope this helps.

[http://askubuntu.com/questions/130387/stuck-at-login-screen](http://askubuntu.com/questions/130387/stuck-at-login-screen)

sorry not sure if I can post a link to an external site.

---

### Post by AbeFM on 2012-12-20
> **linuxcoffeelover said:**
> I remember I have a problem similar where I was unable to login in via the login screen but was still able to login at the prompt. I think the root account had taken control of the .Xauthority  file or something.

I hope this helps.

[http://askubuntu.com/questions/130387/stuck-at-login-screen](http://askubuntu.com/questions/130387/stuck-at-login-screen)

sorry not sure if I can post a link to an external site.

>  Permissions are good and I've since written them over anyway.

Thanks, but, I've tried that. To death. :-)

---

### Post by apochry on 2012-12-20
Have you tried ```
sudo chown username:username .Xauthority
``` where you replace "username" with yours?

Or possibly the first answer in [this]("http://askubuntu.com/questions/129610/login-screen-wont-accept-my-password") askubuntu.

It seems the case when files in your /home folder get owned by root, which often happens when running graphical applications as root using the "sudo" command, which is WRONG. More on this [here]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo").

Regards
 - Christo

---

### Post by steeldriver on 2012-12-20
> **AbeFM said:**
> 
```
abe@HBO:~$ cat .xsession-errors
initctl: Unknown job: lightdm-session
The script you are attempting to invoke has been converted to an Upstart
job, but gnome-session --session=ubuntu is not supported for Upstart jobs.

```

Do you by any chance have a custom ~/.xsession or ~/.xinitrc maybe? or a modified /etc/X11/Xsession?

---

### Post by dannyboy79 on 2012-12-20
have you checked to make sure your / or /home partitions aren't full?

---

### Post by AbeFM on 2012-12-21
Plenty of space to go around, nothing I know of is terribly custom. Unless there's something in installing subsonic (new version out recently) I've got nothing.

---

### Post by fdrake on 2012-12-21
i had the same problem once i did this:
```

sudo aptitude remove gnome 
sudo apt-get install gnome

```
restart.
hope this works for you

if not post/attach your "dmesg" output

---

### Post by hic3456 on 2013-04-28
Thanks!
that was exactly my problem: .Xauthority owned by root:root
(how did *that* happen???)

You're a star!

---

