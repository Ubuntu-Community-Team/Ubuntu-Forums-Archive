---
title: "How do I add a path in bash?"
date: 2007-02-22
forum: General Help
---

### Post by billdotson on 2007-02-22
I want to add this: ~/bin ($HOME/bin) 
to my Path in BASH so I can run my own scripts.  How do I add it?

---

### Post by highneko on 2007-02-22
# You can safely type this into your terminal:
printf '\nif [ -d ~/bin ]; then\n PATH="$HOME/bin:${PATH}"\nfi\n' >> .bashrc

---

### Post by llamakc on 2007-02-22
I believe the Ubuntu default ~/.bash_profile has that at the end. Uncomment these lines:

if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi


And type:

source ~/.bash_profile

You'll be good to go. You can verify by typing:

echo $PATH

---

### Post by billdotson on 2007-02-22
ok the lines were already not commented when I went in there but when I type source ~/.bash_profile it made it work.

So could you please explain what I technically just did because I would rahter not just copy and paste without knowing what I really did.

Thanks

---

### Post by billdotson on 2007-02-22
Also when I record using my DVD recorder/player the name of the vob file changes depending on how many shows I recorded.  So for instance if I had it set to record 2 shows the vob file would be movie2-1.vob.partial  

If I had only 1 it would be movie1-1.vob.partial

if I had 3 it would be movie3-1.vob.partial  and so on.  Is there a way to automate it to do it the right way no matter how many titles it has on it or do I just have to make independent scripts like vob1 for 1 title, vob2 for 2 titles, and so on?

---

### Post by llamakc on 2007-02-22
> **billdotson said:**
> ok the lines were already not commented when I went in there but when I type source ~/.bash_profile it made it work.

So could you please explain what I technically just did because I would rahter not just copy and paste without knowing what I really did.

Thanks

typing "source /path/to/file" tells BASH to import and use the settings in the file you 'sourced'. 

Is this a clean install? Have you carried over old dot-files from an earlier install or distro? Are the permissions and ownership correct?

Here's what my .bash* files look like:

```

ken@llamakc 09:58:12:~$ ls -lh .bash*
-rw-r--r-- 1 ken ken  237 2007-02-02 21:38 .bash_aliases
-rw-r--r-- 1 ken ken  218 2007-01-30 19:41 .bash_aliases~
-rw------- 1 ken ken 4.7K 2007-02-22 19:05 .bash_history
-rw-r--r-- 1 ken ken  220 2006-09-21 18:03 .bash_logout
-rw-r--r-- 1 ken ken  414 2006-09-21 18:03 .bash_profile
-rw-r--r-- 1 ken ken 2.3K 2007-01-22 15:42 .bashrc
-rw-r--r-- 1 ken ken 2.3K 2007-01-22 15:41 .bashrc~

```

---

### Post by llamakc on 2007-02-22
> **billdotson said:**
> Also when I record using my DVD recorder/player the name of the vob file changes depending on how many shows I recorded.  So for instance if I had it set to record 2 shows the vob file would be movie2-1.vob.partial  

If I had only 1 it would be movie1-1.vob.partial

if I had 3 it would be movie3-1.vob.partial  and so on.  Is there a way to automate it to do it the right way no matter how many titles it has on it or do I just have to make independent scripts like vob1 for 1 title, vob2 for 2 titles, and so on?

I understand what it IS doing. I don't understand what you mean by "the right way". Explain what it is you want as an end product.

---

### Post by billdotson on 2007-02-22
well I installed from a LiveCD but the LiveCD doesn't contain the latest kernel.  (it is an Edgy Eft LiveCD) it downloads and installs kernel 2.6.17 or something like that with update manager (or at least it did the time before this install) This is a pretty clean install.  I haven't modified anything other than the sources.list and the /etc/fstab and installed some software.

Is there a way I can automate the vob to work correctly regardless of the number of titles?

---

### Post by highneko on 2007-02-22
I read gdm isn't a login shell or something and doesn't read the .bash_profile file. Someone suggested using .bashrc instead so that's what I use. Have fun.

---

### Post by llamakc on 2007-02-22
> **highneko said:**
> I read gdm isn't a login shell or something and doesn't read the .bash_profile file. Someone suggested using .bashrc instead so that's what I use. Have fun.

This may matter for the OP. I don't use GDM and login directly to a BASH shell. OP can put those lines as highneko suggested in ~/.bashrc also and it will work just fine.

---

### Post by billdotson on 2007-02-22
well I did what you said to do highneko and I didn't really know if it did anything.  So then I did the thing llamakc said to do.  but anyway it is working regardless.  

I would really like to know if there is a way to automatically insert the title # so I don't have to use 7 different vob scripts (vob1, vob2, etc.)

---

### Post by llamakc on 2007-02-22
> **billdotson said:**
> well I installed from a LiveCD but the LiveCD doesn't contain the latest kernel.  (it is an Edgy Eft LiveCD) it downloads and installs kernel 2.6.17 or something like that with update manager (or at least it did the time before this install) This is a pretty clean install.  I haven't modified anything other than the sources.list and the /etc/fstab and installed some software.

Is there a way I can automate the vob to work correctly regardless of the number of titles?

If you are equating "work correctly" with the mannerisms of another program or expectations, please be specific. I still don't get what your question about the VOB files is. What do you want it to do?

---

### Post by llamakc on 2007-02-22
> **billdotson said:**
> well I did what you said to do highneko and I didn't really know if it did anything.  So then I did the thing llamakc said to do.  but anyway it is working regardless.  

I would really like to know if there is a way to automatically insert the title # so I don't have to use 7 different vob scripts (vob1, vob2, etc.)

