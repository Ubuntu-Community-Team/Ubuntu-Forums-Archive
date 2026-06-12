---
title: "Programs and Screen full ob bugs ... should I format my Labtop ?"
date: 2017-02-09
forum: General Help
---

### Post by dav1309 on 2017-02-09
Hello to everyone,

I installed Ubuntu on my labtop arround 6 months a go and since them the OS is full of bugs:

[FONT=arial]For instance, the windows of the programs collapse into a extremely small window which I can't even open. They still continue appearing in the program bar as opened, but they are in some weird way minimized and many times I can't manage to maximize them, having to close them [/FONT]

[FONT=arial]Many times when I am going to Suspend the Laptop (not Turn Off), Ubuntu simply gets stuck and ends up crashing and turning totally off. When I reboot my computer a black screen with a text saying something like "Orphan node not found" appears in screen.[/FONT]

[FONT=arial]Other times, when I am using some program, the program's window some times starts blinking and becoming semi-transparent, so I can see both Program and the Desktop at the same time and it just blinks and blinks.

Some of the functions of the programs, for example Libre Office have also stopped working. When I click in the "insert formula" option in Libre Office the windows go all crazy and I can't even see the formula that I am tipying (because some random window appears on top of it) and the window which contains help for pre-defined formulas used to appear and no longer appears any where.

Because of this I plan to totally re-install Ubuntu from a memory stick. Do you think these could solve my Bugs ? ... this glitches are to strange and they make me believe that somehow  I did not install Ubuntu well in the first place. I really don't now what, since installing Ubuntu I did not do anything, its straight forward.

[B]Ubuntu 16.04 LTS
 Memory: 7,7 GB
 Processor Intel Core I7-3537U CPU @ 2 GHz x 4 Graphics: Intel Ivybridge Mobile (EVEN THOUGH I really have a NVIDIA GeForce 720M) 
OS Type: 64bit[/B][/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]
[/FONT]

---

### Post by TheFu on 2017-02-10
Welcome to the forums.

Have you been patching the system every 1-4 weeks?  [https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](https://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc) - slightly dated, but still relevant.  Basically, use "apt" instead of "apt-get."

Have you looked at the log files for issues?  On Linux, the logs tell the story.  For example, when a driver has issues or when some hardware is starting to fail. Those things should be in the logs.
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

I wrote a script to capture system information: It will post that to a pastebin clone - just provide the URL back here. [http://blog.jdpfu.com/2015/09/05/getting-comprehensive-system-information](http://blog.jdpfu.com/2015/09/05/getting-comprehensive-system-information) do NOT copy/paste the script from the article. Use the [download link]("http://blog.jdpfu.com/files/quick-sys-info.sh").

Certain laptops have known issues or non-standard setup needs. If you shared the exact model and specs, then someone might be able to help. 

Best to stick with 1 question per thread.  Disable suspend and try to only work on the GPU / Display issues for now.

Good luck to you.

---

