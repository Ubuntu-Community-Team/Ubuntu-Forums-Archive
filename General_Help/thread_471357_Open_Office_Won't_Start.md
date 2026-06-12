---
title: "Open Office Won't Start"
date: 2007-06-11
forum: General Help
---

### Post by tuco penguin on 2007-06-11
Help!  When I try to run any OpenOffice 2.2 application, the splash screen appears for a few seconds and then disappears and the application never actually runs.  The system monitor shows the open office process starting and then going away.  I don't know where to find OpenOffice log files to begin troubleshooting this.

Running Feisty, recently applied recommended security updates.

Any help appreciated!

---

### Post by qpieus on 2007-06-12
Open up a terminal and type

oowriter

That's the command line way to load openoffice writer. Look in the terminal output as the program tries to load. Any error messages there might indicate what the problem is. This has worked for me in the past. I had some program (not OO) that wouldn't load. The terminal output showed that a dependent program was not the right revision.

---

### Post by tuco penguin on 2007-06-12
```
** (process:1510): WARNING **: Unknown error forking main binary / abnormal early exit ...

```

Hmmm... that's pretty cryptic.  I found a thread about this error over on the official Open Office forums.  The gist was to try moving some of the MS true type fonts to any new directory.  I took the approach of trying to uninstall msttcorefonts package altogether, but Synaptic said a whole bunch of my MythTV packages were dependents and would be removed too (that seems a bit silly, really.)

Maybe I need to follow the instructions in that thread a little more literally.

Does the above message mean anything to anybody?

---

### Post by qpieus on 2007-06-12
No, that's a mystery to me, sorry. For sure read through the other thread you found. You could also try uninstalling OO and then reinstalling it.

---

### Post by Hagar Delest on 2007-06-14
Have you tried to delete or rename your OOo user profile ? ~/.openoffice.org2

---

### Post by nantetokuma on 2007-06-15
Hello,
I had the same problem. I've installed "Ubuntu Studio" and OOffice wasn't working with the same error... But if OOffice was the first thing I open in a session (after a gdm restart) it worked.

So I've uninstall OOffice, reinstall OOffice, restart gdm and now it seems to work fine...

I'll tell you if it stil work in few days... for the moment, can't help more because it works...

Dawidbass

---

### Post by nantetokuma on 2007-06-16
No, that's not working... (reinstall)
But for me, sometime OO start, sometime no, and if I restart X, sometime it starts...

Don't understand, so I stay under Dapper for the moment...

If you've got suggestions...

Bawidbass aka nantetokuma

---

### Post by carloslosgrande on 2007-06-17
Ok, I've had this before and yes its definitely a bug between Feisty and OpenOffice.
Last time removing and reinstalling OO didn't work and I had to reinstall the system...........:mad: annoying!
For my system its caused by the language install or on this occasion SCIM. I just set it up again and after restart - pow! OO is broken again.:frown:
I'm seriously considering trying some other office setup

---

### Post by tuco penguin on 2007-06-18
Thank you for the responses.   Just so you know I haven't gone away, I am still struggling with this.  I have tried completely uninstalling/reinstalling using Synaptic.  Same problem.  I have also tried uninstalling and installing the official OpenOffice verion from that web site (as oposed to the version created by the Ubuntu Feisty distribution team... didn't realize they were different.)  Required me to build .deb files from .rpms using alien.  The only difference there was the splash screen that starts for a few seconds is different, and the gnome icons are different.  The end result though is no OpenOffice and no error message.

---

### Post by Hagar Delest on 2007-06-18
Try to delete your OOo user profile (~/.openoffice.org2). If no improvement, try to launch OOo from a terminal to see what's the error message.

---

### Post by carloslosgrande on 2007-06-18
Hi, I looked back thru my old threads and found the answer to [COLOR="Navy"]my[/COLOR] problem here;
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
because it was SCIM that caused it so this fixed it.

Hagar's advice sounds good and if I get stuck again I just may ditch the ubuntu version for the official version.

---

### Post by tuco penguin on 2007-06-19
renamed the 'user' directory under ~/.openoffice.org2.  Did not help.  Open office created a new directory, but never actually started up itself.

---

### Post by tuco penguin on 2007-06-19
Thanks for the lead.  Tried that without success too, though.

---

