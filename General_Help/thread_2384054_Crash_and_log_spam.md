---
title: "Crash and log spam"
date: 2018-02-01
forum: General Help
---

### Post by mistcloud-misty on 2018-02-01
Hello, not quite sure where this goes. I've been using 17.10 for 2 months without any issues once I figured out how to change some settings. However, at long last I experienced my first wayland crash and finally decided to check the logs to see if anything looked abnormal. I didn't see any dump in the kernel logs but the syslog shows a lot of this: [https://pastebin.com/d4TQSHcE](https://pastebin.com/d4TQSHcE)

These happen over and over and over, as far back in syslogs as I can go. I'm not sure if they are causing any issue though, because as I said, no issues up until now. 

This appears to be as much information as I can get from between those spam logs and hard shut down and turning back on: [https://pastebin.com/KDXMcaeq](https://pastebin.com/KDXMcaeq)

Reboot went fine. Nothing new there. I didn't login to any system error messages. I'm guessing that my entire gnome session crashed, possibly from the xwayland losing connection resulting in every single process dying. Crash was sudden: screen froze completely while trying to change tab. No keyboard response, trackpad nonresponsive. Not even the sound of anything internal whirring to life as if trying to plug through a sudden process. Just nothing. 

Running a Lenovo Legion Y520, fresh install, AMD graphics card not being used due to lack of a driver so I'm using the Intel graphics.

---

