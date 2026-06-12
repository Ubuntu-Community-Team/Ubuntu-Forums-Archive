---
title: "Chrome Remote Desktop does not come up after reboot"
date: 2023-01-29
forum: General Help
---

### Post by dellarovere2 on 2023-01-29
I am running Ubuntu 20.04LTS
Trying to setup Chrome Remote Desktop for multiple users on the machine. It was working for me on 18.04LTS, but I am unable to set it up so that the hosts would be up after reboot. Every time the system reboots, I need to explicitly log in through SSH and run a setup command, like

```
DISPLAY= /opt/google/chrome-remote-desktop/start-host --code="REDACTED" --redirect-url="https://remotedesktop.google.com/_/oauthredirect" --name=$(hostname)

```

After that the host is up and I can login, but after the reboot I need to go through the exercise again.

I have deleted and regenerated the .config/chrome-remote-desktop directory several times.

Here is the output of journalctl

```

$ journalctl --reverse --grep=chrome-remote-desktop
-- Logs begin at Sat 2022-01-22 14:58:20 PST, end at Sun 2023-01-29 18:23:28 PST. --
Jan 29 18:21:46 neva systemd[1267]: pam_systemd(chrome-remote-desktop:session): Failed to release session: Access denied
Jan 29 18:21:46 neva systemd[1267]: pam_unix(chrome-remote-desktop:session): session closed for user userA
Jan 29 18:21:46 neva systemd[1]: chrome-remote-desktop@userA.service: Failed with result 'exit-code'.
Jan 29 18:21:46 neva systemd[1]: chrome-remote-desktop@userA.service: Main process exited, code=exited, status=1/FAILURE
Jan 29 18:21:46 neva chrome-remote-desktop[1108]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 562, in _wait_for_x
Jan 29 18:21:46 neva chrome-remote-desktop[1108]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 580, in _launch_xvfb
Jan 29 18:21:46 neva chrome-remote-desktop[1108]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 671, in _launch_x_server
Jan 29 18:21:46 neva chrome-remote-desktop[1108]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 782, in launch_session
Jan 29 18:21:46 neva chrome-remote-desktop[1108]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 1829, in main
Jan 29 18:21:46 neva chrome-remote-desktop[1108]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 1950, in <module>
Jan 29 18:21:46 neva systemd[1268]: pam_systemd(chrome-remote-desktop:session): Failed to release session: Access denied
Jan 29 18:21:46 neva systemd[1268]: pam_unix(chrome-remote-desktop:session): session closed for user userB
Jan 29 18:21:46 neva systemd[1]: chrome-remote-desktop@userB.service: Failed with result 'exit-code'.
Jan 29 18:21:46 neva systemd[1]: chrome-remote-desktop@userB.service: Main process exited, code=exited, status=1/FAILURE
Jan 29 18:21:46 neva chrome-remote-desktop[1109]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 562, in _wait_for_x
Jan 29 18:21:46 neva chrome-remote-desktop[1109]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 580, in _launch_xvfb
Jan 29 18:21:46 neva chrome-remote-desktop[1109]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 671, in _launch_x_server
Jan 29 18:21:46 neva chrome-remote-desktop[1109]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 782, in launch_session
Jan 29 18:21:46 neva chrome-remote-desktop[1109]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 1829, in main
Jan 29 18:21:46 neva chrome-remote-desktop[1109]:   File "/opt/google/chrome-remote-desktop/chrome-remote-desktop", line 1950, in <module>
Jan 29 18:21:37 neva at-spi-bus-launcher[1740]: dbus-daemon[1740]: Activating service name='org.a11y.atspi.Registry' requested by ':1.1' (uid=1002 pid=1721 comm="/opt/google/chrome-remote-desktop/chrome-remote->
Jan 29 18:21:37 neva chrome-remote-desktop[1721]: [0129/182137.295973:INFO:file_host_settings.cc(31)] Host settings file /home/userC/.config/chrome-remote-desktop/host#48b2b6fc536fe30b1242a264964655fa.settings.j>
Jan 29 18:21:36 neva dbus-daemon[1349]: [session uid=1002 pid=1349] Activating via systemd: service name='org.a11y.Bus' unit='at-spi-dbus-bus.service' requested by ':1.14' (uid=1002 pid=1718 comm="/opt/google/c>
Jan 29 18:21:35 neva chrome-remote-desktop[1107]: 2023-01-29 18:21:35,086:INFO:['/opt/google/chrome-remote-desktop/chrome-remote-desktop-host', '--host-config=-', '--audio-pipe-name=/home/userC/.config/chrome-re>
Jan 29 18:21:35 neva chrome-remote-desktop[1107]: 2023-01-29 18:21:35,020:INFO:Launching X session: ['/opt/google/chrome-remote-desktop/chrome-remote-desktop-host', '--type=xsession_chooser']
Jan 29 18:21:10 neva systemd[1109]: pam_unix(chrome-remote-desktop:session): session opened for user userB by (uid=0)
Jan 29 18:21:10 neva systemd[1108]: pam_unix(chrome-remote-desktop:session): session opened for user userA by (uid=0)
Jan 29 18:21:10 neva systemd[1107]: pam_unix(chrome-remote-desktop:session): session opened for user userC by (uid=0)
Jan 29 18:21:08 neva sudo[1059]:     root : TTY=unknown ; PWD=/ ; USER= userA; COMMAND=/opt/google/chrome-remote-desktop/chrome-remote-desktop --start
Jan 29 18:21:06 neva chrome-remote-desktop[973]: sudo -u userA /opt/google/chrome-remote-desktop/chrome-remote-desktop --start
-- Reboot --



```

