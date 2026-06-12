---
title: "Improving Install"
date: 2008-03-13
forum: General Help
---

### Post by SteveHillier on 2008-03-13
Please forgive me if what I am about to say has been said, been taken notice of, or otherwise deemed the ramblings of a techy who has been in the industry too long.
I had occasion today to download the Nvu web editor.  Don't rant at me for that, I have used it on the WIndows platform so stick with what you know, eh!
In the past when I have installed new software on L:inux it has been a wonder thereafter to know where it has been installed and how to get to it.  I was pleased to see Nvu in my Application list.
I understand that other distributions may put things in different places and I have been out of software development for so long now [Windows 2 had just come out as had IBM OS/2 and a machine with 1Mb RAM was like - Wow!!], I am not sure what would be involved (or even how things get put in application lists).
It would be nice if at all possible if when an application was installed if it was ALWAYS placed in the application list or if a quick way similar to the dredded drag 'n' drop of a shortcut into a known folder had the same effect.  Even a prompt during the process "Where do you want to place this application" would help.
I was reading today a forum on the Serif products and people saying that they like these products but they are not available on Linux except under wine or something similar, and coupled to this was the age long argument about software suppliers not offering Linux options because Linux is not mainstream and how can Linux become mainstream if software providers don't make there product available on Linux.  I simply want to add that application installation not being 100% user friendly will add to that sense of "Linux is not for me" to the wider non- techy user.
My humble **apologiles **to anyone who has raised this before, worked on it, or included it in Hardy Heron.  Maybe I might be in time for Inquizative Iguana, Jumping Jerbil, Krazy Kangaroo or Licencious Lobster if you know what I mean.
Bye for now

Apologiles - I mean apologies

---

### Post by kidders on 2008-03-15
Hi there,

Your post mentions a few different issues ...

> **SteveHillier said:**
> In the past when I have installed new software on L:inux it has been a wonder thereafter to know where it has been installed and how to get to it.With a few exceptions, most applications are installed into /usr. The structure of a standard Linux filesystem is very well-defined, so once you get used to the way files are organised, it should be easy to find things, because most platforms & developers adhere to the conventions.

Even so, it's still possible to lose things. If you do, you can always try ...[LIST]
[*]**dpkg-query --listfiles [pkgname]** - List all files & directories created by an installed package.
[*]**slocate [something] **- Search your slocate filesystem index for something.
[*]**find [something]** - Do a live search of your filesystem for something.
[/LIST]These utilities all have man pages if you need more info.

> **SteveHillier said:**
> I understand that other distributions may put things in different placesThat's not generally the case. For the mostpart, there is no significant variation in how different distros organise files.

> **SteveHillier said:**
> I am not sure what would be involved (or even how things get put in application lists).One way to get a list of installed packages is **dpkg --get-selections | grep -w install**.

> **SteveHillier said:**
> It would be nice if at all possible if when an application was installed if it was ALWAYS placed in the application list or if a quick way similar to the dredded drag 'n' drop of a shortcut into a known folder had the same effect.Where possible/sensible/meaningful, application binaries are symlinked in (or installed directly into) /usr/bin. Environments like Gnome & KDE also maintain application lists, but it's up to individual developers whether they want to install links to their apps into them. It's hard to imagine why the developers of PHP would want that, for instance.

> **SteveHillier said:**
> Even a prompt during the process "Where do you want to place this application" would help.I can say with some certainty that this is very unlikely to happen. In some circumstances, particularly on distros with less well-developed package managers than Ubuntu's (ie Debian's), applications give you a choice between installing to /home or /usr (ie user-specific or system-wide). Others (mostly closed-source, badly developed, or with potentially non-native libraries), eg coldfusion, realplayer, etc. do give you full control ... most users will choose to put these in /opt, out of convention.

One thing I would say is that it's important not to confuse being "Windows-like" with being user friendly. Particularly given the tremendous complexity of what Linux package managers like apt/emerge/rpm do, which lacks any comparison in Windows, they are very user-friendly. Where application files end up seems to be the thing that bothers you most, so I'll try to list some of the influencing factors. Hopefully, something here will help...

**I - Linux apps are rarely self-contained**
For example, if you decide you want to share files with Windows boxes, you cannot "just install" Samba. In practice, Samba would be the top level in a hierarchy of interdependent packages (including, for example, security, authentication, file access monitoring, printer management, etc.), all of which are then maintained, configured & kept up to date by the package manager, which then goes on to monitor software conflicts/incompatibilities on an ongoing basis. If none of these were in predictable, well-defined locations on your hard disk, Samba would be unable to function efficiently, and I suppose the package manager would fall over!

**II - Access control & optimisation**
Often for reasons that are less important these days than they were in the past, Linux organises its stuff by purpose, not by association. So, for instance, where on a Windows box you might look in C:\Program Files\OpenOffice for documentation installed by OpenOffice, on a Linux box you would look in /usr/share/doc. This allows package managers, file indexers, and applications that might want to make use of groups of files such as "all installed documentation" or "all application icons" to function. It also allows efficient management of filesystem optimisation & access control.

**III - Convention**
Since the Linux platform is so open, convention is vital to ongoing development. As a result, even if the Ubuntu gods *wanted* to manage files differently, they couldn't. I suppose it's down to the principle of least astonishment. To take Samba as an example again, I (and everything else on my Linux box) expect to find its configuration files in /etc. If I "apt-get install"-ed it, I would expect to find utilities like "smbpasswd" in /usr/bin. If I compiled & installed it myself, I would put them in /usr/local/bin. Anyhow, you get the idea. In an OS where finding & changing the operating frequency of your CPU, or the packet routing policy of your box are achieved by reading & writing files, convention is paramount.


Anyhow, forgive the length of this post ... I hope there's something useful in it.

---

### Post by SteveHillier on 2008-03-25
I suppose I asked for that!!
Thanks for the reply, I am older and wiser now.  Whether I am capable of making use of any of it I don't know just yet.
I would however like to make this small response to the answer given.
I was not advocating a widespread change of storage locations.  The exposition you give is understandable - shove all the binaries together, shove all the documents in one place - that kinda makes sense.
What I was requesting is could there ALWAYS be a shortcut (oops! sorry! I mean symlink) placed in the menu system.
You see, I spend most of my time working on Windows machines (I build, repair, upgrade, sort out problems etc) and it really does not matter where Windows puts the executable file (or anything else for that matter).  I know if I put a shortcut into c:\documents and settings\%username%\start menu\programs\* then I can make that program available to the user for their use.  To make it available for all users then I put it in ~\All Users\~ (where ~ are the bits either side of the %username%.  Of course Vista is different.  Certainly the location is in c:\users\%username%\~ and the new access control stuff will make a difference.

---

