---
title: "Help installing a certain software"
date: 2017-02-01
forum: General Help
---

### Post by clipper996 on 2017-02-01
I'm having troubles making VSync work on proprietary NVIDIA drivers, so i resolved to try and use this software called "libstrangle" which limits the FPS;
However since I'm totally ignorant when it comes to installing it and making it work (I don't even know what "LD_PRELOAD" is and google just confused me more), i'd like to know if someone can just try to give me a step-by-step guide on how to make it work. 
Here's the link for the thing: [URL="https://github.com/torkel104/libstrangle"]https://github.com/torkel104/libstrangle
[/URL]

---

### Post by mastablasta on 2017-02-02
after installing the service, use their script: 
> The included script strangle.sh, which installs into your PATH as just "strangle", can be used to simplify this.
 Examples:
strangle 60 /path/to/game

make sure the file strangle.sh is executable:
[URL="http://askubuntu.com/questions/484718/how-to-make-a-file-executable"][SIZE=2]http://askubuntu.com/questions/484718/how-to-make-a-file-executable
[/SIZE][/URL][SIZE=2][/SIZE]
to use LD preload you need you add that to your gamnes launcher (i.e. shortcut).

---

