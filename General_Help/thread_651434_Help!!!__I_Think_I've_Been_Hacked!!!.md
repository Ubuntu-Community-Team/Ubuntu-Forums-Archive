---
title: "Help!!!  I Think I've Been Hacked!!!"
date: 2007-12-27
forum: General Help
---

### Post by Ertai87 on 2007-12-27
So, I think I may have been hacked, which is disappointing considering I switched to Linux because I thought my Windows was being hacked.  This is why I think I've been hacked:

First off, I had my laptop in sleep mode.  I brought it out of sleep mode, signed in, re-logged into Pidgin, and then I couldn't give any input to my computer.  Everything was working fine, but then all of a sudden all I could do was move my mouse.  No keyboard, no clicks, nothing.  So I rebooted.

Upon rebooting, my input was fine, but I went into my system monitor and found that one of my processes, SCIM, was a "zombie".  I didn't kill it, and it's never done that before.  Upon trying to restart it (without killing the zombie), it said the new process "exited abnormally".  Upon trying to kill it, I appear to be unable to.

Additionally, I haven't had any security or program updates since before Christmas, although I check every day.

So, opinions?

---

### Post by shad0w_walker on 2007-12-27
I'm gonna put it simply. If you have been hacked I will eat my hat and fridge. What probably happened is there is something in your laptop that disagrees with sleep mode. It happens from time to time with some hardware and can cause things to lock up/act oddly/whatever. The process exiting abnormally is probably from the reboot and the program not having a chance to shutdown cleanly.

---

### Post by Ertai87 on 2007-12-27
I rebooted again cleanly after finding this zombie thing, and after reboot it became a zombie again.  Then I made the post here.

---

### Post by p_quarles on 2007-12-27
> **shad0w_walker said:**
> I'm gonna put it simply. If you have been hacked I will eat my hat and fridge. What probably happened is there is something in your laptop that disagrees with sleep mode. It happens from time to time with some hardware and can cause things to lock up/act oddly/whatever. The process exiting abnormally is probably from the reboot and the program not having a chance to shutdown cleanly.
+1. That is exactly what happened, and the fact that SCIM was running as a zombie is certainly not evidence of an intrusion.

---

### Post by Ertai87 on 2007-12-27
Correction: IS running as a zombie.  How can I make it run normally again?

---

