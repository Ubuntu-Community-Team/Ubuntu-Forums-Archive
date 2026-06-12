---
title: "Run Script as specific User on Startup (Server 18.04)"
date: 2018-06-04
forum: General Help
---

### Post by grimmspector on 2018-06-04
Hello, I need to have a specific script run from a users home directory, kind of like having a service startup, that I do not want run as root. It needs to be run on startup, and I'm having one heck of a time figuring out a way to do it in Ubuntu. Ideally I'd like to be able to take over it's terminal if I login as that user or another user, so I can interact with the script when need be directly. Anyone got any solution? Thanks.

---

### Post by TheFu on 2018-06-04
Welcome to the forums.

boot and logins aren't connected.   Booting can happen  50 hrs before anyone logs in.  

What this means is that you have to pick - non-interactive scripting or interactive which is launched by a user AFTER they login.  Pick and there are solutions for both.

---

### Post by grimmspector on 2018-06-05
> **TheFu said:**
> Welcome to the forums.

boot and logins aren't connected.   Booting can happen  50 hrs before anyone logs in.  

What this means is that you have to pick - non-interactive scripting or interactive which is launched by a user AFTER they login.  Pick and there are solutions for both.

What I am aiming for is to get an application running at boot without any user intervention. Ideally I'd like a user to be able to access the terminal it's running it later if they login and take control of it, but this isn't strictly necessary if it cannot be done (which would surprise me if that were the case). So I would say that I'm looking for non-interactive.

---

### Post by TheFu on 2018-06-05
> **grimmspector said:**
> What I am aiming for is to get an application running at boot without any user intervention. Ideally I'd like a user to be able to access the terminal it's running it later if they login and take control of it, but this isn't strictly necessary if it cannot be done (which would surprise me if that were the case). So I would say that I'm looking for non-interactive.

If you just want to run a script at boot, it cannot be interactive and the userid cannot have encrypted HOME directory, then you can just use anacron @reboot to run.  Scripts of this sort shouldn't assume **any** environment variables.  HOME will not be set.  The PATH and LD_LIBRARY_PATH will be minimal. Don't expect any other env to be set.  [https://askubuntu.com/questions/335615/does-ubuntu-support-reboot-in-crontab](https://askubuntu.com/questions/335615/does-ubuntu-support-reboot-in-crontab) has examples. Inside the script, you can use **su -l {userid} -c {command}** to run any process under a different userid. Check the manpage for more details.

Key thing is, there cannot be any GUI programs involved.  They will not work.

---

### Post by papibe on 2018-06-05
Hi grimmspector. Welcome to the forum ):P

It is easier for us to help you if you give us some specifics.

