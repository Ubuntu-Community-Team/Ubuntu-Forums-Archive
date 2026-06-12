---
title: "increase terminal screen font size"
date: 2013-02-07
forum: General Help
---

### Post by HalinQuincy on 2013-02-07
Hi,
       I've got 12.04 Server installed. I use a 24" screen so the default font in reeeaaallly tiny. 
What file do I need to edit and specifically how, so that I can have a permanently larger font. 
I found something that allows me to make a larger font in the default terminal window, but I lose it on logout and shutdown. Can Someone help me make this persistent?

---

### Post by furything on 2013-02-07
As you are using 12.04 and assuming you are using a GUI not command line only you can use MyUnity
[http://podzemski.com/2012/04/27/changing-the-default-font-size-on-ubuntu-12-04/](http://podzemski.com/2012/04/27/changing-the-default-font-size-on-ubuntu-12-04/)

Or 12.04 and 12.10 you can install gnome tweak
[http://hacksforge.com/how-to-change-font-size-in-Ubuntu-LTS.html](http://hacksforge.com/how-to-change-font-size-in-Ubuntu-LTS.html)

or by hand command line
[http://podzemski.com/2012/10/20/ubuntu-12-10-font-siz/](http://podzemski.com/2012/10/20/ubuntu-12-10-font-siz/)

I use 12.10 and so use gnome tweak

---

### Post by HalinQuincy on 2013-02-07
> **furything said:**
> As you are using 12.04 and assuming you are using a GUI not command line only you can use MyUnity
[http://podzemski.com/2012/04/27/changing-the-default-font-size-on-ubuntu-12-04/](http://podzemski.com/2012/04/27/changing-the-default-font-size-on-ubuntu-12-04/)

Or 12.04 and 12.10 you can install gnome tweak
[http://hacksforge.com/how-to-change-font-size-in-Ubuntu-LTS.html](http://hacksforge.com/how-to-change-font-size-in-Ubuntu-LTS.html)

or by hand command line
[http://podzemski.com/2012/10/20/ubuntu-12-10-font-siz/](http://podzemski.com/2012/10/20/ubuntu-12-10-font-siz/)

I use 12.10 and so use gnome tweak
actually, I just have the command line interface that is installed by default. I can't see the input well enough to trust what I am typing without using a magnifying glass to read what is on the screen and that makes the process rather slow <g>.
I've read that there really isn't much one can do (as regards Server functions) from a GUI. One ends up at a command line anyway to install, configure, manage and monitor on the Server.
I need to hone my command line skills anyway <g>.
I'll Keep the gui option open tho'.
So...... I still need instruction on how to set the font size and make it persistent.
Anyone?
Mahalo

---

### Post by Cheesemill on 2013-02-07
Does this help...

[http://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console](http://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console)

---

### Post by sudodus on 2013-02-07
I don't run the server edition, but a desktop edition, that I boot into text mode (with the option to start a graphical desktop environment later on). I set the font size of the text screen with the following line in the file

[FONT=Courier New][SIZE=3]/etc/default/grub[/SIZE][/FONT]

```
#GRUB_GFXMODE=640x480
```So remove the # sign at the beginning of the line and select an available mode, that you find running vbeinfo from the grub menu.
```
GRUB_GFXMODE=800x600x32
``` works well for me.

So edit that file with sudo, save, and run
```
sudo update-grub
``` After reboot you should see the difference.

---

### Post by HalinQuincy on 2013-02-07
> **Cheesemill said:**
> Does this help...

[http://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console](http://askubuntu.com/questions/173220/how-do-i-change-the-font-or-the-font-size-in-the-tty-console)
Sorry, but I kinda have to assume not. Your link leads to a page that displays a sort of GUI within which the font is adjusted. 

Again.. It is my understanding that 12.04 Server is ALL command line. So I must assume that there is a file somewhere that needs editing to change the terminal font size and make it persistent.

Mahalo

---

### Post by Cheesemill on 2013-02-07
> **HalinQuincy said:**
> Sorry, but I kinda have to assume not. Your link leads to a page that displays a sort of GUI within which the font is adjusted. 

Again.. It is my understanding that 12.04 Server is ALL command line. So I must assume that there is a file somewhere that needs editing to change the terminal font size and make it persistent.

Mahalo
That link ***does*** describe how to change the font of your tty, they are just doing the configuration from gnome-terminal in their example. You can follow exactly the same instructions from a normal tty instead.

---

### Post by sudodus on 2013-02-07
> **Cheesemill said:**
> That link ***does*** describe how to change the font of your tty, they are just doing the configuration from gnome-terminal in their example. You can follow exactly the same instructions from a normal tty instead.
Do you know if my method works also in the server edition,editing that line with 
GRUB_GFXMODE ?

---

### Post by Cheesemill on 2013-02-07
> **sudodus said:**
> Do you know if my method works also in the server edition,editing that line with 
GRUB_GFXMODE ?
It's meant to but I have never had any luck with that method personally.

---

### Post by Habitual on 2013-02-08
[What is a "Terminal?"]("http://en.wikipedia.org/wiki/Terminal_emulator")
[What is a "Console?"]("http://en.wikipedia.org/wiki/System_console")

---

### Post by ke5sfy on 2013-02-08
[http://www.securitronlinux.com/uncategorized/setting-a-larger-console-font-on-ubuntu-12-04/](http://www.securitronlinux.com/uncategorized/setting-a-larger-console-font-on-ubuntu-12-04/)

I run a 12.04 server and this works for me.

---

### Post by HalinQuincy on 2013-02-09
Thanks!! your solution worked just fine. Sorry for doubting. But there seems to be so many answers to so many variations in the tools for so many editions of Ubuntu (& other flavors), I just never know what to assume.<g>.
Now I can get on with configuring the hardware files and Services.
Mahalo Nui Loa

---

### Post by Habitual on 2013-02-09
> **HalinQuincy said:**
> I just never know what to assume.<g>.

Just don't assume that "terminal" is a console, or a console is a terminal.

[What is a "Terminal?"]("http://en.wikipedia.org/wiki/Terminal_emulator")
[What is a "Console?"]("http://en.wikipedia.org/wiki/System_console")

---

