---
title: "Remote Desktop"
date: 2024-01-31
forum: General Help
---

### Post by gordi21x6-8 on 2024-01-31
Hello everyone, I've installed Ubuntu on a PC that will serve as a web server, specifically Ubuntu 24.04. Everything went well with the installation, and I didn't encounter any issues configuring it. I set up remote access and changed the password to a personal one. The problem is that whenever I restart or log out, the password gets randomly generated again.


Is there any way to keep the password fixed permanently? Since it's a server machine, I can't be physically present every time I need to access it.


Apologies if I haven't explained myself clearly as I'm using a translator since my English level is very basic.


If this is not the appropriate place to post it, I kindly ask the administrators to move it to its corresponding place. Thank you very much in advance.

---

### Post by TheFu on 2024-01-31
Ubuntu 24.04 isn't release and shouldn't be used except for testing.  Perhaps the Ubuntu 24.04.1 release will be ok for servers. That will come around August.
Bugs are expected with pre-alpha software like 24.04.

I won't be installing 24.04 until June, which is a few months after the late-April release planned.  I wait a few months for each, huge, bugs to be corrected.
BTW, "New" isn't "better."  **New** is the enemy of **stable**.

**For remote access, use ssh.  That's the short answer.**

There are multiple ways to setup remote access.  VNC, RDP, should be avoided for security and performance reasons.  NX is the more secure and more efficient protocol, if you need a full desktop.  Of course, since 24.04 isn't released, all bets are off. Nobody knows how external projects will or won't work.  

For now, stick with ssh.  ssh is the way that Unix systems communicate. It is the core way to transfer files (sftp, scp, rsync, etc.), backup files (rdiff-backup and most other backup tools that are network aware use ssh tunnels), do secure remote system management (ssh, ansible, clusterssh, etc) and ssh is the basis for about 50 other commonly used tools.  BTW, ssh -X will allow you to run remote programs (including GUI programs) on remote computers, but have the window displayed on your local workstation.  This isn't new. It has been possible since the mid-1990s with ssh, but since the mid-1980s using normal X/Windows without ssh providing the authentication and network tunnel.

User passwords don't change, so if that's happening, chalk it up to running pre-alpha software.  If the remote access tool you are using has a separate password, you are doing it wrong.  Run, don't walk, run away!

---

### Post by ActionParsnip on 2024-01-31
I suggest you report a bug.

What are you wanting to do on the remote system that needs the full remote desktop? There may be a sleeker solution to what you want to achieve

---

### Post by eggsome on 2024-03-06
Hey, I just wanted to say thank you for asking this question. I found this thread when I was trying to understand why I could not login via RDP to 24.04 at all.
I had no idea that the username/password were different from the system accounts (which I don't think is completely off base, since they pre-populate the currently logged in user as the default username anyway).

However I then ended up with your problem, in that the password would rotate after every reboot/login.
The solution to this is to set the password on the command line like this:
```
 grdctl rdp set-credentials Username Password
```

In my testing, credentials set this way persisted across reboots, but in the event they don't for you - you could always setup a startup script to force this.

---

### Post by rob190 on 2024-10-23
The problem is the keyring doesn't get unlocked. The usual way around this is to create a new keyring WITHOUT a password and set it as the default. Delete the remote desktop password from the 'Login' keyring. Reboot. If you can, check the new keyring is still set as the default. Set the remote desktop password. Logging in via remote desktop will then add that password to the current default keyring. Once that is done, set the original 'Login' keyring to default.

---

### Post by ds526 on 2024-11-08
About half a year has passed since 24.04 Noble Numbat was officially released.  Now that 24.04.1 is out I made the leap to install Numbat on my test VM.  I had some "fun" figuring out the use cases for the two different tabs/screens for Desktop Sharing and Remote Login under the System Settings in this new LTS.   When or why would a user choose to use one versus the other, or both?  Below is an anecdotal account of my experience, and some caveats I encountered along the way.  Keeping in mind, I am not a veteran Ubuntu user, and Windows 10 is my daily driver OS, so some of this info may seem obvious to many readers but it might be useful to novice users or Windows daily drivers. The bulk of my experience with Linux started around 1997 with Slackware and my usage had been centered around the CLI aspects of the operating system, running it as a server OS instead of a GUI.  So the fact that we now have a graphical Linux distribution in the year 2024 that we can finally RDP into from a Windows client, is a great accomplishment! This will help speed up the adoption of the Linux desktop, I hope.

The **Desktop Sharing **page:  "Share your existing desktop with other devices. The remote connection uses the existing screen resolution"
* "Existing" means that you must be actively logged in to a desktop session!
* This page has an extra toggle option that says "Remote Control" to "allow desktop **shares **to control the screen". Leave this OFF for a read-only, view-only connection. No mouse/keyboard input allowed from the remote connectors.
* Share**s**: meaning multiple remote users can connect & view and/or control.  I connected twice to the share from the same remote computer and was able to see what the other sessions were doing.
* It's basically RDP plus the ability for the local user to watch the remote user(s).  On a Windows machine, this would be known as "Remote Assistance" (however, I've never really used that feature, so IDK)
* The port to connect to is 3390, a non standard RDP port. UNLESS you have disabled Remote Login, then the port will stay 3389. Maybe it can be customized in some config file somewhere to something completely different.
* I went and changed the resolution and it correctly changed on the remote computer but the local display became corrupt and completely lost control.
* You will _not_ be able to connect from a remote machine unless the user is logged in and their Gnome session is running.
* When my local screen went Locked after 5 minutes, my RDP session(s) was killed.

