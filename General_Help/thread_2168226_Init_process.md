---
title: "Init process"
date: 2013-08-16
forum: General Help
---

### Post by emerson1979 on 2013-08-16
Hello Everyone
                       Does anyone know of a linux distro that uses the init process?


Thank You

---

### Post by chadk5utc on 2013-08-17
What is it that you are trying to do? Most Linux distro's will take an init command?
Im not sure what exactly your question is? So to simply explain the "init process" Ill give you some links to read and maybe this will help you.
[http://manpages.ubuntu.com/manpages/lucid/man5/init.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/init.5.html)
[http://linux.die.net/Intro-Linux/sect_04_02.html](http://linux.die.net/Intro-Linux/sect_04_02.html)

---

### Post by 3rdalbum on 2013-08-17
> **emerson1979 said:**
> Hello Everyone
                       Does anyone know of a linux distro that uses the init process?


Thank You

Question: Why? As far as I'm aware, there are no advantages to using Init, and many advantages to using anything BUT init.

If you really want a Linux distro that uses the old Init, you could have a look at Slackware. It's a bit archaic so it might still be using Init. Probably all mainstream distros use something a bit more modern.

---

### Post by emerson1979 on 2013-08-17
I'm studying for the LP Icertification and it test for knoweledge of init. It doesn't cover upstart or other vatiants of init.

---

### Post by Bashing-om on 2013-08-17
emerson1979; Hi !
See if this gives ya a bit of direction:
Here's an abbreviated version of what happens when you turn the power on after the machine has been shut down for a while:

First, code in the BIOS chip on the motherboard gets loaded into memory automatically and begins running. Next, the Power-On Self Test (POST) code checks all of the hardware to make certain it's working. In the process it clears all of the RAM space except the very small part it's using to run the POST.

When the POST completes, the BIOS code then begins loading the operating system code into memory. This becomes a "chicken-or-egg" situation, since loading the code requires code to already be there and the BIOS chip isn't large enough to hold all of the necessary code. The solution, in most Linux distributions, is to create a pseudo-disk in RAM, and load it with an abbreviated copy of the system that has all the things needed to load the full system, but nothing else (such as a normal user interface or keyboard drivers). That abbreviated copy is the "initrd.img" file, the INITial RamDisk IMaGe. Once it's loaded, control goes over to it, and it begins loading the actual full system from the "vmlinuz" file. While all this is going on, you see only the splash screen (but you can edit GRUB's actions to see play-by-play reports of it all, if you want to).

When the full system is all loaded, control goes to the "init" process, which sets up the console and virtual terminals, loads the window manager and display code, and lets you log in. The init process continues to run in the background until you shut down the machine, allowing the system to do its work more or less invisibly. init == PID #1 !!!!!!! The father of all processes.

You can view the log of all this by firing up a text editor and looking at /var/log/syslog. This file records each significant event -- and gets huge in a hurry.

I hope this helps answer your question, but it will probably prompt many more. Welcome to this wild and wonderful world!
//

-----------------------
here is another version:
Here is a typical sequence of phases your system goes through as it boots:

    bios screen
    Black with blinking cursor (short). Disk activity LEDs blink and flicker.
    Purple without cursor (long)
    Boot splash graphic (via plymouth)
    Black screen (short). Backlight may go off at this point.
    Maybe more plymouth
    Login screen. Sound (e.g. drums) plays 

Here's what's going on under the hood during each of these steps:

    BIOS detects hard drive with a bootloader (grub) present and starts it
    grub selects a kernel and loads it
    If the kernel supports Mode Setting (KMS), it puts the video card into its preferred resolution using a frame buffer (vesafb). The framebuffer is initialized with a purple background.
    plymouth displays a bootsplash image.
    gdm is started, which instantiates a new X session for the login screen to replace the framebuffer's graphics
    X attempts to put the card into one of its higher resolutions, such as the preferred resolution
    The login screen is drawn on the screen 
----------------------
Keep this advise in mind !
> 

The communication problem involved here is simply that "the operating system" isn't a single clearly defined concept. To some folk, it's only the group of core programs that enable booting up the machine, selecting programs to run, and handling input and output for those programs. To others, it's the whole computer-as-appliance package, including all the utility programs, development tools, and applications.

Learning about that first definition is daunting but possible, and can be a really fun ride while doing so. Learning all about the second is almost impossible, since the package changes faster than humans can learn about it.

-----------
 install the package and follow the instructions in /usr/share/doc/upstart/README.Debian to add a boot option that will use upstart instead of init. If your system boots and shut downs normally (other than a slightly more verbose boot without usplash running) then it is working correctly.
-----------
 you're already seeing Upstart in action.
It doesn't do a lot yet beyond replace /etc/inittab, which you will notice is gone without anyone saying much about it, or replacing it with some kind of informative placeholder. The /etc/event.d directory replaces it, which looks scary since it replaces a single nice easy-to-understand file to a whole directory of separate files. But fear not, for it replaces more than /etc/inittab--soon it will replace all of /etc/init.d. 
-----------

See these links for details:


[http://www.gentoo.org/doc/en/kernel-config.xml](http://www.gentoo.org/doc/en/kernel-config.xml)
[http://blogas.sysadmin.lt/?p=141](http://blogas.sysadmin.lt/?p=141) <- how does Linux detect, plug in my hardware 

[http://www.ibm.com/developerworks/library/l-linuxboot/](http://www.ibm.com/developerworks/library/l-linuxboot/) <-Inside the Linux boot process
[https://en.wikipedia.org/wiki/Linux_startup_process](https://en.wikipedia.org/wiki/Linux_startup_process)


[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by newb85 on 2013-08-17
I guess I don't understand.  Ubuntu uses upstart instead of the traditional init, but init is still PID #1?

---

### Post by Bashing-om on 2013-08-17
@ newb85 yep .. for discussion do:
```

ps aux

```

As I understand it .. upstart is a process started early on by "init"

[INDENT][INDENT]I am open minded (I Hope)[/INDENT][/INDENT]

---

### Post by VMC on 2013-08-17
> **newb85 said:**
> I guess I don't understand.  Ubuntu uses upstart instead of the traditional init, but init is still PID #1?
Not everything has been converted yet. They still rely on init. If you go to* /etc/init.d* and look at the symlinks, those have been converted.

---

### Post by chkneater on 2013-08-17
Nonono, upstart is new and slowly replacing init.  That's why you don't see the processes at startup anymore, you can set grub to display it if you want.

Related question (not trying to derail, sorry), could init. cause probs with USB based OS's and is upstart a fix to that?

---

### Post by newb85 on 2013-08-18
Okay, so basically, init is being phased out as its "responsibilities" are being transferred to upstart.  Is that about right?

---

### Post by ian-weisser on 2013-08-18
All linux distros use the init process.
Sysvinit, upstart, and systemd are three ways to provide the init process. Any, when running, show up as PID#1, init.
Upstart replaced sysvinit in Ubuntu.

Each has strengths and weaknesses.
Each responds similarly to a set of common commands. Examples: The 'init' command, and /etc/init.d scripts.
In addition, each has a set of its' own commands and interfaces.  Example: Upstart's /etc/init conf files.

---

