---
title: "Search for Documents?  Google in XP Desktop"
date: 2006-11-25
forum: General Help
---

### Post by shane2peru on 2006-11-25
In Windows I had a nice feature that I found myself often using.  It was not actually a Windows feature, but Google Desktop.  I could type a few words and search my whole desktop and find the document I needed.  It would even search inside of OpenOffice documents (with the appropriate plugin) and find any document that was contained the word 'apple'  for example.  I do a loooooooot of work in OpenOffice, and write preaching outlines in OpenOffice weekly.   I need to be able to go back and find an outline that I used a scripture reference in the past.  Is there any search program that will look inside my Open Office documents and find text inside the document?  Thanks in advance.

Shane

---

### Post by Ramses de Norre on 2006-11-25
Check out the grep man page, I'm pretty sure grep can do what you want. But it's cli so you might need to get accustomed to it.

---

### Post by shane2peru on 2006-11-25
Thanks for the quick reply!  I have read about these man pages before, but don't know where they are or how to find them.  Thanks for the help.  I don't mind command line things.  Thanks.

Shane

---

### Post by Ramses de Norre on 2006-11-25
To view a program's man page you just type "**man program**" in terminal, so for grep: **man grep**.

---

### Post by shane2peru on 2006-11-25
Ok, thanks!

Shane

---

### Post by shane2peru on 2006-11-25
how do I get back out of that man page and back to the console?

Shane

**Edit:  **If I'm not mistaken this man page is the same as grep --help.

---

### Post by ButteBlues on 2006-11-25
shane - If you want a Google Desktop-esque search platform, grep is not what you want.


If you've got your extra repositores enabled, type the following command in a terminal:

```
sudo aptitude install beagle
```

Alternatively, you can open Synaptic and search for "beagle" and install it that way.

This will install the beagle back-end as well as beagle-search, a front-end GUI for accessing beagle.



For more information on what Beagle is and how it works, you can read their site, [here](http://beagle-project.org/Main_Page).

---

### Post by kosmic on 2006-11-25
Or you can try "tracker" is better than Beagle, less power hungry than beagle and the mono libraries :)

More info here - [http://jamiemcc.livejournal.com/5630.html?view=56830](http://jamiemcc.livejournal.com/5630.html?view=56830)

---

### Post by shane2peru on 2006-11-25
> **a simple façade said:**
> shane - If you want a Google Desktop-esque search platform, grep is not what you want.


If you've got your extra repositores enabled, type the following command in a terminal:

```
sudo aptitude install beagle
```Alternatively, you can open Synaptic and search for "beagle" and install it that way.

This will install the beagle back-end as well as beagle-search, a front-end GUI for accessing beagle.



For more information on what Beagle is and how it works, you can read their site, [here]("http://beagle-project.org/Main_Page").
   I have beagle, and have tried it.  It doesn't search inside the Open Office Documents, unless I'm missing something.  I also found a 1GB log file inside Beagle's directory once, and deleted it!  1 GB - I don't have that kind of space to use for a log.  Is there a way to search inside Open Office .odt files?  Thanks.

Shane

---

### Post by ButteBlues on 2006-11-25
> **kosmic said:**
> Or you can try "tracker" is better than Beagle, less power hungry than beagle and the mono libraries :)

More info here - [http://jamiemcc.livejournal.com/5630.html?view=56830](http://jamiemcc.livejournal.com/5630.html?view=56830)
"Better" is immensely subjective. While Tracker is arguably lighter, and claims to be faster, anyone who's running 512 MB or more of RAM won't notice any difference to begin with. Furthermore, a project that is farther along in development, supports more types of files, has more features, and has a nice API seems far "better", in my opinion, than a fledgling attempt at it.


Shane:

1. Yes, beagle uses indexes. So does Google Desktop. So does Tracker. What it all boils down to is a 1 GB index isn't much, really. Furthermore, you can always disable the indexing of all but a few things (such as your folder with the OpenOffice documents in it).

2. Beagle does work with the contents of OpenOffice documents. Or at least it always has for me. Perhaps you simply aren't letting it index them before trying to search them. Run the following and wait maybe 15 to 20 minutes depending on the size of your home folder for beagle to index everything rather quickly:

```
beagle-shutdown
rm ~/.beagle -R
export EXERCISE_THE_DOG=1
beagled
```

---

### Post by shane2peru on 2006-11-25
> **kosmic said:**
> Or you can try "tracker" is better than Beagle, less power hungry than beagle and the mono libraries :)