The **Remote Login** page:  "Remotely connect to your user account when it isn't being used. The display resolution can be set from the remote."
* This screen requires the user to elevate/authenticate to let you change these options. I believe it is because an additional root/kernel-land network service or module is being activated, I would guess.
* This port will be ALWAYS 3389, the standard RDP port.  Maybe it can be customized in some config file somewhere to something completely different.
** The display resolution can be set from the remote?  *We'll see about that...
* It's only for one user at a time.  This is the more "pure" Microsoft Windows RDP style experience, however, once connecting from the RDP client, you still have to log in again using your local Linux account so there are those extra steps.

***Login Details***... This might confuse new users... because it's just the login for the RDP protocol and not to the desktop session.  Once you login via RDP you still have to login via the Ubuntu desktop mechanisms.  *Keychain/Keyring password* popped up at some point and I'm not sure what initiated it...  I think someone above had this same issue.   I might have goofed this up as well.   Not having the keychain set up right kept my Remote Login username/password settings in memory until the session was logged out. Upon logging back in, the username and passwords were set back to the original settings when the keychain password had not been entered? Or did it?   But I had not been prompted for the keychain password again.  Frustrating this can be, because at this point the user has now had to define up to 3 passwords...  Local account password, Keychain password, RDP password.  I'm just not really confident that this ties together all too elegantly, but I could just be confused too.  Upon further logins I was not prompted for a keychain password, and saw that the settings persisted. I don't know, it's late and my brain is fried.  I could be gaslighting myself. I also use a Mac sometimes so I could be confusing Keychain for Keyring.. sorry!

It took a bit of tinkering at which point I could somewhat get everything to work, using the Windows 10 RDP mstsc client. Half of the time my client gave a somewhat generic error, "An authentication error has occurred. More data is available. Remote computer: <IP>."  I attribute this crappy error to Microsoft, not Ubuntu.  It ended up being that the username had to be specified in the mstsc client prior to connecting, it seems.  Or maybe not, I am not sure.  Does this happen with the Windows 11 RDP client?  I haven't really been interested in going to Win 11, so maybe someone with Windows 11 can check.

When I connected in using **Remote Login** on 3389, it gave me a notification at the upper login screen "**GNOME Remote Desktop Handover Daemon, **This connection is insecure. Do you want to continue with an insecure connection?  To make it secure set <b>"use redirection server name:i:1"</b>*[Sic] *in the RDP config file.  *Disconnect / Continue*".  I clicked Continue and then proceeded to click the user and enter the password as if sitting at the local desktop, not the RDP username and password I defined in the system settings.  Then another popup: **Session Already Running. **Remote login is not possible because a local session is already running for <username>. To login remotely, you must log out from the local session or force stop it.  Force stopping will quit any running apps and processes, and could result in data loss."  OK, force stop. Finally, after a bit of lag, I got in to the desktop. Not nearly as graceful of handover as a native Windows RDP service would provide. But hey, I am still very grateful we've gotten this far.
I went into the Display Settings and the Resolution was _hard-coded _to 1920x1080. Even though the local session's screen resolution is set to 1440x900.  I could _not _change the resolution during the **Remote Login** session, despite what it says above. I tried to submit a bug report, but I couldn't get that to work.

