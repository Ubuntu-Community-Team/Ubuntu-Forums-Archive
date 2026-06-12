---
title: "Is 'Make Link' a 'FAIL' awaiting a bug-fix?"
date: 2012-10-15
forum: General Help
---

### Post by Ace..... on 2012-10-15
This looks like a serious bug to me.
Perhaps others could confirm?
*********

Has anybody tried to make a document link (typically I guess, to place on the desktop as a clickable icon)?

Try this:

Open Gedit - copy and paste a few bytes of text - save as 'AA-test' in your document dir.
Open Nautilus and check your doc dir - yes it's there.

Rclick it - 'make link'.

What you now see is a new file called 'Link to AA-test ' - both are the same file size.

Dclick the 'Link to' file and delete a couple of bytes (2 characters), and save.

My sys is set to make bakups, so I now see:

Link To AA-test~[COLOR=White]_____[/COLOR] 945bytes
AA-test[COLOR=White]____________- [/COLOR]943bytes
Link To AA-test[COLOR=White]______[/COLOR] 945bytes

The above is clearly incorrect cos my bakup is called 'Link To'

Now open 'AA-test' directly, and delete 2 more characters and save.
I now see:

AA-test[COLOR=White]____________-[/COLOR] 941bytes
Link To AA-test~[COLOR=White]_____[/COLOR] 945bytes
AA-test~[COLOR=White]___________-[/COLOR] 943bytes
Link To AA-test[COLOR=White]______[/COLOR] 945bytes

It seems conclusive that 'make Link' is not functioning correctly.
Further tests can be made, eg. rename 'Link To' - 'Linq To'.
When you load it in Gedt, top-left informs you are working on 'Linq To AA-test'.

Apart from this being confusing...... it looks like instead of having a small link file, my doc, and my bakup doc.........  I now have 4 full size docs wasting space on my HDisk.

This is surely a bug no?

:confused:

---

