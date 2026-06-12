---
title: "quanta documentation"
date: 2005-10-28
forum: General Help
---

### Post by Robgould on 2005-10-28
I installed Quanta from synaptic.  Seems to work fine, but for one issue, all the documentation is missing.  One of the things I like about Quanta is how the cocumentation is built right in.  Anyone know what I need to do to get this?

---

### Post by Robgould on 2005-10-30
Can anyone help here?

---

### Post by jobezone on 2005-10-30
If you right-click on the quanta package in Synapitc, you'll see that it Recommends a few packages, one of which seems to be html-reference . Perhaps that is what you're looking?
Aditionally, you'll find quanta`s documentation at **/usr/share/doc/quanta/**.

---

### Post by Robgould on 2005-10-30
I did not know that you could right click like that.  Thanks for that tip.  I installed everything there, but still no luck.  Thanks though.

---

### Post by Robgould on 2005-10-30
[quote=jobezone]Aditionally, you'll find quanta`s documentation at **/usr/share/doc/quanta/**.[/quote]

The docbook is there and that part works fine, but there should also be a file for html, one for php, and one for css.  I don't understand why these folders are not there.  If anyone has these on their computer and would like to share, that would be great.  

Anone have any more ideas?

---

### Post by Robgould on 2005-11-16
Is anyone else having this issue?  That would be a step.  Is there anyone else running quanta on ubuntu that does not have the documentation?  Is there anyone else who is running quanta that does have the documentation?  Any feedback at all would be appreciated.

---

### Post by Robgould on 2005-11-16
nobody on here is running quanta?  You can't take time to click and see if you have documentation installed or not?

---

### Post by madjo on 2005-11-16
I have quanta installed, but also don't have the documentation.. 

it is either delivered with KDE or isn't present in the repositories (because a search on Quanta didn't really give me helpful hints).

---

### Post by Robgould on 2005-11-16
Thanks for the reply.  At least I know which way to look now.  If I figure it out, I will post.

---

### Post by Robgould on 2005-11-16
Think I found it.  Will try later.  Go to quanta website...google....get redirected to kdewebdev site.  Goto download.  Bottom of page there is documentation download section.  You will probably have to create correct directory for files.  I will try this later.

---

### Post by Robgould on 2005-11-18
To get quanta documentation, download from the quanta website.  Documentation for each language is a seperate download.  To instal copy files into the appropriate folders.  Give yoursel rights with

sudo chmod 775 /yourpath

There is also a handbook available here: 

 [http://docs.kde.org/stable/en/kdewebdev/quanta/](http://docs.kde.org/stable/en/kdewebdev/quanta/)

---

### Post by kperkins on 2005-11-19
kdewebdev is available through apt-get, or Synaptic (of course that's just a metapackage to install al thekde web development stuff).
You might, also, want to try installing khelpcenter (if you install that you should have what's in that last link ^).
The package wdg-html-reference provides context help for html.  There is a debian package (phpdoc) that provides php context help, but isn't included in Ubuntu. Other than that download the packages at quanta.kdewebdev.org and untar in /usr/share/apps/quanta/docs and install using the install.sh included

---

### Post by atiaxi on 2006-09-24
Hello,

  I've been reading this thread in the vain hope that I'd be able to just install a package, but it's starting to not look that way.

  Quanta reccommends both phpdoc and wdg-html-reference, but if I try to install them, I get:
[INDENT]
Package wdg-html-reference is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wdg-html-reference has no installation candidate
[/INDENT]
I've already done an apt-get update, I've got universe and multiverse in my sources.list and I've googled darn near everything on the topic, all to no avail.  Any advice?

---

### Post by cmoman on 2006-10-03
It appears wdg-html-reference may not been in the Ubuntu repositories.
A google search revealed a debian package which after downloading I installed using 
sudo dpkg -i wdg-html-reference_4.0-2_all.deb 

Seemed to do the trick. Haven't tried phpdoc yet but I am sure the process will be similar.

Perhaps the repositories are considered out of date but here is two links that might help.

[http://archive.ubuntu.com/ubuntu/pool/universe/p/phpdoc/](http://archive.ubuntu.com/ubuntu/pool/universe/p/phpdoc/)

[http://archive.ubuntu.com/ubuntu/pool/universe/w/wdg-html-reference/](http://archive.ubuntu.com/ubuntu/pool/universe/w/wdg-html-reference/)

if you want more up to date information follow the links in the Documentation intro in Quanta

download the documentation for
html
css
javasrcipt
php-quanta
mysql quanta
unzip each of these packages in your home directory.
in each, you'll find a install.sh script

Then, as root go to 
/usr/share/apps/quanta/doc/

and remove the symlinks  css > ...wdg-html-ref....
remove php > ...phpdocs
 (the ... means I can't remember the file ref exactly, they referred to the older version of the documentation that were install via the .deb files above)

Again, as root go into each newly unzipped directory and run ./install.sh

It will then install the documentation in /usr/share/apps/quanta/doc/

Fire up Quanta and it will find all the new documentation.

---

### Post by CA_Warren on 2006-12-17
I'm sorry to say this, as it's one of those 'beat-your-head-against-the-wall' things, but there's a very simply solution to this issue.

](*,) 

If you're in the 'Documentation' pane (click the little blue book on the right side of the app), right-click in the empty space below the list of documentations, and click the only context-menu item that comes up - 'Download Documentation'.

It's pretty much that simple. A small dialog comes up that shows the documentations available, and you select one. It'll warn you that the documentation you're downloading isn't signed or verified or some such thing, you tell it to shush and just download the stuffs, and it does it. Done and done.

Hopefully this will massively simplify the process for anyone else having this issue.

---

### Post by jobezone on 2006-12-18
> **Robgould said:**
> The docbook is there and that part works fine, but there should also be a file for html, one for php, and one for css.  I don't understand why these folders are not there.  If anyone has these on their computer and would like to share, that would be great.  

Anone have any more ideas?

After installing the html-reference i mentioned, since it is all documentation, you would (maybe) find it at /usr/share/doc/html-reference (or a similar directory).

offtopic: Like the smaller fonts at ubuntuforums.

---

