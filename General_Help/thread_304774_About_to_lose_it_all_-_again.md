---
title: "About to lose it all - again"
date: 2006-11-22
forum: General Help
---

### Post by John Murphy on 2006-11-22
Please someone Help!

I have been down this road before with Dapper where it may have been this exact same problem or a hardware problem that ultimately mottally wounded said Duck!

Now running Edgy without any real problem other than non-functioning media players (80% of the time) I tried to install Maya 7 which I previously got running under Dapper. I tired to do so from .deb's I compiled and saved previously using Alien. All seemed fine until - no Maya!!!

This can have happened with any program - as borne out by the previous situation with dapper.I have tried reinstalling the packages - even removing them as there s no uninstaller as such. I tried googling but nothing. 

The problem now lies in that whether it be through the terminal, add/remove or the Synaptic Packet manage I can do nothing! I cannot download or install updates, I cannot even open the add/remove programs as it crashes all the time telling me it needs to reinstall awcommon but it cannot find the package - even though it's right there in the same install folder as before!

The more I use linux the more I have to agree with the doubters, The switch to Mac was a breeze and there's no such problem when it comnes to adding or removing programs.

Linux is 'different' as luinux users like to state. It's different alright!!! How can you keep an installation up long enough to get all the media players properly installed (codecs and all) so that it will play streaming content and downloads properly without all the errors and player conflicts?

And how can you install a program like Maya for example withoout the fear or need for a reformat and fresh install of Ubuntu immediately afterwards?

Right now I'm scared to restart the machine as experience tells me there's a fsk coming and shortly thereafter a rightly destroyed installation.

If I sound negative, don't worry about it! I've been here before and this is Reality - not negativity!!!

Please Help!

[I]
This is another dying breath of a now almost totally disillusioned Linux Convert[/I]

---

### Post by renzokuken on 2006-11-22
> Linux is 'different' as luinux users like to state. It's different alright!!! How can you keep an installation up long enough to get all the media players properly installed (codecs and all) so that it will play streaming content and downloads properly without all the errors and player conflicts?

i have about 6 or 7 media players all running perfectly on my box, never conflicted or crashed in the year since my last install, no idea what you've done.

---

### Post by meng on 2006-11-22
Sounds like you're trying to do something quite unconventional for Ubuntu. Not that there's anything wrong with that, you're free to do what you want, just don't be surprised if it breaks!

alien is not a perfect tool for creating .debs, on top of that you created a .deb that worked in Dapper and you expect it to work in Edgy. Then you talk about not being able to uninstall it, I'm not sure what you mean by that, as "dpkg -r" and "dpkg -P" are commands specifically for removing/purging installed packages. I don't know what awcommon is, so I can't comment on that.

Then you talk about fsck destroying your install. Again, I don't know what you're talking about. fsck runs every 30 mounts (or so, depends on partition size and setting) to check on integrity (or something) as a routine maintenance procedure.

All that said, it's not my job (or anyone else's) to convince you to use an OS that's not working for you. Some users misinterpret that as snobbery, but I call it realism.

---

### Post by mssever on 2006-11-22
I dont know anything about Maya, but I do my best to avoid rpm packages, as thats where Ive experienced significant system breakage. The main reason I use Ubuntu instead of Fedora is for this reason. If a particular program isnt available from the repositories or as a .deb, I think twice before installing it.

That said, it would be helpful to know what steps you took so we can perhaps spot the problem. Also, it is important to know the specific error messages you get. And the command line tools are ideal for troubleshooting.

Something is wierd, because installing a program shouldnt break your system. Ive never had such a thing happen to me in eight years of using Linux.

---

### Post by krismatth3 on 2006-11-22
I also have no problems with any of my media players or any system stability, so I must question your statement "I've been here before and this is Reality".

---

### Post by John Murphy on 2006-11-22
> **renzokuken said:**
> i have about 6 or 7 media players all running perfectly on my box, never conflicted or crashed in the year since my last install, no idea what you've done.

Take a look at this post - I think it says it all! And try too to see if you can view the content on the digital tutors site! You CAN do this in Mac or Doze without any of this hassle. Good for you that you have them all up and running, maybe you could share the knowledge then!

[http://ubuntuforums.org/showthread.php?t=301807](http://ubuntuforums.org/showthread.php?t=301807)

And why 7 players? Mac does it all with 3!!!! In this sense Linux is even worse that Windows!

---

### Post by John Murphy on 2006-11-22
> **meng said:**
> Sounds like you're trying to do something quite unconventional for Ubuntu. Not that there's anything wrong with that, you're free to do what you want, just don't be surprised if it breaks!

Like I said these are the same debs created previously on Dapper and they installed perfectly. I followed the same routine on edgy and it's messed up the installation


> All that said, it's not my job (or anyone else's) to convince you to use an OS that's not working for you. Some users misinterpret that as snobbery, but I call it realism.

