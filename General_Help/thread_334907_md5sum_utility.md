---
title: "md5sum utility"
date: 2007-01-09
forum: General Help
---

### Post by rioghal on 2007-01-09
I am in need of a GUI app that does md5sum and sha1sum verification.

---

### Post by taurus on 2007-01-09
Applications -> Accessories -> Terminal
```
md5sum **filename**
```

---

### Post by rioghal on 2007-01-09
> **taurus said:**
> Applications -> Accessories -> Terminal
```
md5sum **filename**
```
I need a GUI app.. which is why I stated 'GUI app' in my original post.
I'm trying to convert some Windows users to Ubuntu and they don't like dealing with a terminal.

---

### Post by teaker1s on 2007-01-09
k3b will check,don't know about gnomebaker you will need to check

---

### Post by rioghal on 2007-01-09
> **teaker1s said:**
> k3b will check,don't know about gnomebaker you will need to check
Gnomebaker won't do it.

---

### Post by jimcooncat on 2007-01-09
I don't know how to tie these two commands together in a command line:
```

md5sum `zenity --file-selection`
```
That will give you the md5 and filename on STDOUT

```
 zenity --info --text "md5sum is: xxxx xxxx"
```

will display some text.

---

### Post by maxamillion on 2007-01-09
jimcooncat: Take the two commands and combine them in a file without an extension...
```
nano someFile
```

enter your commands in there like this

```
#!/bin/bash
md5sum `zenity --file-selection`
 zenity --info --text "md5sum is: xxxx xxxx"
```

save, then make it executable...

```
chmod +x someFile
```

then at the command line do 

```
./someFile
```

if I understood what you were talking about, this will give the result you wanted....

---

### Post by rioghal on 2007-01-09
> **jimcooncat said:**
> I don't know how to tie these two commands together in a command line:
```

md5sum `zenity --file-selection`
```That will give you the md5 and filename on STDOUT

```
 zenity --info --text "md5sum is: xxxx xxxx"
```will display some text.
Actually, you gave me a great idea: Why not write it in zenity until I can find a python/ruby/perl/C++ app?

---

### Post by jimcooncat on 2007-01-09
Ha ha! That beats my:
```
export ZENTMP=`zenity --file-selection` && zenity --info --text `md5sum $ZENTMP`
```
I was trying to do a one-liner, but I don't think I should have used the "export" command. After all, something else might have set ZENTMP and I wiped it out.

Edit:
A little better. But not input and pass/fail comparison test like rioghal's.
```
 zenity --info --text $(md5sum $(zenity --file-selection))
```

---

### Post by bodhi.zazen on 2007-01-09
LOL There already is a great gui for checking MD5 sums,

It's called "terminal"

```
md5sum -c downloaded.iso.md5
```

This command will do this:
> bodhi@Arch:~$md5sum -c groups.md5sum
groups: OK
bodhi@Arch:~$

See this link for some how to's:

