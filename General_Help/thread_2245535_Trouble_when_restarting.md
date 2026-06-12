---
title: "Trouble when restarting"
date: 2014-09-24
forum: General Help
---

### Post by Penfold1971 on 2014-09-24
I have a machine that I have been running headless for the past two years plus. Recently I upgraded it from Ubuntu 12.04.4 to version 14.04.1.

I normally shut it down remotely from my Intel iMac, with the Terminal command 'sudo shutdown -h now', when it requires a restart after certain updates. I then go and physically power the machine on again. This all worked well until version 14.04.1. What happens now is that I can't communicate with it remotely after carrying out those steps. the remote machine isn't recognised.

Upon re-connecting the monitor, kb and mouse and powering back on, I get a screen offering me choices as to what to restart into, with Ubuntu 14.04.1 being at the top of the list, followed by 'memtest' (can't remember exactly the wording) and another option which I also forget.

I suppose I have two initial questions :

1) is the command 'sudo shutdown -h now' appropriate with Ubuntu 14.04.1?

2) is there a way I can make the machine boot into Ubuntu 14.04.1 by default so as to not have the process hang waiting for me to go and physically choose a boot option?

I must admit that I am not expert in these matters. I can only do what I do, and only 'know' what I know because I've had a lot of advice and help from these forums.

---

### Post by ian-weisser on 2014-09-24
Okay, so your restart seems to hang at the GRUB screen.

See [http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry](http://askubuntu.com/questions/148095/how-do-i-set-the-grub-timeout-and-the-grub-default-boot-entry) for how to fix that.

---

### Post by Penfold1971 on 2014-09-25
OK, thanks for that. This is new territory, so might need to come back and ask more questions.

---

