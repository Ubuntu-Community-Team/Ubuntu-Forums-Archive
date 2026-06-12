---
title: "Using rsync, tying myself in a knot I fear"
date: 2007-12-10
forum: General Help
---

### Post by Cadmus on 2007-12-10
I've just started messing around with rsync, but it's not quite behaving as I expected.

The Scenario:
[list]
[*]I have a big server which holds disc images of computers we use
[*]Some of our people are homeworkers, so it'd be useful to keep these images on a laptop too
[*]In case images change I'd like to use rsync so when I take the laptop out I'm happy I have the latest copies of everything
[/list]

Initially I found that doing ```
rsync --progress cadmus@server:/home/cadmus/images/* ~/images
``` on the laptop was causing it copy over everything, so I added a -t flag and all seemed well.

This solution somehow didn't feel right, so I tried using -c instead to stop rsync copying everything, but this seemed to slow the process down a lot when it was checking the files, is this because the files I'm working with are large (1-3GB) and calculating the checksums takes a while?

Anyway, I removed the -c flag and it all seemed to be working, not downloading files that hadn't changed. Then I tried touch-ing one of the files on the server and now that file is always downloaded. Shouldn't it stop after it's done that once?

If someone can show me where I'm going wrong here it would be grand. Still getting to grips with *nix remote functions.

---

### Post by mahousaru on 2007-12-10
Have you considered using unison?  I believe it uses rsync to do the err syncing, but it will display a results window asking you what you want to do.  It is great for small directory structures, but big ones (ie my 2 GBs of office docs) can make it bottom out.

---

### Post by Cadmus on 2007-12-10
I'll take a look into unison, thanks, I suppose what I really need is 'rsync logic for dummies' to help me get a handle on why it's repeating these files.

In other news I found the solution to another problem I was having with rsync and argument lists being too long :)

---

### Post by Aikon- on 2007-12-10
The "too-long argument list" is probably because you are using the * at the end of your directory listing.

rsync can take in just a folder and will copy the contents on its own, i.e. you don't need to pass the * at the end of the path, just end it with "images/" and you should be good to go.

---

### Post by Cadmus on 2007-12-10
> **Aikon- said:**
> The "too-long argument list" is probably because you are using the * at the end of your directory listing.

Got it in one, but that was a different problem on a different machine, thanks though :)

To get back to my original post could the problem be related to a time difference between the two machines? For various reasons the two computers don't get much in the way of internet connectivity and it's doubtful they're synchronised down to the second. I'm going to try using the --modify-window option with a suitably long opening and seeing if that makes it work.

---

### Post by Cadmus on 2007-12-10
Hmm, been taking a longer look at this and I may well have seen a problem where there was none. At the end it's giving a speedup factor of over 1000 but that includes two larger files which are behaving. How long would you say is reasonable for a copy of a single file over aprox 700M across a 100M lan? If the answer is more than 60 seconds I might have been mistaking rsyncs checking for copying.

---

### Post by psusi on 2007-12-10
It would take at LEAST 60 seconds to copy 700 mb over fast ethernet.  Usual results are about double that though.

---

### Post by fjgaude on 2007-12-10
You might install grsync, with its gui it's easy to see what should be done in each situation... it too of course uses rsync but you don't have to remember the various options. I also use unison to my laptop, but use only grsync to my main boxes... handling about 25 Gigabytes at a time. No problems.

Both programs can be obtained with Synaptic in the Ubuntu repos.

---

### Post by Cadmus on 2007-12-11
Took a bit more of a dive into google this morning and found the problem, it seems that for what I want (where I know that changes will only ever occur on the server) I should be using the -u flag. Thanks for all your help people.

I'll have to look up grsync when I have a machine where I'm not using just the command line version for sakes of space.

---

