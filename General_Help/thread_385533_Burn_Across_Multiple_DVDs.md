---
title: "Burn Across Multiple DVDs"
date: 2007-03-15
forum: General Help
---

### Post by Adler on 2007-03-15
Hi All,

I'm trying to burn my complete 45GB music collection. But, can't seem to find the way to "span" multiple DVDs to do the job.

Any help?

Adler

---

### Post by bruenig on 2007-03-15
just burn it 4.7 gigs at a time

---

### Post by Adler on 2007-03-15
bruenig,

Thanks, but that is not the solution. I can do dual-layer DVD burns @ 8.5 gigs at a time, but want to burn across multiple disks.

Adler

---

### Post by bruenig on 2007-03-15
What do you mean burn across multiple disks? All burning across multiple disks will do is split up the files and put however much on each disk. That is no different than what I am saying to do.

---

### Post by Adler on 2007-03-16
bruenig,

We are probably talking the same language, but I wasn't clear enough. 

I use K3B, and not Gnome Baker. If I try to burn a file bigger than the disc size it will not allow me to burn.

I would prefer not to try to pull about the files to meet the size of the disc, but "span" across multiple disks all at once. I did do this years ago, but I was running M$, and forgot the name of the s/w that I used.

Adler

---

### Post by Adler on 2007-04-06
Bump

Adler

---

### Post by qpwoeiruty on 2007-04-06
Have you tried [multiCD](http://danborn.net/multiCD/)?
It's in the repositories too: sudo apt-get install multicd

---

### Post by Adler on 2007-04-06
qpwoeiruty,

Thanks for that!

I've got about 55GB of .mp3 music, and want to burn it to Disk(s).

I'd quickly hit the Site that you mentioned, and didn't see a (gtk)interface. I'm sure that I could run it in terminal, but how would this interface with my preferred burner K3B?

Thanks again!

Adler

---

### Post by gurgle on 2007-04-07
I would like to know this as well. Something like how Mac OS X handles it. When it needs a new disc it just pops out the old one and has you put in anotther disc.

---

### Post by qpwoeiruty on 2007-04-09
I honestly don't know.

The best I can think of ATM is to make a single directory with all your music, copy the default .multicdrc into your home directory, and configure it to make ISOs and pass it to k3b to do the burning...

Create an empty .exclude_list in your home directory, then the code to split+burn:

```
ls /path/to/files > /home/$(whoami)/.include_list; /path/to/multicd --files_list /home/$(whoami)/.include_list --cd_size 8G --maxfile_size 1G --image_file1 /var/tmp/multicd_image1 --image_mount /var/tmp/multicd_image_mount --fs_type ext2 --cdrecord "k3b --dvdimage" --mkfs_opts "-m 0 -q -F -b 2048" --exclude_list /home/$(whoami)/.exclude_list
```

Replace /path/to/files with the path to your mp3s and /path/to/multicd to wherever you put the multicd script

You can make a desktop launcher of it if you'd like or have it ask the path you want to backup each time (with a minor change). If KDE's desktop is like Gnome, make sure Terminal=true in the .desktop file

gurgle: multicd burns with cdrecord by default. It just pops out the disc and waits for the next one.
You can watch progress in the command line by: 
multicd 2> err
tail -f err

---

### Post by Adler on 2007-04-09
qpwoeiruty,

Thanks for that. I'll give it a try later this week. 

Seems like you put your mind to this. Thanks.

Adler

---

### Post by qpwoeiruty on 2007-04-10
> **Adler said:**
> qpwoeiruty,

Thanks for that. I'll give it a try later this week. 

Seems like you put your mind to this. Thanks.

Adler

No problem, but be sure to get the new version. I accidentally had an extra > in the code. Good luck!

---

### Post by Adler on 2007-04-10
qpwoeiruty,

I did the multicd install using apt-get, and went looking for it in my Files, but no luck. I did also try running it as usr, and Root. Root worked, and again I went looking to find a file. No luck. hmm...

As far as I know to get this right I should be looking to edit a script according to the location of my music -- /Home/XXXXXXX/Music -- and add K3B to your script suggestion. But, need to find the app in the first place. LOL

I am assuming that I should be using a text editor for the whole process. At this point, it almost becomes a K3B add-on if you know what I mean. But, I may be running ahead of myself.

Once I got the script edited to burn my 55GB of .mp3s across multiple disks I could do the Icon. 

BTW -- gurgle?

Thanks for your posts.

Adler

---

### Post by Adler on 2007-04-12
qpwoeiruty,

You still out there?

I'm now backing up everything to a Seagate drive.

Still looking to span discs for my .mp3 collection.

Adler

---

### Post by jandrioli on 2008-01-05
the answer is multiCD

[http://danborn.net/multiCD/index.html#desc](http://danborn.net/multiCD/index.html#desc)

no User interface though. dont be scared of the cmd line...

---

### Post by Adler on 2008-01-05
jandrioli,

Thanks for the Link! I've bookmarked it.

Man, this was an old thread!

Thanks for the response.

---

### Post by freerick on 2008-03-30
I would recommend using tar to create an archive that spans multiple volumes. I ran into the same problem trying to archive a VirtualBox image.
This article explains how to do it:

[http://www.cgi-interactive-uk.com/splitting_large_files.html](http://www.cgi-interactive-uk.com/splitting_large_files.html)

--Patrick

:popcorn:

---

### Post by commonplace on 2008-05-30
I'm about to try [DiscSpan]("http://sourceforge.net/projects/discspan") and see how it works. It sounds just like what I'm (and we're) looking for, though!

/Kevin

---