### Post by tuco penguin on 2007-06-20
Tracing the error with strace leads me to belive a SIGSEGV error is to blame.  This is for an invalid memory reference?  I ran a memory check and my memory looks fine, although I do believe the rise of this problem correlates to the day I returned from vacation, turned on my PC and only heard "beep... beep... beep... beep"  No screen, nothing.  Cycled power, same.  Opened, removed and reseated memory, and PC awakes happy again.

I don't really understand what SIGSEGV is, but my assumption would be a rather low level programming error, which means bug, not a hardware malfunction.  Am I way off base?  Is a trip to the store for a fresh stick of memory in order?

OpenOffice is probably the most critical app I have on my system, and I can't live without it much longer.  I'm to the point of contemplating reinstalling Ubuntu Feisty or (gasp) booting the Windows partition I was getting ready to wipe clean after 6 happy months with Ubuntu.

---

### Post by carloslosgrande on 2007-06-21
Hi Tuco, I also don't know what SIGSEGV means.
When my OpenOffice couldn't be fixed from the answers I got here I just reinstalled. I know some believe that this isn't the best answer but it certainly works.
I use the following to make the reinstall reset my setup to previous so that I don't have to go back and get everything one by one.

> Ubuntu Tricks - how to generate a list of installed packages and use it to reinstall packages

This tutorial will work for any Debian based system, but is written specifically for Ubuntu.
I’ve recently had the occasion to make a complete list of software installed on one of my Ubuntu boxes, and then reinstall it from scratch. Here’s a quick and easy way to generate a list of installed .deb packages, and then use that list to quickly reinstall them.
digg_url = 'http://digg.com/linux_unix/Ubuntu_tricks_how_to_create_a_list_software_and_use_it_to_restore_your_pc';
First, let’s make the list. You’ll be doing all of this in a Terminal Session:
dpkg --get-selections | grep -v deinstall > ubuntu-files
NOTE: Wordpress interprets two dashes (- -) as one dash (–). When you’re putting this into your CLI, make sure it’s dropping two dashes ‘- -’ without the space between them.
Now you’ve got a list of all of your installed debs in a fairly small file. In my case, I simply moved this file to a thumb-drive. You could also store it on a seperate partition or on a disk somewhere. Heck, it’s not that big, email it to your gmail account.
So now you’ve got this list and all is well, until you’re Ubuntu install either dies or has to be reinstalled for some reason. Go ahead and do the base install.
Once you’ve got Ubuntu back up and running, copy your ubuntu-files back into your home directory and do the following:
sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --set-selections < ubuntu-files

NOTE: Wordpress interprets two dashes (- -) as one dash (–). When you’re putting this into your CLI, make sure it’s dropping two dashes ‘- -’ without the space between them.
Now you’ve told your system what it needs to install, so let’s install it all.
sudo dselect
This will open up a dselect session. Type ‘I‘ and allow dselect to install of the the packages listed in your ubuntu-files document. When it’s finished, type ‘Q‘ and hit the ENTER key to exit dselect.
Now you’re a lot closer to where you were before.

Thanks to UbuntuGeek for this, I've used it several times now, and I always keep an up to date copy ready in my backup files. The major problem is just waiting for it all to complete.

---

### Post by tuco penguin on 2007-06-21
Thanks.  That looks very handy.  I will likely give it a try soon.

---

### Post by Erdaron on 2007-06-30
This is an old thread, but I'm having the same problem, so I'm going to resurrect it.

