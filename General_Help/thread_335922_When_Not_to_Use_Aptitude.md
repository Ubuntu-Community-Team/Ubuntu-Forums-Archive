---
title: "When Not to Use Aptitude?"
date: 2007-01-10
forum: General Help
---

### Post by esaym on 2007-01-10
Everyone says to use aptitude but I would like to know when I shouldn't use it and use apt instead.  Or is it always totally compatible?

---

### Post by rioghal on 2007-01-10
I have been running Ubuntu Dapper for three months using aptitude for all package management tasks, never used apt-get, and everything is great.

---

### Post by dcstar on 2007-01-10
> **esaym said:**
> Everyone says to use aptitude but I would like to know when I shouldn't use it and use apt instead.  Or is it always totally compatible?

"Everyone"??, there is a perfectly good GUI tool called Synaptic which most - if not all - users should be using for package management (unless you are running a server without an X system).

Aptitude and Synaptic exist to make working with the arcane command line Apt system easier, why people don't take advantage of the tools that make life easier (for the vast majority of users) constantly baffles me.

---

### Post by bodhi.zazen on 2007-01-11
IMO use aptitude

See this thread for some info:

[http://ubuntuforums.org/showthread.php?t=3773](http://ubuntuforums.org/showthread.php?t=3773)

---

### Post by superm1 on 2007-01-11
> **bodhi.zazen said:**
> IMO use aptitude

See this thread for some info:

[http://ubuntuforums.org/showthread.php?t=3773](http://ubuntuforums.org/showthread.php?t=3773)
I have had aptitude resolve more dependencies than it should during a package install.  
Try installing a command line system.
Now do apt-get install mythtv-frontend.
Compare with aptitude install mythtv-frontend. 

It will at least 100mb difference in the result of packages installed.

---

### Post by bionnaki on 2007-01-11
apt-get works just fine
particularly now with auto-remove

aptitude is fine and so is apt-get

---

### Post by po0f on 2007-01-11
bodhi.zazen,

I fail to see the relevance between the link you posted and whether or not aptitude should be used for package management.  (Hint: the thread is over two years old and deals with random crashes, just FYI.  ;))

---

### Post by rioghal on 2007-01-11
> **dcstar said:**
> "Everyone"??, there is a perfectly good GUI tool called Synaptic which most - if not all - users should be using for package management (unless you are running a server without an X system).

Aptitude and Synaptic exist to make working with the arcane command line Apt system easier, why people don't take advantage of the tools that make life easier (for the vast majority of users) constantly baffles me.

"sudo aptitude purge appname" will remove the app AND all it's deps and config files, so long as those deps are no longer used by any other app. I don't think uninstalling an app via Synaptic will remove the app as well as all its deps and config files that are no longer used by other apps. This is one reason I stopped using Synaptic and switched to aptitude.

---

### Post by bodhi.zazen on 2007-01-11
> **po0f said:**
> bodhi.zazen,

I fail to see the relevance between the link you posted and whether or not aptitude should be used for package management.  (Hint: the thread is over two years old and deals with random crashes, just FYI.  ;))

Ouch, I hate it when that happens. #-o

 It should have been a link discussing the issue ....

Let me look again ...

To ALL: Whoa .... Lets not start WW3.

both apt-get and aptitude are fine tools. Please explain WHY you prefer one over another ...

I prefer aptitude not at the time of installation but rather at the time of package removal. Aptitude has worked better for me removing packages if they were installed with aptitude.

Oh and here is that link:

[http://www.ubuntuforums.org/showthread.php?t=294135](http://www.ubuntuforums.org/showthread.php?t=294135)

---

### Post by aysiu on 2007-01-11
> **bionnaki said:**
> apt-get works just fine
particularly now with auto-remove

aptitude is fine and so is apt-get Just to clarify, "now" means "as of Edgy Eft."

---

### Post by rioghal on 2007-01-11
> **aysiu said:**
> Just to clarify, "now" means "as of Edgy Eft."

Ah, yes, good point.

---

### Post by po0f on 2007-01-11
[quote=aysiu]Just to clarify, "now" means "as of Edgy Eft."[/quote]

For the week I used Dapper before moving on to beta Edgy, I learned to use aptitude and never looked back.  :)

BTW, another "yea" for aptitude.

---

### Post by Titus A Duxass on 2007-01-11
> Aptitude and Synaptic exist to make working with the arcane command line Apt system easier, - What a load of tosh!

For a start aptitude is a command line tool, secondly the command line is not arcane.

I also agree with SuperM1 that aptitude installs far too much compared to apt.

Try following the MythTV install using aptitude and not apt-get, you get truck loads of extra guff instead of a slim install.

---

### Post by superm1 on 2007-01-11
> **bionnaki said:**
> apt-get works just fine
particularly now with auto-remove

aptitude is fine and so is apt-get
Second this - 
Aptitude will automatically remove dependencies for you, but this same functionality is available in both Synaptic as well as apt-get.

Synaptic has a section for "Autoremovable"
apt-get has an "autoremove" parameter that can be used.  If you want to take out configuration files with it, add --purge on your removal.

---

### Post by konst88 on 2007-01-11
I would like to explain why aptitude installs more packages then apt-get.
Aptitude treats recomended packages, as dependencies, and this is the reason it installs automaticaly both dependencies, and recomnded.
And aptitude has better dependency resolving system.

---

### Post by Jongi on 2007-01-11
I have a great liking for aptitude

---

### Post by rioghal on 2007-01-11
> **konst88 said:**
> I would like to explain why aptitude installs more packages then apt-get.
Aptitude treats recomended packages, as dependencies, and this is the reason it installs automaticaly both dependencies, and recomnded.

You can make aptitude not install recommended package automatically by changing one setting in aptitude. Open aptitude, go to Options -> Dependency Handling and uncheck "Install recommended package automatically".

---

