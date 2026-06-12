---
title: "How can I know which commands run when executing options of right-cliking?"
date: 2014-09-16
forum: General Help
---

### Post by trusalvo on 2014-09-16
When I right-click on an icon, desktop, ... I can see several options. How can I see the command(s) that are called when clicking on any of those?

Probably these commands are stored in some configuration file? Additionaly, perhaps when executing them they get stored in some log file?

Any ideas, please?

---

### Post by ian-weisser on 2014-09-16
Which flavor of Ubuntu are you using?
Different desktop environments can use different ways.

---

### Post by trusalvo on 2014-09-16
Thanks. I'm interested for answers for Ubuntu 14.04 Trusty Tahr, the current LTS release.

---

### Post by trusalvo on 2014-09-16
And for Lubuntu 14.04 Trusty Tahr. Regards

---

### Post by rolkin on 2014-09-17
Take a look at strace. This seems like what you're looking for: [http://linux.die.net/man/1/strace](http://linux.die.net/man/1/strace)

---

### Post by trusalvo on 2014-09-21
Thanks

strace seems to give info when run it along with a command (e.g. strace ls). But I want to know which command runs when I click in an option of the menu that appears when you right-click.

Any ideas, please?

---

### Post by Vaphell on 2014-09-21
i'd say it very unlikely that these options utilize command line tools underneath. There are libs providing low level functionality and both cli and gui programs use them in their code. Why use the cli middleman if you can access the low level function directly with orders of magnitude better performance?
Sure, there are programs that are nothing more than a gui wrappers top of cli, but i wouldn't expect any fundamental block of the desktop (file browser, panels, etc) to belong in that category.

---

### Post by trusalvo on 2014-09-22
Thank you

So, how can I view the libs that are activaded when clicking on a right-click menu option?

---

### Post by Sjaak Adriaanse on 2014-09-23
See the thread I posted recently '[How to find the commands and options that correspond with clicking an icon in Unity?]("http://ubuntuforums.org/showthread.php?t=2245175")' It's not exactly your question but maybe it puts you on the right track.

By the way, the file browser is indeed a program: /usr/bin/nautilus. I can activate it from within Fluxbox.

---

### Post by trusalvo on 2014-09-28
Thanks,  Sjaak Adriaanse. I'd seen that thread, but there is no info there for what I want to know. Regards

---

### Post by trusalvo on 2014-09-28
[http://ubuntuforums.org/showthread.php?t=1786591](http://ubuntuforums.org/showthread.php?t=1786591) could be useful for this.

According  to that thread in past Ubuntu versions at least some of the right-click  context menu options where in  /usr/share/nautilus/ui/nautilus-directory-view-ui.xml . Now I'm with  Lubuntu 14.04 and I don't see something similar inside  /usr/share/pcmanfm/ui . Is there something like that in Ubuntu 14.04?

As jayboe showed, in  the XML file every name of each menuitem has an action. OK, but how can  we know the libs or commands related to those actions?

---

### Post by trusalvo on 2014-09-30
The source code of Nautilus seems to be in [http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.10.1.orig.tar.xz](http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.10.1.orig.tar.xz)

But  I don't have an answer after searching and having a look to the files  inside of that  compressed file. For example, if you search for text with "safely" in  /path/to/nautilus-3.10.1/src/nautilus-view.c you see  "Safely Remove Drive", but I don't see the command(s) that achieve that  action.

---

### Post by trusalvo on 2014-09-30
The source code of PCManFM seems to be in  [http://archive.ubuntu.com/ubuntu/pool/universe/p/pcmanfm/pcmanfm_1.2.2.orig.tar.xz](http://archive.ubuntu.com/ubuntu/pool/universe/p/pcmanfm/pcmanfm_1.2.2.orig.tar.xz)  but I don't find inside the commands or libraries related to the  right-click menu.

Any help will be appreciated.

---

### Post by Vaphell on 2014-09-30
the question is what do you need it for. You have to be a rather proficient programmer to make heads or tails of things you see in the source code. Shouldn't you ask google 'how to do X in terminal' to know the answer?
Do you need to fix something, require command line option to unmount usb or what?

---

### Post by trusalvo on 2014-10-01
Thanks. I'm just trying to understand a bit how this works. For example:
I know how to remove safely an USB flash drive by terminal commands  (sudo  eject or umount + udisks --detach), but I don't find them in the  files of the source code.

/path/to/nautilus-3.10.1/src/nautilus-actions.h seems to be a key file about this. Inside it we can read:
```
#define NAUTILUS_ACTION_EJECT_VOLUME "Eject Volume"
```
Can NAUTILUS_ACTION_EJECT_VOLUME safely remove USB flash  drives by  itself (without using commands)? Is this action  related to any library  ...? Which one? How? Where it is?

Regards from a non-programer trying to learn ... Thanks for helping ...

---

### Post by trusalvo on 2014-10-02
I've run in a Lubuntu terminal "strace pcmanfm" but, after many text  lines, it says "+++ exited with 0 +++" and exists, so what you do later  in PCManFM is not shown there.

Could this be because I run Lubuntu from a Live USB?

Anyway, this would just show "symptoms", but I would like to go to the origins ...

Does  anybody know how is the "NAUTILUS_ACTION_EJECT_VOLUME" from the source  code linked to the command(s) (or the library(es) ... it/they use(s))  that safely remove or eject the USB flash drives?

---

### Post by trusalvo on 2014-10-06
In Ubuntu 14.04, using top in a terminal, I've seen that after   extracting an USB flash drive safely [clicking on "Safely Remove Drive"   or "Eject" (or the icon for it) in the Files (Nautilus) sidebar; or   clicking on "Safely remove parent drive" or "Eject parent drive" in the   Unity Launcher dock of the left] udisksd appears. This is the daemon of   udisks. I know this command to safely remove USB drives (after   unmounting its partitions):

```
 udisksctl power-off --block-device /dev/sdf
```
(instead of sdf can be sdb, sdc, ...)
(udisks --detach /dev/sdf would also do it, but udisks is not installed by default)

But if I use gnome-search-tool (after installing it -in previous Ubuntu   versions it was avaiable by default-) to search inside the Nautilus   source code files the text "udisks", "udisksd" or "udisksctl" 0   occurrences result.

Where in the source code of Nautilus is stablished the command(s) to   safely extract drives? How? (the same for the other right-click menu   options)

Thank you

---

### Post by ian-weisser on 2014-10-06
Unity and Nautilus (and others) use dbus to exchange information with other applications.

dbus is a method of interprocess communication.
It has a handy introspection feature that allows applications to know what methods are available even when the target is not running. 
And dbus has the ability to start (some) applications that are not running. 
It's all terribly clever.

Let's use the dbus-monitor application to eavesdrop on a single right-click selection in the Unity launch bar.
```
$ dbus-monitor
```
Now right-click on any launch bar item (like the File Manager icon) and right-click on any custom option (like Videos)
See the dbus-monitor window go wild with output?
Switch back to the terminal window and Use CTRL+C to end dbus-monitor.

This means that Unity doesn't need _any_ source code with a command calling Nautilus and the Videos folder. Instead, Nautilus makes Videos visible via dbus, and Unity passes the selection of Videos to Nautilus via dbus.

---

### Post by trusalvo on 2014-10-06
Thanks, ian-weisser! So it's not magic ... :-) Well, almost (for a non-programmer like me) ... :-)

---

