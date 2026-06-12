---
title: "Remove &quot;Link to&quot; text from new shortcuts..."
date: 2007-12-29
forum: General Help
---

### Post by ZeusABJ on 2007-12-29
This is just a minor annoyance for me, but an annoyance nonetheless. (as I'm sure we all know) Every time you make a desktop shortcut to something in Ubuntu it inserts the text "Link to" in front of the shortcut. I'd like to remove that feature so I just get the name of the item I am linking to. 

Anyone know how to do this?

---

### Post by kyphi on 2007-12-29
I understand that annoyance.

You could try to right click on the desktop and select 'Create a Launcher' in which case you do not get the "Link to".

For creating launchers on the top or bottom panel right click the panel, select Add to Panel and make a Custom Application Launcher.

---

### Post by PinkFloyd102489 on 2007-12-29
Just hit F2 to rename the link.

---

### Post by kyphi on 2007-12-30
Yes, you could rename the link.  I prefer the right click menu to do that.

You would still be stuck with the 'arrow in the box' emblem.

Creating your launcher from scratch avoids the emblem as well as the wording of 'Link to'.

On top of that you can attach your own icons.

---

### Post by ZeusABJ on 2008-01-02
> **PinkFloyd102489 said:**
> Just hit F2 to rename the link.

My brother you are missing the point. One of my college professors illustrated it best whne he posed this question to our class once: 

"What is the one thing computers truly excel at performing perfectly every time?"

Of course he got a myriad of responses, but nobody hit on the one answer he really wanted. Finally he shushed us all and enlightened us with his answer:

"Repetitive tasks. Where we humans can perform the same job 100 times and produced identical results maybe 75-80% of the time at best computers can perform almost any repetitive job MILLIONS of times and produce the same perfect results 100% of the time. If you are manually performing a repetitive task on your computer you are wasting your time and not using your computer's to its full potential. Always ALWAYS try and find a way to make your computer do all your repetitive tasks FOR you."

The man was brilliant and it was the bets advice I've ever received when it comes to computers. So I reiterate, why rename every link I make manually when I can just remove the text from the "launcher" (to use kyphi's terminilogy).

Kyphi - Is it possible to edit the current launcher that makes these links when I drag to the desktop? OH! Hey I wonder if its somewhere in the Nautilus Configuration Editor! I'll look there...

---

### Post by kyphi on 2008-01-02
Whether or not it is possible to customise the launcher creation process I do not know.  In Dapper, some editing functions in the Configuration Editor do not work.  Full functionality was promised for later versions.  Perhaps you can do so in Feisty or Gutsy.

I tend to keep my desktop as a working surface and wipe it clean when finished.  All my shortcut icons are accessed from the top or bottom panel.

Please be aware that the 'Link to" is exactly what it says = it is a link to something else, a pseudo shortcut.

When you want a shortcut on your desktop to a folder in your Home Directory, just copy and paste the folder to your desktop.  To put a menu item shortcut on the desktop just drag and drop it to the desktop.

Shortcut, Launcher, Icon, Link - all much the same thing.

---

### Post by rowanparker on 2008-01-02
If you somehow made it so it didn't say the "link to" bit then you would get an error every time because you do it in the same directory and the file would already be there with that name.

---

### Post by mdurham on 2008-01-02
> **rowanparker said:**
> If you somehow made it so it didn't say the "link to" bit then you would get an error every time because you do it in the same directory and the file would already be there with that name.
I think that's the reason too, it would be impossible to create a link in the same directory as the target.

---

### Post by kyphi on 2008-01-02
> ... it would be impossible to create a link in the same directory as the target.

Not at all.

Right click on a folder or file in your home directory and choose "Make Link" and you will have a link to your object.  You can even make a link to the link to the link to the link, etc.

If you erased the "Link To" you could not end up with two files of the same name in the same directory - the system does not allow this.  Simply call the link: link1 or Link to differentiate link and target or have them in separate folders.

---

