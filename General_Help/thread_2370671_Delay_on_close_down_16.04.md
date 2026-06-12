---
title: "Delay on close down 16.04"
date: 2017-09-06
forum: General Help
---

### Post by Robbyx on 2017-09-06
I get an error on closedown: A stop job is running for session 2 of user ...

I have tried various solutions as contained in this link

[https://askubuntu.com/questions/626144/crazy-boot-and-reboot-times-after-upgrading-to-ubuntu-15-04-a-stop-start-job-is#630495](https://askubuntu.com/questions/626144/crazy-boot-and-reboot-times-after-upgrading-to-ubuntu-15-04-a-stop-start-job-is#630495)


Rolling back from systemd to upstart made no difference, plus  my system seemed to have strong doubts about starting so I reverted back to systemd

The watchman solution did not work but I think it is because I do not know which job is running whereas the example shows pacman.

Is there a better way to tackle the delay?


Robin

---

### Post by mc4man on 2017-09-06
See here, in the bug report devs suggested they probably should have set the default timeout to 30 seconds, my experience is that when this happens it always times out so set here to 10 secs 

[https://ubuntuforums.org/showthread.php?t=2331743&p=13522335#post13522335](https://ubuntuforums.org/showthread.php?t=2331743&p=13522335#post13522335)

---

### Post by Robbyx on 2017-10-01
Thank you for your help. I did not notice the reply until now and have adjusted system.conf.

Robin

---

