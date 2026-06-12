---
title: "Change my terminal from x-term to mate-terminal for Thunar"
date: 2018-07-19
forum: General Help
---

### Post by raleigh3 on 2018-07-19
How can I change my terminal from x-term to mate-terminal when I click open terminal here from within Thunar?

---

### Post by VMC on 2018-07-19
Does this work:```
[COLOR=#000000][FONT=Verdana][I]exo-preferred-applications
```

[/I][/FONT][/COLOR]

---

### Post by raleigh3 on 2018-07-19
yes.

I picked mate-terminal. 

It  works but gives this message when I close the terminal. 

```
Failed to  execute default Terminal Emulator. input/output error.  ??
```

---

### Post by VMC on 2018-07-19
Do you have mate-terminal installed?
```
locate mate-terminal
```

---

### Post by raleigh3 on 2018-07-19
Yes. :-)
Wondering if 18.04 has a bug.?

---

### Post by #&amp;thj^% on 2018-07-20
> **raleigh3 said:**
> yes.

I picked mate-terminal. 

It  works but gives this message when I close the terminal. 

```
Failed to  execute default Terminal Emulator. input/output error.  ??
```

If you still have 'xterm' installed, either UN-install 'xterm' -OR- optionally you could just do this if  'xterm' is still installed:


```

cd /usr/bin/
sudo mv xterm xterm.oem
```

Next be sure to do this:

```

cd /usr/bin/
sudo ln -s mate-terminal xterm
```

Check to be sure you have this:

```

cd /usr/bin/
ls -l xterm
lrwxrwxrwx 1 root root .. .. ...  xterm -> mate-terminal
```
See if that helps

---

### Post by raleigh3 on 2018-07-20
I tried both methods. Unfortunately neither worked.

I will just live with the issue.

---

### Post by #&amp;thj^% on 2018-07-20
This sounds like a permission problem IE: Read Write and I hope this dose not creep up later and cause you problems. (Failed to  execute default Terminal Emulator. input/output error.  ??)
My method has worked flawlessly on  Xubuntu and Arch XFCE DE's.
BTW I'm not trying to alarm you but just thought it was worth a mention. ;)
To revert from my Post:
```
cd /usr/bin/
sudo mv xterm.oem xterm
```
[/CODE]
And be sure to do this:
```
cd /usr/bin/
sudo ln -s xterm mate-terminal 
```
Again be sure all looks like the below:
```

cd /usr/bin/
ls -l xterm
-rwxr-xr-x 1 root root 721496 May  3 23:40 xterm

```

---

### Post by raleigh3 on 2018-07-20
I reverted it. 

Anyway to send that message to nul or something?

I would hate to have to go back to xterm. It's not a good looking or configurable terminal.

---

### Post by #&amp;thj^% on 2018-07-20
> **raleigh3 said:**
> 
Anyway to send that message to nul or something?


The right way would be is to solve the problem and not just sweep it under the rug. :)
I have to go to work right now so I will give it some thought and post back later.

---

### Post by raleigh3 on 2018-07-20
Not trying to sweep it under the rug.

I have posts at other forums and they are stumped too.

This does not occur with 16.04. Makes me suspect a 18.04 issue.

---

### Post by &amp;KyT$0P# on 2018-07-20
In Thunar go to Edit > Configure custom actions.  Select "Open Terminal Here" and click the Edit button on the right.  What does it show under "Command"?

(There maybe more than one "Open Terminal Here".  If so please post the commands for all of them.)

---

### Post by #&amp;thj^% on 2018-07-21
> **raleigh3 said:**
> Not trying to sweep it under the rug.

I have posts at other forums and they are stumped too.

This does not occur with 16.04. Makes me suspect a 18.04 issue.

As halogen2 suggests see if there is more than one entry for "Open Terminal Here" and I am unable to replicate your error here. :(
I had forgotten that I also had two after making the change to "mate-terminal"
So to be clear I now have only one entry and the command for mine is:
```
exo-open --working-directory %f --launch TerminalEmulator
```
Now also in the "Configure custom actions" you need to see if all necessary options are checked IE: "Appearance Conditions"```

```>>>See Screenshots.
BTW This is on 18.04 so it would be on your end and not so much on 18.04 itself. ;)

---

### Post by kazakore on 2018-07-21
I change it in XFCE Preferred Applications settings window and then Thunar opens whichever I have set there. Does this not work??

---

### Post by raleigh3 on 2018-07-21
I found the answer. As Thunar is my file manager, I made this custom action.
  Open terminal here

```
mate-terminal --working-directory=%f
```

---

