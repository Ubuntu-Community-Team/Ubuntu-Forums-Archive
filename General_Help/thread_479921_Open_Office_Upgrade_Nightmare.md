---
title: "Open Office Upgrade Nightmare"
date: 2007-06-20
forum: General Help
---

### Post by Gyatak on 2007-06-20
I've just wasted hours trying to upgrade Open Office on Feisty, hoping that the bug fixes in 2.2.1 will eliminate some of the major obstacles I've had to getting OO Calc to perform relatively simple tricks--which happen to be mission critical for my project.

The only OOo 2.2.1 download/upgrade I can find is from the OOo site--and they're all in RPM files--doesn't work on Kubuntu/Ubuntu.

Much help exists telling you to download Alien to convert these to DEB files, but I can't install alien because of missing package dependencies.

I finally decided the culprit was the missing libmysqlclient12, which doesn't exist in any of the *copious* repositories I've installed. WHERE DO YOU GET THIS?

I don't really know if it's worth it in the end. I'm just trying to get OO Calc to perform a table lookup correctly on several rows of data, and it doesn't seem to re-set itself between rows. Between this and a lot of missing functionality/customizability in the chart tools, I've about had it with OOo. I really hate supporting Microsoft's monopoly on people's minds, but this is starting to affect my ability to conduct business.

Also, why is it that you can't find a decent text editor in Linux that will do multi-line search and replace. This is stupid.

If anyone has any suggestions, I'd appreciate it.

---

### Post by raja on 2007-06-20
> **Gyatak said:**
>  some of the major obstacles I've had to getting OO Calc to perform relatively simple tricks--which happen to be mission critical for my project.

Have you tried gnumeric ?

> but I can't install alien because of missing package dependencies.

Was this when you were installing it with the package manager?

> Also, why is it that you can't find a decent text editor in Linux that will do multi-line search and replace.

I dont understand exactly what functionality you are looking for here - with the profusion of text editors available, there is no way you will miss anything.

---

### Post by Gyatak on 2007-06-21
> **raja said:**
> > RE: not being able to get OOo Calc to do some basic tricks Have you tried gnumeric ?

No, and I'd like to try it, but it seems to have a dependency on libmysqlclient12, which I can't find anywhere (see below).

Here are the problems I have had with OOo Calc:

[LIST=1]
[*]The chart features don't allow you enough control over which data is displayed on the chart itself.
[*]The lookup function fails to reset itself when it is applied on several rows of data. For example, I have a long list of clients and their area codes and a separate list relating the area codes to cities. Funny things happen when I create a column of lookups to show which cities the clients live in.
[*]There are also buggy things like when you use autofilter to select noncontiguous rows that match certain criteria and try to paste into a selected range spanning multiple rows, it pastes into the rows you filtered out as well.
[/LIST]

> [QUOTE]but I can't install alien because of missing package dependencies.Was this when you were installing it with the package manager?[/QUOTE]
I was using apt-get, and here's what it told me:
[INDENT]The following packages have unmet dependencies:
  alien: Depends: debhelper (>= 3) but it is not going to be installed
         Depends: rpm (>= 2.4.4-2) but it is not going to be installed
         Depends: dpkg-dev but it is not going to be installed
  pluto-sqlcvs: Depends: libmysqlclient12 but it is not installable[/INDENT]

I figured step one was to get libmysqlclint12, which these others seem to depend on, but I can't find it anywhere. I even found the site for it on sourceforge, but the download link had disappeared.

> [QUOTE]Also, why is it that you can't find a decent text editor in Linux that will do multi-line search and replace.
I dont understand exactly what functionality you are looking for here - with the profusion of text editors available, there is no way you will miss anything.
I dont understand exactly what functionality you are looking for here - with the profusion of text editors available, there is no way you will miss anything.[/QUOTE]

The main thing I'm looking for is the ability to do fully-functional regex replaces on data that spans more than one line. I've used text editors in Windows and on Mac that do this, but for some reason this functionality is strangely missing from Kate's features--and any other text editors I've found for Kubuntu. 

Thanks for your response, Raja. Do you have any recommendations?

---

### Post by stchman on 2007-06-21
> **Gyatak said:**
> I've just wasted hours trying to upgrade Open Office on Feisty, hoping that the bug fixes in 2.2.1 will eliminate some of the major obstacles I've had to getting OO Calc to perform relatively simple tricks--which happen to be mission critical for my project.

The only OOo 2.2.1 download/upgrade I can find is from the OOo site--and they're all in RPM files--doesn't work on Kubuntu/Ubuntu.

Much help exists telling you to download Alien to convert these to DEB files, but I can't install alien because of missing package dependencies.

I finally decided the culprit was the missing libmysqlclient12, which doesn't exist in any of the *copious* repositories I've installed. WHERE DO YOU GET THIS?

I don't really know if it's worth it in the end. I'm just trying to get OO Calc to perform a table lookup correctly on several rows of data, and it doesn't seem to re-set itself between rows. Between this and a lot of missing functionality/customizability in the chart tools, I've about had it with OOo. I really hate supporting Microsoft's monopoly on people's minds, but this is starting to affect my ability to conduct business.

Also, why is it that you can't find a decent text editor in Linux that will do multi-line search and replace. This is stupid.

If anyone has any suggestions, I'd appreciate it.

Make sure the universe, multiverse, main and restricted enabled.  Then type:

sudo apt-get install alien

Follow this procedure here:

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

Just substitute the 2.2.1 for 2.2.

Hope it helps.

---

### Post by Gyatak on 2007-06-22
> **stchman said:**
> Make sure the universe, multiverse, main and restricted enabled.  Then type:

sudo apt-get install alien

Follow this procedure here:

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

Just substitute the 2.2.1 for 2.2.

Hope it helps.

Thanks. Apparently I had a corrupt pluto(?) package installed, and when I fixed it alien installed correctly, with all of its needed dependencies.

Thanks for the site. That was helpful. I think I'm on my way to getting it installed now.

---