What scripts have you put in ~/bin. As I read your original post I thought the two problems were separate. Are they not?

---

### Post by billdotson on 2007-02-22
see the vob command is to automatically rip and transcode the vob files on the dvd into .mpg format.  In my script the movie.vob.partial changes according to how many titles are on the DVD.  So if I set up 3 titles to record on the DVD then the movie.vob.partial file is ripped and then the video and audio are extracted from movie3-1.vob.partial.  

Depending on how many titles are on the DVD the name of the .vob.partial file changes.  1 title is movie1-1.vob.partial, 2 titles is movie2-1.vob.partial and so on.  So if I just have movie.vob.partial in the script and it doesn't specify how many titles there are by adding a number_of_titles-1 which makes the vobcopy program not able to extract the audio and video.

The command to extract the video from the vob and transcode it into .mpg format (with no # of title identifier): 

tcextract -i movie.vob.partial -t vob -x mpeg2 > movie.m2v

I currently have vob1, vob2, all the way up to vob7 so if I type vob1 it will rip and transcode the dvd to mpeg if it has one title.  If it has 2 titles I type vob2 and so on.

---

### Post by llamakc on 2007-02-23
> **billdotson said:**
> see the vob command is to automatically rip and transcode the vob files on the dvd into .mpg format.  In my script the movie.vob.partial changes according to how many titles are on the DVD.  So if I set up 3 titles to record on the DVD then the movie.vob.partial file is ripped and then the video and audio are extracted from movie3-1.vob.partial.  

Depending on how many titles are on the DVD the name of the .vob.partial file changes.  1 title is movie1-1.vob.partial, 2 titles is movie2-1.vob.partial and so on.  So if I just have movie.vob.partial in the script and it doesn't specify how many titles there are by adding a number_of_titles-1 which makes the vobcopy program not able to extract the audio and video.

The command to extract the video from the vob and transcode it into .mpg format (with no # of title identifier): 

tcextract -i movie.vob.partial -t vob -x mpeg2 > movie.m2v

I currently have vob1, vob2, all the way up to vob7 so if I type vob1 it will rip and transcode the dvd to mpeg if it has one title.  If it has 2 titles I type vob2 and so on.

I'm still confused. I understand completely what your scripts DO but I do not understand what you WANT them to do. You've mentioned "work correctly" or words to that effect.

Why not share the scripts for vob1 and vob2, and after that explain not what they do, but what you want as an end-product.

---

### Post by billdotson on 2007-02-23
well I want to combine the scripts or something of that sort so that instead of having to run a different vob script like vob1, vob2, etc. depending on the amount of titles that are on the DVD to just have a script called vob that compensates and adds the 1-1 or 2-1 or whatever is necessary.  

The scripts work fine and they do what they are supposed to do, but I want to have 1 script where I can type vob and it will rip the vob and extract it into mpeg format regardless of how many titles are on the DVD.  

So what I am asking is there a way to put a wildcard or some exception to find the file called vob.partial so I don't have to have separate vob scripts that depend on how many titles are on the DVD.   This script isn't to rip movie DVDs, it is to rip the video out of DVDs where I use my DVD recorder to record TV shows to a DVD.  So if I set up 2 shows to record on [assuming the disc is blank] then there will be 2 titles so I would have to invoke thee script vob2

Here is the script for vob1:

#!/bin/bash

vobcopy -t movie
tcextract -i movie1-1.vob.partial -t vob -x mpeg2 > movie.m2v
tcextract -i movie1-1.vob.partial -t vob -x ac3 -a 0 > movie.ac3
mplex -f 8 -o "movie%d.mpg" movie.m2v movie.ac3

See where the vob.partial file is movie1-1?  If there is one title on the DVD then vobcopy puts the number of titles and then a dash after the name movie.  The only thing that changes between vob1 and vob2 and the other vob scripts is the number directly after "movie" changes to reflect the # of titles on the DVD.

Does that make any sense?

---

### Post by ardchoille42 on 2007-02-23
> **llamakc said:**
> I believe the Ubuntu default ~/.bash_profile has that at the end. Uncomment these lines:

if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi


And type:

source ~/.bash_profile

You'll be good to go. You can verify by typing:

echo $PATH

Isn't ordering important here? If someone put a trojaned version of ls in your ~/bin, would that not be called before /bin/ls?

Isn't it better to do this?

```

if [ -d ~/bin ] ; then
    PATH="${PATH}":~/bin
fi

```

---

### Post by llamakc on 2007-02-23
> **ardchoille42 said:**
> Isn't ordering important here? If someone put a trojaned version of ls in your ~/bin, would that not be called before /bin/ls?

Isn't it better to do this?

```

if [ -d ~/bin ] ; then
    PATH="${PATH}":~/bin
fi

```

Perhaps. My quote comes directly from the .bash_profile that ships with Ubuntu.

---

### Post by galileon on 2007-06-23
> **llamakc said:**
> typing "source /path/to/file" tells BASH to import and use the settings in the file you 'sourced'. 


Hi, does that mean that source causes the settings to load rightaway, while not sourcing would make us have to wait until the next login to get them loaded? I'm just slightly confused about the source thing, and its not an easy word to google!

---

### Post by dlodge on 2008-07-18
> **billdotson said:**
> I want to add this: ~/bin ($HOME/bin) 
to my Path in BASH so I can run my own scripts.  How do I add it?
In hardy (not sure of other versions), the ~/.profile script checks for a ~/bin directory; a ~/bin directory is automatically added to the path if present.  You will need to reload the .profile file (e.g. log out and back in) to make the path active.

---

