---
title: "Cannot find package for Eclipse PDT (nor DLTK)"
date: 2016-10-10
forum: General Help
---

### Post by aajax on 2016-10-10
I just completed the installation of a new Ubuntu 16.04.1 system which I WAS intending to use for development, which starts with an IDE.  My initial project is a PHP application.  However, what I've found is that -

[LIST]
[*]When I install Eclipse I get a lot of related stuff installed but still lacking PHP capability.
[*]While there are lots of Ubuntu packages that pertain to Eclipse it is near impossible to tell anything about what they do from [packages.ubuntu.com]("http://packages.ubuntu.com").
[*]Research at [eclipse.org]("http://eclipse.org") makes it look like what I need is a plugin called PHP Development Tools (PDT).
[*]Based on parsing of package names it appears that Ubuntu does NOT include the PDT package.
[*]When I try and install from the Help menu of the installed Eclipse platform I get an error saying I don't have a dependent package called Dynamic Language Tool Kit (DLTK).
[*]Based on parsing of package names it appears that Ubuntu does NOT include the DLTK package.
[/LIST]

I was hoping to get some help in determining the intention of Ubuntu when it comes to Eclipse.  It is beginning to appear as though trying to use Eclipse on Ubuntu may be a bad idea.  My assumption has been that by relying on packages supplied by Ubuntu I had a better chance of avoiding problems with incompatibility, which argues against trying to install packages from [eclipse.org]("http://eclipse.org").

If someone could explain what I should be looking for that would be much appreciated.

---

### Post by gde061-www on 2016-10-11
Alright, so in the interest of disclosure, I have used Eclipse all of once a year ago, but it did involve adding a package for DocBook, so your question made me try to remember how I did it.  It went something like this:

First, you would add the location where DLTK is that you need for your version to the "Available Software Sites" which is under Window-Preferences in my version of Eclipse (Mars).  I would consult his page [http://www.eclipse.org/dltk/install.php](http://www.eclipse.org/dltk/install.php)  to find the correct source... it sound like one for NEON should already be in there, but maybe you are on a different version of Eclipse.  Just dig around till you find the host repository.  I'm not an expert, but from what I can tell, some are on "Sourceforge" some on "Git".... it's all greek to me... maybe somebody can explain what that means with a comment for my benefit as well.

Then you would go to the help menu where the "Install New Software" item is listed, and select under the source, the library you just added, scroll through the list, and you would see the DLTK.

None of this stuff is, as I understand it, anything run by Ubuntu.  Complaining that Ubuntu doesn't include these libraries is like complaining that their is no plugin for parsing LOGO in gedit included in the Ubuntu repositories.  (Can you believe though they actually have one for Fortran.  Kudos for that).  I think the preferred method for installing Eclipse was to get it directly from the eclipse site since Juno is really out of date... (at least that's still first comment that comes up in the SW Center when I just checked).   If you have Juno from the Ubuntu repository, my suggestion would be to dump that, go to the eclipse site and install Neon, which will probably give you DLTK and other stuff you might have to chase around with 3.8.

But I agree it's a little confusing... which is why I wanted to go back and try to remember how it worked.  Maybe someone with more experience than me -- and that's not a high bar to reach -- will come along and explain more details...  we'll see.

---

### Post by aajax on 2016-10-14
One of the things that I've found very exasperating with Eclipse has to do with identifying versions.  When I select Help>About on the installed/running Eclipse it says it is Version 3.8.1.  Then you go to the Eclipse websites, they seem to want to use names (i.e., Neon, Mars, Luna, etc. etc. etc) with several variations of the same base name rather than numbers to designate versions.  This tells you next to nothing when it comes to the sequence of releases.  As a result I haven't yet been able to figure out which name applies to the version I'm running.

With that said, I've more or less deduced that Ubuntu is not staying real current when it comes to Eclipse.  For something as complex as Eclipse, I was hoping to rely on Ubuntu package management to eliminate compatibility issues and update in a manner that tracks with Ubuntu updates.  I'm not a sophisticated enough of a developer to need all of the latest features so I don't feel that I need the most up to date version.  However, I don't want to start using one that is so old that there is no hope of support from Eclipse.

Thanks for the reply which somewhat confirms my own suspicions when it comes to using Eclipse on Ubuntu.  I think I'll try Netbeans where the initial indication is that the Ubuntu packaged version (8.1) is pretty close to the latest and greatest (8.2).

---

### Post by mc4man on 2016-10-14
If I was to take a guess the numbers are the 'build' numbers, seem here in ()
[http://wiki.eclipse.org/Older_Versions_Of_Eclipse](http://wiki.eclipse.org/Older_Versions_Of_Eclipse)
If so that would place the Debian/Ubuntu as pretty old, about 4 years, (3.8.1 2012) - 
[http://archive.eclipse.org/eclipse/downloads/index.php](http://archive.eclipse.org/eclipse/downloads/index.php)
What was actully added from 3.1.1-1 to 3.1.1-8 don't know, Ubuntu changelog is not too verbose

---

