---
title: "Does Linux (Ubuntu) have install packages for apps?"
date: 2007-03-24
forum: General Help
---

### Post by linuxmonkey on 2007-03-24
I'm new to the linux world.  I plan on installing Ubuntu and dual booting from Windows.  I've read some good things about GnuCash.  I also saw that its not easy to install.  Since I'm new to Linux, why don't applications have automatic installs like OSX or Windows?  I found this thread on getting [GnuCash onto Ubuntu]("http://www.linuxmint.com/forum/viewtopic.php?t=1283"), and it looks like some people have issues.

Does all software require terminal commands and long process (compiling, etc) to install onto Ubuntu?  (I may open up a new thread asking this question)

[http://www.linuxmint.com/forum/viewtopic.php?t=1283](http://www.linuxmint.com/forum/viewtopic.php?t=1283)

---

### Post by stokedfish on 2007-03-24
1. When there's a deb file, ubuntu software is *very* easy to install
2. When there's only a source file, it's a bit harder, but still doable

And there's GUIs for it of course, adept, synaptic, kpackage, etc.

---

### Post by llamakc on 2007-03-24
After you have installed you would use one of the package management tools to simply install the package gnucash.

In a terminal this is as simple as:

sudo apt-get install gnucash

and you'd be done.

If you want the latest and "greatest" of anything, you'll end up compiling it from source. To answer your question: NO, all software does not require that.

---

### Post by stokedfish on 2007-03-24
> **llamakc said:**
> After you have installed you would use one of the package management tools to simply install the package gnucash.

In a terminal this is as simple as:

sudo apt-get install gnucash

and you'd be done.
```
fish@fishbook:~$ sudo apt-get install gnucash
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnucash: Depends: libgtkhtml3.8-15 (>= 3.13.6) but it is not installable
E: Broken packages
```
Hahaha...  ;)

---

### Post by llamakc on 2007-03-24
> **stokedfish said:**
> ```
fish@fishbook:~$ sudo apt-get install gnucash
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnucash: Depends: libgtkhtml3.8-15 (>= 3.13.6) but it is not installable
E: Broken packages
```Hahaha...  ;)

What's funny? Are you on Edgy? Do you have "universe" enabled? Did you run an `apt-get update` before attempting to install?

I JUST installed it as a proof of concept on an Edgy box with universe|multiverse|backports enabled. 

Works just fine.

---

### Post by stokedfish on 2007-03-25
No, I'm on Feisty Beta, and yes, Universe is enabled.

---

### Post by Ramses de Norre on 2007-03-25
Edgy:```
ramses@icarus:~$ apt-cache policy gnucash
gnucash:
  Installed: (none)
  Candidate: 2.0.1-3ubuntu3
  Version table:
     2.0.1-3ubuntu3 0
        500 http://archive.ubuntu.com edgy/universe Packages

```Feisty:```
ramses@icarus:~$ apt-cache policy gnucash
gnucash:
  Installed: (none)
  Candidate: 2.0.2-3ubuntu1
  Version table:
     2.0.2-3ubuntu1 0
        500 http://archive.ubuntu.com feisty/universe Packages

```

You might need to check your sources.list file...

To the OP: don't mind all this command line stuff, you can use graphical installers as well if you feel more comfortable with that. They work flawlessly and are perfectly integrated in the OS.

---

### Post by linuxmonkey on 2007-03-25
> **Ramses de Norre said:**
> 

To the OP: don't mind all this command line stuff, you can use graphical installers as well if you feel more comfortable with that. They work flawlessly and are perfectly integrated in the OS.

Is there a good begineers guide to Linux terms ?  I'm not sure what some of the terms used in this thread.

Like:

- Do you have "universe" enabled? 

- Did you run an `apt-get update` before attempting to install?

- universe|multiverse|backports enabled.

---