It seems that native support for VNC is dead in 24.04? Have we gone 2 steps forward and then taken one step back?  I want to say it was there in Focal and/or Jammy, they may have had a hybrid of VNC and RDP support, but I can't remember.  I have yet to try Remote Desktop from a Linux client, MacOS client, or Windows 11 client instead of Windows 10.  

Overall, while there are some caveats and weaknesses, we've come a long way from the old days.  There may be some polishing yet to be done for RDP support.  Thanks to the Ubuntu /Canonical development team for getting this functionality up to where it is, and I hope it can continue being worked on and improved, every little bit will help Ubuntu give Microsoft and Apple a run for their money.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294482&stc=1[/IMG]


[IMG]https://imgur.com/a/5Sp0zNe[/IMG]

---

### Post by TheFu on 2024-11-08
VNC is tied to X/Windows and 24.04 defaults to Wayland for the display server.  Lots of X/Windows programs don't work under Wayland and some that are very important to many people never will. Wayland closes some security issues that those programs have used under X/Windows.

So, whether it is 1 step back or not depends on your security sensitivity.  OTOH, if you care about security, you'd only use RDP through a VPN. Same for VNC.  Sadly, my preferred remote desktop, x2go, which leverages ssh tunnels and an optimized VNC protocol (merged they are called NX), won't work on Wayland either.

Of course, if you just want to run a remote application, you don't need a full remote desktop and they are actually quite bloated anyway. Just use ssh X11 forwarding, which has been working well for 25+ yrs.  Windows people seem to ignore this - or they don't know any better.  Having remote programs completely integrated into my normal desktop has been standard since the mid-1990s.   Heck, this browser is actually running on a different system using a remote ssh tunnel for X11 forwarding.  I do this to avoid using Ubuntu snap versions and to limit access to any important local files.  Same for thunderbird. It runs on a different system than the one I happen to be sitting behind, but if anyone looked at my screens, they'd never know.

---

### Post by ds526 on 2024-11-08
TheFu, thanks for this insight.  I'm living under a rock as far as the various windowing engines/servers and have a lot of research to do about Wayland. I do agree that utilizing a VPN is best for security and don't like to do any RDP or VNC NAT forwarding from the internet into my internal Linux hosts, overall am a fan of having as few ports open on my network as possible.

I've heard about the ssh X11 tunneling forwarding, I've never been able to get it to work but now I want to give it a try, as the RDP process is bloated and tedious.   ChatGPT says I need to enable X11Forwarding in /etc/ssh/sshd_config on my Ubuntu instance, install VcXsrv on my Windows 10 workstation, then ssh -X username@ubuntu_host and then just run firefox or thunderbird?  I'm going to give this a try. If you have any resources or guides of how to accomplish this, I'll welcome that too.

---

### Post by ActionParsnip on 2024-11-08
> **ds526 said:**
> TheFu, thanks for this insight.  I'm living under a rock as far as the various windowing engines/servers and have a lot of research to do about Wayland. I do agree that utilizing a VPN is best for security and don't like to do any RDP or VNC NAT forwarding from the internet into my internal Linux hosts, overall am a fan of having as few ports open on my network as possible.

I've heard about the ssh X11 tunneling forwarding, I've never been able to get it to work but now I want to give it a try, as the RDP process is bloated and tedious.   ChatGPT says I need to enable X11Forwarding in /etc/ssh/sshd_config on my Ubuntu instance, install VcXsrv on my Windows 10 workstation, then ssh -X username@ubuntu_host and then just run firefox or thunderbird?  I'm going to give this a try. If you have any resources or guides of how to accomplish this, I'll welcome that too.

What are you wanting to do on the remote system? There may be a sleeker solution to what you want to do

---

### Post by ds526 on 2024-11-08
ActionParsnip:

I'd like to run Firefox, Thunderbird, and Fragments on the remote 24.04 computer via my Windows 10 workstation.

