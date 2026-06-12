---
title: "strange multi-user behaviour"
date: 2008-06-24
forum: General Help
---

### Post by alecz20 on 2008-06-24
I have been using Ubuntu for quite a while, but never really got too much in depth with it as long as it was doing what I was expecting it to do.

I know Linux is very famous for multi-user stuff, so I created another user (unprivileged), and I noticed some strange behaviour

1 - I wanted to find a similar command to "Super + L" so I can switch users fast, and not go to the "power button". I found the "Ctrl+Alt+L" which locks the screen and gives the option to "Switch user"
The problem is, however, that the initial session is closed, and all work is lost. I thought switching users still keeps the other session running, hence "multi-user" operating system.
Going to the power button and choosing "switch user" works as expected!

2 - Desktop effects cannot be enabled on the other account. "glxinfo" in terminal says "direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)"

3 - I wanted to run Google Earth, but I couldn't find it in the menu, so I went to the terminal and ran it. I saw the splash screen, but soon after I got the same prompt as the "Lock Screen" prompt, where I was asked the password for the initial account.

I re-installed the new version of Google Earth on the new (unprivileged) account, and i got a Desktop Shortcut. Accessing the shortcut would have same result: prompt to login in the main account (administrator).

Same happened when I tried creating a "Desktop User" account.

These problems are very disturbing regarding Ubuntu 7.10 multi-user support.

1 - Switch user from "locked screen" actually performs a log-out (what is the proper short-cut to switch users then?)

2 - Direct rendering does not work in the secondary account (why would Ubuntu disable it, any good reason?)

3 - Running SOME programs in the secondary account is not possible and the user is prompted to login to the main account (what's the purpose of multi-user if I can't run my programs?)

Thanks for reading, and maybe someone can explain me how multi-user stuff works in Ubuntu.

EDIT:
After doing some more research I found out that 3D functions do not work for more than one user unless nVidia  cards are used.
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/137745](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/137745)
The link gives details about this bug/limitation.

I suppose this also explains why Google Earth does not work for the second user account, since it's a 3D application.
I'm using an intel integrated Graphics card (not sure the exact chipset, some GMA something), and I know the drivers are open source. It is troubling that using this card I can't have 2 users using a simple application such as Google Earth!
I guess it's going to be nVidia for me from now on...

---

### Post by pytheas22 on 2008-06-24
> 1 - I wanted to find a similar command to "Super + L" so I can switch users fast, and not go to the "power button". I found the "Ctrl+Alt+L" which locks the screen and gives the option to "Switch user"
The problem is, however, that the initial session is closed, and all work is lost. I thought switching users still keeps the other session running, hence "multi-user" operating system.
Going to the power button and choosing "switch user" works as expected!

