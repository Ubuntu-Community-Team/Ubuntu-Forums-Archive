---
title: "OOo Font Replacement Doesn't Work - Ubuntu Only"
date: 2007-08-24
forum: General Help
---

### Post by david.rahrer on 2007-08-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/52926](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/52926) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I need to ask for your help in making this a priority, as the bug has survived at least 4 versions of Ubuntu.

Here's how it should work.  A friend on Windows sends me a Word doc using Times New Roman in the body.  I don't have Times New Roman but would like to view and print the document with one I do have which is very similar, FreeSerif.  This should be done without actually changing the document, or the font shown in the dropdown box.  This way, I can edit and return the document to my friend and it will still be using Times New Roman, yet reflect my edits accurately.

The way to accomplish this is to set up Font Replacements in OOo >Tools > Options > Fonts (see attached screenshot).  This is how it works on all versions of OOo I can find **except** any flavor of Ubuntu (Windows, Knoppix, etc, and even an Edgy system where OOo was upgraded using standard RPMs converted to debs).  Manually type in Times New Roman in the first box (the one I don't have on the system), select FreeSerif in the second box (the one I do have which is similar) and click the green check mark to set up the rule, then tick "ALL" by the new rule.  From now on, when opening a document with Times New Roman, that text will actually be displayed and printed in FreeSerif on my system, without any changes to the document. 

I can go through all the motions on Ubuntu OOo, but the font display does not change.  As far as I can tell, the config file that stores this replacement information is written correctly, OOo just doesn't make the change like it does in other versions.
```
~/.openoffice.org2/user/registry/data/org/openoffice/Office/Common.xcu
```
It appears to be a genuine bug in the Ubuntu versions of OpenOffice.  A bug report at OpenOffice.org was opened and closed since this isn't a problem with the community version.  I found and added to a bug report at LaunchPad which went back as far as Dapper, and I have found that this is broken in Edgy, Feisty, and even the current alpha of Gutsy (uses an early version of OOo 2.3.0).  

[Here is the bug report]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/52926").  When working with shared documents from other platforms, this ability to replace fonts is essential.  If you want to help me get this one squashed, add to the bug report and perhaps it will at least be assigned to someone and raised from the lowest importance.  

I followed some instructions to upgrade OOo on Feisty to the community version 2.2.1 and, while it did work (bug was gone), I had other issues, not the least of which it looked really ugly :(.  I can perhaps work around this for a while, but for a great piece of work like Ubuntu, I'm sure we can do better.  I really wish I had the experience to allow me to dig into the code and do this myself.  It would be work but it would also be fun to contribute.

Thanks!

---

### Post by Hagar Delest on 2007-08-28
Hi David,

What do you mean by "it looks really ugly" ?

---

### Post by david.rahrer on 2007-09-04
I guess I've gotten used to the more integrated theme in the Feisty version of OOo.  When I install the vanila version, it looks like an older Gnome app and uses old icons.  I'm not saying that can't be done as a workaround for now, but it's not a fix.  I'm about ready to switch some small business users over to Ubuntu from XP and a consistant look goes a long way to making a good impression.

Someone has added the following to the Ubuntu specific bug [I listed above]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/52926"):

> Further research indicates that this bug also appears in Debian, and appears to have been fixed as of package 2.2.1-5.

I would think that, using the changes made to that version one could make the equivalent changes to the Ubuntu specific release - hopefully in time for Gutsy.

---

### Post by Hagar Delest on 2007-09-04
For the old icons, have you tried to change the OOo icons set ? Tools>Options>OOo>Appearance and chose another theme (Industrial/Crystal/Default/...)

---