VcXsrv on Windows 10 triggers Windows Defender according to some, not too far back:   [https://github.com/marchaesen/vcxsrv/discussions/27](https://github.com/marchaesen/vcxsrv/discussions/27)

---

### Post by TheFu on 2024-11-08
You have to have an X/Windows server running on the machine you sit behind. That server needs to be sufficiently good to support standard X11. I've only seen commercial X/Servers on MS-Windows work. Honestly, I haven't used MS-Windows for remote X since around 2002, so my knowledge on this is mucho out-of-date.

For my needs, it was easier to install/cheaper a hypervisor like virtualbox into MS-Windows, then run a small Linux VM with a GUI - like the 23MB TinyCore Linux, then use that as the X/Server for remote access into other Unix systems.  Since it used the real Linux X/Server, compatibility wasn't an issue.  Since it is 23MB in size, it needs very little RAM assigned to the VM and is crazy fast. [http://tinycorelinux.net/downloads.html](http://tinycorelinux.net/downloads.html)  OTOH, TinyCore Linux is a bit odd and not exactly friendly to end users.  It is the basis for many specialized devices that have 1 purpose.  In this case, you'd use it as an X/Server and only as an X/Server.

The *X11Forwarding* settings is the default in /etc/ssh/sshd_config on Ubuntu.

MS-Windows implementation of **ssh** is lacking, BTW.  I have no experience trying to get **ssh -X** working on it.  I do know that Putty uses an odd version of ssh-keys, so if that might be the plan, I can't help.  I have used PuTTY to remotely start GUI programs after starting a local X/Server. Doing this means it *would not* use the ssh tunnel AND we have to manually set the DISPLAY environment variably AND we have to open any firewalls to allow the X/Clients to connect the X/Server. Using a proper *ssh -X* implementation avoids the DISPLAY environment variable - as ssh does that automatically.

The Win10+ ssh implementation doesn't provide the **ssh-copy-id** tool, which makes ssh-key exchange harder. You'll want to do that manually and be careful like we had to be in the mid-1990s.  Copy the public key to the correct file on the remote system and be certain to ensure the file and directory permissions aren't molested. ssh is picky about file permissions.  It only took MSFT 20 yrs to make ssh port for MS-Windows. Hopefully, they will take less time to add **ssh-copy-id** quicker.  It is the easiest way to exchange the ssh key from the ssh-client to the ssh-server.
[Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](Https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)   Run 2 commands. That's it - at least on Linux.

I run thunderbird with this exact line:
```
TB_OPTS="-no-remote "  /usr/bin/ssh -X  deneb /usr/bin/firejail $FJ_OPTS /usr/bin/thunderbird $TB_OPTS $@ &
```
However, I'm a bit of a control freak when it comes to computers and do some security things.  

The basic line would be:
```
/usr/bin/ssh -X  deneb   /usr/bin/thunderbird    -no-remote  $@ &
```
"deneb" is remote system.  
My username is the same on both sides, so it isn't needed.

This is part of a script, so I use the full path to every program for added safety. As /usr/bin/ is in the PATH on both systems, if you trust the PATH being correct (I don't in scripts) AND you don't want to pass any arguments into Thunderbird, then you could use
```
ssh -X  deneb   thunderbird   -no-remote &
```

I almost forgot - Mozilla tries to run their programs locally even when we use ssh, so we have to add the **no-remote** option.

---

### Post by ActionParsnip on 2024-11-08
> **ds526 said:**
> ActionParsnip:

I'd like to run Firefox, Thunderbird, and Fragments on the remote 24.04 computer via my Windows 10 workstation.

VcXsrv on Windows 10 triggers Windows Defender according to some, not too far back:   [https://github.com/marchaesen/vcxsrv/discussions/27](https://github.com/marchaesen/vcxsrv/discussions/27)

If you want a Web browser, you can setup an SSH tunnel then set your local we browser to use the tunnel as a proxy.
Thunderbird is trickier but if you can mount the remote file system via SFTP/SSHFS then you can point a locally installed Thunderbird to the mounted data and read it. I don't know what "Fragments" is, can you expand please

---

### Post by TheFu on 2024-11-08
> **ds526 said:**
> ActionParsnip:

I'd like to run Firefox, Thunderbird, and Fragments on the remote 24.04 computer via my Windows 10 workstation.

VcXsrv on Windows 10 triggers Windows Defender according to some, not too far back:   [https://github.com/marchaesen/vcxsrv/discussions/27](https://github.com/marchaesen/vcxsrv/discussions/27)

I think you'll find that trying to run Firefox and Thunderbird remotely may not work. They are shipped as snap packages in Ubuntu 24.04, which include some mandated constraints.  I run a Linux Mint VM just for this reason. Mint doesn't use any Snaps.

---

### Post by ds526 on 2024-11-09
I had not considered those limitations of Snaps, so that's good to know.  I started playing around with TinyCore and will see if I can run those apps headless through another type of remote environment or just stay on an older LTS.  Thanks for these recommendations!  There are many ways to skin this cat.

---

### Post by TheFu on 2024-11-09
> **ds526 said:**
> I had not considered those limitations of Snaps, so that's good to know.  I started playing around with TinyCore and will see if I can run those apps headless through another type of remote environment or just stay on an older LTS.  Thanks for these recommendations!  There are many ways to skin this cat.

Yep. There usually are 50 different possible solutions to any problem. The trick is to consider all of them quickly and see if they are excellent or terrible as quickly as possible, so you don't waste too much time on dead-end solutions.  I've considered RDP and VNC as dead-end solutions for nearly 15 yrs now.  NX was the go-to when I traveled and needed to leave everything in a safe place.  With Xorg slowly going away, NX-based remote desktops will die.  That means using alternative remote access methods like **ssh -X** or using **ssh as a SOCKS proxy** will be more common.  I've been using ssh as a SOCKS proxy for some time when traveling in non-authoritarian countries and I wasn't worried about having any local data or cached information.  In those other places of the work, I travel with everything on a microSD card, no HDD inside the laptop and a few USB flash drives.  1 to show the computer works and 1 that is what I really use for remote access.  Not everyone has the same level of security needs.  Also, some "free" countries really aren't as free as they may seem.  Even in Europe and Oceania some freedoms I consider very important don't exist. Of course in parts of Asia and the Middle East, travel can have all sorts of challenges for computer security.  For the most part, I've not been hassled, but when you see some censorship as mandated by the govt in those places, it can make you think.  In one country, some of my websites were blocked for wired internet connections, but their cell phone networks didn't block them. Odd.

And to be very clear, there are ways to run Firefox and Thunderbird remotely even as snap packages, but they aren't noob-friendly.  Canonical isn't trying to make Ubuntu point-n-click for all possible use cases.  They are trying to make it easy for the most common uses ... which is 1 computer = 1 person = 1 desktop.   It makes sense, right?

OTOH, for people with knowledge and who are stubborn, it is possible to bend Ubuntu to your needs (for most things).  I did that for years, but about 18 months ago, I decided I shouldn't need to fight against the desktop so much to have it do things I want and there was a distro that already did things the way I wanted that was very, very, similar to what Ubuntu does.  Why not use it?  In some ways, Linux Mint is really dumbed down.  But in many other ways, it doesn't get in the way and allows the user to control how things work.  I don't know if it is the default or not, but Mint uses Xorg still, not Wayland.  Also, they don't load any snap packages or expect people to use snaps. The Mint team has decided to package the most popular snap-only programs for their releases, so end-users don't need to change anything.

But let's be very, very clear.  Ubuntu does 20,000 really well and just because I find less than 20 things that I don't like, that doesn't mean they aren't helping the vast numbers of Ubuntu users.  I'm struggling on my next server OS choice now.  Mostly I have Ubuntu 20.04 servers and standard support for them ends next June, so I will need to replace 2 of my physical server OSes and a number of virtual machine OSes before that time.  The VMs aren't really much concern.  I can wipe and restore those all day without worry.  

Mint isn't appropriate for Servers, so that's out.  Ubuntu 24.04 isn't solid enough yet, from what I've read and in my 24.04 desktop testing, things didn't really turn out well.  I want a basic Server OS with support for KVM/QEMU+libvirt and LXD/LXC containers, but that doesn't require snap packages. Of course, I use lots of other server stuff on my systems, but those items will run fine under either server or desktop distributions.  I don't plan on moving to any non-APT OS, so that leaves Debian.  I've been playing with Debian 12 on a few systems with mixed results.  One install, I was unable to get any networking up.  Not good.  I need to try again - perhaps that is solved or I'm smarter (doubtful, I'm an old dog).

Yep, need to try the current debian again.

---

