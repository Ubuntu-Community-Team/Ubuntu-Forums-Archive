---
title: "[ubuntu] replacing colors in ssh client"
date: 2017-07-13
forum: General Help
---

### Post by damianhlozano on 2017-07-13
Hello,
We have a server with an old software and we use allways this software by connecting machines with putty.  The software has an issue, some menues appear in yellow backgound and White fonts, so it is hard to read.  We allways remplace the "ANSI Yellow" color with anoter color.
Now, I have installed an Ubuntu minimall and I can not use putty because I do not have GUI, I can use ssh but I have still the issue with the yellow color
I think there are 3 different possible ways:
- Or do something to make putty work without gui
- Or replace colors in ssh
- Or use another ssh client, which allow me to replace colors
I dont know how to accomplish anyone of these options
Any idea?

Thanks in advance
Regards!
Damián

---

### Post by efflandt on 2017-07-13
You have not said what old software has those menus or an example of what they look like. Typically if you use a terminal with black background, yellow print (foreground color) should not be a problem, but if you use a white background, yellow print would be a problem.

You can change foreground and/or background colors with ansii escape codes. If the software sets various foreground and background colors within its menus, I would think it would match suitable foregrounds and backgrounds and not sure how you would change that. If it only sets various foreground (text) colors, you just need to use a suitable default background color. You could possibly incorporate ansii escape codes into a prompt in your ~/.bashrc (which has example of color prompt).

Examples of ansii color codes: [http://misc.flogisoft.com/bash/tip_colors_and_formatting](http://misc.flogisoft.com/bash/tip_colors_and_formatting)

A handy command to know if you totally mess up your screen by viewing binary code as text (messed up character set, etc.) or accidentally doing black foreground and background is to blindly type the following at prompt or beginning of line in the shell and hit Enter key to restore a readable screen with normal characters:```
stty sane
```

---