[http://www.ubuntuforums.org/showthread.php?&t=290339](http://www.ubuntuforums.org/showthread.php?&t=290339)

Bottom line:

IMO you should NOT HIDE the CLI to new users, you should REINTRODUCE it. The CLI is part of what makes Linux so powerful.

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by rioghal on 2007-01-09
> **bodhi.zazen said:**
> LOL There already is a great gui for checking MD5 sums,

It's called "terminal"

```
md5sum -c downloaded.iso.md5
```This command will do this:


See this link for some how to's:

[http://www.ubuntuforums.org/showthread.php?&t=290339](http://www.ubuntuforums.org/showthread.php?&t=290339)

Bottom line:

IMO you should NOT HIDE the CLI to new users, you should REINTRODUCE it. The CLI is part of what makes Linux so powerful.

[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

These users will not use Ubuntu if they have to use the terminal right away.. like so many other Windows users, they are willing to learn it a bit at a time but they are afraid to dive right into it full-force. I feel that if I cater to their worries a bit at first, they have a better chance of STAYING on Ubuntu rather than getting overwhelmed and going back to Windows. Yes, the terminal is powerful, but it's also intimidating to people who have used Windows all their lives.

---

### Post by rioghal on 2007-01-09
Hmm.. still looking for a GUI app that does md5sum and sha1sum file verification.

---

### Post by bodhi.zazen on 2007-01-09
> **rioghal said:**
> These users will not use Ubuntu if they have to use the terminal right away.. like so many other Windows users, they are willing to learn it a bit at a time but they are afraid to dive right into it full-force. I feel that if I cater to their worries a bit at first, they have a better chance of STAYING on Ubuntu rather than getting overwhelmed and going back to Windows. Yes, the terminal is powerful, but it's also intimidating to people who have used Windows all their lives.

I understand.

But, you can't hide the CLI forever (unless you want to sys admin for them) and this md5sum "exercise" can serve as a nice introduction.

I would caution you not to go too far in insulating your new users from the CLI. IMO it is unrealistic to "oversell" Ubuntu by "hiding" the CLI.

---

### Post by Sef on 2007-01-09
For an md5sum and sha1sum, you don't have to type in the whole name of the file,  just type in about 3 or 4 letters and hit tab.  The rest of the name will come up.  Note you must change to the directory where the file is, and the file name is case sensitive.

---

### Post by bodhi.zazen on 2007-01-09
> **Sef said:**
> For an md5sum and sha1sum, you don't have to type in the whole name of the file,  just type in about 3 or 4 letters and hit tab.  The rest of the name will come up.  Note you must change to the directory where the file is, and the file name is case sensitive.

On the subject of tab completion ...

Works for commands too.

Type md5<tab_key> and you will get md5sum.

couldn't live without it 8)

---

### Post by Sef on 2007-01-09
> On the subject of tab completion ...

Works for commands too.

Type md5<tab_key> and you will get md5sum.

Thanks.  Always nice to learn something new.

---

### Post by rioghal on 2007-01-09
This is why I was wanting a GUI app to do md5/sha1 verification. You guys have to look at this from a Windows user's perspective. Windows users don't want to:

1) Open a terminal,
2) Type commands to get to where they need to be.. that is IF they are adept at Linux file system navigation.
3) Type in a command to get the file checksum verified.. that is IF they can remember which of the thousands of Linux commands they need to use.

They want to be able to run a GUI app, browse for a file via a file dialog window and have the app do the checksumming itself and report the output.. a couple of clicks and they're done. I mean, that IS what "user-friendly" is all about, right?

If we make Ubuntu seem less than user-friendly from the start, what are they're chances of staying with Ubuntu and learning how to use it correctly? They have a better chance of staying on Ubuntu if you cater to their worries first and then have them learn a bit at a time until they can stand up and be counted an official Linux user - which will give them a huge sense of accomplishment.

I'll admit that the CLI is quite powerful, but these days some users want to do it the easy way (or they don't have time to fuddle with learning the CLI).. and that means GUI.

I've only been on Ubuntu a few months. But, if the person who helped me switch to Ubuntu from Windows had told me to use the command line for most things from the beginning.. I'd have told him to get bent and said "Windows is easier". I now realize that Ubuntu is better, I was tapered into the command line interface.. instead of jumping off the deep end. I'll never go back to Windows, I'm sticking with Linux.. but that's only because I was allowed to learn things at my own pace ;)

---

### Post by teaker1s on 2007-01-09
I've been watching this thread and it seems pointless  thread

my one question is- why would they need to have a md5sum utility unless they are burning iso's and you don't credit them with using command line. 

if it's just verifying cd integrity can't gnombaker do that?

 as they wouldn't need it for basic use just configure synaptic repositories and if they have no internet connection use add cdrom



result no hassle just point and click that my grandparents use

---

### Post by rioghal on 2007-01-09
> **teaker1s said:**
> I've been watching this thread and it seems pointless  thread

my one question is- why would they need to have a md5sum utility unless they are burning iso's and you don't credit them with using command line. 

if it's just verifying cd integrity can't gnombaker do that?


No, gnomebaker can't do it. I sorry to have bothered the forums, I'll seek answers elsewhere.

---

### Post by teaker1s on 2007-01-09
behaving like a forum troll:rolleyes: - it was a legitimate question

---

### Post by rioghal on 2007-01-09
> **teaker1s said:**
> behaving like a forum troll:rolleyes: - it was a legitimate question
I don't appreciate being called a troll.. especially after I spend my free time in these forums answering questions. You should look at some of my prior posts before labeling me a troll. Adding you to my ignore list.

