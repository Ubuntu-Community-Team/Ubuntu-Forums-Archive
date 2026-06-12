---
title: "make &quot;Prnt Scrn&quot; key take screenshot without opening ScreenGrab?"
date: 2020-04-29
forum: General Help
---

### Post by anotherChris on 2020-04-29
I recently upgraded to Lubuntu 20.04.  Before that, I had Lubuntu 17.10, and before that 15.x, and some older versions.  

In versions before 20.04, pressing the Print Screen key on the keyboard would take a screen shot and automatically add it to my directory without doing anything else. 

Now, when I press Print Screen, it opens the ScreenGrab program, which is just so annoying.  Having ScreenGrab available from the Application Menu is great, but I want the Print Screen key to act like it did in older versions and just take a screenshot in the background without doing anything else.

Sorry, I am too ignorant of Linux to have any idea how to modify the Print Screen key's function, but I suspect what I want to do can be done.

---

### Post by guiverc on 2020-04-29
Did you re-install? or how did you move from 17.10 to 20.04??

Because Lubuntu switched from LXDE to LXQt, numerous problems are to be expected unless you re-installed. Given the number of posts you've made on discourse.lubuntu.me & here recently, I'm suspicious you didn't re-install.

Anyway print-screen should work, or I'd suggest you refer to the Lubuntu manual