### Post by p_quarles on 2007-12-27
Do you have any use for SCIM? If not (and I'm betting you would know if you did), you can just remove the service from the session startup routine.

---

### Post by Ertai87 on 2007-12-27
I use it for Japanese text input.  So far it doesn't look like anything's gone wrong with that, but why is it running as a zombie, and why can't I kill it, and how can I kill it, and how can I make it normal again? :'(

Also, it doesnt appear in the session startup routine.

---

### Post by p_quarles on 2007-12-27
Gotcha. Is it currently allowing you to use it for that?

---

### Post by raycosm on 2007-12-27
> **Ertai87 said:**
> 

First off, I had my laptop in sleep mode.  I brought it out of sleep mode, signed in, re-logged into Pidgin, and then I couldn't give any input to my computer.  Everything was working fine, but then all of a sudden all I could do was move my mouse.  No keyboard, no clicks, nothing.  So I rebooted.


Sleep mode for me works fine when I get back to my computer (surprisingly), but I get those same results after I come back from a hibernate. That's most likely your hardware not getting along with suspend/hibernate.

---

### Post by Ertai87 on 2007-12-27
> **p_quarles said:**
> Gotcha. Is it currently allowing you to use it for that?

Sorry, I lightning-edited but you lightning-replied.

Also, just a note: When I came up from suspend, everything worked fine.  Nothing went wrong until I logged back into Pidgin.  Sometimes Pidgin makes my comp unresponsive for a second or 2 while it loads, but this time it was much longer.

---

### Post by p_quarles on 2007-12-27
> **Ertai87 said:**
> Sorry, I lightning-edited but you lightning-replied.

Also, just a note: When I came up from suspend, everything worked fine.  Nothing went wrong until I logged back into Pidgin.  Sometimes Pidgin makes my comp unresponsive for a second or 2 while it loads, but this time it was much longer.
:D 

If it's working, there's not much cause for alarm. Basically, a "zombie" process is one that's not currently running (which is why you can't kill it), but its parent process thinks that it is still running. There may be a way to fix that, but I don't know how. If it's allowing you to enter Japanese text, my advice would be to not lose any sleep over it.

The Pidgin problem is likely unrelated -- I believe that you're experiencing a known bug with that program (i.e., the unresponsiveness).

---

### Post by Ertai87 on 2007-12-27
Previously, though, when I had a zombie process, I went to System Monitor, right-clicked on the process, went to "kill process", and it died.  And what's the parent process of scim anyway?  Isn't scim the parent process of a bunch of other things?  Also, I now have a couple processes I haven't seen before, scim-helper-launcher and scim-helper-manager.

Also, how come it never became a zombie before?  And after rebooting, it's still a zombie...

---

### Post by p_quarles on 2007-12-27
Since I don't use SCIM myself, I'm afraid I can't be much help. I did take a look at the man page, though, and this caught my eye:
> To use scim in GTK IM mode, just start any GTK+ application, then right click in the application, choose "Input Methods -> SCIM  Input  Method" in  the  pop-up  menu,  and  scim should automatically start.  Alternatively, you can use the following commands to set scim as  the  default GTK IM module (again assuming Bourne style shell):
              GTK_IM_MODULE="scim"
              export GTK_IM_MODULE
              <gtk-program>
       Here  scim  will also automatically start when you start your GTK+ program.  However, it&#8217;s still a good idea to start scim explicitly even if you  use  GTK  IM mode, because if only one application is using GTK IM mode, scim will automatically stop  when  you  quit  this  application.
       Then  when you start a new application, scim will start again, this can cause quite long delay for application start and  quit,  giving people the impression of "everything slows down when using scim".
Is something like that possibly related?

---

### Post by Ertai87 on 2007-12-27
I remember setting something like that up with I installed SCIM...when I do the right-click thingy, nothing happens to the zombie process in the system manager.

---

### Post by penguinbreath on 2007-12-27
Correct me if I am wrong, but can't you just type

```
who
```

or

```
who -al
```

in the terminal to see if you are being hacked/been hacked?

---

### Post by p_quarles on 2007-12-27
Running those commands would only alert you to very inept crackers.

---

### Post by Ertai87 on 2007-12-27
There appear to be 2 entries under my local name when I do that...once says tty7, the other says pts/0...what does that mean?

---

### Post by p_quarles on 2007-12-27
Most likely they're both you. Run the "w" command to find out what exactly is being associated with both instances of your login.

---

### Post by Ertai87 on 2007-12-27
Ah, yes, they are both me.  The tty7 entry is my master login, while the pts/0 entry is me starting terminal.  Cool.

---

### Post by Ertai87 on 2007-12-27
OK, so I installed Firestarter since I heard it's worth having, and it says that it's persistent even while it's not running...how can I verify this?

Also, for some reason a Nautilus process started recently.  I never use Nautilus.  When I came here to ask about it, though, the icon in system monitor changed from the shell thingy to something that looks a bit like a photo.  I noticed the second icon on the Desktop icon when I start nautilus.  The command line execute is "nautilus --no-default-window --sm-client-id default2".  Is this normal?

---

### Post by Ertai87 on 2007-12-27
OK, so I'm just wondering: Does anyone have an explanation or experience with the things that happened to me so I know I wasn't hacked?  I have no evidence that I was; nothing appears to be wrong with my system, except the SCIM thingy.  I'm looking for an excuse to drop the issue, but I'm a CS major in university, so having a secure, functioning computer is very important to me.

---

### Post by Ertai87 on 2007-12-28
OK, so I found out that this problem with SCIM is actually a problem with my x-session-manager, which does not appear to be waiting for the scim process to die (more information on exactly how I debugged this and other things I've done at [http://ubuntuforums.org/showthread.php?t=651728](http://ubuntuforums.org/showthread.php?t=651728)).  So does anyone know how to force my x-session-manager to wait?  I have a friend who also uses SCIM and she says her x-session-manager waits.  I'd like to try reinstalling x-session-manager if it's possible to do without reformatting, but first I'd like to try forcing a wait to see if that's the problem.  Does anyone know how?

---

### Post by Ink-Jet on 2007-12-28
Why bother?
Everything seems fine with your computer.

---

### Post by posterboy on 2007-12-28
Maybe I can contribute something on the "zombie". First, you haven't been hacked. A zombie is normally encountered in the Unix-like systems. What is the cause? It is the invariable result of something starting a process, and then the starter dies. This leaves a zombie. A normal "kill" command will never kill these. What WILL work, is to find the starter process, and kill it. If this can't be done, it's quite safe to ignore the thing until a reboot occurs. Normally, it is using zero resources, so it's a no harm, no foul, sort of thing.

---

### Post by Ertai87 on 2007-12-28
That's the problem.  The parent process is x-session-manager, which can't be killed while still logged on, and every time I reboot I have the zombie.  I'm reasonably sure I haven't been hacked since nothing else appears to be wrong (although according to Firestarter my firewall's been off for quite some time which makes me kind of nervous), but I'd like to get this problem resolved if possible.  It just makes me nervous to have processes running that I don't need or aren't using, y'know?

---