---

### Post by teaker1s on 2007-01-09
it's a straight forward question, if you want them to only use basic's 

I set up a edgy wireless desktop for my grandparents 
kde/gnome
open office
couple of browsers
k3b
thunderbird
gimp
and configured the printer
games

they either use gnome add/remove or synaptic.



my experience with ubuntu is if they want more they learn,if they don't then the above covers it

also the bit I can't get my head round is if they don't need terminal,why do they need md5?


comical, I'm not bothered by you ignore listing me-it's funny:D 
secondly the forums you are under no obligation to answer posts and as before you have a very self important attitude and rather just ask what the options are, you snowball the issue.

BAD ATTITUDE

---

### Post by rioghal on 2007-01-09
I'm a woman, and I'm still learning Ubuntu. If anyone would be interested in writing a python app that does md5sum/sha1sum checksumming of files, let me know and I would be willing to write all the documentation for the app as well as helping write the GUI in glade.. I haven't been able to grasp python or ruby yet, glade was easy.

---

### Post by teaker1s on 2007-01-09
you won't be reading this as your ignoring me, but it doesn't matter if your male,female,where you come from,colour of your skin or how much money you have-I'll try and help anyone except rude demanding people=no help
Manners and common decency =help

---

### Post by jimcooncat on 2007-01-10
Amazing how a nice little thread can go downhill. Its too bad. Now I'm off topic.

When I started using computers, all we had was the CLI. So I thought that's what computers were all about, and when the GUI's came along, it took me a long time to get used to.

But the majority of people that started using computers later had only a Windows or Mac GUI, and the command line was hidden behind an icon. Many consider it unfriendly, and it's not obvious where to start to learn how to use it (in the majority of setups).

They may have experienced a neighborhood hot-shot that used the CLI commands to completly hose a system, maybe their own. It happens. They warn their friends that there be dragons, and it's just too powerful for the average user. FORMAT C: anyone?

Remember this was at a time when everyone was root, and we didn't wall ourselves away from dangerous commands with sudo. People retain their attitudes, and pass them along to the next generation.

I'd be interested in a CLI with training wheels -- buttons around the frame for inserting common commands, tutorials attached, easy-to-call man pages, pretty fonts against an appropriate background. Include step by step "wizards" to create cool little apps like the md5sum zenity thing that's the topic, and show the guts of the code while building it. 

It's not appropriate force the use of the CLI in the world we live in, IMHO. Things could be better to introduce it to GUI users.

The situation is common, the arguments old -- the rift between CLI and GUI elitists stinks. You can do whatever you want with your own system, Linux for Human Beings provides you tools for whatever flavor you desire. When you're making stuff for others to use, consider your audience.

---

### Post by jimcooncat on 2007-01-10
Back to the topic, please!

Let's make a user story, and pick on a lady named Janet. Janet wants to download a file from a web site, and the website shows a download link and an MD5 sum. If she clicks on the download link, the site might go to a redirect page for some mirrors, then the MD5 sum isn't showing on her screen anymore. So being able to capture the MD5 sum first in our tool would be appropriate.

So she copies and pastes the MD5 sum first into our tool first. Then clicks on the download link to download the file.

Janet then has to go find the file she downloads. She right-clicks on the file, and an option on the popup menu shows "Verify MD5 sum". She selects that, and gets a pass/fail message. 

A pass message might offer her the opportunity to move the file to another part of her file system, and a fail message might offer to delete the file.

Seems to me in Janet's usage, a browser extension would be appropriate. The MD5 sum is showing on a web page, so popping up a different GUI might obscure the view or distract her. So, she could right-click a highlighted sum and load the tool from that menu. 

Also the browser would know where the download landed in her file system, so if she could right-click to verify from the browser's downloads list, that would make things really simple for her.

Alternatively, you could make the functionality into an icon in the notification area, since its also on-screen at the time, probably. Drag and drop the MD5 sum to it, then drag a file icon to it, and it would pop up the pass/fail message. Since it would be simple to determine if a string is a sum or a filename, your app could handle the order of operations either way. 

rhioghal, does my user story about Janet match what you want for your users? Any feedback on my ideas?

