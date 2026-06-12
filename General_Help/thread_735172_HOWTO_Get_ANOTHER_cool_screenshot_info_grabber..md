---
title: "HOWTO: Get ANOTHER cool screenshot info grabber."
date: 2008-03-25
forum: General Help
---

### Post by Chokkan on 2008-03-25
After having messed around with this script I found [**a great pre-existing thread**]("http://ubuntuforums.org/showthread.php?t=571499") which has a script that is pretty much the same.:( I didn't want to waste all my effort and I was so proud of myself, so I bring you my own humble offering.

Basically, this script will probe your system for info that people generally want to know about when you post a screenshot. It'll then print out that info, along with a spiffy logo, take a screenshot, put it in a folder of your choosing and then make you a cup of tea.......OK it can't do that but it's still cool.

Here's what you need to do:
[LIST=1]
[*]apt-get install scrot *you need this to take the screenshots*
[*]Download the script and put it in your home folder. *does it have to be here? Is there a better place?* 
[*]Read the rest of this post and make any edits you need to the script
[*]Execute the script
```
perl ssinfo.pl
```
[/LIST]

The script which I have based this one on came from the same [**Archlinux thread**]("http://bbs.archlinux.org/viewtopic.php?id=24208&p=1") linked to in the other thread on these forums. What I know about Perl scripts I've learned in the past two days while figuring out what this script does and how it does it. There are a few scripts there but I felt this was easiest for me to understand. I then added some extra bits to the script such as getting info about wallpaper and cursor themes. I also added quite a few more logos (boy was that fun). Kubuntu logo is proving tough and is unavailable at the moment.

I only have access to Ubuntu running Gnome, and Xubuntu and therefore can't attest to how well my additions will work on other flavours. Please post your feedback here and if you are a skilled Perl master please let me know how this script could be improved.

I noticed that there were so many versions of this script that it soon got very confusing. If possible I'd like to avoid too many forks here and maybe we can come up with a script to suit as many people as possible.

**_THINGS YOU (MIGHT) NEED TO EDIT_**
By default the script is set up for Ubuntu but it also supports other distros. You'll need to change the script according to the distro you use, otherwise you'll get the wrong logo.

Other variables are in the Config Options section and are commented so they are easy to understand even for non-experts like me.

If the layout looks bad then try resizing your terminal window to make more room.

Enjoy!

---

