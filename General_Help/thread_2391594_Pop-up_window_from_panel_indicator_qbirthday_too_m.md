---
title: "Pop-up window from panel indicator qbirthday too much to the left, not fully visible"
date: 2018-05-11
forum: General Help
---

### Post by tellapu on 2018-05-11
I managed to install the great birthday reminder tool [qbirthday]("https://github.com/lafrech/qbirthday") (Qt port of GBirthday, a GTK application) on Ubuntu 18.04.  It works fine but the displayed list (pop-up window) is placed to the left side and therefore not fully visible:
[ATTACH=CONFIG]279657[/ATTACH]
How could I change this?

Another smaller issue is that a double click is needed to open the birthday list, instead of a one left click. Any hints?

---

### Post by tellapu on 2018-05-26
Probably a Gnome update improved the placement and visibility of the window. At the moment the window is shown to the right side. But unfortunately not the whole window is seen but a third is cut off on the right side.
Is there anybody who could help with this? It would much appreciated!

---

### Post by tellapu on 2018-05-28
Unfortunately the problem (pop-up window placed too much to the left side) has returned after a restart! Any tip?
Or where do I post a bug report?

---

### Post by tellapu on 2018-06-16
I am still desperate for any lead! Once every other week, the window opens with one click and mostly visible but that is not enough! Any tip?
Or where do I post a bug report?

---

### Post by Claus7 on 2018-06-16
Hello,

I came now across your post. I'm able to fix this from ubuntu flashback, which I think that can work in your case as well.

1) one way to fix your issue would be from *ccsm* and the option: *place windows*
from place windows, while you have already opened your application, you can select it via the place windows menu and define the desired options about the size and position of the window of your application
2) another way would be more tricky: 
with the command
```
wmctrl -l
```
you will be able to see which windows are open at the time issuing the command, including the application in question. Mark the string displayed from your application, because you will need it later on.
If, for example, I have opened gnome-calculator, the result I would get will be:
> 0x04e00007  0 "username"-"pcname" Calculator
In your case you will have to write down what you will get in the place of the string: Calculator.

Now you could create a script (place it under home directory and give it executable permissions) 
for example you could give the name: qbirthday.sh
then do: ```
chmod 755 qbirthday.sh
```

After that, go to your application when you click it and choose properties and there give the full path to where you have saved your qbirthday.sh file
for example /home/"your user name"/qbirthday.sh

The contents of qbirthday.sh can be something like:
> #!/bin/bash 
"qbirthday" (substitute inside " ", the command which is needed to open qbirthday, without the " ") 
sleep 0.01 (if it works well without this line, you can omit it)
test=$(wmctrl -l | grep '.......' | awk '{print $1}')  (in '...' you have to substitute the string that you got when you issued the command:  wmctrl -l from before, without using the ' ')
wmctrl -i -r $test -e 0,400,100,500,500 (here you give information about the size and position of the window of your application - you can change the values to your liking)

Regards!

---

### Post by tellapu on 2018-06-16
@claus7 Thanks a lot for your help!
1. CSSM: I tried to grab the class, ID, name, ... of the window, but it would only give me the type and it is called "utility". With that I tried to add a setting, but it does not really work. Not sure if it is me or the window ;-). See screenshot:
[ATTACH=CONFIG]280112[/ATTACH]
2. This is looks a complicated ;-). When I find time, I will try. The result of wmctrl is probably "0x03200005  0  N/A MainWindow", interesting it is not related to the user (N/A). Will your script still work?

---

### Post by Claus7 on 2018-06-16
Hello,

you are welcome! I hope that you will be able to solve your issue:

1) I would keep "class" and choose the window of the application, while it is open. It might be the window if it does not work.

2) In order to verify and be be certain about the fact that Main Window belongs to your application, you could issue the command, while qbirthday is running and after that, close the application, and issue the wmctrl -l once again (while you are not closing or opening any other windows in-between). If the only difference is the Main Window, then you should have your answer.

Now, your script would look like this:

> #!/bin/bash 
"qbirthday" 
sleep 0.01 
test=$(wmctrl -l | grep 'Main Window' | awk '{print $1}') 
wmctrl -i -r $test -e 0,200,200,500,500 

Just to point out that after grep you need the ' ', since you have two words.

Regards!

---

### Post by tellapu on 2018-06-30
@Claus7 Thanks a lot for the tips as well as the script! I will keep this helpful script in mind in case the situation changes or I have a similar problem with another app.
In the meantime somebody helped me to find a **workaround**: Reduce the number of displayed birthdays in the  preferences until the window is not anymore too tall for the screen and  the window is fully visible (at least on my system).
There is a also a **launchpad bug report**: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1777240](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1777240)

---