[https://manual.lubuntu.me/stable/2/2.3/2.3.2/screengrab.html](https://manual.lubuntu.me/stable/2/2.3/2.3.2/screengrab.html)

At times I've often opted to start it from terminal, even sometimes using the older `lximage-qt` because it did have some features I found very handy.

---

### Post by anotherChris on 2020-04-29
> **guiverc said:**
> Given the number of posts you've made on  discourse.lubuntu.me & here recently, I'm suspicious you didn't  re-install.

No, I completely re-installed.    If you read the other posts I made here and at the Lubuntu discourse, it's obvious I completely re-installed.

> **guiverc said:**
> Anyway print-screen should work...

I think maybe my original post in this thread was not clear.  My Print Screen key works just fine.  It's just that in 17.10, it worked in the background.  If you hit Print Screen, it *looked like* nothing happened, but if you checked your home directory, there was a screen shot PNG in there for every time you hit Print Screen key.  It was very nice because it didn't interrupt your work flow.

But in 20.04, the Print Screen key doesn't work in the background, it opens the ScreenGrab program everytime you hit Print Screen, which means you have to go through the process of closing ScreenGrab every time you take a screen shot.  I find that annoying and would like the Print Screen key to work as it did in LXDE.  I suspect if I were competent at terminal and programming, I would know how to do that, but I don't.  So, I'm hoping somebody can tell me the commands to make that happen...

---

### Post by guiverc on 2020-04-29
Yeah I missed some information (I tend to read each thread by itself)

Lubuntu 18.04 LTS used `scrot` as its capture program ([https://packages.ubuntu.com/bionic/lubuntu-desktop](https://packages.ubuntu.com/bionic/lubuntu-desktop)) which has changed twice since then.

You could change the default I suppose, but I have not tried or done it for that program. The manual for making that change can be found at 

[https://manual.lubuntu.me/stable/3/3.2/3.2.17/alternative_configurator.html](https://manual.lubuntu.me/stable/3/3.2/3.2.17/alternative_configurator.html)

I had a quick look at scrot ([https://packages.ubuntu.com/focal/scrot](https://packages.ubuntu.com/focal/scrot)) and it didn't look that heavy (the main changes were made to keep Lubuntu light** given the software stack has now changed).

Having had a quick look, yes the `screengrab` window did appear whenever I used it, which didn't worry me as it always opened on my second screen away from where I was looking, but I don't use it often.

If you have issues with what I've provided, or don't get the response you want, leave a note here or discourse.lubuntu.me & I'll respond when I'm able.

** light within limits anyway

---

### Post by anotherChris on 2020-04-29
Thanks.  Since I am basically a Linux-non-user-level skill, I will have to research the links you provided and try later.

---

### Post by Dennis N on 2020-04-29
Change the keyboard shortcut for Print Screen Key:

Preferences > LXQt Settings > Shortcut Keys
Look for 'Print' in Shortcut Column and select it.
Press 'Modify' key.
Change command to 'scrot'
Click OK
Screenshots are saved in home folder.

See attached screenshot.

(Note: This works in my Lubuntu 19.10 - not yet upgraded to 20.04)

---

### Post by GhX6GZMB on 2020-04-29
It's a bit more involved than that. Please see this thread in the "Tutorials" section:

[https://ubuntuforums.org/showthread.php?t=2433158](https://ubuntuforums.org/showthread.php?t=2433158)

Works perfectly.

---

### Post by Dennis N on 2020-04-29
> **ml9104 said:**
> It's a bit more involved than that. Please see this thread in the "Tutorials" section:

[https://ubuntuforums.org/showthread.php?t=2433158](https://ubuntuforums.org/showthread.php?t=2433158)

Works perfectly.
Well, the question was to use Print-Screen to take a screenshot in the background and add it to his [home] directory without doing anything else, like it worked in older Lubuntu versions. Your linked thread adds more functionality.

From post #3:
> If you hit Print Screen, it looked like nothing happened, but if you checked your home directory, there was a screen shot PNG in there for every time you hit Print Screen key. It was very nice because it didn't interrupt your work flow.


What I suggested  in post #6 does exactly that.

---

### Post by GhX6GZMB on 2020-04-29
> Well, the question was to use Print-Screen to take a screenshot in the background and add it to his [home] directory without doing anything else, like it worked in older Lubuntu versions. Your linked thread adds more functionality.



True.
The problem with scrot alone is, that it does not drop the screenshot in the [home] directory, but in the current directory, which can be anywhere. And current directory does not mean that scrot has write permissions. Whether you have a screenshot or not is an open question.

---

### Post by Dennis N on 2020-04-29
> **ml9104 said:**
> True.
The problem with scrot alone is, that it does not drop the screenshot in the [home] directory, but in the current directory, which can be anywhere. And current directory does not mean that scrot has write permissions. Whether you have a screenshot or not is an open question.

I tried this out in Lubuntu 19.10, and regardless of the file manager's current directory, a scrot screenshot was always saved to my home folder (~/).

**Exception**:
If I issue the scrot command from the terminal prompt, the screenshot is saved to the terminal's current directory (if permitted). Is this what you mean by 'scrot alone'?

But, since the premise of the question is to use the Print Screen button, those screenshots always goes to the home folder.

---

### Post by anotherChris on 2020-04-29
> **ml9104 said:**
> The problem with scrot alone is, that it does not drop the screenshot in the [home] directory, but in the current directory, which can be anywhere. And current directory does not mean that scrot has write permissions. Whether you have a screenshot or not is an open question.

I don't know about LXQt, but previously the screenshots were written to the home directory unless you changed it to the pictures directory, where they logically should have been written to...
[https://ubuntuforums.org/showthread.php?t=2311918](https://ubuntuforums.org/showthread.php?t=2311918)

---

### Post by Dennis N on 2020-04-29
> **anotherChris said:**
> I don't know about LXQt, but previously the screenshots were written to the home directory unless you changed it to the pictures directory, where they logically should have been written to...
[https://ubuntuforums.org/showthread.php?t=2311918](https://ubuntuforums.org/showthread.php?t=2311918)

I checked this with Lubuntu 19.10 (LXQt desktop). If you set it up as in post #6, and you use the Print Screen button to take a screenshot, the screenshot is always automatically saved to the home folder (~/).

Maybe you can add an option to the scrot command in the keyboard shortcut (post #6) to change the destination, but I've not looked into that. If you do, please post your modification.

---

### Post by Dennis N on 2020-04-29
> Maybe you can add an option to the scrot command in the keyboard shortcut (post #6) to change the destination
Using information on the scrot man page, we can modify the command in post #6 to save all screenshots to ~/Pictures. See attachment.

---

### Post by GhX6GZMB on 2020-04-30
> **Dennis N said:**
> Using information on the scrot man page, we can modify the command in post #6 to save all screenshots to ~/Pictures. See attachment.

I strongly doubt that your suggestion will work. There is a reason "man scrot" lists this example:

```
[COLOR=#111111][FONT=monospace]scrot '%Y-%m-%d_$wx$h.png' -e 'mv $f [/FONT][/COLOR][~/shots/]("file://%7E/shots/")[COLOR=#111111][FONT=monospace]'[/FONT][/COLOR]
```
I'd suggest:

```
[COLOR=#111111][FONT=monospace]scrot '%Y-%m-%d-%T.png' -e 'mv $f /home/"username"[/FONT][/COLOR][/Pictures/]("file://%7E/shots/")[COLOR=#111111][FONT=monospace]'[/FONT][/COLOR]
```
instead.

The issue is, that if the screenshot file name is not unique, you will only be able to take one shot, then the file name already exists, and the next shot won't work.
Also, if you do a logout - login to a different user, access rights will block writing the file.

Last, but one: using ~/ in commands is a very bad idea. Only the shell expands ~/, other commands don't. Use the full path, perhaps using the $USER environment variable to generate the path.

And finally: why anyone would want to build a repository of screenshots is a mystery to me. But OK, I'm flexible :)

---

### Post by Dennis N on 2020-04-30
> The issue is, that if the screenshot file name is not unique, you will only be able to take one shot, then the file name already exists, and the next shot won't work.
They are unique because the name contains a time stamp. Here are screenshots just taken today (30 Apr) as a test:
```
dmn@Tyana-vm:~/Pictures$ ls  -1 | grep -i 2020-04-30
2020-04-30-115246_1920x1080_scrot.png
2020-04-30-115702_1920x1080_scrot.png
2020-04-30-115851_1920x1080_scrot.png

```
And they are in the Pictures folder. 115246 means it was taken 11:52:46 AM MST.

I wouldn't have posted that command unless I had tested it first.

---

### Post by GhX6GZMB on 2020-04-30
> **Dennis N said:**
> They are unique because the name contains a time stamp. Here are screenshots just taken today (30 Apr) as a test:
```
dmn@Tyana-vm:~/Pictures$ ls  -1 | grep -i 2020-04-30
2020-04-30-115246_1920x1080_scrot.png
2020-04-30-115702_1920x1080_scrot.png
2020-04-30-115851_1920x1080_scrot.png

```
And they are in the Pictures folder. 115246 means it was taken 11:52:46 AM MST.

I wouldn't have posted that command unless I had tested it first.

Thanks for the example. Perhaps I've been too finicky in my approach to scrot.
My need for screenshots is different, though, I just need the copy - paste functionality.

Cheers.

---

### Post by GhX6GZMB on 2020-04-30
One final comment:

change ~/Pictures to $HOME/Pictures. ~ depends on a shell, $HOME always works.

Cheers.

---