Would really appreciate any suggestions about which logs to look into or what else I can do to debug this further.

---

### Post by TheFu on 2023-01-30
1) You have set the DISPLAY to be empty.  This isn't a good idea.  DISPLAY has special meaning for all Unix systems that have X/Windows or Wayland, so don't screw around with it if you don't know what it does.  Leave that environment variable alone.

2) Don't use a program that is tied to a GUI session that only happens after a local graphical login.  That's asking for failure, as you are learning.

3) Use x2go, which runs as a service and supports multiple concurrent users without any local user session running.
x2go has a client and a server. On the remote system, install the server.
On the client systems, install the x2goclient.  For MS-Windows clients, you'll want to install the font package from the x2go website too.

Additionally, x2go (and all remote desktops) need a light DE, so plan to connect and use XFCE, Mate, LXQt.  Gnome doesn't work.  I think KDE-Plasma doesn't work either, since both of those really want direct access to a GPU ... and x2go works without any GPU.

x2go works over ssh, so get that working from each client first.  It supports ssh-keys, so connections can be really convenient.  x2go uses the NX protocol which is an optimized, compressed, tunable version of VNC, but runs 2-3x faster and uses secure ssh tunnels. Those are all built-into the client/server connection.  The ssh port/server is the only port used.  It can be configured bi-directional, but doesn't have to be.

There are lots of things that x2go can do besides providing a fast, efficient, remote desktop over secured connections. The project runs a website with lots of documentation for those other things, which might be useful.

---

### Post by ActionParsnip on 2023-01-30
What are the users doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by dellarovere2 on 2023-02-03
Thank you for your reply. The reason why I am trying Chrome remote desktop is because the client is the Chromebook. I do not think x2go solution will work with it.

Also, the reason why I would like to have the full desktop session is to be able to do some development. Obviously it is achievable with multiple SSH windows and a text editor, but a desktop session is preferable.

---

### Post by ActionParsnip on 2023-02-03
What will the users do on the remote system once connected?

---

### Post by dellarovere2 on 2023-02-03
As an example, bring up an IntelliJ IDE and do development.
I also have a problem with scanning to Chromebook, but my Ubuntu works well with my scanner, so another task is doing scanning.

---

### Post by TheFu on 2023-02-03
> **dellarovere2 said:**
> Thank you for your reply. The reason why I am trying Chrome remote desktop is because the client is the Chromebook. I do not think x2go solution will work with it.

Also, the reason why I would like to have the full desktop session is to be able to do some development. Obviously it is achievable with multiple SSH windows and a text editor, but a desktop session is preferable.

So, I did software development on a chromebook for a few months using crouton in guest-only mode, before just wiping ChromeOS off my systems (Toshiba CB35-5015U and Acer C720).  At the time, they were the best, cheap-ish, options.  I did it all local for my webapp development.

I use Unix as an IDE and have for nearly 3 decades.  Nothing is more efficient, but it does take a bit of practice and being around others doing the same method really helps.  