In Hardy 8.04, there's an applet in the Gnome panel that you can click and see a list of all the users on the computer; select the account you want to switch to and it changes over very quickly, leaving everything else running.  I guess this isn't available in Gutsy, but you could either upgrade your entire system (not a bad idea since Hardy has long-term support) or temporarily enable the Hardy repositories so that you can grab the newer version of Gnome (I can give instructions if you can't figure it out by searching online).

> 2 - Desktop effects cannot be enabled on the other account. "glxinfo" in terminal says "Direct Rendering: NO (if you want to find out why do ...blablabla - I don't remember exactly, but I can find out if it would help solve the problem.)"

This is a known issue.  Compiz (the program behind desktop effects) originally wasn't designed to be used by more than one user at a time--after all, it eats up a huge amount of resources so you probably don't want more than one session running at once.  I hear (but can't confirm) that nvidia and ATI cards can now run compiz for more than one user at the same time, but if you have Intel or some other video chipset, it won't work.  If you do have nvidia or ATI, you may need to be using the Hardy build of compiz to take advantage of its newer functionality.
> 
3 - I wanted to run Google Earth, but I couldn't find it in the menu, so I went to the terminal and ran it. I saw the splash screen, but soon after I got the same prompt as the "Lock Screen" prompt, where I was asked the password for the initial account.

I'm not sure but I bet that this is related to the inability to run more than one compiz instance at once.  Google Earth probably requires direct rendering and you can't have that on more than one account at once.
> 
3 - Running SOME programs in the secondary account is not possible and the user is prompted to login to the main account (what's the purpose of multi-user if I can't run my programs?)

That's weird.  Can you give examples of programs that are doing this?

---

### Post by alecz20 on 2008-06-24
Hey, thanks for the reply!

1 - I think the same applet exists in 7.10 regarding the user switch. However I really need a "key combination". The reason is mainly in applications such as Diablo 2, which reset the entire session if I want to use Alt+Tab, but has no problem switching to other terminal, such as Ctrl+Alt+F1, and back with Ctrl+Alt+F7.

2 - I recently learned about the compiz limitation, and the workaround with NVidia and ATI cards and the new Hardy. However I read a lot of people have freezes/lockups with Hardy, and I don't know if they are solved.

3 - Google Earth is the application that I found so far (haven't looked too much into it yet). I suppose it needs Direct Rendering, but the behavior is REALLY strange:
   - splash screen
   - session forced closed
   - return to other account and prompt for password (black background)

#1 and #3 are still issues, I'd consider #2 solved.

Thanks again.

---

### Post by pytheas22 on 2008-06-24
I don't know of any hotkey for fast user switching.  I guess you could write your own if you figured out which commands the applet is using, but I have no idea.  Could you play Diablo in fullscreen but simply switch to another workspace by pressing control-alt-arrow key, and from there use the applet?  That might be a work around.

I also remember at one time, before the nice fast-user-switching applet appeared, having Fedora set up so that one user could log in on the control-alt-f7 screen, another on control-alt-f8 and another on control-alt-f9.  I think this involved running multiple instances of gdm.  I don't remember how exactly I did it, but I'm sure I just followed directions online somewhere; if you look maybe you can find something similar.  Then you could simply control-alt-fX to switch users whenever you need.  It should also be possible to control-alt-f1-6 and run startx from there to start a new X session with a different user; you just need to tell it which screen to start the session on, but again I don't know exactly how to specify that.  I think it involves something like :1 for screen 1, :2 for screen 2 and so on.

EDIT: I looked it up; actually the syntax to start a new X session on different screens is quite simple.  Just log in as whichever user you want to own the session and type:

```
startx -- :1
```

I seem to have some issues when I do this--if I switch out of the new session and back in to it, it's broken.  But at least it gets you closer to a solution, maybe.

As for Google Earth, I don't know why it would do what it does.  It sounds like it might just be crashing X and dumping you back to the first session.  Maybe take a look at /var/log/Xorg.0.log to find out, or run Google Earth from a terminal to see if it says anything?  Or you could try asking Google; I'm not sure if they support their Linux build of Google Earth or not.  Unfortunately it's proprietary and closed-source so it would be hard to figure out its behavior on your own.

---

### Post by alecz20 on 2008-06-25
Switching workspaces when Diablo is running in full-screen mode has the same behavior (crashing the session). The only "switch" that does not crash is "Ctrl+Alt+FX"
I might try with the F: 7,8,9 and see if it works. 

About the fast-user-switch applet... there's something wrong with it. It is worse than "lock-screen -> switch user". When selecting another user, the session crashes or closes, or even causes a hang in a full screen with messages all over.

I have to reboot, via Ctrl+Alt+F1, login and sudo reboot.

The only way what works without problems to switch the user is via the red "power button" on the upper right corner.

I don't really understand why out of three ways to switch the user one works fine and the others crash.


Regarding Google Earth, I'd like to know other people's experiences. I might also contact Google and ask them about it, but it would be nice to know if this problem is isolated or global.

Thanks for the help and suggestions.

Edit: I will check that log file when I get back home.

---

### Post by alecz20 on 2008-07-15
Well,

Now that I got more time to play around, I tried to reproduce the crash using:

- Shutdown menu -> switch user
- Quick User-switch Applet (User-Switcher
- Terminal switch Ctrl+Alt+F7 and Ctrl+Alt+F9

None of these methods crashed the session for me with Compiz either on or off.

I don't know what caused it before, but I can't seem to reproduce it now. I know I did some updates, but I don't know.

EDIT: Using Lock screen -> switch user, still crashes the initial session (of the user that locks the screen)
Without compiz, I was unable to re-login on the first user. Ctrl+Alt+F7 says: "Reloading system log daemon..." and hangs there.

I don't know what to look for in /var/log/Xorg.0.log
Now I want to figure out a way to relog in as the first user without rebooting or logging out the 2nd one.
Ctrl+Alt+Backspace doesn't work either, session still hangs. I have to reboot.

Conclusion: don't use Lock screen to switch user... something goes wrong.
I'll just keep posting in this thread anything new I find.

---