Funny, Bill Gates tried to do just that - for 15 years!!!!

---

### Post by John Murphy on 2006-11-22
> **mssever said:**
> 

That said, it would be helpful to know what steps you took so we can perhaps spot the problem. Also, it is important to know the specific error messages you get. And the command line tools are ideal for troubleshooting.

Something is wierd, because installing a program shouldnt break your system. Ive never had such a thing happen to me in eight years of using Linux.

Here is the initial URL for the instal from way back:

[http://ubuntuforums.org/showthread.php?t=66859](http://ubuntuforums.org/showthread.php?t=66859)

This time around howeve I only needed to physically install the debs.

I installed AWCommon-Server then AW Common and Maya exactly as detailed but alas no maya in command line, An error. I then decided to try removing it and reinstalling it and that is when I got the could not find packet message. It installed, or it would not have given me the option to reinstall it - right??? At any length this has com[pletely broken add/remove programs, synaptic managaer and any such similar functions in the terminal. I never had hassles like this with windoze and though [I only got my Mac a month ago I love the simplicity - most of the time you just drag the app to the thrash and say 'adios' and maybe delete one or two Library Entries. Why does linux decide to wipe you out if the install goes bad. 

As for the fsdk - I was met by this on the previos dapper install just before it's death and [prior to that on SuSe which I hated. Ubuntu looked to have some measure of promise with Dapper but that installation only lasted 3 days before the GUI literally 'melted' before my eyes and wanted to start in whatever language it decided fit!

---

### Post by renzokuken on 2006-11-22
> **John Murphy said:**
> Take a look at this post - I think it says it all! And try too to see if you can view the content on the digital tutors site! You CAN do this in Mac or Doze without any of this hassle. Good for you that you have them all up and running, maybe you could share the knowledge then!

[http://ubuntuforums.org/showthread.php?t=301807](http://ubuntuforums.org/showthread.php?t=301807)

And why 7 players? Mac does it all with 3!!!! In this sense Linux is even worse that Windows!

i have seven because i like to try out various players, they all have slightly different layouts/functions and i am more comfortable with some than others, i have three video players and four mp3 players. they were all simple to install, all through synaptic possibly except for exaile, but that doesnt give any errors either.

the only thing that doesnt work is streaming video on the bbc website, but i have never tried to get that working.

i dont see what your gripe is.

Linux is free, its not perfect, but Windows and Tiger u have to pay for so they should be better really, even though i beleive my ubuntu installation is a thousand times more stable and better configured than my XP install is and ever will be

---

### Post by mssever on 2006-11-22
> **John Murphy said:**
> I installed AWCommon-Server then AW Common and Maya exactly as detailed but alas no maya in command line, An error. I then decided to try removing it and reinstalling it and that is when I got the could not find packet message. It installed, or it would not have given me the option to reinstall it - right??? At any length this has com[pletely broken add/remove programs, synaptic managaer and any such similar functions in the terminal. I never had hassles like this with windoze and though [I only got my Mac a month ago I love the simplicity - most of the time you just drag the app to the thrash and say 'adios' and maybe delete one or two Library Entries. Why does linux decide to wipe you out if the install goes bad.
The way Im understanding you, its pretty much impossible for the breakage you described to occur. Yet it happened. So Im obviously missing something. Thats why I asked for details. Without those details, Id have to either be a mind reader or make a lucky guess to figure out the problem.

What steps did you take, exactly. A copy and paste from the terminal would be great.
>  As for the fsdk - I was met by this on the previos dapper install just before it's death and [prior to that on SuSe which I hated. Ubuntu looked to have some measure of promise with Dapper but that installation only lasted 3 days before the GUI literally 'melted' before my eyes and wanted to start in whatever language it decided fit!

fsck is merely a disk check utility. It is completely unrelated to losing X or Gnome or whatever you lost.

By the way, Ive had problems with media in Edgy, which is one reason I havent upgraded my main machine. Remember, its called edgy for a reason. Its a bit unstable and was never intended to be as stable as Dapper.

---

### Post by kiaran on 2007-05-21
I am having the same problem with the awcommon package. My apt-get and synaptic package managers are completely broken. This is so frustrating!

Running this:

*sudo dpkg --purge awcommon*

Returns:
[I]
dpkg: error processing awcommon (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 awcommon[/I]

I've also tried:

[I]sudo dpkg --remove awcommon
sudo apt-get remove awcommon
sudo apt-get autoremove awcommon[/I]

Can anybody help us find a way to remove this cursed package so I can get my package managers working again?

---

### Post by ragingmon on 2007-05-29
I removed awcommon following this link >> [http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it](http://blog.tremend.ro/2006/08/10/the-package-jedit-needs-to-be-reinstalled-but-i-cant-find-an-archive-for-it)

read on the comments, especially the comment of chas.

hope it helps

---

