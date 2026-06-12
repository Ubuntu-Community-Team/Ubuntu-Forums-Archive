---
title: "Variables in the Location bar in Nautilus"
date: 2005-07-08
forum: General Help
---

### Post by aburda on 2005-07-08
I used a file manager under windows that let me set shortcuts when typing in a path to a given location, for example


C:\Program files\emule\incoming

all I had to type was /emule

which would put me in the incoming directory.

Is there anyway to do something similar with nautilus, for exampe $emule and it maps it to the correct directoyr (based upon what I have set it to?)

Thanks

Aaron

---

### Post by frodon on 2005-07-08
Edit your .bashrc file in your home directory :```
cd $HOME
gedit .bashrc
```Add as many lines you want like that : ```
setenv amule /mnt/your_disk/amule/incoming
```redo a source of the file : ```
source .bashrc
```
Now you can type $amule in your file brother and will go to the directory you've specified.
Does it works ?

---

### Post by smoon on 2005-07-08
[QUOTE=frodon]Edit your .bashrc file in your home directory :```
cd $HOME
gedit .bashrc
```Add as many lines you want like that : ```
setenv amule /mnt/your_disk/amule/incoming
```redo a source of the file : ```
source .bashrc
```
Now you can type $amule in your file brother and will go to the directory you've specified.
Does it works ?[/QUOTE]

This does not work - at least not for me.

aburda, why don't you use bookmarks? They can be found in the "Places"-menu of Gnome's panel and Nautilus' menubar. You can easily edit them with `gedit ${HOME}/.gtk-bookmarks'. The GTK+-fileselector lets you edit them in a graphical manner as well. The only weird thing I just found out is that nautilus uses a different bookmarking system when in browser mode than when it operates in spatial mode... Anyone has an idea why this is so or if this is going to be fixed?

---

### Post by frodon on 2005-07-08
[QUOTE=smoon]This does not work - at least not for me.[/QUOTE]Strange ... it works perfectly with konqueror why not with nautilus ?
For sure if you type $HOME in nautilus you will go in home directory, ok i will search to know why it doesn't work.

Ok i find what's wrong, after following the steps to edit your .bashrc file you need to restart your session in order that nautilus take care of new environment variables
Now it should work without problems

Thanks for feedback

---

### Post by aburda on 2005-07-08
Hi guys,

       Frodon, I tried $HOME and even that doesn't work in Nautilus so I didn't bother trying setting my own shell variables.  This seems like a pretty dumb design flaw, it wouldn't have taken much to make the shell variables accessible.
       Smoon, the reason I don't use the bookmarks is because I try to avoid using the mouse as much as possible and I also like as few keystrokes as possible.  Through the Location bar (if variables worked) I can just press Ctrl-l and type the location I want and hit enter.  With Bookmarkts its actually about 5 keys and I have to sort through a list which consumes a lot more of my brain power.
       I'm starting to think I should ditch gnome (its a memory hog) and often I come across KDE apps I want to try.  How is Kubuntu?

             Aaron

---

### Post by frodon on 2005-07-08
[QUOTE=aburda] I'm starting to think I should ditch gnome (its a memory hog) and often I come across KDE apps I want to try.  How is Kubuntu?     Aaron[/QUOTE] Don't do such a thing !! I'am a gnome fan !
I'm not at home for the moment and i've just tested it with KDE and RedHat and all works, but in few hours (after job !) I will test that with ubuntu and gnome and see why it doen't work, that I can't do for the moment. It's not so complicated, don't move to KDE for that.

---

### Post by aburda on 2005-07-08
[QUOTE=frodon]Don't do such a thing !! I'am a gnome fan !
I'm not at home for the moment and i've just tested it with KDE and RedHat and all works, but in few hours (after job !) I will test that with ubuntu and gnome and see why it doen't work, that I can't do for the moment. It's not so complicated, don't move to KDE for that.[/QUOTE]
 Ok, Ok....I'm sticking with Gnome, I actually tried out Mandrake before I tried Ubuntu and hated it, but that was a long time ago.  There are a couple of other things I don't like about gnome so its not just this one thing and am curious if KDE would be better......all the same, if I get around to trying out Kubuntu it won't be anytime soon.

BTW, I'm certain that you can't use variables in the location bar...I've tried all of the possible different options....something to add in the next version I guess.  Although give it a shot when you get home....in case I've over looked something.

Aaron

---

### Post by frodon on 2005-07-08
[QUOTE=aburda]I'm certain that you can't use variables in the location bar..[/QUOTE]

I hope you're wrong ... because konqueror do it and i prefer gnome .....  :mad: 
If you're curious try XFCE, it look likes KDE but i find it better ... but i'm not objective.

---

### Post by aburda on 2005-07-08
I'm less interested in the appearance than I am in functionality.  One of the things I absolutely detest in gnome is the 'file open' dialog box (you can see it in Rythmbox when you press ctrl-0).  I'm not a terrible fan of gedit (I like gvim but also want tabs) and thought I might try kate.  But all in all I am fairly satisfied with gnome.  Its a total memory hog but I just invested $100 into another 512mb so there is no point in using that as a reason to switch now.

---

### Post by frodon on 2005-07-08
After many tests ..... my method works only with KDE and konqueror.
 :-x

---

### Post by smoon on 2005-07-08
[QUOTE=aburda]I'm less interested in the appearance than I am in functionality.  One of the things I absolutely detest in gnome is the 'file open' dialog box (you can see it in Rythmbox when you press ctrl-0).  I'm not a terrible fan of gedit (I like gvim but also want tabs) and thought I might try kate.  But all in all I am fairly satisfied with gnome.  Its a total memory hog but I just invested $100 into another 512mb so there is no point in using that as a reason to switch now.[/QUOTE]

You could try out rox-filer as well. It doesn't support $VARIABLES either, but if you hit / you get a little entrybox at the bottom which you can use to browse through your filesystem _very_ fast. As for GNOME being a memory (or better: a ressource) hog, I think this is being worked on by the GNOME devs at the moment and has high priority. And honestly I don't think KDE is better on your ressources than GNOME... If that really matters try XFCE instead.

---

