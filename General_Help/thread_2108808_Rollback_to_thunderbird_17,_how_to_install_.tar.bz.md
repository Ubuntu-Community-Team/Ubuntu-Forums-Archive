---
title: "Rollback to thunderbird 17, how to install .tar.bz2"
date: 2013-01-25
forum: General Help
---

### Post by TaylorHolmes on 2013-01-25
Hello,

I'm new to Ubuntu 12.04 (with Unity) on a 64-bit machine.

I'm attempting to *down*grade my thunderbird installation from 18 to 17, since the ever-so-popular Lightning extension is not compatible with 18.

I've already uninstalled thunderbird 18.

Ordinarily, I would install software via Ubuntu Software Center, Synaptic, or using apt-get.  But since I'm trying to NOT install the latest release of TB, I have to do things a bit more manually.

I downloaded TB17 from 
[http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/17.0.2/linux-i686/en-US/thunderbird-17.0.2.tar.bz2]("http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/17.0.2/linux-i686/en-US/thunderbird-17.0.2.tar.bz2")

Keep in mind, this downloaded folder of files does NOT contain a compilable source file, so compiling it from source isn't an option.

I extracted the tar.bz2 into a new folder named "thunderbird" in /home/username/, as this tutorial explained:

[https://support.mozillamessaging.com/en-US/kb/installing-thunderbird-linux#w_unpacking-the-thunderbird-archive](https://support.mozillamessaging.com/en-US/kb/installing-thunderbird-linux#w_unpacking-the-thunderbird-archive)

(scroll down to "Unpacking the Thunderbird archive")

I'm stuck at the end of "Unpacking the Thunderbird archive".  This tutorial assumes I'm using GNOME, but I'm not.  I'm using Unity.  Now that I have this folder full of stuff, I'm not sure what to do from there.

When I extract the tar.bz2 and use terminal to do the following

```

>cd home/username/thunderbird
>ls
```

which spits out the following:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230646&stc=1&d=1359146135[/IMG]

At this point, I'm not sure What's left for me to do to get this running.  Any suggestions?

---

### Post by windscape on 2013-01-25
Hi,

Try running it using ```
./thunderbird
```

---

### Post by TaylorHolmes on 2013-01-25
> **windscape said:**
> Hi,

Try running it using ```
./thunderbird
```

Doing that spits out

```
solderblob@TaylorDesktop:~/thunderbird$ ./thunderbird
XPCOMGlueLoad error for file /home/solderblob/thunderbird/libxpcom.so:
libxul.so: cannot open shared object file: No such file or directory
Couldn't load XPCOM.

```

---

### Post by windscape on 2013-01-25
Hi,

Looks like the better script to run it is ```
./run-mozilla.sh
```

---

### Post by TaylorHolmes on 2013-01-25
> **windscape said:**
> Hi,

Looks like the better script to run it is ```
./run-mozilla.sh
```

Running that in either directory:

```

solderblob@TaylorDesktop:~/thunderbird$ ./run-mozilla.sh

run-mozilla.sh: Cannot execute .

solderblob@TaylorDesktop:~/thunderbird$ cd ~
solderblob@TaylorDesktop:~$ ./run-mozilla.sh
bash: ./run-mozilla.sh: No such file or directory
solderblob@TaylorDesktop:~$ 


```

---

### Post by gifford on 2013-01-25
I'm running 12.04 and my thunderbird is at 17.0.2. How did you get to version 18?

Both synaptic and the software center only list 17.0.2 for me. Are you using an external PPA?

---

### Post by TaylorHolmes on 2013-01-25
> **gifford said:**
> I'm running 12.04 and my thunderbird is at 17.0.2. How did you get to version 18?

Both synaptic and the software center only list 17.0.2 for me. Are you using an external PPA?

Really?  Wow, I don't know WHAT the HELL is going on, ....

When I look at Synaptic or Ubuntu Software Center, all I see is TB18!!! All over the place!  What do you mean by "external PPA"?  
Whatever it is, that may be the solution.

---

### Post by gifford on 2013-01-25
Did the initial install come from Ubuntu when you set up your system? If you added a PPA from Ubuntu Tweak or some other source, that would be what I consider an external PPA. You can check your PPA's for mozilla thunderbird. If there is, you have added the PPA somehow. Disable it and run sudo-apt-get update and check then check software center or synaptic to see if 17.0.2 is now listed.

---

### Post by TaylorHolmes on 2013-01-25
OK, I'm not sure what PPAs are, but here's a head-scratcher.

There appear to be (at least) two completely separate launchpads for thunderbird.  

[https://launchpad.net/thunderbird](https://launchpad.net/thunderbird)
[https://launchpad.net/~mozillateam/+archive/thunderbird-next](https://launchpad.net/~mozillateam/+archive/thunderbird-next)
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

I don't know what any of this means.  I'm also confused as to why my USC and Synaptec think the latest version of Thunderbird is 18, not 17.

I'd LOVE for someone to explain to me how to figure out which "PPA" I have, and how to change it.

---

### Post by TaylorHolmes on 2013-01-25
OK, I went into USC -> Edit -> Software Sources -> Other Software, and here's the list attached to this comment post.

I'm guessing that I need to get rid of the "next" PPAs and change them to "Stable" PPAs?

---

### Post by TaylorHolmes on 2013-01-25
OK so I changed the PPAs to the "Stable" ones.  USC now shows Thunderbird 17.0.2, as promised.  

I then ran sudo apt-get update, which spat out this:

```
W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
```


And now that I think about it, I've seen this message before.  Ubuntu Update Manager kept harassing me about these 404ing, so I decided to do... something, I can't remember what I did.  I guess I must have switched PPAs.

Now I've got to figure out why these PPAs are 404ing.

---

### Post by gifford on 2013-01-25
The PPA's that list thunderbird next are the ones to uncheck and disable. They are the ones that give you version 18. Yes, stable should give you 17.0.2.

---

### Post by gifford on 2013-01-25
I actually do not have any mozilla PPA's in synaptic at all. You could try disabling all of the mozilla thunderbird PPA's, run sudo apt-get update, and then see if synaptic list the correct version of Thunderbird and try to install.

---

### Post by TaylorHolmes on 2013-01-25
Well, the solution was to get rid of ANY and ALL thunderbird PPAs through Synaptic, then install thunderbird via either Synaptic or Ubuntu Software Center.

---

### Post by gifford on 2013-01-25
Glad it worked for you.

---