More info here - [http://jamiemcc.livejournal.com/5630.html?view=56830](http://jamiemcc.livejournal.com/5630.html?view=56830)
Tracker is not in the repos, at least not in mine.  Thanks.

Shane

---

### Post by kosmic on 2006-11-25
Ok, I admit "better"  was not the best term to use :(.

But beagle with me sometimes uses my CPU at 100% and wont go down :(, instead i have 0(zero) problems with Tracker.

Also tracker doesn't depend of the mono libraries, and beagle for me in the same system seems more slower and bloated than tracker.

---

### Post by kosmic on 2006-11-25
> **shane2peru said:**
> Tracker is not in the repos, at least not in mine.  Thanks.

Shane

yes tracker is not in the repos, if you want to install tracker go to the page I gave you, and download the debs of tracker from there

---

### Post by ButteBlues on 2006-11-25
As a matter of interest, below is a link to a screenshot that demonstrates that OpenOffice format documents are indeed indexed by beagle.

(Much apologies that Image Socket scales it down)

[http://imagesocket.com/view/beagle_odtworks75a.png](http://imagesocket.com/view/beagle_odtworks75a.png)

---

### Post by ButteBlues on 2006-11-25
> **kosmic said:**
> Ok, I admit "better"  was not the best term to use :(.

No worries.

> But beagle with me sometimes uses my CPU at 100% and wont go down :(, instead i have 0(zero) problems with Tracker.

I've never experienced that particular error myself. If you ran the beagle with EXERCISE_THE_DOG, it would use your CPU a lot in the beginning, as that particular variable tells it to go gung-ho on the indexing. Regularly, it merely indexes during idle time.

> Also tracker doesn't depend of the mono libraries,

Which is a moot point anymore, as now that Tomboy is default in GNOME, the Mono libraries are included anyways. ;)

> and beagle for me in the same system seems more slower and bloated than tracker.

Use whatever works best for you.

---

### Post by shane2peru on 2006-11-25
I guess I didn't have beagle installed.  I installed it via synaptic, because I like the idea of having the gui, however I can't find the gui now.:-k  It actually wasn´t the index file that was 1 GB, it was a log.  I don't know why either, I only have 4 GB for my /home, so 1/4th of my drive, is quite odd.  I will write if off could have been an error, or rare occurance, and give it another go.  How do I gui?  I'm ok at cli, and prefer cli for apt, but I'm still slightly gui dependent.

Shane

---

### Post by ButteBlues on 2006-11-25
The GUI is "beagle-search". (The GUI in my clip is actually the new Kerry 0.2, which is a KDE front-end for Beagle, so my screenshot will look a bit different from what you'll see)

Once the beagle daemon (beagled and beagle-helper processes) are running, it should begin indexing immediately. By pressing Alt+F2, you can run "beagle-search" to bring up the GUI. If you set in Preferences to begin indexing automatically, then from now on, you should have a search tray icon that'll start with your session which when clicked will bring up the beagle GUI.

---

### Post by kosmic on 2006-11-25
> **a simple façade said:**
> No worries.



I've never experienced that particular error myself. If you ran the beagle with EXERCISE_THE_DOG, it would use your CPU a lot in the beginning, as that particular variable tells it to go gung-ho on the indexing. Regularly, it merely indexes during idle time.



Which is a moot point anymore, as now that Tomboy is default in GNOME, the Mono libraries are included anyways. ;)



Use whatever works best for you.

Yes I have to admit I love Beagle, but the problem with the 100% cpu usage, turn me to "tracker", also You are right the mono libraries are installed by default in ubuntu so it is a moot point as you said.

But in the end is a matter of taste ;)

---

### Post by ButteBlues on 2006-11-25
> **kosmic said:**
> Yes I have to admit I love Beagle, but the problem with the 100% cpu usage, turn me to "tracker", also You are right the mono libraries are installed by default in ubuntu so it is a moot point as you said.

But in the end is a matter of taste ;)
Pretty much. As long as it works for you, what's the difference? It's all about choice anyways.

---

### Post by shane2peru on 2006-11-25
> **kosmic said:**
> 
But beagle with me sometimes uses my CPU at 100% and wont go down :(, instead i have 0(zero) problems with Tracker.

I have found some programs do that to my computer too.  I have found that Gdesklets did that to mine, so I had to switch to adesklets.  For no reason, just jumps the cpu to 100%.  It is really annoying.  I will check out Tracker too, if it isn't too dificult to install.  I'm still using Dapper, I noticed they mentioned Edgy.  What deb do I download?  Thanks.

Shane

---

### Post by shane2peru on 2006-11-25
> **a simple façade said:**
> The GUI is "beagle-search". (The GUI in my clip is actually the new Kerry 0.2, which is a KDE front-end for Beagle, so my screenshot will look a bit different from what you'll see)

Once the beagle daemon (beagled and beagle-helper processes) are running, it should begin indexing immediately. By pressing Alt+F2, you can run "beagle-search" to bring up the GUI. If you set in Preferences to begin indexing automatically, then from now on, you should have a search tray icon that'll start with your session which when clicked will bring up the beagle GUI.

Ok, got it!  Thanks! 
Shane

---

### Post by Nonno Bassotto on 2006-11-26
> **shane2peru said:**
> I also found a 1GB log file inside Beagle's directory once, and deleted it!  1 GB - I don't have that kind of space to use for a log.

I dual boot between windows and ubuntu. Currently my Google Desktop folder is 695,3 MB while beagle is 414,4 MB (they index the same directories). Check out how much space Google Desktop uses under
```

C:\Documents and Settings\YourUsername\Local Settings\Application Data\Google\Google Desktop

```

---

### Post by john_markh on 2006-12-13
I use beagle and it does the job (perfectly).
No issue with 100% CPU or OpenOffice documents. Also, it has nice integration with Evolution (a bonus, you might say...).
:)

---

### Post by xpan on 2006-12-16
Can any of the two search into the contents of other types of documents? (e.g. ps, pdf, tar, etc)

In windows I used X1 which rocked!

---

### Post by ButteBlues on 2006-12-16
> **xpan said:**
> Can any of the two search into the contents of other types of documents? (e.g. ps, pdf, tar, etc)

In windows I used X1 which rocked!
You could probably find such info at [www.beagle-project.org](www.beagle-project.org)

---

### Post by shane2peru on 2006-12-16
Ok, I have tracker and beagle.  It took a bit to get tracker installed, and frankly I'm un-impressed with it's search ability.  I have tried to find documentation on how to correctly use it and was unable.  I would like to do a search on multiple words like 'apples and oranges' and it looks up every word individually.  Not my cup of tea.  I often need to search for Bible references in my documents "John 3:10"  and need to only find that phrase.  Beagle does that for me.  I set a bi-monthly cron job to delete my log files from Beagle incase it gets to large.  I think somehow Beagle got stuck in a search cycle and wrote logs all night.  Mind you I am talking about a super large log file, not index file.  There is a difference between the two.  My index is/was not the problem.  Thanks for all the posts.

Shane

---

