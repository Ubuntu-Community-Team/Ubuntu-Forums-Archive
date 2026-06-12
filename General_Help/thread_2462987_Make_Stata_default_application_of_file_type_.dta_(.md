---
title: "Make Stata default application of file type .dta (etc.)"
date: 2021-05-31
forum: General Help
---

### Post by enzmannd on 2021-05-31
I installed the proprietary statistics program Stata (versions 16.1 and 17.0) -- I am working with Ubuntu 18.04. Stata knows different file types (.ado, .cht, .do, .dta, .smcl ...) and should start and open this file when you double-click on one of the files. However, this did not work for .ado, .do and .dta files (e.g. a .dta file is treated by the system as an .html file).

I asked in the StataForum (of the Stata program) how the problem can be solved (see [https://www.statalist.org/forums/fore-type-dta-etc](https://www.statalist.org/forums/fore-type-dta-etc)), but all recommended actions fail.  While every instance of the started program got an "active" icon in the program bar (left) immediately after the first installation of Stata, this has not been the case since I tried to use the Krusader file manager to link the .do extension with Stata to change permanently (right mouse click on the file &#8594; Open with &#8594; other &#8594; [select the program "/user/local/stata16/xstata-se" with the option "remember application association for all files of type ..."). Since then Stata does not start anymore with its original icon, but only shows the unspecific Linux icon in the program bar of the active programs -- and all instances of Stata are then "collected" under this program, i.e. a new instance of Stata no longer has its own icon in the bar showing active programs.

In the link above to the question in the StataForum I have described the problem in more detail.  To solve the problem, I then used the "stata-integration.bin" script available on GitHub (see [https://github.com/dirtyhawk/stata-integration](https://github.com/dirtyhawk/stata-integration)). This initially solved the problem perfectly for Stata 16.1, but unfortunately the script does not work for Stata 17. So I tried again to link file extensions to Stata 17 with Krusader (as described above). But since then I have had the old problem again, which cannot be solved by reinstalling, (and) restarting the system or running "stata-integration.bin" again.

As a Linux novice I am not able to configure mime-types accordingly, now I hope for a helping hand from this forum.

---

### Post by monkeybrain20122 on 2021-05-31
Can you right click one of these files, from properties, choose "open with" and set xstata to default? Can't see your post the stata forum without a membership to login.

---

### Post by enzmannd on 2021-06-01
As I described in he second paragraph of my post: I **can** set Stata to be the default program for files via the property window, this is not the problem. The problem is that when starting Stata, (1) it will not get its original icon but the default Linux icon, (2) several instances of the program (if I start it more than once) will be "collected" behind this icon instead of getting an icon of its own in the programs bar (left). 

With respect to the StataForum: You should be able to see the posts there without a membership login.

---

### Post by dragonfly41 on 2021-06-01
If a free evaluation licence period was offered I might be tempted to experiment. 
But you are required to dive straight in and purchase a licence. 

If you are exploring mime types, read /etc/mime.types.

Meanwhile, there are other free maths frameworks to experiment with.

---

### Post by enzmannd on 2021-06-01
Obviously we had a misunderstanding: I thought you were referring to the StataForum when you wrote that you can't see my post there without a membership login (you should be able to see it without a membership login). Stata itself is proprietary software, I am not looking for alternatives to Stata (there is R etc.), but would like to solve the problem I described.

I am not excactly "exploring" mime types but I assume that the issue has to do with mime types and I am unable to solve it although I tried to understand it. But I am lost and that is the reason why I posted my question here. If you think I should better post my question in a different forum I will do. 

In /etc/mime.types the program Stata (or xstata) is not listed. The script "stata-integration.bin" available on GitHub (see [https://github.com/dirtyhawk/stata-integration](https://github.com/dirtyhawk/stata-integration)) does something with mime types (and in my first attempt successfuly), but I don't understand the logic.

---

### Post by dragonfly41 on 2021-06-01
I was responding to this call for help ...

> As a Linux novice I am not able to configure mime-types accordingly, 

Referring here ....

[https://github.com/dirtyhawk/stata-integration](https://github.com/dirtyhawk/stata-integration)

> The script will do the following:

1. install all mimetypes relevant to Stata (.do, .dta, .smcl, .gph, .stpr, .stsem);
2. install file-type associations for each newly installed mimetype to Stata;
3. install Stata icons for the application menu entry as well as each mimetype in several sizes;

Use at your own risk. The script has been tested on Ubuntu (16.04 through 20.10) and should work in all modern Linux desktop environments that support the freedesktop.org
 specifications on icons, application shortcuts and mimetypes
. I, however, do no not warrant this. Actually, I do not even warrant that the script works at all. That's your own risk

Since I do not have Stata installed, my personal ploy would be to  search through the entire filesystem to locate "Stata related" files ending with extensions ...

(.do, .dta, .smcl, .gph, .stpr, .stsem);

Or you could post an issue here ...


[https://github.com/dirtyhawk/stata-integration/issues](https://github.com/dirtyhawk/stata-integration/issues)


[Later edit]

Refer here for troubleshooting clues.

[https://acarril.github.io/posts/install-stata-linux](https://acarril.github.io/posts/install-stata-linux)

---

### Post by monkeybrain20122 on 2021-06-01
incidentally, stata is a command line application that runs in the terminal, to invoke the GUI you need to click on the launcher for xstata and it is the one that would appear in the context menu. First of all you need to make sure the .desktop file is placed in the proper directory (most likely /usr/local/applications if you install it system wide, i.e with sudo, or if it is in /opt/ you need to copy or link the .desktop file to /usr//local/applications), then open the .desktop file with an editor and look at the Exec line, it should end with %F for it to be open files by right click, if not, add it.

Without a copy of stata to experiment with this is all I can tell you.

BTW, I clicked your link to the stata forum it says invalid page url

---

