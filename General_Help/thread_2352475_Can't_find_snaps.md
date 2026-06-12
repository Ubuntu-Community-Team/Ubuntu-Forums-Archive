---
title: "Can't find snaps"
date: 2017-02-12
forum: General Help
---

### Post by aa4bb on 2017-02-12
I'm just now trying out snaps. I see 681 snaps listed in uappexplorer.

Following an example, I was able to install and run "hello-world". However...

I thought issuing "snap find" in terminal would show me all the available snaps in the snaps store. But it only returns two, docker and lxd.

Issuing "snap find [specific appname]" returned 0 snaps, where specific appname was listed in uappexplorer,

What might I be missing here?

---

### Post by Geoffrey_Arndt on 2017-02-12
Try this place:   [https://uappexplorer.com/](https://uappexplorer.com/)

Edit:   I didn't read your post well enough . . . . so I see you're already familiar with this site.   But sorry, I can't answer why the snap find command returns no finds. 

  Perhaps another source repo needs to be added ??    But why mess with the CLI  as the website install method seems easy??

---

### Post by howefield on 2017-02-13
> **aa4bb said:**
> I thought issuing "snap find" in terminal would show me all the available snaps in the snaps store. But it only returns two, docker and lxd.

It used to list all snaps but that changed some time ago. For me snap find returns 4 snaps, not sure why those 4 and not others. Shrug.

This [link]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1609368") might help with the why.

> Issuing "snap find [specific appname]" returned 0 snaps, where specific appname was listed in uappexplorer, What might I be missing here?

Try 

```
snap find .
```

Does that give you more ?

---

### Post by vasa1 on 2017-02-13
> **howefield said:**
> ...

Try 

```
snap find .
```

Does that give you more ?
That gives me a lot more!

Just ```
snap find
``` gives me four as well:```
$ snap find
Name               Version   Developer   Notes  Summary
docker             1.11.2-9  docker-inc  -      The docker app deployment mechanism
lxd                2.8       canonical   -      LXD - the container lightervisor
mongo32            3.2.7     niemeyer    -      MongoDB document-oriented database
rocketchat-server  0.51.0    rocketchat  -      Group chat server for 100s,  installed in seconds.
```

Re. > **howefield said:**
> ...
This [link]("https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1609368") might help with the why.
...
And a friendlier explanation is here: [http://www.omgubuntu.co.uk/2016/08/command-sudo-snap-find-error-not-a-bug](http://www.omgubuntu.co.uk/2016/08/command-sudo-snap-find-error-not-a-bug)

---

### Post by aa4bb on 2017-02-13
Thank you all very much. The omgubuntu.co.uk explanation gave me a lot of insight. 

I had searched various resources, over several hours, before posting this question. I think that snaps may turn out to be a great addition, but the documentation is a little slow catching up. Once I learn more, I'll see if there's a way I can help with that.

---

