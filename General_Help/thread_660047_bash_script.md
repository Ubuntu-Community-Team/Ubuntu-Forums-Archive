---
title: "bash script"
date: 2008-01-06
forum: General Help
---

### Post by ingo on 2008-01-06
Hi, 

I want to try to write a bash script which adds a couple of repositories to /etc/apt/sources.list 

I know it easily done with vi or what have you, but I'd like to know how to edit/replace files via a script.

Any gurus out there?

:popcorn:

---

### Post by bodhi.zazen on 2008-01-06
In general look at sed to edit a file and echo to add a line

echo "repo" >> /etc/apt/soures.lst

Question is where are you going to get the name of the repo from ?

You can use read to input text, or look at something like zenity if you want a gui.

I suggest you use # to inactivate a repo and remove the # to activate it. This would be very easy with sed.

---

### Post by ingo on 2008-01-06
> **bodhi.zazen said:**
> Question is where are you going to get the name of the repo from ?That is easy if I understand you right - I just put it in the bash script myself. This way it is obviously 'static', but that is exactly what I am after.

How about replacing a file though? Mind, no need if I can comment a line out. Had a quick look at sed but I reckon I have to try it out to understand it. Will do so after having sent this post off :)

---

### Post by bodhi.zazen on 2008-01-06
> **ingo said:**
> That is easy if I understand you right - I just put it in the bash script myself. This way it is obviously 'static', but that is exactly what I am after.

How about replacing a file though? Mind, no need if I can comment a line out. Had a quick look at sed but I reckon I have to try it out to understand it. Will do so after having sent this post off :)

1. make a back up first (in you script, use a conditional to check for the presence of a back up file if none, backup).

2. sed will replace your file.

sed -i -e 's_xxx_yyy_g' /etc/apt/sources.list

---

### Post by ingo on 2008-01-07
Great hint, cheers! In addition, here is a great introduction to sed:

[http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

However, using sed throws up another question - what is the path of the file that is to replace the old sources.list? Can that be hidden in the bash script somewhere? Or is the best solution to put the script in its own folder on a stick and have subfolders which contain relevant files so that their paths remain constant?

---

### Post by bodhi.zazen on 2008-01-07
Well, bash scripts are supposed to make life easier, automate repetitive or complex tasks.

Perhaps post your script to give me a better idea of what you are trying to do exactly.

My advice is you save the script in ~/bin

With sed you edit the /etc/apt/sources.list directly

Or you can create a number of alternate soruces.list

I would put them in /etc/apt

sources.list.default
sources.list.enabled

Then in your script use cp

DEFAULT="/etc/apt/sources.list.default"
ENABLED="/etc/apt/sources.list.enabled"
REPO="/etc/apt/sources.list"

cp -f $ENABLED $REPO

Or

cp -f $DEFAULT $REPO

This would be a snap with zenity to give you a list, default or enabled ...

HTH

---

### Post by yabbadabbadont on 2008-01-07
Isn't there an /etc/apt/sources.list.d directory in which you can place additional sources?  Just put each different source into its own file with a unique name.  Then copy or remove them from the /etc/apt/sources.list.d directory and update, to enable or disable them.

---

