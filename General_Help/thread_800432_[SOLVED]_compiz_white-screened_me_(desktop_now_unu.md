---
title: "[SOLVED] compiz white-screened me (desktop now unusable)"
date: 2008-05-19
forum: General Help
---

### Post by Kymus on 2008-05-19
I was originally going to post about a problem I was having with enabling compiz-fusion (it was giving me that error "The composite extension is not available") and I wanted to make sure that was the exact error and that it was still doing it.

Well lucky me, because instead of giving me an error, it white-screened my desktop completely. I tried ctrl-alt-backspace and it was still there, so then I reseted and again it's still there (I am now forced onto my windoze partition... whoopee), thus making my desktop virtually unusable. I did some alt-tab-ing and it seems like everything is running.. it's just persistently white. How the heck do I fix this? :confused::confused:

---

### Post by Kymus on 2008-05-19
bump

---

### Post by Kymus on 2008-05-20
bump

---

### Post by danwood76 on 2008-05-20
If you choose the failsafe gnome session from the sessions chooser that will let you log in.

This errors is usually caused by incorrect graphics driver installation.

What graphics card/drivers do you use?

-- edit --

Btw when you login to the failsafe gnome you wont have desktop effects and so on.
But al least you will be able to reinstall your drivers from a GUI as opposed to the CLI.

---

### Post by Kymus on 2008-05-20
> **danwood76 said:**
> If you choose the failsafe gnome session from the sessions chooser that will let you log in.

This errors is usually caused by incorrect graphics driver installation.

What graphics card/drivers do you use?

-- edit --

Btw when you login to the failsafe gnome you wont have desktop effects and so on.
But al least you will be able to reinstall your drivers from a GUI as opposed to the CLI.

Thank you very much for the input!

In 7.10 I had the same problem (though after resetting or CTRL+ALT+Backspace it would go away). 

I have (I believe) an ATI X800 GTO and the drivers are the restricted drivers which were automatically provided and installed by Ubuntu upon upgrading to 8.04.

---

### Post by Kymus on 2008-05-20
well, running GNOME in failsafe mode stops the white screen, but the menus are not visible. My desktop looks just how it should, but there's just a complete lack of menus. Just to be sure, I tried moving the screen around, but that didn't change anything; still no menus.

---

### Post by danwood76 on 2008-05-20
Like I said in my previous post this is just really so you can have a GUI to reinstall the drivers.

When I have had this issue before I took this steps to rectify it:

1. Log in on failsafe GNOME

2. Completely remove fglrx using synaptic

So search using synaptic for fglrx and right click the following two packages and select completely remove:
xorg-driver-fglrx
fglrx-control (You may not have this one installed)

3. Reboot and log back into failsafe GNOME

Note here that you may end up in low graphics mode, this isnt bad as we are going to re install the ati drivers anyway, it was just necessary to get the kernel module unloaded fully.

4. Using synaptic re install the packages we removed a second ago.

5. Restart and you should have the drivers working again.

The problem is basically caused by the OpenGL vendor defaulting to mesa instead of ATI, this then causes compiz to fail and give you the white screen.

---

### Post by Kymus on 2008-05-20
and I'm back!

thanks a lot :)

..hopefully next time Compiz will just give me an error instead of a white screen... that's what started this whole thread *grumble*

---

### Post by danwood76 on 2008-05-20
Yeah the white screen of death is a bit odd.
but once you know what it is then its not too bad.

I guess it would be better if compiz just didnt work if compisiting wasnt enabled but I guess thats a suggestion for the compiz team.

---

### Post by Kymus on 2008-05-20
> **danwood76 said:**
> Yeah the white screen of death is a bit odd.
but once you know what it is then its not too bad.

I guess it would be better if compiz just didnt work if compisiting wasnt enabled but I guess thats a suggestion for the compiz team.
+1!

---

### Post by wastedfluid on 2008-05-20
> **danwood76 said:**
> Like I said in my previous post this is just really so you can have a GUI to reinstall the drivers.

When I have had this issue before I took this steps to rectify it:

1. Log in on failsafe GNOME

2. Completely remove fglrx using synaptic

So search using synaptic for fglrx and right click the following two packages and select completely remove:
xorg-driver-fglrx
fglrx-control (You may not have this one installed)

3. Reboot and log back into failsafe GNOME

Note here that you may end up in low graphics mode, this isnt bad as we are going to re install the ati drivers anyway, it was just necessary to get the kernel module unloaded fully.

4. Using synaptic re install the packages we removed a second ago.

5. Restart and you should have the drivers working again.

The problem is basically caused by the OpenGL vendor defaulting to mesa instead of ATI, this then causes compiz to fail and give you the white screen.


Would this be the same as..

I have two kernels, -17-generic, -17-server..

In -17-generic, I have compiz enabled, and fglrx..

However, when bootnig to -17-server, I get to thel ogin screen, put in user/pass - screen goes totally white.

However, if I do a Safe login w/ Gnome, it works..

So, if i remove fglrx, reboot.. log in to -server, and install fglrx again - will it work in both the -server kernel, and -generic?  I guess it doesn't really matter, because if I can use the server kernel.. I will to access my full 4gb of memory.

Let me know.  Will give Thanks.

---

### Post by danwood76 on 2008-05-20
Yes thats the same issue.

---

