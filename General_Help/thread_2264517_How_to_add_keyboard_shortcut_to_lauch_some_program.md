---
title: "How to add keyboard shortcut to lauch some program?"
date: 2015-02-08
forum: General Help
---

### Post by abcuser on 2015-02-08
Hi,
1. I installed Pinta image editing program using:
sudo apt-get install pinta

Pinta icon is added to Launchpad, but I have a lot of icons on Launchpad, so I would like to launch Pinta program with keyboard shortcut.

2. I opened terminal and typed in:
pinta
to check the command to lauch Pinta and Pinta starts-up successfully.

3. In Launcher | System Settings | Keyboard | Shortcuts tab | Custom Shortcuts | + icon  in Custom Shortcut dialog I added:
Name: Pinta
Command: pinta
Appy button.

4. Double clicked in new Pinta line Disabled column and "ew accelerator" (probably New accelerator, can't see whole text and column can't be resized to see whole label) and pressed Super+P
Now in Pinta line there is Super+P. So this new shortcut was accepted by Ubuntu.

5. So keyboard shortcut should be set now. I closed keyboard dialog and pressed Super+P but nothing happened.
I exected that Pinta would be lauched, but it is not. No error returned.

6. I got back to terminal and search for the whole path:
which pinta
and I got returned:
/usr/bin/pinta

7. I Repeated steps from 3 to 5 and adding full path from step 6. But still no Pinta is lauched and no error returned. It just doesn't happen anything.

How to set keyboard shortcut to launch Pinta? Is there a way to debug why Pinta is not lauched on keyboard shortcut?

Thanks

---

### Post by ajgreeny on 2015-02-08
Have a look for the pinta.desktop file in terminal with command ```
ls /usr/share/applications | grep pinta
```and assuming that it what it is called copy it to your desktop with command ```
cp /usr/share/applications/pinta.desktop Desktop/
```

---

### Post by abcuser on 2015-02-08
I set Command: pinta
Shortcut to: Super+Control+P
and Pinta lauches without a problem.

But for some reason Super+P can not be set to launch a program.

I also tried changing Command to: gnome-terminal and I also can not assign Super+P to launch a program, but I can launch termial by Super+Control+P.
So it looks like there is nothing specific to Pinta, just for some reason Super+P can't be used for shortcut. Why? I would still like to use Super+P, I use Ubuntu and Windows and on Windows I have Super+P shortcut to lauch Pinta and I would like to have the same on Ubuntu.

Any idea how to set Super+P?

Is there some other program using this shortcut and it gets involved in accepting this shortcut before Ubuntu does? How to check this?
Thanks

---