It is possible, but not recommended to setup guacamole on your remote system to provide a desktop via a webapp.  Just be certain guacamole only listens on localhost, so and ssh-tunnel into it will provide the needed authenticated security. [https://guacamole.apache.org/](https://guacamole.apache.org/)  Guacamole (and any remote desktop without key-based authentication), shouldn't be allowed.  VNC, RDP, and webapps are the main ways that crackers get into our systems after they get on the LAN.

You need to get away from end-user applications that tie into a GUI session to allow access.  That's where x2go and guacamole don't fail.

I've posted an ssh-socks5-proxy script in these forums a few times that expects to see a chromium-browser.  This is because chromium supports specifying the socks5 proxy in the command line options unlike other popular browsers. Anyway, if you can ssh into the remote system, then you can use it as a SOCKS5 proxy for any webapps running on the same LAN, not just remote desktops like guacamole, but for jellyfin media servers, nextcloud access, and 10,000 other webapps you might self-host, but want access into while traveling.

Here's a step-by-step, How-To from someone I'd trust: [https://www.linuxbabe.com/ubuntu/apache-guacamole-remote-desktop-ubuntu-20-04](https://www.linuxbabe.com/ubuntu/apache-guacamole-remote-desktop-ubuntu-20-04)  I'm not thrilled that the steps put maintenance of the software into your mandate, since there isn't a current PPA or package provided. This hasn't been updated since 2013 [https://launchpad.net/~guacamole/+archive/ubuntu/stable](https://launchpad.net/~guacamole/+archive/ubuntu/stable), but the project is maintained under the Apache project umbrella.


OT: 
BTW, vim supports remote editing of files via rsync. 
```
$ vim rsync://dev/projects/gallery/src/templates/search.html.tt
```
Anyway, I know that isn't helpful to you and switching the way you work isn't something I'd ask someone already efficient in their current method to do.  
Ever heard of sshfs?  Just something to consider for your editor too.

---

### Post by TheFu on 2023-02-03
OT:

IntelliJ IDE. Sigh.

I wouldn't wish that pile of xxxxx onto my worse enemy.  

Does your system have 64G or 128G of RAM?  Seems Java development is always a hog and always will be.  I remember when the Java Devs came to our govt lab before it was released trying to convince us to stop cross-platform C++ development.  They claimed that it would get faster, more RAM efficient, better with storage, and since it was designed from the ground up to be secure, there wouldn't be security-related bugs. That was nearly 30 yrs ago.  I'm still waiting for any of those to be true.

A few good friends are 100% java developers. They make a good living at it and they aren't dumb people.  OTOH, they say runtime speeds have massively improved, which would be hard now that everyone has a supercomputer on the desk.  I'm not joking.  My normal $400 desktop (Ryzen) is faster than the Cray Y-MP I used in college, barely. At that time, it was in the Top 10 fastest computers in the world.

---

### Post by dellarovere2 on 2023-02-03
Thank you for your suggestions. It definitely would take some time to set up and try out. I do not depend on it for living, so the priority will not be very high.

---

### Post by dellarovere2 on 2023-02-10
I decided to dig deeper and see if I can solve the problem. And I actually have figured it out. I would like to document my findings and solution here, just to have a record of it in case anyone is interested.

First, I run

```
journalctl --reverse SYSLOG_IDENTIFIER=chrome-remote-desktop
```
instead of
```
journalctl --reverse --grep=chrome-remote-desktop
```.

There I saw this:
```

Feb 10 09:53:38 neva chrome-remote-desktop[1337]: (EE)
Feb 10 09:53:38 neva chrome-remote-desktop[1337]:         and start again.
Feb 10 09:53:38 neva chrome-remote-desktop[1337]:         If this server is no longer running, remove /tmp/.X20-lock
Feb 10 09:53:38 neva chrome-remote-desktop[1337]: (EE) Server is already active for display 20
Feb 10 09:53:38 neva chrome-remote-desktop[1337]: Fatal server error:
Feb 10 09:53:38 neva chrome-remote-desktop[1337]: (EE)
Feb 10 09:53:36 neva chrome-remote-desktop[1338]: (EE)
Feb 10 09:53:36 neva chrome-remote-desktop[1338]:         and start again.
Feb 10 09:53:36 neva chrome-remote-desktop[1338]:         If this server is no longer running, remove /tmp/.X20-lock
Feb 10 09:53:36 neva chrome-remote-desktop[1338]: (EE) Server is already active for display 20
Feb 10 09:53:36 neva chrome-remote-desktop[1338]: Fatal server error:
Feb 10 09:53:36 neva chrome-remote-desktop[1338]: (EE)
Feb 10 09:53:36 neva chrome-remote-desktop[1340]: xdpyinfo:  unable to open display ":20".
Feb 10 09:53:36 neva chrome-remote-desktop[1341]: xdpyinfo:  unable to open display ":20".
Feb 10 09:53:36 neva chrome-remote-desktop[1342]: xdpyinfo:  unable to open display ":20".

```

When I checked the existence of the lock file, it was there. So, it looked like the DISPLAY was always set to 20 for all the users.

I found the code for /opt/google/chrome-remote-desktop/chrome-remote-desktop which sets that variable: [https://source.chromium.org/chromium/chromium/src/+/HEAD:remoting/host/linux/linux_me2me_host.py;drc=155999e40f29d706591d3d0e24493f2521251411;l=1070](https://source.chromium.org/chromium/chromium/src/+/HEAD:remoting/host/linux/linux_me2me_host.py;drc=155999e40f29d706591d3d0e24493f2521251411;l=1070). 
```

[COLOR=#000000][FONT=monospace]  [COLOR=#770088]def[/COLOR] [COLOR=#0000FF]get_unused_display_number[/COLOR]():[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    [COLOR=#137333]"""[/COLOR][COLOR=#137333]Return a candidate display number for which there is currently no[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace][COLOR=#137333]    X Server lock file[/COLOR][COLOR=#137333]"""[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    display = FIRST_X_DISPLAY_NUMBER[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    [COLOR=#770088]while[/COLOR] os.path.exists(X_LOCK_FILE_TEMPLATE % display):[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]      display += [COLOR=#116644]1[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    [COLOR=#770088]return[/COLOR] display
[/FONT][/COLOR]
```

I augmented logging to output the value of the  of os.path.exists() and it turned out that for all three users it was outputting False.

So, turned out it was a race condition. The system tried to start the server for all three users, checked the existence of the lock file pretty much at the same time and all three passed. But then it created it for one and failed for two others.
I tried to figure out how to space the users in time, but could not find the way to do thet, so I went with the solution of making the DISPLAY different for all users based on their UID. I changed the local version of the script to be:

```

[COLOR=#000000][FONT=monospace]  [COLOR=#770088]def[/COLOR] [COLOR=#0000FF]get_unused_display_number[/COLOR]():[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    [COLOR=#137333]"""[/COLOR][COLOR=#137333]Return a candidate display number for which there is currently no[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace][COLOR=#137333]    X Server lock file[/COLOR][COLOR=#137333]"""[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    display = FIRST_X_DISPLAY_NUMBER * (os.getuid() - 999)[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    [COLOR=#770088]while[/COLOR] os.path.exists(X_LOCK_FILE_TEMPLATE % display):[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]      display += [COLOR=#116644]1[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    [COLOR=#770088]return[/COLOR] display
[/FONT][/COLOR]
```



And it seems to be working for me now.

---

### Post by TheFu on 2023-02-10
Good digging. Beyond what I would have done without a paid contract. Nicely researched.

Just to clarify, the standard for setting a DISPLAY variable is 
```
{ip}:{head}
```
where the IP is optional and 'head' is controlled by the GPUs connected to different monitors.  For about the last 15 yrs, the idea that there would be a separate GPU used to support multiple monitors (i.e. heads) hasn't really been the method used. Since we have single GPUs that support 2, 3, 4 monitors, it is just software that can be setup to merge all those heads into a single virtual desktop, usually through a checkbox.  In the 1990s, we'd have 1 GPU for each display/head and would run a different X/Server tied to each GPU.  Dragging and dropping windows between them wasn't possible, but we could launch an application to a specific GPU by controlling the DISPLAY value for the program as it was launched.  Back then, I'd work on 3 monitor 64-bit systems with 256 color GPUs - which was pretty high-end at the time.  Back then, only a few vendors supported 64-bit hardware and AMD was just beginning to dream about 64-bit support.

So the DISPLAY must include the : character to be valid. Without the IP part, localhost is the default.  Additionally, X11Forward needs to be allowed.  That can be accomplishes by disabling the firewall or by a setting in the sshd_config file or by manually telling the local X/Server to allow X/Client connections from a specific remote host using the 'xhost' command. Often, a combination of those things is needed.

Anyway, 
```
export DISPLAY=:20
```
is the required setting, not just the number.

---

