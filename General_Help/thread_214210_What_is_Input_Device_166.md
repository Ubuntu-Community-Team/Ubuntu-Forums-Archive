---
title: "What is Input Device 166?"
date: 2006-07-12
forum: General Help
---

### Post by Optiker on 2006-07-12
I posted on the EasyUbuntu subforum when this first came up, but it seemed to be broader than just EasyUbuntu, and there didn't seem to be any help there, so here is the broader question, with the recent EasyUbuntu context.

I am getting error messages in my Kubuntu Dapper 6.06 installation on two different computers that reference Input Device 166. What is that, and what do I do about it?

Most recently, on my home computer I ran EasyUbuntu and got that message when I first ran the console lines that are given on the EasyUbuntu download page, but in spite of that, the GUI for EasyUbuntu came up. The console output was as shown below: 

[COLOR="Purple"][B]X Error: BadDevice, invalid or uninitialized input device 166
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
Major opcode: 144
Minor opcode: 3
Resource id: 0x0
Failed to open device[/B][/COLOR]

In spite of that, it seemed to run OK, but the log included many, many additional errors referring to Input Device 166, as well as uncountable lines that were simply "error". A quick check showed that perhaps there were no changes as a result of running EasyUbuntu, and it didn't actually work.

In fact, I saved the log to an OpenOffice document and there was a total of around _85 pages_ in the log! At about 50 lines per page, that's over 4200 lines in the log - many of which were just "error".

On my other computer, this Input Device 166 has occasionally turned up as I've tried to resolve a problem with it being unable to access repositories. That's another issue that's still unresolved after many posts here and on other Liunx forums.

Comments welcome. Since this is a relatively new installation, and I'm a fairly new user who doesn't have a lot to want to try to preserve in reinstalling, I'm leaning towards deleting the installation and starting over. The next step if that doesn't resolve the problems is to give up (AGAIN!) on Linux. Therefore, since I do want to work towards migrating to Linux over the next six months, I would desparately like to get it resolved.

Thanks!
Optiker

---

### Post by Rui Pais on 2006-07-12
hi,
check if you have an entry for a wacon device on your /etc/X11/xorg.conf.

If thats the case try to comment it out (put a # on beginning of each line) like this:
```
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      #/dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
```

do it for any 
> Section "InputDevice"
  Driver        "wacom"
you find.

Reboot and check if that still happens...

---

### Post by Optiker on 2006-07-12
Rui...

Yes indeed - three sections on wacom. I've commented them out and will check it out later when I get the chance to reboot into Kubintu.

Thanks!
Optiker

---

### Post by Rui Pais on 2006-07-12
I don't know if it works. I read somewhere that was the cause of that issue... 
it won't hurt anyway, so deserves a try.

Maybe you don't need to reboot.

Just logout and on the login screen press Ctrl+Alt+Backspace. That should reiniciate the X Server. Maybe thats is enough.

Good Luck.

---

### Post by Optiker on 2006-07-12
Rui...thanks but was/am working in Windows, so need to reboot.

Optiker

---

### Post by Optiker on 2006-07-12
RUI...

Well, that was interesting!  :)

I commented out the wacom sections as you suggested (did that from Windows using an Ext file utility since I was working in Windows), and when I tried to boot into Kubuntu, it locked up right after the text screen finishes. Normally, it would launch X and the Kubuntu load screen would come up, but it went back to the low res "Kubuntu" screen with the progress bar, but no text appearing below...just locked up there. When I manually shut off the computer to get out of it, it went through an orderly shutdown with the shutdown text scrolling down below the progress bar as usual, then powered off.

I went in and uncommented those three wacom sections, and it booted back into Kubuntu just fine. However, when I tried to run konqueror as sudo, I get the following...again that same device 166 error.

[B][COLOR="Purple"]optiker@optiker-desktop:~$ kdesu konqueror
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/COLOR][/B]

Back to square one!

Thanks!
Optiker

---

### Post by Rui Pais on 2006-07-12
Hi Optiker,
that's strange, the X dont start... cause comment it only prevent a module to load. 
Are you sure that you haven't left some "EndSection" line uncommented or something alike? 
Check if any other lines have references to the named devices, like:
InputDevice "stylus" 
or "cursor", "eraser" what ever it was in your e wacom entries. Comment those too.

Do you have any Wacom Tablet or device related? 

I'm not sure if thats the solution, but shouldn't have give any problems to X. I make some search and theres quite a lot people complains about that. Unluckly i couldn't find the link to where i read that suggestion i posted... 

btw, what the output of:
```
sudo cat /var/log/Xorg.0.log | grep "(EE)"
```

---

### Post by Jun-Dai on 2006-07-16
> **Optiker said:**
> RUI...

Well, that was interesting!  :)

I commented out the wacom sections as you suggested (did that from Windows using an Ext file utility since I was working in Windows), and when I tried to boot into Kubuntu, it locked up right after the text screen finishes. Normally, it would launch X and the Kubuntu load screen would come up, but it went back to the low res "Kubuntu" screen with the progress bar, but no text appearing below...just locked up there. When I manually shut off the computer to get out of it, it went through an orderly shutdown with the shutdown text scrolling down below the progress bar as usual, then powered off.


If you had the same problem as me, you have to comment out the references to the wacom devices in the **ServerLayout** section.  See here: [http://ubuntuforums.org/showthread.php?p=1264009#post1264009](http://ubuntuforums.org/showthread.php?p=1264009#post1264009)

---

### Post by Optiker on 2006-07-17
Rui...see the note below...I apparently missed the three lines towards the bottom in xorg.conf.

Jun....that took care of it. I had apparently missed the three lines at the bottom when I commented out the others. With all wacom lines commented out, X is at least running as usual.  Haven't tried anything yet that gave me those device errors, but I'm sure that will be resolved.

Thanks both for your replies.

Now if I can just get the problem of not being able to DL from repositories resolved, I'll be in business! That issue is posted in numerous threads and other forums, and not solved yet.

Thanks again!

This thread can be consiered closed.

Optiker

---