### Post by ALinuxWindowsBalance on 2012-10-15
I get the same results.
It looks like it; that's weird. 
I've never seen that before, usually links are only a line of code like ```
gedit ~/doclocation
```
and less than 1KB. I guess it is broken. Well, now you can easily back up single files! :3

---

### Post by Ace..... on 2012-10-15
> **ALinuxWindowsBalance said:**
> I get the same results.
It looks like it; that's weird. 


Thanks for confirming that!
I've just had a look at 'how to report a bug':

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Wow....... I'm struggling with figuring out what to do.
I tried ubuntu-bug but one is supposed to add the offending program name.

Adding ubuntu, or make-link doesn't work cos they are not packages.

Ah.......... okay.

There is a direct link:

[https://bugs.launchpad.net/ubuntu/+filebug?no-redirect=](https://bugs.launchpad.net/ubuntu/+filebug?no-redirect=)

This should work

---

### Post by LewisTM on 2012-10-15
This is all perfectly normal.

1) If you execute [FONT="Courier New"]ls -al <link>[/FONT] or [FONT="Courier New"]du <link>[/FONT] in a terminal you will see that each link takes virtually no space. In contrast Nautilus (and Thunar) display a positive value corresponding to the original file (the target). I'm not 100% sure what is the reason behind this but I guess it's far more informative than returning the meaningless size of the link.

2) If you edit a link inside gedit, the app thinks it's a real file (that the whole point of links) and uses the link's filename in its title. Perfectly normal. 

3) If you make modifications, file managers will report the new size on the _target_ because they are constantly in tune with file system changes. They do not, however, reevaluate link information (which is inferred). Close the window and open a new one - or press F5 - and you will see the sizes match.

Cheers!

---

### Post by Ace..... on 2012-10-15
Thanks for replying Lewis.
Obviously I'm gonna disagree big time with you on this one, but that's fine.

> **LewisTM said:**
> 

This is all perfectly normal.

1) If you execute [FONT=Courier New]ls -al <link>[/FONT] or [FONT=Courier New]du <link>[/FONT] in a terminal you will see that each link takes virtually no space. In contrast Nautilus (and Thunar) display a positive value corresponding to the original file (the target). I'm not 100% sure what is the reason behind this but I guess it's far more informative than returning the meaningless size of the link.

2) If you edit a link inside gedit, the app thinks it's a real file (that the whole point of links) and uses the link's filename in its title. Perfectly normal. 

[I]
This is all perfectly normal.[/I]

[COLOR=Navy]Perhaps normal but certainly not correct.[/COLOR]


*1) If you execute [FONT=Courier New]ls -al <link>[/FONT] or [FONT=Courier New]du <link>[/FONT]  in a terminal you will see that each link takes virtually no space. In  contrast Nautilus (and Thunar) display a positive value corresponding to  the original file (the target). I'm not 100% sure what is the reason  behind this but I guess it's far more informative than returning the  meaningless size of the link.*

[COLOR=Navy]I honestly can see no reason in purposefully mis-reporting the size of a file, AND since when did file size become meaningless?[/COLOR]

*2) If you edit a link inside gedit, the app thinks it's a real file  (that the whole point of links) and uses the link's filename in its  title. Perfectly normal. *

[COLOR=Navy]No the above is a complete mis-understanding of what a link is and what it should do.

If I place my link code (represented by an icon) onto my desktop.....
..... the one thing we can be certain of, is that when I Dclick that icon, I do not want to be editing a document called Link To ********.

The fact that this is occurring, is proven by the auto creation of a bakup file, called Link To ********

What I definitely want from my links, is that when I click them, they launch the document that I ask for. [/COLOR]

---

### Post by LewisTM on 2012-10-15
We will agree to disagree. But be aware that you are disagreeing with a lot of other Linux users.

1) File manager are there to help people find information about their files. I don't see how reporting a file size of 20 bytes for a link can be informative in any way. We could change it to '---' to make it non-applicable, it's just a link.

2) Absolutely no true. Many people like to rename their links (file or directory) and work with that. I can make a link to /media/918290718937dh/Documents on my desktop and call it "Mom's files" and that's fine. The behavior you describe, you will get with a "Launcher" akin to a "Shortcut" in Windows. That will launch the desired application with the target file. Launchers are NOT links.

3) An app is oblivious to whether the file it is working on is a link or a real file. It will happily make a backup of what it is currently working on, with the current file contents and name. This is fundamentally how Linux works.

---

### Post by Ace..... on 2012-10-15
> **LewisTM said:**
> We will agree to disagree. But be aware that you are disagreeing with a lot of other Linux users.

1) File manager are there to help people find information about their files. I don't see how reporting a file size of 20 bytes for a link can be informative in any way. We could change it to '---' to make it non-applicable, it's just a link.

2) Absolutely no true. Many people like to rename their links (file or directory) and work with that. I can make a link to /media/918290718937dh/Documents on my desktop and call it "Mom's files" and that's fine. The behavior you describe, you will get with a "Launcher" akin to a "Shortcut" in Windows. That will launch the desired application with the target file. Launchers are NOT links.

3) An app is oblivious to whether the file it is working on is a link or  a real file. It will happily make a backup of what it is currently  working on, with the current file contents and name. This is  fundamentally how Linux works.

*We will agree to disagree. But be aware that you are disagreeing with a lot of other Linux users.*

[COLOR=Navy]Yes absolutely..... this is not a pointless fight.
What this is doing is highlighting an element of linux that is totally counter-intuitive, and misleading AND there is no reason why such issues cannot be tidied up in future releases eg.[/COLOR]

*2) Absolutely no true. Many people like to rename their links (file or  directory) and work with that. I can make a link to  /media/918290718937dh/Documents on my desktop and call it "Mom's files"  and that's fine. The behavior you describe, you will get with a  "Launcher" akin to a "Shortcut" in Windows. That will launch the desired  application with the target file. Launchers are NOT links.*

[COLOR=Navy]Intuitively, when we Rclick on a file and see the menu with an option to 'Make Link', the vast majority (just a guess) of people who begin to use ubuntu will assume this to be 'Make Shortcut' cos there is no menu command to 'Make Launcher' (I actually don't know how to do that).
If we had a menu option 'Make Launcher' this would avoid the confusing situation below:[/COLOR]

*3) An app is oblivious to whether the file it is working on is a link or  a real file. It will happily make a backup of what it is currently  working on, with the current file contents and name. This is  fundamentally how Linux works.*

[COLOR=Navy]Yes clearly this how it works, but this doesn't mean that the way the command (Make Link) is offered, is 'well done'.
We end up with 4 files.

I have to presume that this is useful........ but all I want to do is stick a shortcut/launcher onto my desktop, so I can quickly pull up a doc that I need.

This has been a normal part of gui desktops for decades now!
"Choose the file - Rclick - make shortcut - stick it where you want".[/COLOR]

[COLOR=Navy]Sure that uses windows terminology.... but hey... everybody understands what I'm saying.
AND
Bear in mind...... the result of Make Link is so close in resemblance to Shortcut, and because it is offered in the same manner, one will automatically assume that this is what it is.

Oh yes - File size reporting...... sure, we will agree to disagree cos to me 'reporting a file size' should mean 'reporting the file size'....... a no-brainer as far as I'm concerned. ;)

[/COLOR]

---

### Post by Ace..... on 2012-10-16
@ Lewis
To clarify this situation of launcher v Make Link I did some researching, and found an interesting document that confirmed what you had said:

[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

Apparently, in versions prior to 11.10 ubuntu did have a Rclick Make Launcher (shortcut), but in 11.10 this was dropped in favour of Make Link.

This seemed like a very good conclusion to the thread, seeming to vindicate both our positions - for myself at least to the extent that Rclick to make a shortcut/launcher had been considered useful.
Why no longer, I really don't know.

But at least it offered the opportunity of changing thread status to solved.  :)

However, I figured it only right to check out the file size question.

For this I had to install Krusader - a serious File Manager that I have used before, that is capable of reporting file sizes accurately.

This cleared away the fog, and enabled a much better understanding of what is happening with Make Link.

What it showed is worthy of note:

Link to AAA-test [COLOR=White]______--[/COLOR] 29Kb
Link to AAA-test~ [COLOR=White]______[/COLOR] 55.3 Kb
AAA-test [COLOR=White]_____________-[/COLOR] 56.3Kb
AAA-test~ [COLOR=White]__________----[/COLOR] 44.3Kb (the bakup is no longer updated)

**Procedure:**
1. 'AAA-test' was created and then modified, producing 'AAA-test~' bakup.
2. 'Link to AAA-test' was created, producing Link to AAA-test~ bakup.
3. 'Link to AAA-test' was modified.

**Conclusion:**
So now, the bakup file for 'AAA-test' is in fact 'Link to AAA-test~'.

Not a great situation for alphabetical sorting.
But worse, because the named bakup file 'AAA-test~' is now no longer updated.

It's a time bomb becoming hopelessly out of date, yet it is sat there being reported as the bakup to AAA-test.

For people who use icon view, and alphabetical sorting, the user can confidently see AAA-test has its bakup sat there beside it (no sizes in icon view).

Yet it's not a bakup. :shock:

Clearly this is how 'Make Link' is meant to work.

However, what it does (in effect) is populate the hardisk with bakup files that are not bakup files, in amongst fully functioning bakup files. :shock:

All this from a user friendly Rclick menu.

It's a cautionary tale, and makes one wonder why 'a simple link to launch a file' has not been offered.

Perhaps after all, 'Make Link' does require a 'bug fix'. ;)

---

### Post by Wim Sturkenboom on 2012-10-16
// Edit: see post #12

// Edit:
// safe to ignore, you're already further than I am ;)

Running Ubuntu 10.04, I can NOT confirm this. In nautilus, links created using the command line (ln -s) as well as a link created using 'make link' correctly reflect the size of the file that the link points to (I need to press <F5> to refresh the links but the original file is immediately updated).

Command line is another story; links are fixed size. Those created on the command line are 7 bytes, those created using 'make link' are 22 bytes.

Conclusion; in 10.04, Nautilus follows the link and gives the size of the target.

---

### Post by LewisTM on 2012-10-16
I admit it's all a bit convoluted. The problem, you probably realize now, stems from the fact that the backup function is an Application feature, not an OS feature. Apps can't track how files are linked and if they are being modified from another location, let alone another program. In the end, they can't garantee that a backup always corresponds to the previous version. It's a poor man's version control system. Git and CVS are sophisticated Linux file versioning systems but personally I just use Dropbox to keep backups of file versions for my important documents.

What you really need is launchers. In my defence, I use Xfce so I didn't know launchers could no longer be created in Unity world. In Xfce, you can create symbolic links on the desktop but also **Application** Launchers (e.g. [FONT="Courier New"]gimp /home/user/diagram.tif[/FONT]) and **URL** Links (e.g. [FONT="Courier New"]file:///home/user/document.odt[/FONT]). It's very convenient, perhaps you should give it a try :D

---

### Post by Ace..... on 2012-10-16
Yes, convoluted is good description.

For that reason, I believe that 'Make Link' should not be available from the Rclick menu.
It is just too similar to 'create shortcut', and even appears as if it's a shortcut, yet it is an entirely different concept - better suited to users who understand how it actually functions and are aware of the orphaning of the original bakup file.

I propose, it should be in the main menu, and 'Make Launcher' should take its place in the Rclick.

To this end, I have posted this to the ideas sandbox (because it is clearly not a bug).

[http://brainstorm.ubuntu.com/idea/30242/](http://brainstorm.ubuntu.com/idea/30242/)

The site is linked to this one, but you need to create* another* account :roll:, in order to post, and vote on the suggestions.

At the moment the suggestion is awaiting moderation, before it passes thru to the voting stage.

It's the X Factor for Ubuntu :grin:

---

### Post by Wim Sturkenboom on 2012-10-16
OK, I think I've found your problem. When you edit your symlink with gedit, the backup is a regular file (not a symlink to the backup).

```

