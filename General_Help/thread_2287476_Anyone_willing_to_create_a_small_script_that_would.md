---
title: "Anyone willing to create a small script that would solve a known issue for 14.04?"
date: 2015-07-19
forum: General Help
---

### Post by jake69 on 2015-07-19
If only there were a small bash script - that only ran when a new kernel was about to be installed - and it deleted all except the new kernel that get's installed and the one prior to it (leaving a grand total of 2 kernels at any time). It would have to run after the new kernel was completely installed though.

If someone were to create this script, and tell the user where to put it/ how to use it - it would solve the low disk space issue that came with the default efi install of ubuntu 14.04. It could be run as a cron job that runs only when and after a new kernel is installed. Perhaps something to do with running sudo apt-get autoremove (at the proper time). The end result, once it had been used the first time, might be something like this ...

On the first run of the script, suppose you had the following kernel names where they are stored ...

kernel-1
kernel-2
kernel-3

Where kernel-1 is the oldest kernel and kernel-3 is the newest kernel.

Now the user runs sudo apt-get upgrade (after update of course); and, it just happens to be that a new kernel is slated for installation. The the entire upgrade proceeds normally (including the new kernel) until it is finished. Then the script runs (because something has detected that a new kernel was just installed). The scrupt then leaves the directory containing kernels in the following state ...

kernel-3
kernel-4

Where, in this new state, kernel 3 is the older and kernel-4 is the newer.

Now the script has been run for the very first time on that user's system.

Now, at some later date, the user performs a sudo apt-get upgrade again. Again, a new kernel is slated for installation. Again the script runs after the upgrade is complete. After the script has run we see the following in the directory containing kernels ...

kernel-4
kernel-5

And so on into the foreseeable future.

I don't know bash scripting or I would do it and put it out there for everyone, and I don't have time to embark on a journey to learn it.

Any takers?

---

### Post by v3.xx on 2015-07-20
Kinda like this?

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by monkeybrain20122 on 2015-07-20
> **v3.xx said:**
> Kinda like this?

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Well actually "sudo apt-get autoremove" would do it if you want to keep two kernels.

---

### Post by vasa1 on 2015-07-20
> **monkeybrain20122 said:**
> Well actually "sudo apt-get autoremove" would do it if you want to keep two kernels.
That's what I rely on.

```
11:53 AM ~ $ dpkg --list | grep "ii  linux-image"
ii  linux-image-3.13.0-39-generic                     3.13.0-39.66                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                     3.13.0-55.94                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                     3.13.0-57.95                            amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic               3.13.0-39.66                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic               3.13.0-55.94                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic               3.13.0-57.95                            amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                               3.13.0.57.64                            amd64        Generic Linux kernel image
11:54 AM ~ $ 

```
Though I suspect there's a time-lag before only two kernels remain. I feel the third kernel isn't removed immediately but after a few days. That's not a problem for me. I wouldn't use any exogenous script.

Edit: From the top of /etc/kernel/postinst.d/apt-auto-removal
```
#!/bin/sh
set -e

# Author: Steve Langasek <steve.langasek@canonical.com>
#
# Mark as not-for-autoremoval those kernel packages that are:
#  - the currently booted version
#  - the kernel version we've been called for
#  - the latest kernel version (determined using rules copied from the grub
#    package for deciding which kernel to boot)
#  - the second-latest kernel version, if the booted kernel version is
#    already the latest and this script is called for that same version,
#    to ensure a fallback remains available in the event the newly-installed
#    kernel at this ABI fails to boot
# In the common case, this results in exactly two kernels saved, [B]but it can
# result in three kernels being saved.  It's better to err on the side of
# saving too many kernels than saving too few[/B].
```

---

### Post by jake69 on 2015-07-20
> **v3.xx said:**
> Kinda like this?

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I suppose the person at that link has the right idea in mind, but the logic behind it seems a little overly complicated to me.

> 
[COLOR=#000000]Well actually "sudo apt-get autoremove" would do it if you want to keep two kernels.[/COLOR]


Hadn't heard about using only [COLOR=#000000] "sudo apt-get autoremove"  by itself (if I'm understanding you correctly).

What I did last night to manually remove old kernels involved just two commands ...

