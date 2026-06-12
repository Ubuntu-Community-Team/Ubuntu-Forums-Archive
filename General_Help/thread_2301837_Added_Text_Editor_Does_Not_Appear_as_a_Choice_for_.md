---
title: "Added Text Editor Does Not Appear as a Choice for Editing a Text File"
date: 2015-11-05
forum: General Help
---

### Post by oldefoxx on 2015-11-05
Aside from the included gedit and nano text editors, I located and installed three more:  Leafpad, Cream, and GVim.  These were based on an online article of the 15 best text editors for Linux.  I did this because I frequently need to see the guts of more than one text file at once, as a way to simplify cut/copy & paste. and work with an opened terminal at the same time.  One editor only shows one file at a time, though it can be accessing several at once.

Of these choices, cream is by far the best.  But there is a problem with it:  It is the one that does not show up as a choice when you decide to do an Open with... and want an editor besides gedit to be used.  I get the impression that if you select a particular editor often enough, it might become the new default.  But for that to happen, you have to use the selection process.  Right now I have to click on the cream icon, then open the file from there, so there is no way to impress on the selection process that this is the editor I want to default to.

So, problem is, somehow GVim and Leafpad engrained in the selection process that they can be used with the same kind of files that gedit and nano customarily support, but cream did not do that.  How do I get it added to the list?  And do I have any input control over which text editor is the default?

---

### Post by bab1 on 2015-11-05
Cream is not a text editor.  It is a set of plugins for VIM just as Gvim is an enhanced version of VIM.  

Here is how to change to the Cream version of VIM.

[http://tips.webdesign10.com/how-to-change-the-default-text-editor-on-ubuntu-with-nautilus]("http://tips.webdesign10.com/how-to-change-the-default-text-editor-on-ubuntu-with-nautilus")

---

### Post by oldefoxx on 2015-11-05
Thanks for the quick response and the info on Cream.  I followed your lead, and there Cream looks nothing like what I have on my screen, which is a white background.  There it is black, but that is likely handled in user preferences.

I had looked a Vim as a possibility, but the Cream makeover is so much better in my eyes.  The three editors, cream, gedit, and leafpad appear very much alike on the surface, but leafpad does not seem to support highlighting with a mouse, and has a terribly cramped window when it comes to locating folders and files to be loaded or saved.  It would never be my first choice as a consequence.

Your distinction that cream is not a text editor in the true sense has no meaning to me.  It does the job of editing text really well, and that is what counts.  It's like being smart and using Wordpad in place of Notepad in Windows.  A no-brainer after you compare the two.

What you missed from my post is that **cream does not show up as a choice** when you right-click on a text file.  That is what I am trying to get dealt with.  I can't choose it if it is not listed anywhere as a choice to be made.  In Windows, you had an "Other" option, but in Gnome, you don't.  With Other, I could browse or enter a path to the file I wanted to use.  But that is not available to me here.

---

### Post by mc4man on 2015-11-05
In a terminal - 
```
sudo -H gedit /usr/share/applications/cream.desktop
```

Find the Exec= line & add %f to end of line, ie.
```
Exec=cream %f
```
Save & cream will be in the context menu of registered mimetypes.

---

### Post by bab1 on 2015-11-05
> **oldefoxx said:**
> Your distinction that cream is not a text editor in the true sense has no meaning to me.  It does the job of editing text really well, and that is what counts.  It's like being smart and using Wordpad in place of Notepad in Windows.  A no-brainer after you compare the two.

I did not reply solely  for your benefit.   The distinction may indeed be lost on you.  So be it.  Others will read and understand. 
> 
What you missed from my post is that **cream does not show up as a choice** when you right-click on a text file.  That is what I am trying to get dealt with.  I can't choose it if it is not listed anywhere as a choice to be made.  In Windows, you had an "Other" option, but in Gnome, you don't.  With Other, I could browse or enter a path to the file I wanted to use.  But that is not available to me here.
I didn't miss anything.  I gave you an alternative.

[COLOR="#0000FF"]Edit: It appears that the answer has been supplied by @mc4man. [/COLOR]

---

### Post by bab1 on 2015-11-05
> **mc4man said:**
> In a terminal - 
```
sudo -H gedit /usr/share/applications/cream.desktop
```

Find the Exec= line & add %f to end of line, ie.
```
Exec=cream %f
```
Save & cream will be in the context menu of registered mimetypes.
Interesting.  So having a .desktop file at /usr/share/applications is the trigger for the context menu.  Nice.

---

### Post by mc4man on 2015-11-05
> **bab1 said:**
> Interesting.  So having a .desktop file at /usr/share/applications is the trigger for the context menu.  Nice.

cream installs with a .desktop but no maintainer has bothered to notice that in gnome 3.x the Exec= line must end in a % <letter> to be in the file manager's (nautilus) context menu
Applicable  letters would be f, F, u, U, in this case of cream either f or  F would work fine.

---

### Post by bab1 on 2015-11-05
> **mc4man said:**
> cream installs with a .desktop but no maintainer has bothered to notice that in gnome 3.x the Exec= line must end in a % <letter> to be in the file manager's (nautilus) context menu
Applicable  letters would be f, F, u, U, in this case of cream either f or  F would work fine.
Sometimes this stuff is confusing to me.  Here is the pertinent line in my  sublime-text.desktop file```
Exec=/opt/sublime_text/sublime_text -n

```

Sublime-text is an option when I right click on a text file.  I'm not saying what you recommend won't work.  Maybe there is something deeper?  What am I missing here?

---

### Post by mc4man on 2015-11-05
> **bab1 said:**
> Sometimes this stuff is confusing to me.  Here is the pertinent line in my  sublime-text.desktop file```
Exec=/opt/sublime_text/sublime_text -n

```

Sublime-text is an option when I right click on a text file.  I'm not saying what you recommend won't work.  Maybe there is something deeper?  What am I missing here?
Don't know, sublime text here has this as the Exec= line (in /usr/share/applications
> Exec=/opt/sublime_text/sublime_text -n %F
If the %F is removed then Sublime Text *immediately*  disappears from the context menu. This is a known requirement & has been since gnome 3 appeared quite some time ago.

---

### Post by bab1 on 2015-11-05
> **mc4man said:**
> Don't know, sublime text here has this as the Exec= line (in /usr/share/applications

If the %F is removed then Sublime Text *immediately*  disappears from the context menu. This is a known requirement & has been since gnome 3 appeared quite some time ago.
I see my mistake.  I looked at the [Desktop Action Window] section
```
[Desktop Action Window]
Name=New Window
Exec=/opt/sublime_text/sublime_text -n
OnlyShowIn=Unity;
```
 
Lower down is the line you mentioned. This is good info to know and hard to come by.  Thanks for your time.

---