When launching Writer from terminal, I get this:
```
javaldx: Could not find a Java Runtime Environment! 

** (process:12100): WARNING **: Unknown error forking main binary / abnormal early exit ...

```
(BTW, I have JRE 1.6.0-1 isntalled, check in Synaptic, that's another issue, though.)

Things I have tried that did not work:
Reinstalling OOo using Synaptic
Reinstalling OOo using official RPM using alien
Removing ~/.openoffice.org2
Removing n019043l.* from /usr/share/fonts/type1/gsfonts (suggested [here]("http://www.oooforum.org/forum/viewtopic.phtml?t=57039&highlight=feisty"))
Running oowriter as sudo

Running strace -f oowriter shows a lot of stuff, including these few lines, which I do not understand (being a fair newb):
```
[pid 11594] <... nanosleep resumed> NULL) = 0
[pid 11594] write(5, "8\2\4\0\2\0\340\2\4\0\0\0\323\323\323\0C\0\5\0\1\0\340"..., 72) = 72
[pid 11594] ioctl(5, FIONREAD, [0])     = 0
[pid 11594] poll([{fd=4, events=POLLIN|POLLPRI, revents=POLLHUP}], 1, 0) = 1
[pid 11594] poll([{fd=4, events=POLLIN|POLLPRI, revents=POLLHUP}], 1, 0) = 1
[pid 11594] getpid()                    = 11594
[pid 11594] open("/usr/lib/charset.alias", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
[pid 11594] open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 6
[pid 11594] fstat64(6, {st_mode=S_IFREG|0644, st_size=25460, ...}) = 0
[pid 11594] mmap2(NULL, 25460, PROT_READ, MAP_SHARED, 6, 0) = 0xb7f1f000
[pid 11594] close(6)                    = 0
[pid 11594] write(2, "\n** (process:11594): WARNING **:"..., 93
** (process:11594): WARNING **: Unknown error forking main binary / abnormal early exit ...
) = 93

```

Is any of this information indicative of what is causing the error?

Also, when I first installed Feisty, OpenOffice definitely worked, even after kernel updates and such. The only major change I can think of between then and now, is installing proprietary ATI drivers (fglrx). I have not tried removing them. (Though I just might, because it also seems they killed my machine's ability to hibernate properly.)

---

### Post by nantetokuma on 2007-08-08
Hello, I've found interresting things about this prob.

For me, it's not only with OpenOffice but with ardour2, Pure Data, PDF files... and prehaps other applications that i've not try. With ardour2, i've the loading page and I can load a session. Session open and when displaying it, it quits... With Pure Data, it opens but windows are empty... With PDF files in Evince or Acrobat, it doesn't display anything.

So I do Alt-Ctrl-Backspace to restart gdm and X, I log in and now, every application is running correctly...

I've been working with another screen (a flat screen) for two weeks and it didn't do that at all. Every thing was working on first start of my session.

I'm working with UbuntuStudio Feisty. My video card is a 
```
dawidbass@ubuntu-PC:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)
```
And my Xorg.conf file is
```
Section "Monitor"
        Identifier   "V995"
        HorizSync    30-96
        VertRefresh  50-150
        Option      "DPMS"
        #ajouter la ligne suivante pour V-freq: 75.00Hz // h-freq: 94.24KHz
        #Modeline  "1600x1200" 242.01 1600 1728 2024 2568   1200 1200 1204 1256
EndSection



Section "Device"
        Identifier  "ATI Technologies, Inc. RV350 AU [Radeon 9650]"
        Driver      "fglrx"
        # If X refuses to use the screen resolution you asked for,
        # uncomment this; see "Bugs and Workarounds" for details.
        Option "NoDDC"

        # === Video Overlay for the Xv extension ===
        Option          "VideoOverlay"          "on"

        # === OpenGL Overlay ===
        # Note: When OpenGL Overlay is enabled, Video Overlay
        #       will be disabled automatically
        Option          "OpenGLOverlay"         "off"

        # === Use internal AGP GART support? ===
        # If OpenGL acceleration doesn't work, try using "yes" here
        # and disable the kernel agpgart driver.
        Option          "UseInternalAGPGART"    "no"

        # You don't actually need this next BusID bit - unless maybe you have dual monitors?
        # I've removed it from mine (single monitor only) and all is well.
        # I think it's a leftover from fxglrconfig - doh!
        BusID       "PCI:1:0:0"
EndSection

```
When I've used Flat screen, I've put nothing in the Monitor section exept the identifier...
It's very strange. But I can make it work with restarting X so I can work...

If someone have the same problems, tell us. Thanks
dawidbass

---

### Post by Zeenomorph on 2007-08-17
I have the same problem, I installed the Chinese language pack, now Open Office won't even start.  The fix that Carlosgrande got works, I can run office, but I have to open my terminal and input those commands every time.  I'd like to just be able to run the program as I used to be able to.  

I have removed the Chinese software, and I have reinstalled OpenOffice.  Still the problem persists.  There is no way into the program unless I open the terminal and enter these lines of code everytime!  It's crazy!

[http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)

---

### Post by kimdh on 2007-08-27
i was having problems on feisty with scim + openoffice until i found this thread - thanks everyone.  i installed scim-bridge per carloslosgrande's directions.  i didn't want to run the script every time, so i  tried to change the default settings settings.  i'm not quite sure if this is the right way to go about doing this, but it seems to work for me.
```
sudo vi /etc/X11/xinit/xinput.d/all_ALL 
```
and changing ```
GTK_IM_MODULE="scim-bridge"
```

does anyone know any potential problems with setting scim-bridge as the default gtk im module?

(this is my first post, woot!)

---