I think this may help: [https://ubuntuforums.org/showthread.php?t=1809501](https://ubuntuforums.org/showthread.php?t=1809501)

Take a look at post #14 for part of the solution. Use crontab with the special string '@reboot' if you want the session to start at boot time.

Let us know how it goes. If these does not help, please give us more information, examples, etc.
Best Regards.

---

### Post by grimmspector on 2018-06-06
> **TheFu said:**
> If you just want to run a script at boot, it cannot be interactive and the userid cannot have encrypted HOME directory, then you can just use anacron @reboot to run.  Scripts of this sort shouldn't assume **any** environment variables.  HOME will not be set.  The PATH and LD_LIBRARY_PATH will be minimal. Don't expect any other env to be set.  [https://askubuntu.com/questions/335615/does-ubuntu-support-reboot-in-crontab](https://askubuntu.com/questions/335615/does-ubuntu-support-reboot-in-crontab) has examples. Inside the script, you can use **su -l {userid} -c {command}** to run any process under a different userid. Check the manpage for more details.

Key thing is, there cannot be any GUI programs involved.  They will not work.

No need for GUI anything, in fact the server doesn't have GUI anything, as it's a server install with no GUI added. Everything is command line.

The issue here is that the su command always asks for a password when trying to run something as a user, even if I'm in root. So how would that work at boot?


> **papibe said:**
> Hi grimmspector. Welcome to the forum ):P

It is easier for us to help you if you give us some specifics.

I think this may help: [https://ubuntuforums.org/showthread.php?t=1809501](https://ubuntuforums.org/showthread.php?t=1809501)

Take a look at post #14 for part of the solution. Use crontab with the special string '@reboot' if you want the session to start at boot time.

Let us know how it goes. If these does not help, please give us more information, examples, etc.
Best Regards.

I don't know how much more specific I can be beyond saying I want to run a script under a specific user, and ideally want to be able to then interact with that console later if possible (like the screen command for instance).

---

### Post by TheFu on 2018-06-06
Did you look at the links?   There are clear examples.

Root won't be asked for a password to run any local process as another userid.  If you try to run a script over NFS, then root is blocked for security, by default.

Perhaps if you post what you've put into the crontab AND tell us which crontab you are using (there are at least 3 different places), then we might be able to help.

If you want to interact with a running program, that program will need to allow remote control/commands in some manner. That isn't too hard, just open a FIFO (named pipe?) and have the process read from it with a simple parser for the specific commands.  Then you can make another tool that writes to the FIFO with approved commands ... or any process like "cat" can be used as well.  If you want non-local control, which is usually bad idea due to security, you can do the same with sockets.

---

### Post by SeijiSensei on 2018-06-06
Root can run commands as other users via the "su" command.  I believe if you create or edit /etc/rc.local and add this line to it:

```
su -c /path/to/your/script username
```

it will run the script as "username".  Commands place in /etc/rc.local are executed at the end of the boot sequence.  The script must be marked executable by that user, of course.

---

### Post by grimmspector on 2018-06-08
> **SeijiSensei said:**
> Root can run commands as other users via the "su" command.  I believe if you create or edit /etc/rc.local and add this line to it:

```
su -c /path/to/your/script username
```

it will run the script as "username".  Commands place in /etc/rc.local are executed at the end of the boot sequence.  The script must be marked executable by that user, of course.

Ok, well that won't allow the interactivity, so before I go that route I just have to ask then, is there a way I can on boot have it autologin a specific user and have that user in their terminal initiate a script? Then I can setup a user that has no ability to do anything but use that script and it should be fine, and if I remotely connect to that specific terminal session I can interact with it.

---

### Post by SeijiSensei on 2018-06-08
Is the "interactivity" limited to a specific set of commands?  If so you could include an "[expect]("https://likegeeks.com/expect-command/")" script in your main script to respond to the prompts.

Is there no way to start this process so that it doesn't require console input?

---

### Post by TheFu on 2018-06-11
> **grimmspector said:**
> Ok, well that won't allow the interactivity, so before I go that route I just have to ask then, is there a way I can on boot have it autologin a specific user and have that user in their terminal initiate a script? Then I can setup a user that has no ability to do anything but use that script and it should be fine, and if I remotely connect to that specific terminal session I can interact with it.

On a desktop, you can autologin and when the login session happens, automatically start GUI programs (or non-GUI programs). GUI programs would be attached to the X-session and usually not available elsewhere.  You could force the startup to go into a remote desktop session, and those tools allow re-connections over the network.  Multimedia doesn't work too well over these and it is an extra step for all local connections to the GUI, since locally, they'd need to run the remote desktop client  program and connect to the correct remote session.   

I run my main desktop in a similar manner - it runs on a headless server and uses x2go. I connect for assorted client locations (and inside the same room) from Windows/Linux/OSX desktops to access the same session. For people who are always remote, it isn't hard for them to understand and works fairly well.  I've connected from 5 continents over the years with ISDN or faster connections and it works fine for office productivity needs.  I've been having issues with firefox being very slow since Oct'17, but dillo, chromium, and lynx are still working well.

I don't know how to make autologin work under x2go to connect to an already-active session, since the session identifier is dynamic and something that is picked from a list.  ssh-keys or ssh-certs can be used for automatic authentication between the client and server. If there isn't already an x2go session, then auto-connection will happen.

VNC is 2-3x slower than x2go and doesn't come with good encryption between the client and server, but on a secured LAN, it should be fine.  People use VNC over VPNs or through ssh tunnels.

No way to know if either of these methods will work for your needs until you try them out.

For non-GUI stuff, there is tmux or screen. Lots of youtube videos on both of those.

---