### Post by jeffathehutt on 2007-03-25
Your system comes with some documentation, just go to the menu - System->Help->System Documentation and it should give you the basics.

Universe, multiverse, and backports all refer to software repositories.  Think of them as collections of software for Ubuntu.  For instance, some programs are in the 'main' repository, which comes enabled by default.  Other software may be included in the universe repository, which is not enabled by default.  If it is not enabled, you cannot install software from there.

'apt-get update' is used to update the list of packages available, so you should type 'sudo apt-get update' into the terminal before you install software.  If you don't issue that command, you may not be installing the latest version of the software.

---

### Post by daz4126 on 2007-03-25
You might find the graphical front-ends easier to use.

Go to the system menu and select administration -> software sources
The Ubuntu tab shows a list of tick boxes with the various repositories (see jeffathehutts explanation above). If you're not bothered about restrictive licenses and stuff like that, go ahead and tick them all.

The other tabs allow you to set other preferences too. You might need the 3rd party tab in the future if you try to install some software that is not in the Ubuntu repos.

Now go back to the system menu and select administration -> Synaptic Package Manager
This should allow you to search for any program in the repos that you have enabled. You can either browse by category or simply enter a name to search by. I found gnucash this way. Clicking on the box next to a program gives you a list of things you can do. Select 'install' then click on 'update'. That last bit is important as changes don't take effect until you press update. You can also use synaptic to uninstall programs.

Don't worry - I thought exactly the same as you when I first started using ubuntu, but now think that synaptic is the best thing ever - it takes care of updates and everything. When you find a program you like the first thing to do is check if it is in the repos (by searching in Synaptic) it usually will be if it is any good. If it isn't then the next best option is to search for a .deb file. If you click on these in Firfox, Ubuntu has a built-in installer program for them. The last resort is to install from source which hardly ever happens - if you need to do this do a search online or come back to these fourms to ask for help.

Hope that helps you out,

DAZ

---

### Post by linuxmonkey on 2007-03-25
> **daz4126 said:**
> You might find the graphical front-ends easier to use.

Go to the system menu and select administration -> software sources
The Ubuntu tab shows a list of tick boxes with the various repositories (see jeffathehutts explanation above). If you're not bothered about restrictive licenses and stuff like that, go ahead and tick them all.

The other tabs allow you to set other preferences too. You might need the 3rd party tab in the future if you try to install some software that is not in the Ubuntu repos.

Now go back to the system menu and select administration -> Synaptic Package Manager
This should allow you to search for any program in the repos that you have enabled. You can either browse by category or simply enter a name to search by. I found gnucash this way. Clicking on the box next to a program gives you a list of things you can do. Select 'install' then click on 'update'. That last bit is important as changes don't take effect until you press update. You can also use synaptic to uninstall programs.

Don't worry - I thought exactly the same as you when I first started using ubuntu, but now think that synaptic is the best thing ever - it takes care of updates and everything. When you find a program you like the first thing to do is check if it is in the repos (by searching in Synaptic) it usually will be if it is any good. If it isn't then the next best option is to search for a .deb file. If you click on these in Firfox, Ubuntu has a built-in installer program for them. The last resort is to install from source which hardly ever happens - if you need to do this do a search online or come back to these fourms to ask for help.

Hope that helps you out,

DAZ

Thanks for the explanation.  Who controls what programs show up on the repose?  Is it safe to say that any program on the repo sites are m safe, and virus/malware free?

---

### Post by daz4126 on 2007-03-26
Well, you don't need to worry about viruses as much when using Linux (most viruses are spread by sharing files with a windows machine). I would suspect that the files in the repositories are clean. I think that they are maintained by Ubuntu so should be trustworthyIf you add any 3rd party repos you should probably check those out.

DAZ

---

### Post by Ramses de Norre on 2007-03-26
All official repos are maintained by the same people that maintain your OS, so yes, they are safe.
Watch out with third party repos, most are safe but there is no control for them.

---