### Post by mdurham on 2008-01-02
> **kyphi said:**
> 
If you erased the "Link To" you could not end up with two files of the same name in the same directory - the system does not allow this.  Simply call the link: link1 or Link to differentiate link and target or have them in separate folders.

This is exactly what rowanparker & I are suggesting would be a problem, I think you misunderstood our posts.
Cheers

---

### Post by rowanparker on 2008-01-03
> **mdurham said:**
> This is exactly what rowanparker & I are suggesting would be a problem, I think you misunderstood our posts.
Cheers
You just explained it better than me :)

---

### Post by kyphi on 2008-01-03
No, there has not been any misunderstanding.  We are all talking about the same thing.

A shortcut on the desktop can have the same name as the file in your home directory that it links to.

If you put that same shortcut into your home folder then the system will not allow this since both shortcut and objective would have the same name.

The original question was how to create shortcuts without the "Link to" prefix.  I think that question has been answered.

---

### Post by ZeusABJ on 2008-01-13
> **kyphi said:**
> The original question was how to create shortcuts without the "Link to" prefix.  I think that question has been answered.

Not really, I mean other than creating a custom application launcher. I sort of just let it go because no one really seemed to have an answer for me. I'm talking about changing he behavior of cling something and dragging a shortcut to the desktop. This is akin to "shortcut to" under Windows XP. to remove that I just hack a registry key or download Tweak UI and uncheck the box that says "Use prefix "shortcut to" when making shortcuts. Here's the Microsoft knowledge base article on the matter:

[http://support.microsoft.com/kb/253212](http://support.microsoft.com/kb/253212)

I was hoping to do the same thing in my Ubuntu install but it seems nobody knows how. So my question actually has not been answered. I was just given another alternative by kyphi, but I think its overkill to create a custom launcher just for this. I'm sure someone will come up with a solution at some point.

---

### Post by phenest on 2008-01-13
> **kyphi said:**
> If you put that same shortcut into your home folder then the system will not allow this since both shortcut and objective would have the same name..

Putting a shortcut in the same folder as the objective is pointless anyway.  The reason for making shortcuts is to have them point to the objective in an entirely different folder.

I would also like to know the answer. How to remove the "Link to" text when creating shortcuts?

---

### Post by phenest on 2008-01-13
Ok. Here's what I've found:

If you right click the file and click 'Make Link', the shortcut is prefixed with "Link to". If you middle click the file, then drag to the desktop and click Link Here, the shortcut has the same name as the original file. Of course, if you use the middle click and drag within the same folder, the shortcut is prefixed with "Link to" again. This is to prevent the shortcut having the same name as the original file.

If you don't have a middle mouse button, you can press both left and right together to emulate a middle click.

---

### Post by gimfred on 2008-07-07
I'm finding it hasn't be answered and phenest solution isn't working either. I am wanting to link to files on a box, but on a different partition. (I'm right into segregation, as far as purposes go.) No matter how I create a link, it puts "Link to" in front. I do not want this. If it was in the same directory as the object, it is understandable -- the system should recognise different file types though and not just file names.

It has only been 6 months; would gnome devs have realised this convenience and removed it already?

---

### Post by guraknugen on 2008-07-19
> **rowanparker said:**
> If you somehow made it so it didn't say the "link to" bit then you would get an error every time because you do it in the same directory and the file would already be there with that name.

Why on earth would I want a link to a file in the SAME directory? Wouldn't the file itself be enough?

---

### Post by guraknugen on 2008-07-19
> **phenest said:**
> Putting a shortcut in the same folder as the objective is pointless anyway.  The reason for making shortcuts is to have them point to the objective in an entirely different folder.

I would also like to know the answer. How to remove the "Link to" text when creating shortcuts?

Me too. I was rather surprised the other day when this happened, because I can't remember that happened before with earlier versions of Nautilus.

I saw a fix for this somewhere, which seemed to include rewriting the source code and recompile, and I found myself too much of a newbie to do that, yet.

I think I will try that Custom Application Launcher thing for now&#8230;

---

