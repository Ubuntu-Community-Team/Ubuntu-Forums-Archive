---
title: "Hidding Folder and Files"
date: 2013-10-13
forum: General Help
---

### Post by CnYyBYP on 2013-10-13
[B][I]Hey! I'm new to Ubuntu and Linux OS completely.
[/I][/B]I've been searching mostly all day on how to hide folder and files.
Finally, I've discovered a way and quite simple actually.

Experts won't see it as much, but this will be nice for current and future beginners with the same problem.
So, I'll get to it. I'm guessing you want to "hide" or "restrict" access to a folder and it's activity.
Here's the thing.
You can simply hide it using the 
***mv*** command to add a (.) to it's name at the Terminal but it's activity will be recorded in Ubuntu's Dash, Search Bar or what ever you want to call it.

[I]Here's how it goes:

1. Place the folder where you want it to be. (It can be either Desktop,Documents,Media,along side the primary HDD,etc.)
2. Remember it's path ( "Where's it located" )[/I]
3. *Go to*** System Settings ***and click* [B]Privacy.
[/B]4.* There's going to be tabs the say: ***Search Results - Recent Items - Files - Applications - Diagnostics.**[I] 
   Go to** Files. **[/I][I]There you can choose to not record activities of types of files and folders.
   Click the **'+' **[/I][I]icon in Don't record activity of the following folders and search for the folder of your choice.(This case the one you want to hide)
5. Now go to **Recent Items **[/I]*and choose "***ALL***" and ***Delete History**[I]. (This will clear any left overs)
6. Now check if the folder appears on Ubuntu's Dash, Search Bar or whatever. 
(If it shows the name of folder you want to hide or it's activity somethings wrong, please retry this or ask me.)
If it doesn't show anything then you're good to go! :D Happy Hiding.

Now, if you want it to not appear anywhere and it's not easily seen by for others to see hide it using the **mv **command.
Example: Let's say it's located in Desktop.

Open up [B]Terminal ( Ctrl + Alt + T )
[/B]Type
[/I]**cd Desktop**[I]
it will show something like this:

[/I][B]user@user:~/Desktop$ dir

[/B]*Next, type this: (Let's say the folder name is Link)*[B]mv Link .Link
[/B][I]
Now the folder should be hidden to access it again you can either do so using the Terminal or making it visible again by repeating the steps like this:

[B]cd Desktop
mv .Link Link
[/B]
Huzzah! Everything is done.[/I]:p[I]

Tips:
Adding (.) before typing name to a folder makes it hidden. Removing it will take away it's hidden property.
Thus making [/I]**Link .Link*** and ***.Link Link**[I] look like it does.

To hide:
cd Desktop    
mv .Link Link 



To undo:
cd Desktop
mv .Link Link






[/I]

---

### Post by coldraven on 2013-10-14
Using Nautilus, the default file browser, just press Ctrl+H to see hidden files.
Then you can just press F2 to rename the file or folder.

You can also copy/paste the location by pressing Ctrl+L which will change the breadcrumb bar at the top of the window.

---

