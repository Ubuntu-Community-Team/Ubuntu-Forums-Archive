---
title: "New to Ubuntu, computer illiterate--Error Message"
date: 2017-04-30
forum: General Help
---

### Post by vineyridge on 2017-04-30
> An error occurred.  Please run Package Manager from the right click menu or get in the terminal to see what is wrong.  The error message was: "Error:  Broken count >0".  This usually means that your installed packages have unmet dependencies

I am not a computer person.  I don't know what dependencies are.  I don't know what Counts are or how they could be broken.  I can't even figure out what right click menu they are talking about to pull up the Package Manager, and I certainly wouldn't know how to fix it with the terminal.  

I CAN learn.

Could someone please walk me through this and tell me in easily understood steps how to find and correct this error?

---

### Post by Frogs Hair on 2017-04-30
Start by running the software updater and report any errors.

---

### Post by Adam_GUI on 2017-04-30
A dependency is a package that another package needs to function.

Your system is telling you that you have a held broken package and that the most likely culprit is that a dependency package was not installed.

Ubuntu is normally good about installing dependencies.  But, sometimes stuff happens.

I assume you're running default Ubuntu 16.04?

I'm currently installing into a virtual machine to try and get on the same page.  I run XUbuntu, and a few of the packages are different.

Have you opened your package manager?  It should also give you an error message.

---

### Post by vineyridge on 2017-05-01
Thank you both.  I ran the software updater, and when I tried to install the updates, update-manager crashed.  

I followed instructions, went to the terminal, and ran apt-get install -f.  Followed its instructions as well.  The error notification is now gone.

This is the first time in probably 20 years that I've really used a non-graphical interface.  One forgets a good bit at 70, but I managed to work through it.

As long as I'm here, do I want Synaptic?  If I do, how do I find it to install?  I'm assuming .png files are installation files in Linux, but the only Synaptic file that came with my download is synaptic_synaptic.  Is that it?  Is it better to install things through apt-get?

Where can I find my Package Manager?

---

### Post by howefield on 2017-05-01
> **vineyridge said:**
> As long as I'm here, do I want Synaptic?  If I do, how do I find it to install?

You don't mention which operating system that you are using, assuming vanilla Ubuntu with the Unity desktop environment you should have the Ubuntu Software application pinned to the launcher. That will allow you to manage your software installations and removal. So you do not need Synaptic Package Manager however if you want it, install via Ubuntu Software.

> I'm assuming .png files are installation files in Linux, but the only Synaptic file that came with my download is synaptic_synaptic.  Is that it?  Is it better to install things through apt-get?

.png files are normally image files (pictures). I'd suggest it is better to install via the terminal with apt-get only for the reason that you get feedback, eg, it is easy to see exactly which packages are being installed or removed and if there is an error you are likely to get a better clue than you would with Ubuntu Software or Synaptic. 

> Where can I find my Package Manager?

As above, pinned to the launcher or search the dash for Ubuntu Software.. after a few letters being typed the Ubuntu Software icon should be visible for selection. If you are using a different operating system to Ubuntu or one of the Ubuntu variants (flavours) please post.

---

### Post by Adam_GUI on 2017-05-01
I've found synaptic to be invaluable and have continued its use past the Ubuntu Software Manager taking default.
It could have shown exactly which package was considered broken, too.

[ATTACH=CONFIG]274891[/ATTACH]

---

### Post by vineyridge on 2017-05-01
I can't seem to find anything in this operating system.  I typed in package manager in the bar that is supposed to search the computer, and nothing came up.  I got archive manager and something that couldn't possibly be it.  I typed in synaptic and got a square with PNG, and a file named synaptic_synaptic.png.  What good is an image file going to do me?  

What is the Ubuntu equivalent of Windows Explorer that will give me a look at everything, including hidden files, that are on the computer?  I may not want to use everything that is on the computer, but I do want to see it.   I just searched for file manager in the search this computer button, and all the files that show up are squares with PNG, and all the file extensions for the various file managers that appear are .png.

  I suppose I could go to the terminal and ask for a list of root,and then go to each directory and list it, etc., etc.,; but that is very slow, painstaking and repetitive.  There never was the equivalent of a back button on DOS;  is there one in linux/Ubuntu terminal language?

Yes, I'm plain vanilla Ubuntu, and there is a very steep learning curve.

---

### Post by Frogs Hair on 2017-05-01
The synaptic package manager needs to be installed . What happened with the software updater ?

---

### Post by vineyridge on 2017-05-01
> **Frogs Hair said:**
> The synaptic package manager needs to be installed . What happened with the software updater ?

Damned if I know.  It downloaded a while, then when I tried to install the downloads, I got a crash of updater-manager with a hugely long details file.  The computer sent me to the terminal to use apt-get install with a particular parameter that I have forgotten.  I used the terminal, everything went through, and the error message disappeared and has not returned.

If you'd like to see the details of the crash, I took a screenshot which can only be posted through post bin.  I have a link to post bin in my email.

---

### Post by Frogs Hair on 2017-05-01
You can also copy and paste the output here. Use ctrl +alt +t to open the terminal , next , after closing the software updater copy and paste the command below and post the output here. 

```
sudo dpkg --configure -a 
```

---

