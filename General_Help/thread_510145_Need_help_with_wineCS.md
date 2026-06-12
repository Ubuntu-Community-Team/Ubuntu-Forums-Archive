---
title: "Need help with wine/CS"
date: 2007-07-26
forum: General Help
---

### Post by nu buntu on 2007-07-26
Hi everyone, I'm new to ubuntu and I think its great!  I recently installed wine and steam so I could play counter-strike.  I got it all installed properly, the games updated and ready to play.  But when I launch the CS window, the screen goes all weird colours and I get booted out to the login screen.  After I log in, nothing is open or running.  Can someone please help me?

---

### Post by frodon on 2007-07-26
Could you give more details, i'm not sure to understand what step fail reading your post.. You have no problem to run steam right ?

---

### Post by nu buntu on 2007-07-26
No, I have no problem running steam.  I click launch game, and it says preparing to play cs...  After that, I see the cs window opening, but right then, it logs me out, so I have to log back in.

---

### Post by frodon on 2007-07-26
Ok, first check that you have installed the drivers for your graphic card, use the restricted driver manager if needed.

Check also that you have direct rendering enabled, run this command in a terminal to know :
```
glxinfo |grep render
```You should see "direct rendering: yes" if enabled.

Then use wincfg tool and check that you have set your display options like in the screenshot below :
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=22959&d=1168764525[/IMG]

---

### Post by nu buntu on 2007-07-26
Ok, I typed the thing in to my terminal, and this is what I got.

```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
```

Also, where can I find out if I have the drivers installed and if I don't where to go to get them/how to install?

Also, where can I get the winecfg tool or is there a command I have to type to use it?

---

### Post by frodon on 2007-07-26
My guess is that you don't have your graphic drivers installed.

The easiest way is to use the restricted driver manager :
[IMG]http://www.michaellarabel.com/external/restricted-0.jpg[/IMG]

then :
[IMG]http://www.michaellarabel.com/external/restricted-1.jpg[/IMG]

Then click depending of the graphic card you have.

---

### Post by nu buntu on 2007-07-26
I do not have that option under administration on my computer.  I am using Ubuntu 6.10, would that make a difference at all?

EDIT: nvm, I'm updating to Ubuntu 7.04 now.

EDIT2: Alright, I tried to use the distribution upgrade thing, it gets stuck on file 36 and it just sits there and does nothing.  What should I do?

---

### Post by frodon on 2007-07-26
> **nu buntu said:**
> I do not have that option under administration on my computer.  I am using Ubuntu 6.10, would that make a difference at all?

EDIT: nvm, I'm updating to Ubuntu 7.04 now.Yes it makes difference because this tool is only available since feist fawn 7.04. Keep us up to date if you have problems we will try to help you.

---

### Post by nu buntu on 2007-07-26
Good news, I updated to 7.04, turned on my graphics card driver, and I can now use counter-strike.  Thanks for all your help :)

---

### Post by frodon on 2007-07-27
Glad that it works now, all you need now is training :)

---

