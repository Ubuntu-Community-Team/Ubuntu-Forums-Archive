---
title: "what packages to install"
date: 2018-10-04
forum: General Help
---

### Post by Skaperen on 2018-10-04
if one wants to install some particular feature of Ubuntu Linux. is there a good website (besides Google) to find out which packages to install and whether a reboot is needed?

---

### Post by ajgreeny on 2018-10-04
*Thread moved to **General Help**.* which is more appropriate and a better fit as this is not a query about OS installation or upgrading.

I am not sure you will get any helpful answers either, as we have no way to know what you want to use the computer for so ask a more detailed question.

If the computer needs rebooting after installing a package (seldom except for new kernels or firmware) you will usually be told, and it will not reboot on its own; you will have to do that yourself.

---

### Post by TheFu on 2018-10-04
> **Skaperen said:**
> if one wants to install some particular feature of Ubuntu Linux. is there a good website (besides Google) to find out which packages to install and whether a reboot is needed?

I don't think of Ubuntu as having "features", since it is just a platform for other packages maintained by 3rd party project/programming teams.  

If you load up synaptic, you can browse through all the packages reading the descriptions, but they will generally say the service they provide using an industry standard name, which is very different from the naming that commercial OSes like Windows or OSX name things.  Took me way to long to figure out how to enable CIFS on OSX because they called it something else.  Same for ssh/sftp.  Stick with the standard protocols and the search in most package managers and manpages will find at least one and sometimes 10 implementations.

If you are really new to Linux, learning how Linux distros are different technically and culturally from other, commercial OSes would be a good use of your time. But seems you've been around here a long time, so that probably isn't helpful.

---

### Post by Skaperen on 2018-10-05
i'm really just looking for a good source of information about packages, such as categorizing them in groups of what someone might want to install.  Ubuntu breaks up packages so that people can install just the aspect of a package that they actually want, such as only documentation.  i don't want to focus on what it i am looking at installing; rather, i want to figure it out for myself.  then i mat come back later for my next project.

i am not new to Linux.  but things like how packages are divided up is difficult to track.  i have been using Linux since 1994, but cannot name all the distros off the top of my head.  likewise i cannot pick out all the packages i need to install for some concept purpose (the feature i referred to).  some things might be easy with just that one line description.  some not so.  for example on my current project i found a few documents that indicated a certain package was an old thing that had been replace by another thing.  but the description gave no such clue.  i am hoping for up to date information compiled into one place.

---

### Post by TheFu on 2018-10-05
Every package installed via the package management system includes a paragraph about it.  The easiest way for most people to see that is through synaptic.  Synaptic also groups the software into major areas.

Most commands will come with a manpage which will describe in detail how to do things. Sadly, GUI programs tend to reduce this or ignore the need for a manpage completely.

But perhaps the easiest answer for the specific issue today is to say what you are looking to achieve and maybe someone has an idea for how to accomplish that?

---

### Post by Skaperen on 2018-10-05
if this information comes in the form of seeing the paragraph for one package at a time based on requesting it by package name, then it will be of little help for this kind of need.  ultimately it would help if the package names are already acquired as a means finally verify that the correct packages are being installed.  an ability to search such descriptions, and limit that search to only package descriptions would be needed.  using Google for this kind of search is unlikely to be of much success unless there is a web site that Google has fully indexed that lists package descriptions and nothing else.

if i had this information and a source to keep it updated, i would make such a site along with a basic search mechanism in the hopes that Google would eventual index it.

if synaptic just shows this paragraph instead of outputting it to stdout. then i would not likely be able to scrape it to acquire the information.

it is a common problem to find things like the name of something when information source require you to already know its name in order to get the information.  this is where the value of searches come into the picture.  although things are improving in this area, search engines still don't provide a means to focus a search by concept.

i just tried synaptic:

problem 1:  the font is too small, making view a strain, and the usual means to enlarge the font while viewing (hold Ctrl while rolling the mouse roller) had no effect.  enlarging the window enlarged the display area but had no effect on font size.

problem 2:  the research i have already done has revealed a couple packages that provide older elements that are no longer needed.  these packages were included in the search (it looks like way too many packages are listed).  the descriptions did not include any recent information.  it appeared that the descriptions are as old as the package itself, from a time that the package was relevant.  but some are no longer relevant.  there should be information that tells if the package is relevant today.

---

### Post by Skaperen on 2018-10-05
what i am envisioning is a web site that has a database of packages for each of any distro/system, a database of concept topis that people could have an interest in, and a database of users that could connect packages to concepts (like tagging them) for relevancy and could vote these connections up (is relevant) or down (is not relevant). then the public could pull up a concept an see which packages they may want to install.  such a site, once there have been enough votes, could publish a repository of metapackages that follow the voted relevancy connections.

---

