---
title: "Greeting Scripts."
date: 2008-05-01
forum: General Help
---

### Post by MechWarrior001 on 2008-05-01
Hi, I'm MechWarrior001 (Mech for short) and I'm kinda new to Ubuntu.

I'm not sure if this is in the right forum but is there a way to make a script that has Ubuntu make a greeting message of user choice pop-up when you login/logon?

---

### Post by chewearn on 2008-05-02
If you would like to display message boxes, or dialog boxes, a common tool is zenity.  Install it by:
```
sudo apt-get install zenity
```

To find out how to use it:
```
man zenity
```

You can use zenity in a bash script.  Here is a sample to show a dialog box:
```
#!/bin/bash
zenity --info --title "Message" --text "Hello world\!"

```

Now, if you add the script to Sessions > Start-up, you should get the dialog box every time you logged in.


If you are looking more for a notification pop-up balloon kind of message, you can use libnotify-bin.  I will provide an example, if you need help to figure this one out.

---

### Post by MechWarrior001 on 2008-05-02
```
sudo apt-get install zenity
```Is that a repository link?

```
man zenity
```Do I type that in Terminal?

```
#!/bin/bash
zenity --info --title "Message" --text "Hello world\!"
```How and where do I go to make a bash script?

P.S. Is terminal the Linux version of Command Prompt/Command.com/MS-Dos?

---

### Post by chewearn on 2008-05-03
Yes, terminal is the command prompt.  To open a terminal:
Top panel menu > Applications > Accessories > Terminal

Most things don't need the terminal.  But for what you want to do, bash scripting is one easy method.

To create a bash script, simply open the text editor:
Top panel menu > Applications > Accessories > Test Editor

Save your file anywhere is your home directory.  You then need to set the executable flag:
```
chmod +x <filename.sh>
```

where <filename.sh> is the file name you saved using the Text Editor.

---

