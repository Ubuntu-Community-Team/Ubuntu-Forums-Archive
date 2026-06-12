---
title: "clamtk"
date: 2014-01-26
forum: General Help
---

### Post by deaton25 on 2014-01-26
I have clamtk! Should I set  clamtk for manual or automatic updates?Clam says that if my computer is receiving automatic updates then I should set the wizard at automaticI have no idea if my computer is now receiving them automatically or notIf I am receiving automatic updates how would I even know that the process was happening ?I rather like checking for updates manually. I can actually see and know that the update process is happening.Where and how does 'sudo freshclam' fit into all this?When , why and how would I use it ?  When would it become unnecessary or worse than that?Frequently when I use 'sudo freshclam' I get weird messages at the console to the effect that the update process is locked or another clam process is operative. Why?  Then , later on, if I  use 'sudo freshclam' it works just fine. No problem. Why? What happened to set it right?All that being said, I like clamtk. Unlike Commodo antivirus for linux, it actually works!!! It actually notices problems and allows me to quarantine them.I use chrome under ubuntu 12.04. I know nothing about computers or ubuntuThanks!

---

### Post by Dave_L on 2014-01-26
This is how you can check whether you're receiving the virus definition updates:

```
$ freshclam -V
ClamAV 0.97.8/18401/Sun Jan 26 14:23:36 2014
```

"0.97.8" is the version of the software.
"18401" is the version of the virus definitions.
"Sun Jan 26 14:23:36 2014" is the date/time of the most recent update.

---

### Post by rburkartjo on 2014-01-26
update how ever  you want. i just manually update calmtk virus definitions. you are getting the lock message because you probably have more than one terminal opened as root user or the spm open. you also might also try this. open a terminal and type sudo apt-get install clamscan. this is the same as clamtk but runs from the terminal. then open a terminal and type sudo freshclam to update your definitions. and then type sudo clamscan -r / (note there is a space between clamscan and -r and between -r and /)
this will check all your files. note it might take a few seconds to start. enjoy linux

---

### Post by deaton25 on 2014-01-26
thanks 
i did what you suggested and i got what you said i would if i was receiving virus definition updates
therefore, i guess i must be receiving automatic updates, no?

---

### Post by deaton25 on 2014-01-26
thanks
what is 'spm'? how would i know if it is open? how would i close it?
whenever i type 'sudo freshclam' at the console, i never have more than one terminal open: so that can't be the problem, correct?

---

### Post by Dave_L on 2014-01-26
> **deaton25 said:**
> thanks 
i did what you suggested and i got what you said i would if i was receiving virus definition updates
therefore, i guess i must be receiving automatic updates, no?

Do you mean you typed the command "freshclam -V"? Try it later, maybe tomorrow, and see if the output has changed. I think it updates twice a day by default.

---

