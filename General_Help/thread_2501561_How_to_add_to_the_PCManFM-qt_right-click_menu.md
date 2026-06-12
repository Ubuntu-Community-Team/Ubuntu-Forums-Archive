---
title: "How to add to the PCManFM-qt right-click menu?"
date: 2024-10-12
forum: General Help
---

### Post by goemonburo on 2024-10-12
I am trying to add a script to my file manager (PCManFM-qt, I believe.  I am running Lubuntu 22.04LTS) and I did this before several years ago and this successfully carried over from the upgrade.  But I believe at the time I used a tool to manage this and it seems that tool has been discontinued. 

My question is what are the actual scripts and config files required to do this via the CLI?  It seems there MUST be a file, somewhere, that has my earlier edits buried in it and those work great, if I could find that file I could perhaps add the new line item to it?

I did a bit of hunting and used ChatGPT which kindly set me up with the item in the Taskbar's left-click menu, where all the applications are.  But what I want is to right click on a jpg and have it run a shell script I've written, operating on that file and saving it in a sub-directory.

Can anyone direct me to the right files to edit to make this work?  I have created a .desktop file for it, I have "chmod +x"ed the script.  I just don't know where to edit the PCManFM-qt.  (All of this is conjecture, maybe I'm totally barking up the wrong tree?)

Thank you in advance for any help.

---

### Post by ne29914 on 2024-10-13
> **goemonburo said:**
> But what I want is to right click on a jpg and have it run a shell script I've written, operating on that file and saving it in a sub-directory.

Sorry, but what has that to do with PCManFM? You might as well say you want the screensaver or the backup system do the job.
I'm at a loss here.

---

### Post by Holger_Gehrke on 2024-10-13
Sounds like you're trying to define a 'Custom Action'. Some nice documentation for those can be found at [https://github.com/lxqt/pcmanfm-qt/wiki/custom_actions](https://github.com/lxqt/pcmanfm-qt/wiki/custom_actions)

Holger

---

### Post by goemonburo on 2024-10-14
> **ne29914 said:**
> Sorry, but what has that to do with PCManFM? You might as well say you want the screensaver or the backup system do the job.
I'm at a loss here.

Well, seeing as it's _literally_and_exactly_ connected to PCManFM-qt, as evidenced by the below helpful reply and by my eventual solution, which both involve adding to the (as the original post states) PCManFM-qt right click menu...I'm kind of baffled as to what's got you "at a loss."  But since you were, does that now clarify?  

(And I'm not sure what the admin policy on belittling replies is, but yours seems to fall into that "troll" category, certainly doesn't offer anything useful to the thread, and just wastes readers' time and mine, so I'm reporting you.)

---

### Post by goemonburo on 2024-10-14
So, I believe I independently solved this without seeing the reply by @Holger_Gehrke which seems to essentially be the same thing.  Since I had already successfully integrated this the way I was wanting years ago (and it was still working), I used grep to search for files in .local that contained the title string of the action...which was sort of unique.  There was only one folder where a .desktop with that string resided:

    ~/.local/share/filemanager/actions

And that's the key.  You add a .desktop item here, in my case, it was just:

[Desktop Entry]
Type=Action
ToolbarLabel[en_US]=My ScriptName
ToolbarLabel[en]=My ScriptName
ToolbarLabel[C]=My ScriptName
Name[en_US]=My ScriptName
Name[en]=My ScriptName
Name[C]=My ScriptName
Profiles=profile-zero;

[X-Action-Profile profile-zero]
Exec=/my/home/directory/myscript.sh %F
Name[en_US]=My ScriptName
Name[en]=My ScriptName
Name[C]=My ScriptName

It shows up now perfectly, runs the script I want to run on any selected files, and I couldn't be happier.  Most of the other instructions I read were about .desktop files that related to the "Open With" menu, which was not what I was hoping to do.

---

### Post by goemonburo on 2024-10-14
Thank you so much, @Holger_Gehrke, as it turns out, I independently figured this out but had I not, your post would have been the solution I'd been sure was out there somewhere.  It's exactly what I did:  Make a custom action, and it's working great.  Thank you for sparing the time and sharing your expertise!

---

