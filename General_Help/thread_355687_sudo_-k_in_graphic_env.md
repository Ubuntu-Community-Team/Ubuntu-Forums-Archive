---
title: "sudo -k in graphic env"
date: 2007-02-07
forum: General Help
---

### Post by dowoshek on 2007-02-07
Hello,
I'm looking for a solution simmilar to "sudo -k" terminal command, but which I could use in graphic environment.
"sudo -k" kills the timestamp, so for every next sudo command you'll again need typing your password. This way I'd like to avoid situation when I work all the time with root privilages and decide when EXACTLY should it be stopped.
Any suggestions?

---

### Post by DagMan on 2007-02-07
sudo -k will work for gksudo too, so if it applies to your situation, you can add it to the end of the command like gksudo gedit ; sudo -k or in the case of a nautilus script you can add it to the end of the script.

---

### Post by dowoshek on 2007-02-08
What can i say... it works :)
And thank you for help.

---