wim@i3-2120:~/test$ ls -l
total 12
-rw-rw-r-- 1 wim wim 231 Oct 16 16:26 abc.txt
-rw-rw-r-- 1 wim wim 111 Oct 16 16:23 abc.txt~
lrwxrwxrwx 1 wim wim  22 Oct 16 16:24 Link to abc.txt -> /home/wim/test/abc.txt
-rw-rw-r-- 1 wim wim 221 Oct 16 16:26 Link to abc.txt~
wim@i3-2120:~/test$ 

```


PS
12.04 behaves the same as 10.04 as described in post #9

---

### Post by Ace..... on 2012-10-16
> **Wim Sturkenboom said:**
> OK, I think I've found your problem. When you edit your symlink with gedit, the backup is a regular file (not a symlink to the backup).

```

wim@i3-2120:~/test$ ls -l
total 12
-rw-rw-r-- 1 wim wim 231 Oct 16 16:26 abc.txt
-rw-rw-r-- 1 wim wim 111 Oct 16 16:23 abc.txt~
lrwxrwxrwx 1 wim wim  22 Oct 16 16:24 Link to abc.txt -> /home/wim/test/abc.txt
-rw-rw-r-- 1 wim wim 221 Oct 16 16:26 Link to abc.txt~
wim@i3-2120:~/test$ 

