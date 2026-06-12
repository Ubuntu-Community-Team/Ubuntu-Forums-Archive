---
title: "sudo broken on hardy server edition"
date: 2008-05-02
forum: General Help
---

### Post by sammydee on 2008-05-02
Hi all.

God knows what the hell I did, it may have had something to do with changing the system hostname, but sudo now seems utterly broken.

If I do sudo command, something like this happens:

```

sam@desktop:~$ sudo su
[sudo] password for sam: 
sam@desktop:~$ sudo command
[sudo] password for sam: 
sam is not in the sudoers file.  This incident will be reported.
sam@desktop:~$ sudo anything
[sudo] password for sam: 
sam@desktop:~$ 

```

Weirdly it only said I'm not in the sudoers file when I typed sudo command to paste in this post to show what happens if I sudo a command! It hasn't said that at any other time.

I've managed to get root access by booting into recovery mode and doing passwd so I can su root now. How do I get sudo back?!

On an unrelated topic, pulseaudio broke at the same time. Might be again due to me changing the system hostname.

Sam

EDIT: Fixed it, I had accidently removed myself from the admin group. DOH!

---

