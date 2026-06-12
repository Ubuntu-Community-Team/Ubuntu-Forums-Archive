---
title: "sudoedit - how to use it correctly? (19.04)"
date: 2019-06-20
forum: General Help
---

### Post by GhX6GZMB on 2019-06-20
Newbie: How to edit system files in a smart way?

I have a wonderfully running Lubuntu 19.04 installation and am very happy :)

But editing system files is a problem. After issues with gedit and dissatisfaction with nano, I'd like to use a different editor.

My dream setup would simply be "sudoedit <file-name>" from a terminal window. Unfortunately, this brings up "nano", which is the worst editor I've ever seen.

Examining both ~/.bashrc and /etc/environment brings me no joy in setting a permanent environment variable for EDITOR=/bin/<my_favorite_editor>.

Q: which files does Lubuntu 19.04 use for this kind of configuration, and how should they be modified? I've spent hours searching the Web, but earlier versions apparently use a completely different structure.

Thank You.

---

### Post by gsahli on 2019-06-20
I think what you mean is this link: /etc/alternatives/editor -> /bin/nano
Change the link to change the default. Which editor do you prefer?

---

### Post by him610 on 2019-06-20
Try using vi or emacs. Lots of folks swear by those.

---

### Post by HermanAB on 2019-06-21
Bah... Ed is the official UNIX editor.

However, in a pinch, I must confess that I use nano, which has a friendly line of help with the most useful key strokes right at the bottom of the screen.

---

### Post by kpatz on 2019-06-21
I use vi myself (vim) but then I'm a unix guy from way back.  There's a definite learning curve for that one.  Nano or Emacs is friendlier for sure.  Once you memorize the ctrl keys using them is a piece of cake.

---

### Post by TheFu on 2019-06-21
EDITOR=/bin/<my_favorite_editor>.
probably isn't correct if you seek a "pretty" editor.  Most pretty editors would be installed into /usr/bin/.  If you trust your PATH, then you don't need to spell out the specific path to the editor you want.

Also, you want to export the variable. If you don't do that, then it isn't used by subprocesses.
What you probably want to add to your ~/.bashrc is:
```
export EDITOR=gedit
```

Personally, I'm a vim user, but for someone really new to Unix/Linux, that would be too hard.  Vim is an amazing tool in the hands of an expert, but if you want an editor more like Notepad++, then gedit or geany or atom are likely what you seek.  Try those three, see which you like.

But be aware that on Unix servers there isn't any GUI and the only editor likely to be found will be vim. This applies to almost all routers too - the only editor will be vim.

---

### Post by GhX6GZMB on 2019-06-21
Again, Thank You all.

You're obviously all experienced *nix people with deep insights.

I'm just a normal user needing text editor, spreadsheet, presentations (LibreOffice) etc. for daily use and have no ambitions to delve into the depths of the Linux/Lubuntu OS.
That being said, I'm an engineer (electronics design) and like to know what's going on.

My need for editing system files might arise every 6 months, which is why ed, vi, nano, emacs etc. are no option. I'd have to endure the learning curve every time. This is why I'm looking for a GUI editor.
Gedit works well, the other option is FeatherPad, which is native Lubuntu 19.04 and simple enough for my needs.

I'll try checking the /etc/alternatives/editor directory and see what I find out.

Thanks.

---

### Post by kpatz on 2019-06-21
Use vi or nano for everyday editing of text files (say, if you're creating scripts or programs for your own use) and you'll get used to them in no time.

---

### Post by GhX6GZMB on 2019-06-21
> **kpatz said:**
> Use vi or nano for everyday editing of text files (say, if you're creating scripts or programs for your own use) and you'll get used to them in no time.

Thanks, but that's exactly my point: I've no use for simple text editors in my daily life. I should have written "document editor" instead of text editor.

UPDATE: added the following lines to [B]~/.profile
[/B]
EDITOR="/bin/featherpad"
export EDITOR

Works wonderfully now, using the sudoedit <SYSTEM_FILE> command from the terminal, FeatherPad comes up with a system file for editing.

---

### Post by deadflowr on 2019-06-21
You can edit system files from the file manager by using the open as root function.
It's up in the Tools menu item.
It'll prompt for the admin user password then open a new file manager window as root.
Then just double click on the file you want to edit and it'll open it and allow you to edit and save as root.

Lubuntu 19.04 comes with the needed packages to do this out of the box.

Edit: You might want to right click on the file before hand and check the properties settings so it's set to open the correct (preferred) editor.

---

### Post by GhX6GZMB on 2019-06-21
@deadflowr: very interesting.

I tried it out, and it works as a 100% GUI solution, where an editor can be selected by right clicking on the file. I'll keep this in mind, Thank You.

I now have **two** solutions for GUI editing system files. Brilliant!

---

### Post by GhX6GZMB on 2019-06-21
Double post, sorry!

---

