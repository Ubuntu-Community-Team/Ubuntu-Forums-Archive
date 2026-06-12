---
title: "Ubuntu script won't work in Lubuntu"
date: 2017-09-10
forum: General Help
---

### Post by steve169 on 2017-09-10
In Ubuntu 16.04 I wrote a script that clears the clipboard:[INDENT]
chmod a+x ./ClearClip
#!/bin/bash
xsel -bspc
exit
[/INDENT]

It runs from a desktop icon and works fine.

I also run Lubunu 16.04 from a thumb drive. I copied the same script to Lubuntu's desktop, but it won't work from the desktop icon. It *will* work if I run it from Terminal.

One difference:

In Lubuntu, I right-clicked the icon and went to Properties -> Permissions. (See attached screen shot.)

Unlike in Ubuntu, there is no check box to enable running the file as a program.

Advice, please.

---

### Post by vasa1 on 2017-09-10
> **steve169 said:**
> ...

One difference:

In Lubuntu, I right-clicked the icon and went to Properties -> Permissions. (See attached screen shot.)

Unlike in Ubuntu, there is no check box to enable running the file as a program.

Advice, please.Click on "Nobody". You'll see more options to make the file an executable and to choose who is allowed to execute the file (run the file as a program).

---

### Post by again? on 2017-09-10
Does that command clear both the selections for you?
Does not clear the primary selection (mouse highlight/mouse middle click paste) for me.
To clear both the primary and clipboard selections I need to run both
```
xsel -c
xsel -cb
```

Combining the options in one command 
```
xsel -bspc
```
only clears the clipboard selection here.

---

### Post by steve169 on 2017-09-11
Dear Guber2:

Thanks. I'll correct the commands.


Dear Vasa1:

I changed the "Nobody" to "Anyone," rebooted, but the script still isn't executing when I click the icon.

Any further suggestions?

---