```

Yes.
That is.... I presume that 'symlink' is the appropriate term for the link file created by the 'Make Link' command.

I created a link to a radio telephone manual - the phone being so complex that I needed the manual rapidly to hand just so I could begin to learn to use the functions real time.
But I noted that when I edited the name (cos it was really long) for the icon, the result actually changed the name of the pdf file.

Obviously I didn't want to do that - I just wanted a snappy link to a doc.
This caused me to run some tests, and the confusion grew, particularly as it seemed that I now had 4 files all corresponding to the testdoc size at different save points. 

As you point out, by launching the symlink for editing, I thought I was launching the original file,  but in fact I was editing the symlink, which then gained a bakup which became the bakup for the original file.
The original file bakup was then orphaned from the process.

I was left with:
1 symlink
1 symlink backup (which in fact it was not, as it was a full sized doc bakup)
1 original doc (correctly updated)
1 original doc bakup (no longer updated yet masquerading as a bakup)

( as your tests show)

I just think this is way too complicated for the unsuspecting user.

Hey..... it was way too complicated for me, and I've been working with PC's since the Hercules Graphics Card was the biggest advance in computing technology.  LOL

---

### Post by Wim Sturkenboom on 2012-10-16
> 
by launching the symlink for editing, I thought I was launching the original file
You are editing the original file, just under another name. But I (finally) start to understand where your confusion comes from ;)

FYI vi shows the same behaviour as gedit. So I assume they just 'open the file' without caring about the fact that it's a symlink or not.

---

### Post by mc4man on 2012-10-16
As far as the brainstorm - this isn't a Unity or even Ubuntu thing, nautilus now uses 'make link' instead of 'create launcher/shortcut' (symlink vs. a .desktop
So as far as nautilus 3.x+ don't see Ubuntu having much interest in modifying in this regard.

Text editors that create backups will name the backup based on the filename opened, again don't see that easily changed. (and really not really Ubuntu's concern, up to the app to address if at all.

---

### Post by Ace..... on 2012-10-16
> **Wim Sturkenboom said:**
> You are editing the original file, just under another name. But I (finally) start to understand where your confusion comes from ;)

FYI vi shows the same behaviour as gedit. So I assume they just 'open the file' without caring about the fact that it's a symlink or not.

Yes, that's exactly the problem.

The os/add-on package does not create a bakup of the symlink (if it was changed).
It creates a bakup of the file that is being linked to.

**IE. if you change a file that is 29bytes in size, you do not expect its bakup to jump to (say) 1Mb in size.**

As Lewis said, and I'm relying on him being correct...... **this is normal.**

The question is...... whether this follows 'good working practice'?

**It may do. vis a vis what 'make Link' was designed to do.**

But this begs the further question:

Should not the bakup sys recognise the symlink, and if it has changed then say, a symlink of 29 bytes might become a symlink of 30 bytes (but not 1Mb).

Plus..... the fact that Nautilus fails to report the file size correctly, means that confusion reigns.
There is no distinction between the genuine symlink file and its bakup which is reported as being the same size (yet they are totally and utterly completely different files - one being a link, and one being a doc, for example).

For myself, the prob is that this thread contains a lot of viewers, but very few are jumping in to defend 'Make Link' (actually almost nobody, cos Lewis was merely explaining how it worked - and only by implication, does that mean there is good reason behind its methodology).

I think there has to be reasons for how it works (in this convoluted manner).

If nobody is jumping in..... then perhaps it means there is no support for its methodology, and how it integrates with auto-file-bakup.

Hence my post to the 'ideas sandbox'.

I think that the 'thread readers' should get off the fence, and state whether they are content with the current implementation of 'the ability to create a launch link to a doc'.

That is not to say they are against 'Make Link'......
... but more on whether this command creates confusion in the way it is implemented.

Is that fair?

Anybody? :-(

---

### Post by LewisTM on 2012-10-16
[Symlinks]("http://en.wikipedia.org/wiki/Symlinks") have been around since 1978 (before Hercules graphics!). They have always worked consistently and are one of the strengths of UNIX-like OSes; they are even beginning to appear on Windows.

I agree Unity users should be able to create launchers more easily. As for the backup story, as mc4man has said, it has nothing to do with Nautilus but rather with the text editor. Should it dump the backup text in the current directory with the current filename + '~'? Or should it track where the file actually is and make a backup there? There is no point in making a backup of the symlink itself, it's just a pointer, it wouldn't change at all.

You should wrap your head around the concept of the old symlink and embrace it, not fight it.

10-4

---

### Post by Wim Sturkenboom on 2012-10-16
> 
Should not the bakup sys recognise the symlink, and if it has changed then say, a symlink of 29 bytes might become a symlink of 30 bytes (but not 1Mb).

There is no such thing as a 'backup sys' ;) It's a functionality of the editor in use. In vi, I had to switch it on. The editors just use fopen(); they don't stat()/lstat() the argument that is passed to them first to see if it's a file or a link.

> 
Plus..... the fact that Nautilus fails to report the file size correctly, means that confusion reigns.

In my case Nautilus reports correctly every time.

> 
There is no distinction between the genuine symlink file and its bakup which is reported as being the same size (yet they are totally and utterly completely different files - one being a link, and one being a doc, for example).

There is; just check the icon to see the difference. And in icon view, you can even include the type under the icon so it tells you in text that it is a link; just setup the preferences in nautilus for that.

> 
I think that the 'thread readers' should get off the fence, and state whether they are content with the current implementation of 'the ability to create a launch link to a doc'.

Yep, I am. When I saw the option 'make link', it behaved as I expected by creating a symlink.

---

### Post by Ace..... on 2012-10-17
Well I think it is good that users are defending Make Link, cos at least it shows why it was included.

@Lewis I think your last line is an important statement
*You should wrap your head around the concept of the old symlink and embrace it, not fight it.*

This is surely correct - as is:
*I agree Unity users should be able to create launchers more easily. *

You are obviously correct re there being no need to back up the symlink etc.
But you understand that my concern was always the confusion, created from the 'displayed filename stating it is a bakup of the symlink' and the misleading file size reporting (clarified by Krusader).

But don't forget.... I now understand all this.
The issue is 'that I didn't understand this', and neither did the fist chap who responded.

The obvious remark 'well you have to learn' is all well and good, if you realise that there is something to learn.
Hence my proposal to return 'Make Launcher' to the menu system - indicating, just by its presence, that it must be different to 'Make Link'. 

@Wim Sorry about the term bakup sys I didn't know what it was/is called, but I meant the sys that auto creates a 'bakup file copy' indicated by ~.

Re Filesize misreporting: Krusader reports a different filesize to that reported by Nautilus re symlinks.
As to the confusion this causes - see the 1st & 2nd posts of this thread.

Re distinction between the two 'Link to *******' files (doc & symlink) you are correct - **I'm evidently losing my marbles.**

Apart from that latter fact...... it has been a good thread.
I've marked it as solved because the title question has been answered.

I've just checked the progress of
[http://brainstorm.ubuntu.com/idea/30242/](http://brainstorm.ubuntu.com/idea/30242/)

Thank you Wim for clarifying the misunderstanding of the Moderator.

A shame he didn't see fit to approve it for 'voting'
I can't see any reason why 'providing Make Launcher' could be anything but beneficial.

At the very least it deserves a vote  :)

---

### Post by Wim Sturkenboom on 2012-10-17
> **Ace..... said:**
> 
@Wim Sorry about the term bakup sys I didn't know what it was/is called, but I meant the sys that auto creates a 'bakup file copy' indicated by ~.
The editor :)

> **Ace..... said:**
> 
Re Filesize misreporting: Krusader reports a different filesize to that reported by Nautilus re symlinks.
As to the confusion this causes - see the 1st & 2nd posts of this thread.
The only thing I found in Nautilus is that I have to refresh (<F5>) to see the correct results.

---

### Post by mc4man on 2012-10-17
I don't see issue with the filesize of the link, (size= link target) or link backup, (size of target before edit), and obviously the link backup is no longer a link, just a file

The actual filesize of a link is the number of characters in path, 1 byte per char. (break the link to see

The whole deal with 'custom launchers' was something nautilus decided to drop, ie. > open with > use a custom command is gone also

A basic shortcut template could be something like this, then all backups are the actual edited filename itself

```
[Desktop Entry]
Encoding=UTF-8
Name=[COLOR="Blue"]Link to 44[/COLOR]
Type=Link
URL=file://[COLOR="Blue"]/home/doug/Desktop/44[/COLOR]
Icon=(null) 
```
blue is editable to what/where ect., icon is optionable

---

### Post by Ace..... on 2012-10-18
> **mc4man said:**
> 
The whole deal with 'custom launchers' was something nautilus decided to drop, ie. > open with > use a custom command is gone also

A basic shortcut template could be something like this, then all backups are the actual edited filename itself

```
[Desktop Entry]
Encoding=UTF-8
Name=[COLOR=Blue]Link to 44[/COLOR]
Type=Link
URL=file://[COLOR=Blue]/home/doug/Desktop/44[/COLOR]
Icon=(null) 
```blue is editable to what/where ect., icon is optionable

I wonder why these features were dropped?

For the Desktop Entry shortcut template.
I have to say....... this works perfectly. =D>

The original file (that has been linked to) can be modified, and its bakup file is its name~
eg·
brainstorm 881 bytes
brainstorm~ 865 bytes

This satisfies 'intuitive working', and basic 'safe working practice' ie. you have a bakup and you can find it. :wink:

**The link itself**

I created it by copying your text into gedit, and editing the blue elements as instructed.
the test was a text file (it works for jpgs, so I guess it is fine for all)

Name=[COLOR=Blue]Link to brainstorm[/COLOR]
URL=file://[COLOR=Blue]/home/mark/Documents/brainstorm
[/COLOR]
I saved this as 'test.Desktop', in Desktop directory.
It appears on the desktop as "Link to brainstorm" and is clickable.

**Interesting features of the link**
Filename display:
Nautilus displays the file as per Name= [COLOR=White]____[/COLOR] Link to brainstorm
Krusader displays the file by its filename [COLOR=White]___[/COLOR]test.Desktop

Editable:
It is editable, using gedit via Krusader, or via gedit menu open.
It cannot be edited via Nautilus (or I don't know how).

After editing:
Nautilus displays the bakup file by its bakup filename:[COLOR=White]__[/COLOR]test.Desktop~
Krusader displays the bakup file by its bakup filename: [COLOR=White]_[/COLOR]test.Desktop~

File size reporting:
Both Krusader AND Nautilus report the correct filesize.

**Conclusion**
This really is the version of Make Link that I personally would have liked to see.
Any edited file is backed up using conventional naming methodology.
File sizes are correctly reported in the packaged file manager.

The only minor variant is filename display in nautilus, but if you choose the same 'Name=' as its actual filename, then there can be no confusion whatsoever.

**The Question:**
Is a little add-on difficult to make, so that you browse to the file, or Rclick when you have found it, then enter its name.

If it is not overly complex, perhaps it is this methodology that should be proposed to the idea sandbox?

---

### Post by Ace..... on 2012-10-19
The sandpit mod cheesehead suggests that 'the orphaning of the linked file bakup' is a bug.
IE. Rather than adding another version of a link creator........ the issue of the orphaned bakup file should be addressed.

[http://brainstorm.ubuntu.com/idea/30242/](http://brainstorm.ubuntu.com/idea/30242/)  (comments at bottom)

He may be right.
As Lewis said, once you get your head around the concept, the reporting of symlink size is understandable.

He also suggests that I report a separate bug...... stating 'Make Link is behaving in an unexpected manner'.
However that seems merely to create a parallel bug investigation about the same problem.

I have posted mc4man's link code, and in the meantime I will log the orphaned bakup file as a bug.

Here is the bug link:

[https://bugzilla.gnome.org/show_bug.cgi?id=686465](https://bugzilla.gnome.org/show_bug.cgi?id=686465)

---

### Post by Ace..... on 2012-10-22
My goodness..... that was quick.
The bug has been fixed. :P

Total time: around 1 week, from identification to a fix.
Pretty impressive community this is.

However, I actually don't understand what the fix is.
Could somebody enlighten me

[**Bug 686465**]("https://bugzilla.gnome.org/show_bug.cgi?id=686465") -        Make Link orphans the backup file of the linked file

I think it makes sense to follow symlinks by default when opening one, before launching the application. I now pushed a fix to git that does so, closing as fixed.

---

### Post by LewisTM on 2012-10-22
Wow! 
The fact that the bug was fixed for Nautilus 3.4.x and is tagged as major means that we might actually see it percolate to future Ubuntu maintenance updates.

I don't know what the fix means either. Since it's a Nautilus fix, it won't affect how text editors behave. Maybe it reads the link and passes the target filename as the argument for opening a file? That would make it behave very much like a launcher. Some may like it, some may not. We shall see.

---

### Post by Ace..... on 2012-10-22
> **LewisTM said:**
> Wow! 
The fact that the bug was fixed for Nautilus 3.4.x and is tagged as major means that we might actually see it percolate to future Ubuntu maintenance updates.


It certainly looks that way.

I note that this was fixed within 24 hrs of my posting it!

[ ]("https://bugzilla.gnome.org/page.cgi?id=describeuser.html&login=cosimo.cecchi%40gmail.com")[INDENT][Cosimo Cecchi]("https://bugzilla.gnome.org/page.cgi?id=describeuser.html&login=cosimo.cecchi%40gmail.com") [COLOR=DarkGreen]                            [nautilus developer]                      [/COLOR][COLOR=DarkGreen]                    2012-10-19 22:38:21 UTC         [/COLOR][COLOR=DarkGreen]I think it makes sense to follow symlinks by default when opening one, before launching the application. I now pushed a fix to git that does so, closing as fixed.[/COLOR][/INDENT]                               I figured that 'git' must be an acronym, and discovered:

[http://en.wikipedia.org/wiki/Git_%28software%29](http://en.wikipedia.org/wiki/Git_%28software%29)
Extract:

**Git** ([/]("http://en.wikipedia.org/wiki/Help:IPA_for_English")[&#609;]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[&#618;]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[t]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[/]("http://en.wikipedia.org/wiki/Help:IPA_for_English")) is a [distributed revision control]("http://en.wikipedia.org/wiki/Distributed_revision_control") and [source code management]("http://en.wikipedia.org/wiki/Source_code_management") (SCM) system with an emphasis on speed.[[3]]("http://en.wikipedia.org/wiki/Git_%28software%29#cite_note-2") Git was initially designed and developed by [Linus Torvalds]("http://en.wikipedia.org/wiki/Linus_Torvalds") for [Linux kernel]("http://en.wikipedia.org/wiki/Linux_kernel") development; it has since been adopted by many other projects. Every Git [working directory]("http://en.wikipedia.org/wiki/Working_directory") is a full-fledged [repository]("http://en.wikipedia.org/wiki/Repository_%28version_control%29") with complete history and full revision tracking capabilities, not dependent on network access or a central server.

[Linus Torvalds]("http://en.wikipedia.org/wiki/Linus_Torvalds") has quipped about the name "[git]("http://en.wiktionary.org/wiki/git")",  which is English slang for a stupid or unpleasant person. Torvalds  said: "I'm an egotistical bastard, and I name all my projects after  myself. First '[Linux]("http://en.wikipedia.org/wiki/Linux_kernel")', now 'git'."[[4]]("http://en.wikipedia.org/wiki/Git_%28software%29#cite_note-whythegitname-3")[[5]]("http://en.wikipedia.org/wiki/Git_%28software%29#cite_note-4") The [man page]("http://en.wikipedia.org/wiki/Man_page") describes git as "the stupid content tracker".[[6]]("http://en.wikipedia.org/wiki/Git_%28software%29#cite_note-5")

:)

---

