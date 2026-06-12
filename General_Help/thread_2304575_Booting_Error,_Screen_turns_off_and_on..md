---
title: "Booting Error, Screen turns off and on."
date: 2015-11-28
forum: General Help
---

### Post by Nimit_Bhardwaj on 2015-11-28
I Installed Ubuntu about 3-4 months ago. But from last 3 to 4 days, I'm getting a problem regarding booting in my Dell Inspiron 3543 laptop. When I power on my laptop, the computer starts and navigate to a black screen where a number of commands are executing, a large number, after the commands executed, the whole screen turns black completely, and it appears that the monitor screen of laptop is switching on and off. Then when I use main power button to switch my laptop completely off and switch on it again, the purple screen arises(that screen when we keeps on pressing shift button during starting of  pc), when i select Ubuntu from there(not advanced options), again same commands on the black screen execute as described earlier but this time the computer boots successfully, and starts Ubuntu. I have only Ubuntu installed on my system. So plz tell me a way to troubleshoot this fault. I'm a student of 1st yr computer science engineering so, i don't have enough knowledge  of OS now. Plz help me.

---

### Post by Ricardo_Velasco on 2015-11-28
Greeting :

But try to help you please give me more details of the case .

Any driver you installed your graphics card ?? ..
Graphics card that you have ?? ..

Try these steps :

1. Start the computer and press the Shift key at startup to get the Grub menu. Use the arrow keys to navigate / highlight the entry corresponding to Ubuntu usually the first:

[IMG]http://i0.wp.com/blog.desdelinux.net/wp-content/uploads/2013/06/ubuntu-pantalla-violeta-inicio-1.png?w=100%25[/IMG]






2. Press the e key to edit the entry , which show the details start :

[IMG]http://i0.wp.com/blog.desdelinux.net/wp-content/uploads/2013/06/ubuntu-pantalla-violeta-inicio-2.png?w=100%25[/IMG]


3. Search entry as shown in the screenshot above . Use the arrow keys to get to it , and then I pressed the End key ( End) to go to the end of the line (which may be in the next line, paradoxically

[IMG]http://i2.wp.com/blog.desdelinux.net/wp-content/uploads/2013/06/ubuntu-pantalla-violeta-inicio-3.png?w=100%25[/IMG]


Enter the word nomodeset as shown in the capture and press Ctrl + X to start the system.


That is one possible solution out of a forum in Spanish ( my native language)


Thank you

---

### Post by Nimit_Bhardwaj on 2015-11-28
[IMG][[IMG]http://s17.postimg.org/xhj6i9n6z/IMG_20151129_091208.jpg[/IMG]]("http://postimg.org/image/xhj6i9n6z/")[/IMG]

Check the details what u want

---

### Post by Ricardo_Velasco on 2015-12-03
Next to your command line ''ro'' you can add the word nomodeset ? ..

Try it:

[IMG]http://i63.tinypic.com/ipbm8o.jpg[/IMG]

---