---

### Post by rioghal on 2007-01-10
> **jimcooncat said:**
> Back to the topic, please!

Let's make a user story, and pick on a lady named Janet. Janet wants to download a file from a web site, and the website shows a download link and an MD5 sum. If she clicks on the download link, the site might go to a redirect page for some mirrors, then the MD5 sum isn't showing on her screen anymore. So being able to capture the MD5 sum first in our tool would be appropriate.

So she copies and pastes the MD5 sum first into our tool first. Then clicks on the download link to download the file.

Janet then has to go find the file she downloads. She right-clicks on the file, and an option on the popup menu shows "Verify MD5 sum". She selects that, and gets a pass/fail message. 

A pass message might offer her the opportunity to move the file to another part of her file system, and a fail message might offer to delete the file.

Seems to me in Janet's usage, a browser extension would be appropriate. The MD5 sum is showing on a web page, so popping up a different GUI might obscure the view or distract her. So, she could right-click a highlighted sum and load the tool from that menu. 

Also the browser would know where the download landed in her file system, so if she could right-click to verify from the browser's downloads list, that would make things really simple for her.

Alternatively, you could make the functionality into an icon in the notification area, since its also on-screen at the time, probably. Drag and drop the MD5 sum to it, then drag a file icon to it, and it would pop up the pass/fail message. Since it would be simple to determine if a string is a sum or a filename, your app could handle the order of operations either way. 

rhioghal, does my user story about Janet match what you want for your users? Any feedback on my ideas?

I think you have great ideas and I like your attitude about helping the user do what they want without forcing them to do it "your way". It's not my place to question why a user needs to checksum a lot of files on a daily basis. It's my place to help them do in Ubuntu that which they are doing in Windows the way THEY want to do it. Of course, I can recommend things, but if they want to do it via GUI, then I will help them do it via GUI.

2 of these 11 people have already switched and are looking for GUI apps to replace CLI ones. They say "come on.. it's the 21st century GUI's are easier to handle", and I quite agree. K3b is an awesome burner, but the CLI is more powerful. How many Linux users are going to throw away K3b and do all of K3b's tasks via CLI? If I help these 11 people today, each of them could tell 10 people tomorrow that Ubuntu is great.. and those 10 people could tell 10 people, and so on. Pretty soon, there could be an additional 10,000 people either loving or hating Linux because of my actions in their lives. Word of mouth is the quickest and most effective advertising on the planet.

I'll find a gui app that does MD5SUM/SHA1SUM verification of files, I"m too stubborn to give up :)

---

### Post by bodhi.zazen on 2007-01-10
I'm glad to see this thread is back on track.

rioghal:
[list=number][*]At this time there is no gui in Linux to check MD5SUMS. There are gui's for windows.
[*]I agree with all you have said about new users and am not advocating "forcing" the CLI on anyone. I agree that one needs to get up an running and learn at their own pace. I am active helping new users and you will see I have written a few how-to's.

Yet Linux is not yet 100 % GUI. There are some things that either are only available via a CLI. Checking MD5Sums for example is somewhat obscure.

I applaud the innovation in this thread to write a GUI to check md5sums and would be willing to script or de-bug some of this myself ....

But I would at the same time reiterate that this is a missed opportunity to teach basic CLI skills. If a user is so adverse to the CLI Linux may not be the best OS and checking md5 sums is very easy. It involves all of 1 command:

```
md5sum /path/to/downloaded.iso
```[/list]


teaker1s: Calm down.

---

### Post by rioghal on 2007-01-10
I believe Ubuntu needs a gui app that can easily show the MD5 sum (or md2,md4,sha1,sha,ripemd160,dss1) of a file. The app would benefit from being able to generate as well as check the different checksums of any file, and save the list of checksums to a text file.

I am willing to help test this app and I am also willing to write all the documentation for it as well as help write the GUI in glade if needed.

[bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054") is willing to help with scripting and debugging. I also feel that, once this app is written, the community will jump in and help with the project. This is why I feel that the Ubuntu community is second to none :) It seems all this app needs now is someone willing to write the python (or other?) code.

I propose one of two solutions:

1) Someone can package ghasher for Ubuntu and submit it to the Ubuntu repos or let the Ubuntu community know how to install an Ubuntu .deb for ghasher app. [http://asgaard.homelinux.org/code/ghasher/](http://asgaard.homelinux.org/code/ghasher/)

or

2) We can band together and write a new app for this checksumming purpose. 

