---
title: "how to allow nonroot user to set wakealarm (properly)?"
date: 2017-05-25
forum: General Help
---

### Post by pruda on 2017-05-25
Hi, I'm echoing wakeup time to /sys/class/rtc/rtc0/wakealarm to plan power on at specific times and it works fine, but it requires sudo and I'd like to do this as non root, members of video group. I'm using linux for some time now, but I missed the first lessons about rights and owners, so I'm asking here. When I want to allow specific non root user to plan power on schedule, is this correct way doing that?

1. sudo chgrp video /sys/class/rtc/rtc0/wakealarm
2. sudo chmod 664 /sys/class/rtc/rtc0/wakealarm

When something does not work and I don't have day long for finding why, I usually disable SElinux (on centos, ubuntu luckily does not have it enabled by default) and/or use sudo chmod 777 /what/ever. You guessed that, I'm converted windows user ;-) but I think it's about time to start doing things safely... Thanks.

---

### Post by pruda on 2017-05-26
In addition to that permissions of /sys/class/rtc/rtc0/wakealarm won't survive after reboot. I think that writing chmods to rc.local might solve that, but it does not look clean to me. So what's the correct way?

---

