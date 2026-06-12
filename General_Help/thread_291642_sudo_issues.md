---
title: "sudo issues"
date: 2006-11-02
forum: General Help
---

### Post by PapaLion on 2006-11-02
Alright then - I issued chown -hR username /user/bin/ 
or chown -hR root /user/bin or something similar....

Now when I try to issue the command

sudo 'anything'  I get the error

SUID must be root.

I can't fix this... any ideas?
I'm not near my computer now, i'll update when I can if more info is needed.

---

### Post by zek725 on 2006-11-02
my sudo problem is that anything that goes with **sudo** returns these errors:
```
>>> sudoers file: syntax error, line 0 <<<
>>> sudoers file: syntax error, line 1 <<<
>>> sudoers file: syntax error, line 2 <<<
>>> sudoers file: syntax error, line 3 <<<
>>> sudoers file: syntax error, line 4 <<<
>>> sudoers file: syntax error, line 5 <<<
>>> sudoers file: syntax error, line 6 <<<
>>> sudoers file: syntax error, line 7 <<<
>>> sudoers file: syntax error, line 8 <<<
>>> sudoers file: syntax error, line 9 <<<
sudo: parse error in /etc/sudoers near line 0
```

I'm in Xubuntu. For networking reasons, I tried **smb4k** (with which Konqueror came with it). that was the result. I believe Kubuntu does not use **sudo** but **su** instead. But then, I'm unfamiliar with Kubuntu so this has become a hassle. Help! How do I restore/fix this **sudo** problem!


Edit: Problem solved. > [http://ubuntuforums.org/showpost.php?p=1706595](http://ubuntuforums.org/showpost.php?p=1706595)[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by PapaLion on 2006-11-02
BUMP - original question somewhat hijacked.

---

### Post by caldevil on 2006-11-02
Didn't get your problem properly? Can you explain it again.

---

### Post by matthewstory on 2006-11-03
well, i'm not familiar with any /user folder in linux, i will assume that you meant /usr/ . . .  in any case, why did you issue this command?  A. the files in that folder (/usr/bin) should already be owned by root, and B. this should not resulte in this error.  You are certain that sudo was working directly prior to this command and not working directly after this command?

Try this, oh . . .  reboot into single user mode . . . because you can't use sudo to edit permissions:

cd /usr/bin
chmod 755 sudo
chmod u+s sudo


Then see if when you reboot you can sudo . . . best guess . . .

---

