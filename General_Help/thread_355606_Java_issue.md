---
title: "Java issue"
date: 2007-02-07
forum: General Help
---

### Post by bcdeck on 2007-02-07
I'm running Edgy and having trouble with a Java-based app. When I try to exit the program, one of the windows hangs. It can be moved, minimized, etc, but not closed. The developer is working on it, but in the meantime I'd like to be able to close the window.

If I click on the window, the top bar stays gray instead of turning brown to indicate it is selected. The previously selected window continues to have the brown top-bar, and if If I hit alt-F4, that previously selected window closes.

In system monitor, there will be 2 Java processes, one sleeping and one zombie, and if I try to close the program's process it goes zombie as well. 

Is there anything I can do in terminal or another utility to close these processes?

---

### Post by FluffyElmo on 2007-02-07
From a terminal **ps -eaf |grep java** will list all processes with 'java' in their path, this should include your processes but if it doesn't replace 'java' with something more specific.

The number in the second column is the id of the process. you can kill a process by typing **sudo kill *processnumber*** where 'processnumber' is the number of the process you want to stop. Repeat as necessary, you will have to run this command once for each process, you can also repeat the *ps -eaf |grep java * command to make sure all relevant processes are stopped.

If it the process doesn't stop, then *sudo kill -9 processnumber* will work and is the least 'polite' way to kill a process:) Technically you can kill processes without the sudo, but if a process is stuck killing it as root is probably the only effective way.

---

### Post by bcdeck on 2007-02-07
OK, I found the process ID and killing by ID number worked.

But one of the zombie processes was:  /usr/bin/ssh-agent /usr/

Killing that one crashed the system. Can anyone enlighten me as to what that process is?

---

### Post by FluffyElmo on 2007-02-07
It's used to login automatically to remote ssh sites without having to enter a password. Sort of a key-manager for ssh. Odd that it should have locked, out of curiosity what Java program were you running and does it use ssh? 

It isn't the most necessary process in the world, if you want to stop it from running at boot this discussion addresses that: [http://www.ubuntuforums.org/showthread.php?t=236490]("http://www.ubuntuforums.org/showthread.php?t=236490")

---

### Post by FluffyElmo on 2007-02-07
It just occurred to me, but just because a process is listed as a Zombie in system monitor doesn't mean that it's causing problems. It generally means that it isn't active or that it is waiting for it's parent process to exit. For some processes it may be perfectly normal for them to be listed as Zombies. 

When checking for rouge processes, try typing *top* from the terminal and look for processes using excessive RAM or CPU. In your case, you can probably just kill your Java process and all will be well...

---

### Post by bcdeck on 2007-02-07
The program is a Risk-type game called Lux Delux ( [http://sillysoft.net/lux/](http://sillysoft.net/lux/) ). It is only with the latest update that it started having the sticking issue. I've also noticed that it's a bit unstable -- it's crashed a couple of times (just the program, not my system). 

On a related note, the program seems to have issues with my sound card at times. When it's running and I test audio via sound preferences, I sometimes get this error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.

But if I start an audio app (like playing an audio  stream in Rythymbox) and then start the program, the music often keeps playing.

---

### Post by FluffyElmo on 2007-02-07
I haven't used that program myself so it's hard to say. If it was stable before and now it isn't then it most likely is the program. The following is some general Java advice from when I've had issues with programs...ignore it if it doesn't apply:)

Which JVM are you using? By default Ubuntu ships the GCJ JVM which I've found to be pretty flaky. You should install a Sun JVM if you haven't already, the easiest way is to use EasyUbuntu or install from repositories. Instructions for both are at ubuntuguide.org.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_EasyUbuntu]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_EasyUbuntu")

If you're already using a Sun JVM you may want to try a different version, 1.5.x can be more stable than 1.6.0 for some things. For others the reverse may be true.

---