I realize the CLI is important and I will be working with these folks so they can learn at their own pace. I love Ubuntu and I see this as making this awesome distro better.

---

### Post by lotusleaf on 2007-01-12
It was because of the lack of a good GUI tool on Linux for verifying and generating checksums that I asked the kind developers of the Krusader project in late 2004 to add in support for md5deep, [which they very kindly did](http://krusader.sourceforge.net/phpBB/viewtopic.php?t=1024). Today, if you install [md5deep](http://md5deep.sourceforge.net/) and [Krusader](http://krusader.sourceforge.net/) (both available for Ubuntu in the repos) you can generate and verify the following checksums:

md5
sha1
sha256
Tiger
Whirlpool

The author of the initial post in this thread may now mark this thread solved if they wish. =) Oh, and while md5deep may be used from within Krusader, you may still use md5deep at the command line (which I prefer), it's sure powerful. :)

rioghal said, *"We can band together and write a new app for this checksumming purpose."*

Well, rioghal, Krusader with md5deep seems to do the job, but if anyone wants to make a stand alone GUI program that handles md5deep, that would be very cool too. :) I'd love for Konqueror to have right-click md5deep support. You'll notice in Krusader (if you have md5deep installed, too), in addition to a pull-down menu where you may select checksum generation and verification, you may also add two fuction button/icons to your Krusader toolbar so you only have to click a button to generate or verify checksums. :)

bodhi.zazen said, *"At this time there is no gui in Linux to check MD5SUMS"*

False, since Sep 2005 this has been available with md5deep using Krusader.

[color=blue]*Md5deep is awesome:[/color]*
> md5deep is a cross-platform set of programs to compute MD5, SHA-1, SHA-256 Tiger, or Whirlpool message digests on an arbitrary number of files. The programs run on Windows, Linux, Cygwin, *BSD, OS X, Solaris, and should run on most other platforms. md5deep is similar to the md5sum program found in the GNU Coreutils package, but has the following additional features:

    * Recursive operation - md5deep is able to recursive examine an entire directory tree. That is, compute the MD5 for every file in a directory and for every file in every subdirectory.
    * Time estimation - md5deep can produce a time estimate when it's processing very large files.
    * Comparison mode - md5deep can accept a list of known hashes and compare them to a set of input files. The program can display either those input files that match the list of known hashes or those that do not match. Hashes sets can be drawn from the National Software Reference Library, iLook Investigator, Hashkeeper, or md5sum, and other generic hash generating programs. Users are welcome to add functionality to read other formats too!
    * Piecewise hashing - Hash input files in arbitrary blocks
    * File type mode - md5deep can process only files of a certain type, such as regular files, block devices, etc.  - [quote source](http://md5deep.sourceforge.net/)

Edit: thanks again to [Seth](http://www.ubuntuforums.org/member.php?u=7420) for [md5deep in the Ubuntu repos](http://www.ubuntuforums.org/showthread.php?t=112176) :)

---

### Post by bodhi.zazen on 2007-01-12
lotusleaf: Thanks for the links ....

There goes a weekend of coding :(

---

### Post by lotusleaf on 2007-01-12
> **bodhi.zazen said:**
> lotusleaf: Thanks for the links ....

There goes a weekend of coding :(

bodhi.zazen, you're most welcome. :) Why not work on a standalone GUI front-end for md5deep since it's so feature-rich? The recursive checksum generation is one of many features which is just plain awesome! Krusader has support for md5deep but I would *love* to see a standalone app take advantage of all md5deep has to offer. It doesn't look like Krusader uses all of the features that md5deep has to offer, either. So, how about it? :)

---

### Post by bodhi.zazen on 2007-01-12
I would not mind, but it is likely beyond my feeble abilities. I was thinking of a bash script.

---

### Post by PurplePenguin on 2007-01-12
Don't know if this is what you're after... [Graphical md5sum generation script for nautilus]("http://ketsugi.com/software/graphical-md5sum-generation/")

---

