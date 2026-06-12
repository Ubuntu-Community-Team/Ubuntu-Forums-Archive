---
title: "Kubuntu freeze"
date: 2022-02-07
forum: General Help
---

### Post by demonenero84 on 2022-02-07
So my system froze, I took a look at /var/log/syslog
This is what I get
> 
Feb  7 16:20:24 aris-System-Product-Name gvfsd-trash[1531]: *** Unsupported operation detected on trash directory
Feb  7 16:20:24 aris-System-Product-Name gvfsd-trash[1531]:   dir: /home/aris/.local/share/Trash/files, file: xdg-desktop-portal-gtk.desktop, type: 4#012
Feb  7 16:20:39 aris-System-Product-Name systemd[921]: Started Kate - Advanced Text Editor.
Feb  7 16:20:39 aris-System-Product-Name kglobalaccel5[10727]: Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
Feb  7 16:20:39 aris-System-Product-Name kglobalaccel5[10727]: kf.sonnet.clients.hspell: HSpellDict::HSpellDict: Init failed
Feb  7 16:20:39 aris-System-Product-Name kglobalaccel5[10727]: Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
Feb  7 16:20:39 aris-System-Product-Name kglobalaccel5[10727]: kf.sonnet.clients.hspell: HSpellDict::HSpellDict: Init failed
Feb  7 16:20:40 aris-System-Product-Name kglobalaccel5[10739]: Qt: Session management error: networkIdsList argument is NULL
Feb  7 16:20:52 aris-System-Product-Name systemd[921]: app-org.kde.kate-9a4fa3fc4b7f4e629b705c923a0730e2.scope: Deactivated successfully.
Feb  7 16:20:52 aris-System-Product-Name systemd[921]: app-org.kde.kate-9a4fa3fc4b7f4e629b705c923a0730e2.scope: Consumed 1.402s CPU time.
Feb  7 16:20:52 aris-System-Product-Name org.freedesktop.impl.portal.desktop.kde[1457]: xdp-kde-background: GetAppState called: no parameters
Feb  7 16:23:43 aris-System-Product-Name systemd-modules-load[336]: Inserted module 'lp'
Feb  7 16:23:43 aris-System-Product-Name systemd-modules-load[336]: Inserted module 'ppdev'
Feb  7 16:23:43 aris-System-Product-Name systemd-modules-load[336]: Inserted module 'parport_pc'
Feb  7 16:23:43 aris-System-Product-Name systemd-modules-load[336]: Inserted module 'msr'

So it froze at 16.20.52 (I could not move the mouse or input keyboard commands, I had to do a hard reset), I get a long list of "Unsupported operation detected on trash directory" all at 16.20.24
Any suggestions? should I look inside other files or look for something specific in this file
thanks a lot in advance

---

### Post by el-viejo on 2022-02-07
Looks like Kate had something to do with it (appears it was trying to access dictionary/spelling tools prior to crashing),

Were you actively using Kate when KDE crashed? Looks like it somehow barfed on itself, not sure if that was due to file operations (moving/deleting a temporary/work file) or just from Kate trying to access those other utilities. If you weren't running Kate at all then that's a bit more concerning/odd, but otherwise I'd just chalk this up to (hopefully) a one-off Kate issue.

Edit: May also consider emptying your trash bin.

---

### Post by demonenero84 on 2022-02-07
thanks a lot for the reply :)
Yes I was using kate, my trash bin is now empty

---

### Post by SeijiSensei on 2022-02-07
There are indications Kate is trying to access support for Hebrew. Do you have the appropriate language packs installed?

Take a look in System Settings > Regional Settings > Languages.

---

### Post by SeijiSensei on 2022-02-08
I updated my 22.04 system and encountered the same error you did. Running "sudo apt install hspell" solved the problem.

---

### Post by demonenero84 on 2022-02-08
thanks
if I go to System Settings > Regional Settings > Languages the language is "American English", if I keep my mouse pointer on it I get a message "Not all translations for this language are installed, use the install missing packages button to download and install the missing packages" 
After running "sudo apt install hspell" I still get the same message
Edit: I was able to install the missing packages ( I added a language and the "install missing packages button" appeared, then I removed the other language )

Edit 2:It froze again when using Duckstation (psx emulator), I tried using Duckstation a second time and it froze :( , so I unistalled Duckstation

Since I hard reset a few times ( actually 3 in the last days :) ) should I do anything to check my ssd?
many thanks in advance

---

