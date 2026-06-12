---
title: "Ubuntu 22.04 upgrade problem - text editors"
date: 2022-08-14
forum: General Help
---

### Post by 700 on 2022-08-14
PROBLEM:
Gedit (version: 41.0) is not opening files in a current workspace.

DESCRIPTION:
Problem started after system upgrade from Ubuntu 20.04 to 22.04.

Another text editor called the "Text Editor" (version: 42.2, proposed for Ubuntu 22.10) is already installed, but:
- it's also not opening in a current workspace
- it doesn't show whitespace characters (like with the "Draw Spaces" plugin in Gedit)
- it looks like it doesn't accept any plugins at all

QUESTION:
How to open files with Gedit in a current workspace?

---

### Post by philhughes on 2022-08-14
Don't know about the workspace stuff, but there is a settings for drawing whitespace that is not currently exposed via the GUI. You need to use gsettings or dconf. Click on the link to gitlab in the link below for the full settings:

[https://blogs.gnome.org/chergert/2021/12/03/text-editor-happenings/](https://blogs.gnome.org/chergert/2021/12/03/text-editor-happenings/)

A lack of support for plugins is true at this time:

[https://discourse.ubuntu.com/t/proposal-gnome-text-editor-as-default-text-editor/28286](https://discourse.ubuntu.com/t/proposal-gnome-text-editor-as-default-text-editor/28286)

The major limitation I have noticed compared to gedit is the lack of a sorting function.

---

### Post by 700 on 2022-08-14
It works - in the Gnome Text Editor just a short command in terminal makes whitespace characters visible:
> gsettings set org.gnome.TextEditor draw-spaces "['tab','space']"
Thank you (the question of workspace separation is still open).

---

### Post by vanadium on 2022-08-15
> **700 said:**
> It works - in the Gnome Text Editor just a short command in terminal makes whitespace characters visible:

Thank you (the question of workspace separation is still open).

You may want to expand a little, because I have no clue about the problem as currently described.

---

### Post by 700 on 2022-08-15
> **vanadium said:**
> You may want to expand a little, because I have no clue about the problem as currently described.
I use multiple workspaces in my Ubuntu. I'd like my default text editor to open text files in a currently open workspace (like it worked before my Ubuntu upgrade). I try different text editors, but all of them open text files in a last open text editor window, instead of a current workspace.

---

### Post by dragonfly41 on 2022-08-15
If you open any file in a text editor, or other apps, right click on its top bar and you can move window to any WorkSpace.
There are other tools for this. I have one - Workspace Switcher - in Docky bar at bottom of my screen.

Or .. search "Ubuntu workspace switcher".

---

### Post by 700 on 2022-08-15
> **dragonfly41 said:**
> If you open any file in a text editor, or other apps, right click on its top bar and you can move window to any WorkSpace.
I know that, but it's not quick and not comfortable solution (it's a downgrade after upgrade).
> **dragonfly41 said:**
> There are other tools for this. I have one - Workspace Switcher - in Docky bar at bottom of my screen.
Or .. search "Ubuntu workspace switcher".
Workspaces are switching fine (I mean also a bit laggy/slower than before the system upgrade), but I have also to search where is requested file open after the double click on my current workspace (because the file doesn't show there, but on some other workspace).

---

### Post by dragonfly41 on 2022-08-15
Alright, then in Ubuntu (I am on 20.04) click on Activities in top left bar and I see my current apps on my main workspace, plus to the right all my other workspaces. Does that help your workflow? Also I suggest installing Docky and then Docklet > Workspace Switcher. You just need to figure out a snappy workflow. There are other ways I have tried.

Added note. I ran through the process of opening a text file on my Workspace 1, setting it to be visible on Workspace 2.
Then when I click on it again it is not seen in my Workspace 1, but I can click on Activities (top bar) to see where it is visible on other Workspace.

---

### Post by 700 on 2022-08-15
> **dragonfly41 said:**
> [...] I see my current apps on my main workspace, plus to the right all my other workspaces. Does that help your workflow? [...] I can click on Activities (top bar) to see where it is visible on other Workspace.[...]
It's slowing the workflow when the current activity is jumping around different workspaces. Searching is unnecessary extra process to do.
I think the idea was to group all open files in one window and in one workspace, but it's not a good idea. It's not helpful, because I open many files at once and I spread them around many workspaces. I don't have a time to search for my files and folders and I don't search them when they open in the current workspace I'm in. When files and folders are in the same workspace (and nothing jumps around), than I know where they are right away (without any extra clicks and searches).
Workspaces worked better before the upgrade and this new idea fixed what wasn't broken (and now it's broken).

---

### Post by Claus7 on 2022-08-15
Hello,

maybe not helpful, yet I used two workspaces under xorg ubuntu 22.04.1. 
i) I opened Files in each one of them and clicked a file in order to open with gedit. It opened in the current workspace I had already selected.
ii) I opened gedit and being in the second workspace, I opened from gedit a file: it opened in the workspace I was.

Regards!

---

### Post by dragonfly41 on 2022-08-16
[COLOR=#000000]> It's not helpful, because I open many files at once and I spread them around many workspaces. I don't have a time to search for my files and folders and I don't search them when they open in the current workspace I'm in. When files and folders are in the same workspace (and nothing jumps around), than I know where they are right away (without any extra clicks and searches).

[/COLOR]For juggling many, many files I would look at Obsidian and consider using markdown (.md) instead of text (.txt). 
You can use Pandoc to convert files.

In Obsidian graph view you see a network (galaxy) of all your files. Obsidian co-works with Zettlr markdown editor.

That is, use Obsidian/Zettlr in concert with Gedit (if you must use Gedit). And all of this workflow I would build into an automation script using other tools (I can expand if required).

---

### Post by vanadium on 2022-08-16
For having gedit open a new window (which then should open in the current workspace) each time instead of opening as a tab in an existing window, you could specify the --new-window option on the command line. Unfortunately, an option to always behave like that is not exposed in the Preferences of the application, but you can edit the launcher for gedit to add this command line option.

---

