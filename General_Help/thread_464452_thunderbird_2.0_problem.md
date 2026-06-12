---
title: "thunderbird 2.0 problem"
date: 2007-06-04
forum: General Help
---

### Post by xbobo on 2007-06-04
I have installed tb 1.5 in my Feisty, then want to upgrade to tb 2.0. coz I found it's better than previous version in my windows.

so I search some posts here and downloadn Automatrix 2 to install tb 2.0. When I installed it, at2 asked me to uninstall tb1.5 then tb2.0, I clicked ok. But I can't run tb2.0 after the installation finished. it says:

Failed to execute child process "mozilla-thunderbird" (No such file or directory)

then I just uninstalled tb2.0 by automatrix2 and want to back to tb1.5, but still have the same problem as above.

then I removed automatrix2 and try to install tb thru system add/remove tool, again the problem comes out.

so I still can use tb at all, what should I do now, I really want to use tb rather than evolution mail.

Thanks in advance.

---

### Post by thelocust on 2007-06-04
You could try the script I attached. I am not responsible for what happens I got this script off the internet some were and I don't know if it will fix it but it makes a backup before it does anything so I think you should be pretty safe. If your lucky this will get you Thunderbird 2.0 working with your old configuration and emails.

download it to your desktop and run

chmod u+x installnewthunderbird.sh
and then
bash ~/Desktop/installnewfirefox.sh -install
and 
bash ~/Desktop/installnewfirefox.sh -uninstall
if it doesn't work. Good luck.

---

### Post by jrusso2 on 2007-06-04
It says no  such file or directory.  I would check the link and see if its pointed to the install.  Maybe it didn't even install. Or the link is pointed wrong

---

### Post by a85lee on 2007-06-06
i got the similar problem as well, the thunderbird does not run at all, i used the script and add removal tool to install it, it is still not working, really need a solution. thanks

---

