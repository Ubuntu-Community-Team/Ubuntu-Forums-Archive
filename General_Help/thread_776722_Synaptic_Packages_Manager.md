---
title: "Synaptic Packages Manager"
date: 2008-04-30
forum: General Help
---

### Post by Ken28 on 2008-04-30
When I try to access the package manager this is the error I recieve. I am really new to Linux someone please help.

E: Type '--23:56:18--' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Monicker on 2008-04-30
Looks like you might have some bad info in winehq.list.

Were you following these instructions?

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

### Post by Ken28 on 2008-04-30
Yes and now I get errors on anything dealing with a repository. Did I screw something up?

---

### Post by Ken28 on 2008-04-30
I guess I need to mention that I am a new Linux user and I was trying to Dl Wine to Mint 4.0 so that I can use World Of Warcraft on Linux and cant seem to get it right. spoke with a few people that say Wine is pre loaded in Mint but I have not found it so far.. im a class a newbie and need soemone to really hold my hand ha ha.. I have no clue anymore

---

### Post by Monicker on 2008-04-30
> **Ken28 said:**
> Yes and now I get errors on anything dealing with a repository. Did I screw something up?

Hrmm. I just downloaded the file myself, and I don't see anything unusual about it.

This is what I see:

```
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
#deb-src http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
```


Looks normal.  You could edit yours to match that.
```

sudo -S gedit /etc/apt/sources.list.d/winehq.list
```

---

### Post by Ken28 on 2008-04-30
k heres the part where I sound stupid I have never used Terminal in my life and have no clue other than to copy and pste or simple commands. I do appoligize in advance for any headaches I bring on

---

### Post by Monicker on 2008-04-30
> **Ken28 said:**
> k heres the part where I sound stupid I have never used Terminal in my life and have no clue other than to copy and pste or simple commands. I do appoligize in advance for any headaches I bring on

Not a problem.  From the gui you can do this key combo: ALT + F2

That will bring up a box where you can enter a slightly different command:

```
gksudo gedit /etc/apt/sources.list.d/winehq.list
```


Then you can edit the file and save the changes.

---

### Post by Ken28 on 2008-04-30
k when I go to edit this is waht I see 

--23:56:18--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `gutsy.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

    0K                                                       100%   40.25 MB/s

23:56:18 (40.25 MB/s) - `gutsy.list' saved [181/181]

Where do I edit to put the code you provided?

---

### Post by Monicker on 2008-04-30
> **Ken28 said:**
> k when I go to edit this is waht I see 

--23:56:18--  [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list)
           => `gutsy.list'
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 181 [text/plain]

    0K                                                       100%   40.25 MB/s

23:56:18 (40.25 MB/s) - `gutsy.list' saved [181/181]

Where do I edit to put the code you provided?

Are you running Gutsy Gibbon or Hardy Heron?  The first file you had was for Hardy, but that last one is for Gutsy.

---

### Post by Ken28 on 2008-04-30
Well when I clean on Help and about Firefox it says Gutsy.. all I know is Mint 4.0 Daryna. Recomended by a few people who said it was easiest for new users like myself

---

### Post by Monicker on 2008-04-30
> **Ken28 said:**
> Well when I clean on Help and about Firefox it says Gutsy.. all I know is Mint 4.0 Daryna. Recomended by a few people who said it was easiest for new users like myself

Okay. Before you change anything, please post the contents of that gutsy.list file here.

---

### Post by Ken28 on 2008-04-30
again with me sounding stupid but havent figured out how to diplay files yet .. How do I get info you request?

---

### Post by Monicker on 2008-04-30
> **Ken28 said:**
> again with me sounding stupid but havent figured out how to diplay files yet .. How do I get info you request?

I don't know the layout of Linux Mint.  You should be able to open your text editor and navigate to the gutsy.list file and open it.  Then you can copy/paste the contents.

or from a terminal you can go to the directory where you saved the file and do "gedit gutsy.list"

---

### Post by Ken28 on 2008-04-30
I dont have anything inside gutsy.list unless I am looking in the wrong place. I take it theres no remote access with linux that I can get from someone like in windows lol. I am just afraid that I dl wrong and ended up messing it up and theres no restore point in ths OS :o(

---

### Post by Monicker on 2008-04-30
> **Ken28 said:**
> I dont have anything inside gutsy.list unless I am looking in the wrong place. I take it theres no remote access with linux that I can get from someone like in windows lol. I am just afraid that I dl wrong and ended up messing it up and theres no restore point in ths OS :o(

Well, I have no idea which directory you downloaded the file to.  :)


Of course there are ways to do remote access, but you should be extremely careful about granting such access.

Check around and see where you might have put the file.  Does Linux Mint have Places at the top menu, if so there should a search option there that you can use to find the file; have it search "File System".

---

### Post by Ken28 on 2008-04-30
When I typed in the commands last night I did them in the dir that comes up when you start a terminal. So since I loaded this off of an ISO disc should I just re install to fix anything that I may have done wrong or is there a way of going default on an OS like this? Nothing shows up when I search for Gutsy.list

---

### Post by Monicker on 2008-05-01
> **Ken28 said:**
> When I typed in the commands last night I did them in the dir that comes up when you start a terminal. So since I loaded this off of an ISO disc should I just re install to fix anything that I may have done wrong or is there a way of going default on an OS like this? Nothing shows up when I search for Gutsy.list

Just remove the hardy.list and gutsy.list files, and do a Reload from Synaptic.

Remember, files are case sensitive in linux.  "Gutsy" and "gutsy" are 2 different things.

---

