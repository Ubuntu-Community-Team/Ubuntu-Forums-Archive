---
title: "Wine problems, and user problems please help"
date: 2006-10-26
forum: General Help
---

### Post by begone77 on 2006-10-26
I just installed ubuntu, updated everything, and used this ([http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)) to install wine, I ran winecfg, worked, tryed to run ~/.wine/drive_c/windows/system.ini and got a privliges error, also got some Warning: the specified Windows directory L"c:\\windows" is not accessible

thing, I dont know whats wrong but I think it has something todo with the user, I only have 1 user and its me, he should be admin etc, is there any way to just remove all users compleately so its total admin because Im the only one useing this computor, also any help on wine?

---

### Post by begone77 on 2006-10-26
I also have no .wine dir in my "home" dir, I typed "wine" in the term and got the text but still no .wine dir :/

---

### Post by begone77 on 2006-10-26
here is some text

begone77@begone77-desktop:~$ ~/.wine/drive_c/windows/system.ini
bash: /home/begone77/.wine/drive_c/windows/system.ini: Permission denied
begone77@begone77-desktop:~$ sudo ~/.wine/drive_c/windows/system.ini
Password:
sudo: /home/begone77/.wine/drive_c/windows/system.ini: command not found
begone77@begone77-desktop:~$


also

begone77@begone77-desktop:~$ wine
Usage: wine PROGRAM [ARGUMENTS...]   Run the specified program
       wine --help                   Display this help and exit
       wine --version                Output version information and exit
begone77@begone77-desktop:~$ wine help
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\help.exe": Module not found

---

