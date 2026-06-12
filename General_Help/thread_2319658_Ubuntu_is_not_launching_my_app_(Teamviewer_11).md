---
title: "Ubuntu is not launching my app (Teamviewer 11)"
date: 2016-04-06
forum: General Help
---

### Post by kek3 on 2016-04-06
Yo, hi everyone, I'm new here, I've been on "askubuntu", but my experience was awful... coments like "what do you expects from us" when I ask how can I lock the wallpaper... This community looks the way better :D

My problem is this, I have a** bootable USB with ubuntu 15.10**, full updated and upgraded, and I want to install on it teamviewer. I've followed google tutorials about how to install it, but once I install it, it does not launch. So I try to execute "teamviewer" on terminal, with the result of some errors like "acces denied". I try to change the ownership of the file ( sudo chown ubuntu:ubuntu ..................) but this break the program. I've unistalled it and reinstaled and now the programs has disappeard! I'm getting crazy !

I don't know in what category should I publish this, so any edits would be appreciated

EDIT: I've found some tutorial that solves the problem I have... The problem is solved :D . Because I re-edit this, I can't remember what was the link, but I can explain how I fixed the problem:

1º - We must download and install the packages, also add the architectures missing for this:```
[INDENT] - sudo dpkg --add-architecture i386
[/INDENT]
[INDENT] - sudo apt-get update
[/INDENT]
[INDENT] - sudo apt-get install gdebi
[/INDENT]
[INDENT] - wget [http://download.teamviewer.com/download/teamviewer_i386.deb](http://download.teamviewer.com/download/teamviewer_i386.deb)
[/INDENT]
[INDENT] - sudo gdebi teamviewer_i386.deb[/INDENT]

```2º- Here is were I got the problem. Executing from *dash -> teamviewer* , didn't launch, either doing with "teamviewer" commando on the terminal. In this last one I've got access denied error, even if I didn't run it as sudo ( I learned yesterday that runinng some graphical app with sudo "app" , make the app change the permissions). The problem to solve this is easy, just cd to teamviewer directory and go "ls -l" one by one, until you see some owner that's not you, some root. Then you just need to change the owner ```
"sudo chown youruser:youruser /whatever/your/program/is"
``` and, voilá! the problem is fixed. You just need to execute it (WITHOUT SUDO!!!!!)

---

### Post by RobGoss on 2016-04-06
Glad you got it all sorted out would you mind marking this post as Solved, you can use the Thread tool at the top of this post. Thank you

---

### Post by TheFu on 2016-04-06
Welcome to our forums.  We try to be a little nicer than most other forums.  I suspect the askubuntu folks were providing excellent answers, but perhaps not in a way that made sense to you, on that day.  It is hard for people who have been using Unix/Linux for 20+ yrs to remember what it was like when we were just learning. That is probably what happened there.

Please help the community by posting 
a) which tutorial helped you solve the problem - URL would be great!
b) marking this threat as "SOLVED" - by using the thread tools link near the top so people trying to help won't bother and people looking for a solution will know it was solved and how it was solved.  This helps everyone here. ;)

Hopefully, you'll find lots of answers and may be able to help others out from time to time here.

---

### Post by kek3 on 2016-04-06
Thank you! I've re-edited the post with the solve. Sorry if I made any  mistake, my english and linux experience is not as good as I wish.

I hope becoming a good member of tle forum :razz:

---

### Post by RobGoss on 2016-04-06
Glad everything work out enjoy Ubuntu

---

### Post by TheFu on 2016-04-06
Just be aware that loading .deb files directly may break other dependencies in the future and prevent patching/updates.  When that happens, you'll need to remove the .deb installed package, update/upgrade, then reinstall it (probably a newer version from the same source).  Installing .deb files directly means YOU have taken complete responsibility for keeping that package patched for security issues and new functionality.

That 2nd step - with the chown probably isn't a good idea for generic use, though it may be fine AND required for teamviewer to work (which is doubtful).  I've never used teamviewer - much prefer non-proprietary solutions.

Also, running most GUI apps with sudo is dangerous. There are undesirable complications.  There are few reasons to use sudo on a properly configured system except to load new programs or add permanent storage or modify system settings.  You can run **sudo -H /path/to/program** to reset the $HOME to point to root, which would make it safer (though not completely safe) to run GUI programs as root.  

Nothing wrong with teamviewer, but there may be better, F/LOSS, options. Let me know if you are interested.

I'm positive that your English is better than my mastery of **any** other language. ;)  I don't believe that any meaning was lost.

---