[/COLOR]```
dpkg -l | grep linux-image-
```[COLOR=#000000]

The above command listed all kernels for me (and only kernels). At the time I ran it, there were only installed kernels present but that command will, ultimately, list both installed and not installed kernels.

I suppose that command could be tweaked to only print installed kernels. Or, in other words - exclude kernels that aren't installed (ie: negation)

Then I was able to do ...

[/COLOR]```
sudo apt-get autoremove linux-image-3.13.0-46-generic
```[COLOR=#000000]

The above command is a specific example showing a specific kernel I removed with the command. The gist is to include the full kernel name (with version number and all).

I issued the autoremove command, in my case last night, 3 times - once for each of the 3 old kernels I wanted to remove.

This sounds like a loop to me.

if the dpkg command were used to generate a list of all kernels. Then remove kernels from the list that aren't installed, then remove the last two kernels (ie: the two newest kernels) from the list - there you would have the proper list of kernels to be removed - 3 steps total.

Then that list is passed into a loop block where the the stopping point is a variable and that variable has the number of items in the list loaded into it. Inside the code block, each of the list items is passed into the autoremove command and a variable is used to store the list item. When the number of items is reached (as stored in the stopping point var for the loop, the code exits the block and you are done.

But the caveot is that it be run after the new kernel is installed and not before or it wouldn't work right.

That's my best guess on the code logic.

Psuedo code might look like this ...

```

// generate the entire kernel list using : dpkg -l | grep linux-image-
// remove kernels from the list that aren't installed
// remove the current and next to current kernels (the last two)
// count the number of items in the list and load that number into a variable (let's name this variable klist for now)
// start your loop - in c++ it might look like this : for(int i=o; i < klist; i++) {
// load each item in the list one by one, starting with the first one, into a variable (lets call this one listitem for now)
// sudo apt-get autoremove listitem
// } // bracket that ends the code block/ loop

```

The above is C++ ish (and I'm sure I'm still butchering it) but it seems to me that would be pretty simple to do with bash for someone who knows bash

---

### Post by jake69 on 2015-07-20
This forum software simply refuses to quit adding code tags to the dpkg command in the code segment at the end. People just have to imagine that the last two code blocks are together in one code segment (that's what was intended).

Oh, and, the use of sudo in a script might cause the user to have to enter their password at an unexpected time (if it even worded at all because of that). I think the better option would be for the script itself to have the perms to run as superuse on it's own. Alternatively, if the password were asked for, a line instructing the user might have to be printed to the screen so they know why and what to do.

---

### Post by jake69 on 2015-07-24
I know there are people around here who are passionate and knowledgeable when it comes to system administration. People who actually like doing this sort of thing. I, unfortunately, am not one of them (and I'm sure I'm not alone). Yeah, the code on tux tweaks (at the link in post #2) is a line of bash code, but it isn't a "script" (as in a file that you download onto your local computer and install somewhere) and I wouldn't know how to turn it into one. Not just that, but a lot of users, not just me, would really have no clue how to turn it into a script **file** - let alone where to **put** the file so it **runs** at the proper time. And, tbh, the program logic in that line of code is really not that great anyway in that it's overly complicated to achieve the result. Over complicated usually introduces the possibility of errors - and we are talking about kernels here - the consequences could be severe.

All I'm saying is this - the hope I had was that someone who actually likes doing this sort of stuff, and for whom the knowledge exists and it would be easy - would create a solution to automate the process, And that such a solution could actually be made accessible to the very least experienced end users. What was hoped is that someone would just make something that **just works** for the average end user. Yeah, I know we're talking about linux here, but ubuntu is popular among an end user crowd these days (some might say rightfully so since that's what's getting linux onto more desktops).

Anyhoo ...

Ubuntu doesn't seem to be doing anything about it (and it's been a bug for a long time ~ since 10.04 was released). It wasn't any of the users fault, it was a flaw in the original code - the installer did it to us. Yet we continue to suffer. Am I blaming forum users? Those who might be reading this? No, absolutely not. Am I blaming Ubuntu? Yeah, pretty much. But, at the end of the day, it is what it is. If I had the ability to create a **real** script, post it in a **proper** location where the **file** can be **downloaded**, and post clear **instructions** along with it on **how** to use the script (ie: where to place it and whatever other details may be needed) - I would. But I don't have that ability (nor do I have any desire - I hate that sort of thing with a burning passion - I like to use the system, not fix it). So, until either ubuntu steps up and creates a fix for the problem, or someone with the ability steps up and does it - we go on having the problem.

I'm sure there are many, mature system admins who frequent this forum. People for whom something like this would take 15 or 20 min to complete and post online (if that), and for whom it is a joy to do so. So, where are you?

---

### Post by coffeecat on 2015-07-24
> **jake69]This forum software simply refuses to quit adding code tags to the dpkg command [/quote]

The forum software does not add BBCode tags unless you add them, or unless you have an obscure problem with a browser plugin. The raw text of the particular segment you refer to looks like this, replete with superfluous [noparse][COLOR=#000000][/noparse] tags. 


[quote][noparse]
```

// generate the entire kernel list using : 
```[/COLOR]```
dpkg -l | grep linux-image-
[COLOR=#000000]// remove kernels from the list that aren't installed
// remove the current and next to current kernels (the last two)
// count the number of items in the list and load that number into a variable [/COLOR][COLOR=#000000](let's name this variable klist for now)
[/COLOR][COLOR=#000000]
// start your loop - in c++ it might look like this : for(int i=o said:**
> [COLOR=#000000]klist[/COLOR][COLOR=#000000]; i++) {
// load each item in the list one by one, starting with the first one, into a variable (lets call this one listitem for now)
// sudo apt-get autoremove listitem
// } // bracket that ends the code block/ loop
[/COLOR]
```[COLOR=#000000]
[/noparse]

(The final COLOR tag was closed at the end of the post.)

What with the haphazard addition of multiple pairs of COLOR tags, and the odd placing of the CODE tags, I would guess that you are using WYSIWYG editor mode which makes it very difficult to see what is going on. Why did you add the COLOR tags when the text defaults to #000000 anyway? I suggest you switch to one of the source modes for the message editor. You can do this for an individual post with the toolbar icon that looks something like [size=0]A[/size]/_A_ in the message editor. Or when you have 10 posts, you can choose your default editor mode in your user settings. I gave up using WYSIWYG mode in about 2007.

I've tidied up that bit of the post for you.

---

### Post by vasa1 on 2015-07-24
> **jake69 said:**
> ...

.... What was hoped is that someone would just make something that **just works** for the average end user. ...
Anyhoo ...

Ubuntu doesn't seem to be doing anything about it (and it's been a bug for a long time ~ since 10.04 was released). It wasn't any of the users fault, it was a flaw in the original code - the installer did it to us. Yet we continue to suffer. Am I blaming forum users? Those who might be reading this? No, absolutely not. Am I blaming Ubuntu? Yeah, pretty much. But, at the end of the day, it is what it is. If I had the ability to create a **real** script, post it in a **proper** location where the **file** can be **downloaded**, and post clear **instructions** along with it on **how** to use the script (ie: where to place it and whatever other details may be needed) - I would. ...

What is simpler than sudo apt-get autoremove and leaving the choice up to the user? 

Scripts exist. See **/etc/kernel**. 

And these scripts are developed by "Ubuntu". 

What is specifically wrong with them? You haven't provided details.

They work just fine for me, an average user.

---

### Post by amoun on 2015-07-24
Synaptics > Search for [13.3.0-] then remove all but the latest : Nice to see what is going on

---

### Post by jake69 on 2015-07-28
> **vasa1 said:**
> What is simpler than sudo apt-get autoremove and leaving the choice up to the user? 

Scripts exist. See **/etc/kernel**. 

And these scripts are developed by "Ubuntu". 

What is specifically wrong with them? You haven't provided details.

They work just fine for me, an average user.


I was unaware that any script existed. Personally, I don't want to go in and remove old kernels manually - and have to keep repeating the process. I would prefer to automate this process. Furthermore, I had assumed (apparently I was wrong) that I wouldn't be alone in this preference. Now that I know something exists I may be able to look into using it on my own (I guess I have enough info here to do that now - idk). Thank you so much for pointing out that something exists, what it's called, and where to find it (I assume I have enough information to look into it on my own). This is all I asked for throughout this thread but kept getting a response based on the respondents desires (not mine) - namely, to keep doing the process manually.

At any rate, I'm glad the information came out - sure appreciate it.

---

### Post by jake69 on 2015-07-28
> **vasa1 said:**
> What is simpler than sudo apt-get autoremove and leaving the choice up to the user? 

Scripts exist. See **/etc/kernel**. 

And these scripts are developed by "Ubuntu". 

What is specifically wrong with them? You haven't provided details.

They work just fine for me, an average user.


I wasn't aware there was anything. That's what I've been asking all along. Personally, I don't want to manually remove old kernels and have to keep doing it periodically. I guess I shouldn't have assumed that others would feel the same way about it, or that a way to automate it didn't already exist. Truth is though, I don't know how to make use of those things and that's the other reason I posted here. In hindsight, if I had known better, I would have written my original post like this instead -

I want to automate the removal of old kernels from my system. Can someone instruct me the best way to do this?

Anyway, I do really appreciate the information (I do I do). Thanks to everyone and I'm sorry for the miscommunication.

---

### Post by SeijiSensei on 2015-07-29
Autoremove works fine once you've cleaned out the cruft in /boot.  Otherwise you need to run
```
sudo apt-get remove linux-image-3.xx.xx-xx-generic
```
repeatedly for the kernels you wish to remove.  Leave the current and previous kernels, delete the rest.

---

### Post by jake69 on 2015-08-04
Thanks for all the information everyone. I'm gonna mark this one as solved.

---

