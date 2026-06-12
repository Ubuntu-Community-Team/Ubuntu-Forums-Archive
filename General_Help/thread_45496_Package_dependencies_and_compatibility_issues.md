---
title: "Package dependencies and compatibility issues"
date: 2005-06-30
forum: General Help
---

### Post by musicman2059 on 2005-06-30
I've been starting to notice this mainly with some of the downloadable packages, mainly with compatibility issues concerning some of its dependencies in which are fulfilled, but are a way later version than the required installed version.

I've been finding that it usually concerns mainly libgtk and libglib, as Ubuntu includes libgtk2.4 and libglib3. (or in the ballpark at least)  I've been finding that many packages that are dependent on libgtk1.2 or an earlier version of libglib keep reporting back that neither of these packages are installed.

Is there a way I can solve this, or am I clearling off the mark and missing a crucial package?

---

### Post by Xian on 2005-06-30
[QUOTE=musicman2059]Is there a way I can solve this, or am I clearling off the mark and missing a crucial package?[/QUOTE]
From your description I can't narrow it down to a specific cause. It would help if you would (when you come across one of these packages), run the install command in a terminal and then copy/paste the error output back in this thread. It is much easier to backtrace a problem when there is a detailed record of the occurrence. 

For example if you are installing package foo-x in Synaptic and it gives you a problem, just open a terminal and run the install in Apt so as to get a verbose error message.
```
$ sudo apt-get install foo-x
```

---

### Post by musicman2059 on 2005-06-30
Well, because of the lack of internet connectivity I have to take things with a different method.  (Download to disc, mount, dpkg --install, etc...)  Unfortunately this does mean that depencies become a real issue, but I know for a fact with libgtk (GTK +) that 2.4 is already installed and programs such as GIMP wouldn't work without it.

When I do come across it again, I'll copy over the output here and say which packages related to it that Synaptic says I have installed.

---

### Post by Xian on 2005-06-30
[QUOTE=musicman2059]Well, because of the lack of internet connectivity I have to take things with a different method.  (Download to disc, mount, dpkg --install, etc...)  [/QUOTE]
That's okay. dpkg will still output dep errors.

---

### Post by musicman2059 on 2005-06-30
I knew that already, though.  (apt-get install and dpkg --install creates just about the exact same output! ;))

---

### Post by musicman2059 on 2005-07-01
Okay, so here's an example of one.  Do note that this is just an example.  I do know that I'm outright missing a few of the dependencies here, but I was just focusing on libglib and libgtk.

```
dahbam@dahbam:~/debs$ sudo dpkg --install gsnes9x_3.12-6_i386.deb
Selecting previously deselected package gsnes9x.
(Reading database ... 61372 files and directories currently installed.)
Unpacking gsnes9x (from gsnes9x_3.12-6_i386.deb) ...
dpkg: dependency problems prevent configuration of gsnes9x:
 gsnes9x depends on gdk-imlib1; however:
  Package gdk-imlib1 is not installed.
 gsnes9x depends on libart2 (>= 1.2.13-5); however:
  Package libart2 is not installed.
 gsnes9x depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 gsnes9x depends on libgnome32 (>= 1.2.13-5); however:
  Package libgnome32 is not installed.
 gsnes9x depends on libgnomesupport0 (>= 1.2.13-5); however:
  Package libgnomesupport0 is not installed.
 gsnes9x depends on libgnomeui32 (>= 1.4.2-3); however:
  Package libgnomeui32 is not installed.
 gsnes9x depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
 gsnes9x depends on snes9x-x; however:
  Package snes9x-x is not installed.
dpkg: error processing gsnes9x (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gsnes9x

```

libs installed:
libglib2.0-0
**Required version:** 1.12.13-5, **Installed version:** 2.6.3-1  (2.6.3-1 > 1.2.13-5)
libart2.0-2  
**Required version:** 1.2.0, **Installed version:** 2.3.17-1 (2.3.17-1 > 1.2.0)
libgtk2.0-0  
**Required version:** 1.2.10-4, **Installed version:** 2.6.4-0ubuntu3 (2.6.4-0ubuntu3 > 1.2.10-4)

So... what gives?  Is it the fact that, for example, packages that use libgtk1.2-0 aren't compatible with libgtk2.0-0 or what?

---

### Post by Xian on 2005-07-01
[QUOTE=musicman2059]
libgtk2.0-0  
**Required version:** 1.2.10-4, **Installed version:** 2.6.4-0ubuntu3 (2.6.4-0ubuntu3 > 1.2.10-4)

So... what gives?  Is it the fact that, for example, packages that use libgtk1.2-0 aren't compatible with libgtk2.0-0 or what?[/QUOTE]
Let's just pick one of these and see if we can eliminate that particular error.
Try using this apt install command and then run the configure session again.
Does the same libgtk error appear?
```
$ sudo apt-get install libgtk1.2-dev
```

---

