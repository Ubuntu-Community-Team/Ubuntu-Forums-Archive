---
title: "Disable Beryl's &lt;Shift&gt;+&lt;backspace&gt; shortcut"
date: 2007-01-05
forum: General Help
---

### Post by wcbzero on 2007-01-05
I'm using Edgy and Beryl 0.1.1

There's a shortcut <Shift>+<backspace> that logs me out that I keep inadvertently hitting. It's driving me insane and i can't seem to change it in the normal keyboard shortcuts program ([System] > [prefs] > [kayboard shortcuts]).

Is there another way I can change this

---

### Post by smartbei on 2007-01-05
I am currently running Beryl 1.5svn so this may not apply, but check under the General Options tab in the Beryl Settings Manager to see if there is a shortcut bound to a log out command.

---

### Post by wcbzero on 2007-01-05
Nope, the "logout" command doesn't even exist, and I would upgrade but my video card (ATI x1600) doesn't like the newer versions...

---

### Post by spockrock on 2007-01-05
its not a shortcut its a bug in xgl I believe, if you search, the forums you will find the solution,

---

### Post by Contrid on 2007-01-07
Has someone found a solution to this yet?
It drives me insane. I do alot of coding and use backspace + shift which keeps on logging out everytime.
Please help...

---

### Post by cmost on 2007-01-07
Have you tried running this script?

Filename:  XGL_backspace_fix
File contents:
#!/bin/bash
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

Make it executable and add it to your startup scripts in Gnome-session (or add to autostart in KDE.)  Good luck

---

### Post by Contrid on 2007-01-07
> **cmost said:**
> Have you tried running this script?

Filename:  XGL_backspace_fix
File contents:
#!/bin/bash
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

Make it executable and add it to your startup scripts in Gnome-session (or add to autostart in KDE.)  Good luck

Hi there,

Thank you for the response.
The command works perfectly great in the terminal.

I'm just trying to figure out...
With "executable" do you mean that I can create a new file on my Desktop and name it "keycode.sh" and then add that file to my startup session?
I'm just not sure about the file extension (.sh)

Thanks. ;)

---

### Post by Contrid on 2007-01-07
Thanks alot!!!
I did what I mentioned above and it worked great.
Once again, thank you for your help. You have saved me alot of frustration.

---

### Post by cmost on 2007-01-07
I found this "bug" annoying to no end until I figured out how to solve it!  Glad to be of service!  :-)

---

