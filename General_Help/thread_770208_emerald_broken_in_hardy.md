---
title: "emerald broken in hardy??"
date: 2008-04-27
forum: General Help
---

### Post by jimmy the saint on 2008-04-27
I just installed the emerald theme manager on my new Hardy install and there are no themes!!  There is no repository tab (I believe there usually is) which means that I can't direct the program to the right place.  

Anyone else notice this?  I saw a bug report about it, but I don't know if everyone is having this issue or just some of us.  Has anyone found a workaround?

j

---

### Post by quanumphaze on 2008-04-27
I couldn't get Emerald repositories working in Gutsy as well as Hardy.

The only way to get around this (that I know if) is to download the themes manualy.

You can try to compile from source if you are feeling game and it should work, but I would advise against this if it works good as it is.

---

### Post by diplomat.x on 2008-04-27
I have even downloaded the themes manually but it still doesnt work even after restarting the system. 

The emerald theme pack [http://packages.ubuntu.com/feisty/emerald-themes](http://packages.ubuntu.com/feisty/emerald-themes)

---

### Post by quanumphaze on 2008-04-27
is emerald actually running?

If not:
Press alt+F2 and type```
emerald --replace
```
If this gets it running then you have to add emerald --replace into the Window Decoration plugin for compiz.
Don't do this in a terminal otherwise when you close the terminal session you will lose window decorations (even if you use & at the end to make it run in background, it's still tied to the terminal session).

If so you have to import the themes manually by clicking import in emerald manager and finding the theme file.

---

### Post by diplomat.x on 2008-04-28
Thanks a lawt quanumphaze.

---

### Post by quanumphaze on 2008-04-28
No problem.

Be sure to mark your thread as solved, if/when that feature is re enabled in the new forum software. I think only a mod or the thread starter can do it.

---

### Post by diplomat.x on 2008-04-28
> **quanumphaze said:**
> 
Be sure to mark your thread as solved, if/when that feature is re enabled in the new forum software. I think only a mod or the thread starter can do it.

Not my thread :popcorn:

---

### Post by jimmy the saint on 2008-04-29
Applying the theme is not the problem.  The problem is that the application is not connecting to the theme repositories to download them like it is supposed to.  There is supposed to be a repository tab.  I came accross a bug report that mentioned the line that activates the tab is commented out in the source code.  I have not yet compiled any software from source, but I may give it a shot if that is all that is wrong.  I am wondering if anyone else noticed this or can give me instructions (for a comletely inexperienced user) to compile this from source so that I can activate the tab.
Alternately, does anyone know how to assign the appropriate repo (this is in Emerald NOT synaptic) via CLI?

Thanks

---

### Post by Zorael on 2008-04-29
Using the git install script that's someplace in the first couple of pages in the Desktop Effects and Customization forum, I get a fresh Emerald build with no such tab.

---

### Post by jimmy the saint on 2008-04-29
so it isnt just me.  there is a bug report about this on launchpad and the guy successfully fixed the issue by uncommenting the line in the source code, thereby enabling the repository tab.  I am having trouble compiling with this.  When I figure it out, I will post a solution.

---

### Post by park8b156 on 2008-05-03
So is there any word as far as a fix for this/update/it just works im holding out showing people 8.04 at work for this one thing any help out there?

---

### Post by Zorael on 2008-05-03
Doesn't it work if you download the Feisty theme package? At least that's a workaround. Then you can grab themes from gnome-look.org, kde-look.org and beryl-themes.org.

---

### Post by bouss on 2008-05-03
Tottaly noobish question... but in 7.10 I used emerald and had a theme on my pc. Now I installed emerald, imported the theme but it seems that I can t find the OK -or whatever else- button that confirms the use of the theme.

Doh...never mind... solution was 5 posts above :)

---

### Post by park8b156 on 2008-05-03
OK I installed the fitsy themes. Still didn't work. BUT the themes did show as selectable in emerald. The messing around begin. Then I installed Compiz Icon. Right click compiz Icon on the panel and got to select window manager.  Select compiz, then Right click it again then go to select window .manager and click Emerald. Now for me It worked right away.  If you want more themes then go here. "http://themes.beryl-project.org/" and select a category. So if it works for you spread the word and marked as fixed in the original post.


P.S. I don't see it as necessary to have a repo tab with all the above said but it would be nice.

---

### Post by park8b156 on 2008-05-03
Oh, Ya your downloaded themes should go to Places>File System>tmp

---

### Post by can8dnSix on 2008-05-03
sudo apt-get install compizconfig-settings-manager
sudo apt-get install emerald

Open Advanced Desktop Effects Settings, Check Windows Decorations, in command change entry to "emerald --replace"

Open Emerald Theme Manager; choose your theme (import others) and modify as you'd like. Restart the Desktop; or the computer, whatever you choose. Should be able to just CTRL+ALT+BACKSPACE (make sure you save anything you want to save). Also, I found that gDesklets are pretty slick to use with the modified desktop. Also, te Compiz Fusion Icon is not to bad but does not always work in my experience.

---

### Post by park8b156 on 2008-05-03
With what I just posted you don't have to restart or reset x windows it just works atleast for me and I have like a hundred themes I can load

---

### Post by jimmy the saint on 2008-05-09
Emerald works just fine as far as setting the themes.  I just wish I knew how to compile it from source and build a deb package.  The line for the repo tab is commented out in the ubuntu deb build for some reason.  Someone wrote at launchpad that uncommenting this line and rebuilding the package brings the tab back and gives you access to all of the themes in the repositories without having to download and activate them.  They are all just there to be selected.  There is a lot more available that way than in the fiesty package, and you only need to store the ones you want locally.  much nicer setup that way.  Unfortunate really.

---

