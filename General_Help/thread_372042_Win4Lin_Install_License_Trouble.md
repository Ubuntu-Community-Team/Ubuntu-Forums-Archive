---
title: "Win4Lin Install License Trouble"
date: 2007-02-27
forum: General Help
---

### Post by ibohren on 2007-02-27
Hello,

I'm new to the Ubuntu and Linux community, so I hope I'm posting this in the right section. I'm running the latest Ubuntu release version 6.10. I installed Win4Lin Pro 3.5. When attempting to license it in the terminal it accepts my licenses number but then I get:

License accepted.

/opt/win4linpro/bin/ask_license.sh: 119: cannot create /var/win4linpro/install/license.lic: Permission denied
chown: cannot access `/var/win4linpro/install/license.lic': No such file or directory
chmod: cannot access `/var/win4linpro/install/license.lic': No such file or directory
ibohren@ibohren:~$ 

When I run the program again it still shows me in the 30 evaluation period and does not show as licensed. I verified that the directory /var/win4linpro/install does exist, but for some reason it seems that it can't create the file license.lic here.

Please forgive me, I'm still very new to Bash scripting. Can anyone tell me what this means and what I need to do to rectify this. I am logged in as root, so I'm not sure why I'm getting permission denied.

Thanks in advance.

---

### Post by taurus on 2007-02-27
What command did you run to try to install the license?  Just put the **sudo** in front of the command so you can write to /var/win4linpro/install/license.lic.

---

### Post by ibohren on 2007-02-27
Wow, I can't believe it was that simple. That did it. Thanks a ton for your help.

---

